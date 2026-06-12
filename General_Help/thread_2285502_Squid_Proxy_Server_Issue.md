---
title: "Squid Proxy Server Issue"
date: 2015-07-06
forum: General Help
---

### Post by Adam_Collyer on 2015-07-06
Hi, not sure if this is the right place for this but I'm losing hope of getting this issue solved. 

So, the main thing of my issue is I'm trying to set up a Squid proxy server to log websites visited as well as block certain websites (eg. facebook). 
To do this I created ACLs, one for each category such as social networking or adult content. 

The problem I'm having is when I add a new ACL to the config file (ACLs were created and stored in separate files) I'm finding that if I restart the server it won't start up again, I just get the error that it is already started. I check and I cannot connect to the internet through the server so I know it's not working, as well as checking the running processes. 

I don't get it all the time, only certain ACLs, I thought they were too big and split them in two, it worked for a bit but then didn't. I restart the entire system, it magically works, until I stop the server and it won't start again without a reboot. 

Aldo I'm using Webmin as a GUI to help with the configuration of the server. 

I apologise if this isn't the right place, I might be better going to a Squid Forum, but any help you can give is much appreciated. 

If anyone can help me I'm happy to provide more details as they're needed. :) 

Thanks 

Adam

---

