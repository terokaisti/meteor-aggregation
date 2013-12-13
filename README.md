meteor-aggregation
==================
Aggregation supports for meteor.

### How to Install

    mrt add aggregation
    
### Usage

    People = new Meteor.Collection("people");
    
    if(Meteor.isClient){
    
      // creates pipe
      var pipe = [];
      
      pipe.push({
        $match : {
          favoriteColor : {
            $exists : 1
          }
        }
      });
      
      pipe.push({
        $group : {
          _id : "favoriteColor",
          count : {
            $sum : 1
          }
        }
      });
    
      // excute aggregation (It can be called in only client side)
      People.aggregate(pipe, function(err, docs){
        if(docs){
          Session.set("result", docs);
        }
      });
    }

### Demo

* [Demo](http://aggr-example.meteor.com)
* [Source](https://github.com/jeeeyul/meteor-aggregation/tree/master/example)

### Warning

This project is very experimental. I'm just testing meteor packaging system.
