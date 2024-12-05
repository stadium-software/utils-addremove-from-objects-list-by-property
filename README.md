# Add Remove Object From Object LIst By Property

A script to check a list for an object by a property of that object and (1) add the object if it is not found or (2) remove the object if it is found. 

# Version 

1.0 Initial

# Global Script Setup
1. Create a Global Script called "AddRemoveFromListByProperty"
2. Add the input parameters below to the Global Script
   1. List
   2. Property
   3. Object
3. Add the output parameter below to the Global Script
   1. Result
4. Drag a *JavaScript* action into the script
5. Add the Javascript below into the JavaScript code property
```javascript
//Stadium Script AddRemove From List of Objects By Property v1.0 https://github.com/stadium-software/utils-addremove-from-objects-list-by-property
let arr = ~.Parameters.Input.List;
let property = ~.Parameters.Input.Property;
let ob = ~.Parameters.Input.Object;
let index = arr.findIndex(item => item[property] === ob[property]);
if (index == -1) {
    arr.push(ob);
} else {
    arr.splice(index, 1);
}
return arr;
```
6. Drag a *SetValue* action into the Global Script and place it under the *JavaScript* action
   1. Target: = ~.Parameters.Output.Result
   2. Value: = ~.Javascript

## Usage
1. Drag the script called "AddRemoveFromListByProperty" into a script or event handler
2. Enter values for the script input parameters
   1. List: A List of objects, for example:
   ```json
   [{"Name": "John","Instrument": "Guitar"},{"Name": "Paul","Instrument": "Bass"},{"Name": "Ringo","Instrument": "Drums"},{"Name": "George","Instrument": "Guitar"}]
   ```
   2. Property: The name of the property by which the list will be searched (e.g. Name)
   3. Object: The value the property to locate
   ```json
   {"Name": "George","Instrument": "Guitar"}
   ```
3. Result: The script returns the list of objects with or without the provided object