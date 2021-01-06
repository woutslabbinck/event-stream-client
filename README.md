# event-stream-client
Emits new or potentially updated members of a TREE collection 

## Install

```
npm install -g @brechtvdv/event-stream-client
```

In order to use it as a library, you can leave out the `-g`.

## How to use it

### Command line

```
event-stream-client --pollingInterval 10000 https://lodi.ilabt.imec.be/coghent/objecten
```

### NodeJS

A small example synchronizing with a TREE node
```javascript
  try {
    let url = "https://lodi.ilabt.imec.be/coghent/objecten";
    let options = {
      "pollingInterval": 5000 // millis
    };
    let eventstreamSync = sync.createReadStream(url, options);
    eventstreamSync.on('data', (data) => {
      console.log(data)
    });
    eventstreamSync.on('end', () => {
      console.log("No more data!")
    });
  } catch (e) {
    console.error(e);
  }
```