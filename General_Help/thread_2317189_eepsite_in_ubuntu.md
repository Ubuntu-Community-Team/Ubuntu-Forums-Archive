---
title: "eepsite in ubuntu"
date: 2016-03-14
forum: General Help
---

### Post by grace3 on 2016-03-14
Hello,

I have recently installed i2p and am attempting to find the docroot. The docroot should be at ~/.i2p/eepsite/docroot/; however, this was not created. If I surf to [http://127.0.0.1:7658/help/](http://127.0.0.1:7658/help/) I do indeed get the help page. It must be stored in the actual docroot; but I can't find it.

Can anyone help?

Thanks, Grace

---

### Post by QDR06VV9 on 2016-03-14
Hi grace3..
And that file is under: /home/usr/.i2p(where usr is your user name) Witch is a hidden folder in your home directory.
To show hidden folders you can use the keyboard pressing <Ctrl + h> or in your file manager in preferences show hidden files.
And should be able to get the router config page by entering this in the terminal
```
/home/<user>/i2p/runplain.sh
```
Again <user> is your user name.
See if this helps: [URL="http://linuxsecurityblog.com/2015/04/20/setting-up-a-darknet-website-with-i2p-on-ubuntu/"]http://linuxsecurityblog.com/2015/04/20/setting-up-a-darknet-website-with-i2p-on-ubuntu/

The Link above has install instructions and set-up instructions that are pretty straight forward.
Hope this helps






[/URL]

---

### Post by grace3 on 2016-03-14
> **runrickus said:**
> Hi grace3..
And that file is under: /home/usr/.i2p(where usr is your user name) Witch is a hidden folder in your home directory.
To show hidden folders you can use the keyboard pressing <Ctrl + h> or in your file manager in preferences show hidden files.
And should be able to get the router config page by entering this in the terminal
```
/home/<user>/i2p/runplain.sh
```
Again <user> is your user name.
See if this helps: [URL="http://linuxsecurityblog.com/2015/04/20/setting-up-a-darknet-website-with-i2p-on-ubuntu/"]http://linuxsecurityblog.com/2015/04/20/setting-up-a-darknet-website-with-i2p-on-ubuntu/

The Link above has install instructions and set-up instructions that are pretty straight forward.
Hope this helps
[/URL]

That's exactly what I'm saying. That folder was never created during the install; also the code you provided does not run. Yet, I get the help page, which indicates that a server is running.

---

### Post by QDR06VV9 on 2016-03-14
Go to the link I provided and follow the install instructions which will tell you to D-load a jar file for the install wizard, Then save to your home directory, and finally double click that file.
That should get you all the necessary stuff(Files and Folders) to configure.

---

### Post by grace3 on 2016-03-14
> **runrickus said:**
> Go to the link I provided and follow the install instructions which will tell you to D-load a jar file for the install wizard, Then save to your home directory, and finally double click that file.
That should get you all the necessary stuff(Files and Folders) to configure.

Thank you,

This works as expected.

---

### Post by QDR06VV9 on 2016-03-14
[SIZE=3][B]EDIT: Good job grace3 :D Now if you are satisfied would you mind marking the thread solved to aide others.
[/B][/SIZE]
By the way this version of  I2P needs Java 7(or 8) now Java 6 won't function properly..
And there is a lot to learn setting things(Applications) up so patincence is *key*

Connection refused is a clear case of a client trying to connect on a TCP port but not able to succeed. Here are some of the possible reasons why java.net.ConnectException: Connection refused: connect comes:

1) Client and Server, either or both of them are not in the network.
Yes it's possible that they are not connected to LAN or internet or any other network, in that case, Java will throw
"java.net.ConnectException: Connection refused" exception on client side.


2) Server is not running
The second most common reason is the server is down and not running. In that case, also you will get java.net.ConnectException: Connection refused error. What I don't like is that the message it gives, no matter what is the reason it prints the same error. By the way, you can use following networking commands e.g. ping to check if the server is running and listening on the port.


3) The server is running but not listening on the port, a client is trying to connect.
This is another common cause of "java.net.ConnectException: Connection refused", where the server is running but listening on the different port. It&#8217;s hard to figure out this case, until, you think about it and verify the configuration. If you
are working on a large project and have a hierarchical configuration file, Its possible that either default configuration
is taking place or some other settings are overriding your correct setting.


4) Firewall is not permitted for host-port combination
Almost every corporate network is protected by firewalls. If you are connecting to some other companies network e.g. opening an FIX session to the broker, in any Electronic Trading System, then you need to raise firewall
request from both sides to ensure that they permit each other's IP address and port number. If the firewall is not allowing
connection then also you will receive same java.net.ConnectException: Connection refused exception in Java application.


5) Host Port combination is incorrect.
This could be another reason of java.net.ConnectException: Connection refused: connect.It&#8217;s quite possible that either you are providing incorrect host port combination or earlier host port combination has been changed on the server side. Check the latest configuration on both client and server side to avoid connection refused exception.


6) Incorrect protocol in Connection String
TCP is underlying protocol for much high-level protocol including HTTP, RMI and others. While passing connection
string, you need to ensure that you are passing correct protocol, which server is expecting e.g. if server has exposed
its service via RMI than connection string should begin with rmi://

For more Info: 
[https://www.youtube.com/watch?v=gUD40pAV8WE](https://www.youtube.com/watch?v=gUD40pAV8WE)

[https://geti2p.net/en/get-involved/develop/applications](https://geti2p.net/en/get-involved/develop/applications)

---

