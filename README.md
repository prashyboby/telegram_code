# telegram_code
Telegram bot and code to connect to MongoDB

The idea of this project is to show how to filter useful messages/links/media from any existing Telegram group chat.

Prerequisites : -
  - Create a Bot with appropriate privileges and add the bot to the group chat with admin privileges
  - URL for the webhook of the telegram bot created above
  - A mongoD server running on the local computer
  - Python 3.7 or above installed in the computer
  
The code is a proof of concept to show how to extract URLs with a specific hashtag. The default code looks for hastag "job" in the messages where URLS are forwarded in the groups.

The web_bot_get python server keeps polling on the webhook provided by the telegram bot and keeps fetching the information.
The above fetched information is stripped and selectively forwarded to spark_streamer.py. Spark streamer further does live processing of the messages forwarded to it and puts selected data(URL in case of the checked in code) into a MongoDB database.

In the spark_streamer.py file, the connection to MongoDB client and pushing of URLs into the database are present in the "process" function.

The address and port for MongoDB connection are ('127.0.0.1', 27017) respectively. Make sure you adjust the IP and Port according to your Mongo Server installation in your computer.

The repository has 3 files
 - web_bot_get.py
 - spark_streamer.py
 - PPT which has information about the use case and the flow of data in the project
 
web_bot_get python file predominantly acts as a listener server to the Bot created in the telegram group chat.

Webhook is hardcoded in the code in web_bot_get.py. Modify it to the webhook you create using your own custom bot. Happy "EXTRACTION". 

For any queries contact me @ www.linkedin.com/in/prasanthchakka

