---
title: "Setting up a server"
date: 2012-12-28
forum: General Help
---

### Post by m9365428 on 2012-12-28
I may be in the wrong place but here goes. 
I am an amateur server admin. My only experience has been trying to get a minecraft server up and running, reliably. 

A little background:
I have managed to make a script that will start my server in a screen session. I haven't used that scrip in about a year. (life got in the way).
The server is running Ubuntu server. Trying to avoid a desktop to optimize the memory usage.(trying to turn a desktop into a server for 30)
The server is located on a friends internet and I have a remote connection to it. And that works very well.
I am rethinking how to run the server. I'm looking into using the wrapper script located here. [http://www.minecraftwiki.net/wiki/Tutorials/Server_startup_script]("http://www.minecraftwiki.net/wiki/Tutorials/Server_startup_script")

The problem:
The internet at my friends resets occasionally and as a result the IP of the server changes. We all use Skype to VOIP when we are on the server. I'm writing a script to start the server when the computer starts and I already have a script that will get the box's global IP but I still have to manually tell everyone the new IP. 
I'm trying to find a way to automatically send a message to a list of Skype accounts the updated IP for the server whenever It detects an IP change.

I am working on trying to write a script that will launch at start-up and run periodically while the system is running. I think I can figure that problem out but any ideas on that front would be appreciated. 

If I can figure all this out I plan on developing a post for other admins who want to set-up a linux based server.

Thanks.

---

### Post by sandyd on 2012-12-28
> **m9365428 said:**
> I may be in the wrong place but here goes. 
I am an amateur server admin. My only experience has been trying to get a minecraft server up and running, reliably. 

A little background:
I have managed to make a script that will start my server in a screen session. I haven't used that scrip in about a year. (life got in the way).
The server is running Ubuntu server. Trying to avoid a desktop to optimize the memory usage.(trying to turn a desktop into a server for 30)
The server is located on a friends internet and I have a remote connection to it. And that works very well.
I am rethinking how to run the server. I'm looking into using the wrapper script located here. [http://www.minecraftwiki.net/wiki/Tutorials/Server_startup_script]("http://www.minecraftwiki.net/wiki/Tutorials/Server_startup_script")

The problem:
The internet at my friends resets occasionally and as a result the IP of the server changes. We all use Skype to VOIP when we are on the server. I'm writing a script to start the server when the computer starts and I already have a script that will get the box's global IP but I still have to manually tell everyone the new IP. 
I'm trying to find a way to automatically send a message to a list of Skype accounts the updated IP for the server whenever It detects an IP change.

I am working on trying to write a script that will launch at start-up and run periodically while the system is running. I think I can figure that problem out but any ideas on that front would be appreciated. 

If I can figure all this out I plan on developing a post for other admins who want to set-up a linux based server.

Thanks.

Have you tried using a dynamic-dns service such as no-ip?
You can use ddclient or other to automatically update the address at no-ip when it changes. You can then reach the mine craft server at the no-ip address

---

### Post by m9365428 on 2012-12-28
I have looked at using such a service but I want to avoid it. I'm really trying to push this project as a way to get deeper into the Ubuntu system of developing scripts and workarounds. I simply cann't find a command line txt/im tool that can send a message to Skype.

---

### Post by d4rk0wl on 2012-12-28
You could always create a script to periodically curl information from [http://dynamic.zoneedit.com/checkip.html](http://dynamic.zoneedit.com/checkip.html) on a cron job or something and then echo it to an E-Mail locally on postfix to send out.  I don't know how you would be able to send it to skype although.

Though that seems like a workaround, I also run my server on a dynamic network and as said before it is very easy to configure ddclient to do all the work for you so you don't need to worry about a changing IP address.

---

### Post by m9365428 on 2012-12-29
Cron jobs are certainly what I was looking for to automate the server. I want to avoid opening the ports required to setup an e-mail host on the server. I don't like opening ports at all. 
I already have a script that pulls my IP from whatsmyip.com but I may rewrite it to use that site. (less fluff to filter out)

In truth I have used a dd service and we had problems with random people showing up and ****ing up our stuff. Since then we have been using the global IP directly and have had no random visitors. 

I'm looking at a site that list a process called Skype4Py. If I'm reading correctly I can script a plugin to do what I want. Will keep advised.

If I'm lucky I can use that same infrastructure to to develop a script for the server to answer an incoming skype call from its contact list, merge new callers into a group chat, and add new contacts to the list that are sent through chat. If I can get that to work then when we log onto the server we can auto-join a skype chat populated by all members on the server.

---

### Post by d4rk0wl on 2012-12-30
Have you thought about perhaps sending a notification through SMS?
[http://howto.gumph.org/content/send-sms-messages-from-linux/](http://howto.gumph.org/content/send-sms-messages-from-linux/)

I have not attempted this, but this article looks promising.
I also know that you can send a SMS message from an E-Mail address [number]@[carrier].com or something like that.

Also, some more food for through, I have my server running mobile PC monitor and the app on my phone. It alerts me whenever users log in, box shuts down, ect. I also have it configured that it'll relay to me the box's last known IP address. It would involve you relaying the message to your friends, but it's worth checking out at least.
[http://www.mobilepcmonitor.com](http://www.mobilepcmonitor.com)

Regards,
- D4rk0wl

---

