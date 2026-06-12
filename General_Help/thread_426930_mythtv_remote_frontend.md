---
title: "mythtv remote frontend"
date: 2007-04-28
forum: General Help
---

### Post by rbtprkr on 2007-04-28
Hi, I installed mythtv on feisty the other day, so far so good. I also have a second machine running feisty and have installed mythfrontend, when starting the frontend from the second machine the frontend starts but gives an error saying it could not connect to the backend server. Starting the frontend from a terminal window produces this error:

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-04-28 23:19:40.248 Using runtime prefix = /usr
2007-04-28 23:19:40.286 Gnome-Screensaver support enabled
2007-04-28 23:19:40.286 DPMS is active.
2007-04-28 23:19:40.586 New DB connection, total: 1
2007-04-28 23:19:40.616 Connected to database 'mythconverg' at host: 192.168.2.126
2007-04-28 23:19:40.617 Total desktop dim: 1024x768, with 1 screen[s].
2007-04-28 23:19:40.621 Using screen 0, 1024x768 at 0,0
2007-04-28 23:19:40.671 Current Schema Version: 1160
2007-04-28 23:19:40.671 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-04-28 23:19:40.671 Enabled verbose msgs:  important general
2007-04-28 23:19:41.850 Total desktop dim: 1024x768, with 1 screen[s].
2007-04-28 23:19:41.852 Using screen 0, 1024x768 at 0,0
2007-04-28 23:19:41.853 Switching to square mode (blue)
2007-04-28 23:19:42.074 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-04-28 23:19:42.612 Joystick disabled.
2007-04-28 23:19:42.790 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-04-28 23:19:43.824 Registering Internal as a media playback plugin.
2007-04-28 23:19:52.821 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-04-28 23:19:52.821 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.

I have changed the IP address and passwords in /etc/mythtv/mysql.txt and ~/.mythtv/mysql.txt on the second frontend and in /etc/mysql/my.cnf I have bind-address set to the ip of the backend machine.

---

### Post by Erlander on 2007-04-29
These guides work well.

[https://help.ubuntu.com/community/MythTV_Feisty](https://help.ubuntu.com/community/MythTV_Feisty)

Rob

---

### Post by rbtprkr on 2007-04-29
I should have mentioned that I used the new guides.

---

### Post by nullfactor on 2007-04-29
Out of curiosity... can you connect to other network resources from the machine in question (internet, various shares, etc.)? 

What outputs when you type ifconfig?

Best of luck to you!  MythTV rocks.

---

### Post by bnoussu on 2007-04-29
I just had the same problem. Could not connect from different mythfrontend machine. Check your ip address on backend machine. It is now set to default localhost 127.0.0.1 as it should be ip address that is accessible from local network as it says on the error message: "You probably should modify the Master Server settings in the setup program and set the proper IP address."

---

### Post by superm1 on 2007-04-29
Make sure that the backend is actually running, and then checkout the backend logs in /var/log/mythtv/mythbackend.log.

The backend is pretty informative about anything that goes wrong during its startup procedure.

---

### Post by FryerFox on 2007-04-30
Check out this post:

[http://ubuntuforums.org/showthread.php?p=2322564#post2322564](http://ubuntuforums.org/showthread.php?p=2322564#post2322564)

It seems that the new MySQL turns off network access by default.

---

### Post by rbtprkr on 2007-04-30
I have been messing with this for a couple of hours and have changed the bind address line of /etc/mysql/my.cnf on both the backend and the remote frontend from commented out to the ip of the backend machine and every other combo I could think of, still can't connect to the backend. When I run mythfrontend from a terminal window mythtv opens to the start screen but says it can't connect to the backend server, closing mythtv leaves the same error that is posted above. If the missing socket is really just a file whats in it and where do I put the file, also why is the frontend looking for the backend at 127.0.0.1  doesn't it say that it connected at 192.168.2.126 a few lines above that? isn't that why I changed the address in /etc/mythtv/mysql.txt and ~/.mythtv/mysql.txt? what am I missinng here?

---

### Post by superm1 on 2007-04-30
> **rbtprkr said:**
> I have been messing with this for a couple of hours and have changed the bind address line of /etc/mysql/my.cnf on both the backend and the remote frontend from commented out to the ip of the backend machine and every other combo I could think of, still can't connect to the backend. When I run mythfrontend from a terminal window mythtv opens to the start screen but says it can't connect to the backend server, closing mythtv leaves the same error that is posted above. If the missing socket is really just a file whats in it and where do I put the file, also why is the frontend looking for the backend at 127.0.0.1  doesn't it say that it connected at 192.168.2.126 a few lines above that? isn't that why I changed the address in /etc/mythtv/mysql.txt and ~/.mythtv/mysql.txt? what am I missinng here?
Did you use custom-identifier *anywhere*, on any of your frontends?  Its one of the first few dialogs that pops up during the first time you start mythfrontend.  I've seen it wreak havok very similar to what you are getting.

---

### Post by bnoussu on 2007-05-01
Connection to your mysql db is working as log says. But did you change your backend server's ip in mythtv-setup? I had same problem and when i changed backend server's ip in mythtv-setup from 127.0.0.1 to my eth1 address remote connection began working.

---

### Post by rbtprkr on 2007-05-01
Thanks to all of you for the help, especially bnoussu, I'm embarrassed to say that I had not run mythtv setup on the backend. All good now, thanks again.

---

