# AlexaSkill
Custom skill for Amazon Echo.

Lambda Fubction:
arn:aws:lambda:eu-central-1:516519832899:function:alexa-test

ireland: arn:aws:lambda:eu-west-1:516519832899:function:alexa-test


Facebook App
  - Name:Happening
  - Token: 	
1006558219476497|9O_KoW925DzfKWa8nJjl1xpGo6g


Node Plugins in use:
  - alexa-sdk   found at: https://github.com/alexa/alexa-skills-kit-sdk-for-nodejs
  - facebook-events-by-location   found at: https://github.com/tobilg/facebook-events-by-location

To start Facebook Events Server:
 $cd node_modules/facebook-events-by-location/
 $node index.js

 - example API call: http://localhost:3000/events?lat=40.710803&lng=-73.964040&distance=100&sort=venue&accessToken=1006558219476497|9O_KoW925DzfKWa8nJjl1xpGo6g

 Where the 'Token='' is our Fb App Token

server.js
var AlexaAppServer = require('alexa-app-server');

var instance = new AlexaAppServer({
  server_root: __dirname,     // Path to root
  public_html: "public_html", // Static content
  app_dir: "apps",            // Location of alexa-app modules
  app_root: "/alexa/",        // Service root
  port: 8080                  // Port to use
});

instance.start();
instance.express.use('/test', function(req, res) { res.send("OK"); });