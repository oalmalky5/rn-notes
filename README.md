# rn-notes

## Reducer 

import ```{useReducer}``` insted of ```{useState}```

```const [state, dispatch] = useReducer(reducer, //this second argement is the initial state value that we want) ``` 

after setting the ```useReducer``` method, we need need to define our reducer function 

```const reducer = (state, acttion) => {} ```

it is better if you define the reducer function outside of the component that has the ```useReducer``` method 
the first arguement is ```state``` and the second arguuement is the update or the change that  we want to happen to our intial state
and it's generaly called ```action```  

``` 
     // state === {red: number, green: number, blue: number}
     // action === {colorToChange: 'red' || 'green' || 'blue', amounnt: 15 || -15   }


```

the ```action``` is whatToChange  
and it also takes the amount that we want to change by

one important thing is that we never change the first arguement ```state``` directly   
so we never do 
``` state.somehting = something ```

if we want to change a property inside the state object
we want to rebuild that entire state object from scratch woth changes that we want 
```{...state, red: state.red + action.amount}```
 
```...state``` here we are taking all the existing proprites out of our state object.
then we overwtire the existing proprites with what we want 
this will allow us to not make any changes directly to the intital ```state```  


```dispatch``` is responsible for running the reducer and making changes 


communinty connvinction is that ```action```  takes the proprities 
```type``` which means ```thingToChange```  
```payload``` which means  ```amount to change by``` 

this is up to you .. naming the ```action``` proprites is completely up to the useer 

# Handling Text input in RN

for showing a text input we user the ```TextInput``` from the react native library
it has no styles so here is a basic style to make it better 
```
const styles = StyleSheet.create({
    input: {
        margin: 25,
        borderColor: 'black',
        borderWidth: 1
    }
}) 
```

```autoCapitlize = none``` prop prevents android or ios from captlizing any input given to the textipnut 

```autoCorrect = {false} ``` prevents ios or android from auto correcting the value given to the textipnut

```
const TextScreen = () => {
    const [name, setName] = useState('')
    return <View>
        <Text>Enter Name:</Text>
        <TextInput 
            style={styles.input}
            autoCapitalize="none" 
            autoCorrect={false}
            value={name}
            onChangeText={(newValue) => setName(newValue)}
        />
        <Text>My name is {name}</Text>
    </View>
} 
 
```

everytime there is a text innput your pretty much going to utlilze this pattern 
you will add state variable  
you will add the ```onChangeText``` prop and give it a callback function the accept whatever value you are setting the state to   