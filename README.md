# Viptela-Diagram
This is a Python-Flask based code to generate a diagram of a Cisco SDWAN network (dataplane only) and display the tunnels between the branches. Currently it displays all the tunnels in the same colour (without labelling or differentiation). One future improvement will be labelling and adding different colours to different tunnels. This is only the first development stage. Hence, debug features are turned on.

<img width="715" alt="sdwan" src="https://user-images.githubusercontent.com/31266374/96609909-a860ef80-1318-11eb-9283-e63aa60ac8a6.PNG">


## Use case
As described, this can be used to view the IPsec tunnels created between the branches in a Cisco SDWAN network. *No controllers are displayed*

## Installation

1. This requires Python 3.7+ mainly. Install Python added to path. It is preferred to have a virtualenv created for this project separately. After that following libraries are required.
* Flask, Configparser (optional)
1. You can use 'pip install <library_name>' to install them.

1. Download NextUI js and css files from Cisco devnet (https://d1nmyq4gcgsfi5.cloudfront.net/site/neXt/). NextUI is used to build the UI here. 
1. Use normal folder hierarchy used in a flask project, as explained here (https://flask.palletsprojects.com/en/1.1.x/tutorial/layout
1. You have to put app.js and data.js files in the 'static' folder and viptelaquery.py and app.py in the same directory.
1. Chnage ip address of the server (vmanage), username and password in the getconn.py file.(In the places of IP, username, pwd). *I know that this is not good practise. Need to implement a proper method to store credentials in the future. This is only the first development stage
1. Run getconn.py
1. View from any browser (eg:- http://localhost:5000)

## Configuration

1. The only configuration needs to be done currently is changing ip, username, password as mentioned in the installation step.
*Note: I have put the timeout for a API request as 300s (a big value). This might be required of you are using a VPN connection. Otherwise yuo may bring it down to something like 10s. (default value), as below (in viptelaquery.py)

`response = session.request("GET", url,verify=False,timeout=300)`

## Usage

1. To run, get a terminal/CMD and go to the directory where your project folder lies
1. With virtualenv activated (if one is used only), `Python getconn.py`
1. You would see the Flask server intiated.
1. This has only one web page to display the diagram, view it from a browser (as mentioned in the installation step)

## Testing

This was tested with an actual implementation of a Cisco SDWAN network

## Known Issues

Apart from the lack of credential storing method, if the API calls get delayed too much, the app might throw an unhandled error. But this will be caused due to network latencies such as when connecting through a remote VPN connection to make API requests. Hence, I have put 300s timeout (not recommended, only for testing)

## Getting Involved

You are welome to make improvements to the app via forks or give suggestions and even track/pointout issues.
[CONTRIBUTING](https://github.com/VinuraD/Viptela-Diagram/blob/main/CONTRIBUTING.md)

vinurad@millenniumitesp.com 

## Credits and references

https://github.com/CiscoSE/viptelaquery, Thanks, I used this as the code to make API requests. (I have made some changes to the original code in this project). 

## LICENCE

Please view the LICENCE file
[LICENCE](https://github.com/VinuraD/Viptela-Diagram/blob/main/LICENSE)
