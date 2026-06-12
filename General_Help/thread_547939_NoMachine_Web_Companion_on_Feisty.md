---
title: "NoMachine Web Companion on Feisty"
date: 2007-09-10
forum: General Help
---

### Post by amarriner on 2007-09-10
Hello,
First post here and I'm a relative newbie so please be gentle. :)

I'm trying to get the NoMachine Web Companion working (using the FreeNX server) and am having some trouble. I've got the FreeNX server itself up and running and I can connect via the regular Windows No Machine client (1.5) just fine. However, when I attempt to connect via the Web Companion it doesn't work. 

I have nxserver, nxclient, and nxplugin installed on the server and generated a session file with nxclient. When I go to the Web Companion page, I can click Continue, I get a login prompt, I login, there's a message that says "Setting up the Environment" and shortly thereafter I get an error that says: "Could not start the local X server".

Any help would be **most** appreciated! I apologize I didn't provide much in the way of logs or other setup parameters so if any of that is needed, please let me know. I'm just not all that fluent with NX so I didn't know what was necessary. Thanks again!

---

### Post by jpramlak on 2007-11-14
I'm having issues as well. I can connect successfully from a Windows machine with client ver 1.5.
Even on my Ubuntu box, I can run the 1.5 client and connect locally.

I believe our problem is that the Web Companion package ships with a ver 2.0 client.
(client.zip files under plugin/$OS)

I haven't found a different version of the Web Companion.

-Jay

---

### Post by daflame on 2007-11-18
Your best bet is to update to the latest version.  I haven't tried it with Web companion yet, but you can be my guest.

If you are  interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest **NX 3.0 backend and client**.  I have working versions compiled for gutsy on x86_64 and i386.  If you need another dist package, please let me know and I'll start a VM to build one.

---

### Post by daflame on 2007-11-22
I opened a forum with the packages linked in...  I'm still not going to have AMD64 packages until tomorrow though.

Click [here]("http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx") to see the post.  Please contribute to the refinement of the installation.

---

