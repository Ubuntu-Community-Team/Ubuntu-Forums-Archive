---
title: "Synergy, Win XP, and Ubuntu"
date: 2006-12-21
forum: General Help
---

### Post by nahham on 2006-12-21
I don't know if anyone has a similar problem but I've been trying to install Synergy on two desktops: one with win xp and the other Ubuntu (Ubuntu being my server).  The installation was not the problem everything there went OK.  When I start win xp it connects to the server and it shows (running synergys -f).  Everything now is going well:  I can move between the screens and use the keyboard.  However, when I login to win xp, the synergy server reports that the client is dead.  The exact message is "NOTE: CClientProxy1_0.cpp,221: client "S*******" is dead".  Win xp still reports synergy as connected to the server.  

Any ideas anyone?

Nahham

---

### Post by eXisor on 2006-12-21
AFAIK you have to do the same trick in Xp as you do in ubuntu.

Let me clarify...

a) In ubuntu, you need synergyc/s running to login from xp, but logging in kills the synergy session, so you need to start another synergy c/s once you're in.

b) With xp the same process is required. You flag synergy to run at machine startup, and then need to add another synergyc/s to the startup programs in xp to run once logged in.

Clearer?

PS: I run ubuntu as the client and xp as the server, the situation in a).

---

### Post by nahham on 2006-12-21
Thanks for the reply.

I did try to put synergyc in the startup of win xp but it complained that "Synergy failed to initialize: The service process could not connect to the service controller".  If I try to put synergy.exe in the startup then all what it does is open the main dialog box (the one where it allows you to configure Synergy).  Is there any type of attribute I can pass through with synergyc so that I could make it work?

Saf..

Note:  I did find the way to pass the argument but now it complains that it is already connected

---

### Post by eXisor on 2006-12-22
OK, I just checked and Xp has synergy running as a service. So I think the solution will be to create a synergyc.bat file and put this in your startup folder.

In the .bat file, you need to do a commandline restart of the service.

```
net stop "Synergy Client"
net start "Synergy Client"
```

In my installation the service is called "Synergy Service", so I'm assuming yours is called "Synergy Client". You must use the exact name of the service as it appears in the services list, capitals, spaces and all.

Let me know if this works.

---

### Post by nahham on 2006-12-24
Well.. ](*,) 

I tried what you said but the Synergy Client failed to stop and just says "Stopping" near the Service status.  I also configured win xp to auto login and tried to make it manually start by passing the command "net start "Synergy Client"": it starts and the connection dies shortly after that without me seeing the cursor move on the win xp window.

Any more ideas? :-k 

Nahham..

---

### Post by eXisor on 2006-12-25
Sorry, unsatisfactory as the following suggestions are, this is all I have at the moment.

1 - Do a force reconnect as soon as Xp is fully started.

2 - Set Xp up as the server and run ubuntu as the client. They way I do it.

I think the Xp situation is being caused by the network connection being lost during the login process. Synergy seems to be busy failing as the user Xp session logs in, and that's where the conflict lies. (It also explains why the batch file process does not work, i.e. the synergyc process is failing and is taking no start/stop inputs until the failure process is complete).

A question which comes to mind is... 

Does the user logging in have admin powers? If not, this could be the problem. To run synergy as a machine startup process, admin powers are required, and since the user is not an admin, the process does not have the authority to run inside the user session.

---

### Post by nahham on 2006-12-27
Thank you eXisor for the answers,

Here is where I am right now:

I am willing to make the win xp the server for Synergy but it seems there is a problem there too.  What happens is that the Synergy server works fine on xp, but when I start the client on Ubuntu it fails to connect 

> 
WARNING: synergyc.cpp,265: failed to connect to server: Timed out
DEBUG: synergyc.cpp,237: retry in 1 seconds
WARNING: synergyc.cpp,265: failed to connect to server: Timed out
DEBUG: synergyc.cpp,237: retry in 3 seconds
WARNING: synergyc.cpp,265: failed to connect to server: Timed out
DEBUG: synergyc.cpp,237: retry in 5 seconds
...


It usually then changes the message to 

> 
WARNING: synergyc.cpp,265: failed to connect to server: Connection refused
DEBUG: synergyc.cpp,237: retry in 1 seconds
WARNING: synergyc.cpp,265: failed to connect to server: Connection refused
DEBUG: synergyc.cpp,237: retry in 3 seconds
WARNING: synergyc.cpp,265: failed to connect to server: Connection refused
DEBUG: synergyc.cpp,237: retry in 5 seconds
...



Both computers ping each other fine so the problem isn't really the connection between them.  I am wondering if it is a naming problems because of the Caps:  I have one computer called ubuntuServer and the other Saif_Dell.  On "My Network Places" it shows *share* on ubuntuServer (Ubuntuserver) and *share* on desktop (Saif_dell).  Is there any special way you can make sure you are using the right hostnames?  Or is it another problem?

nahham..

---

### Post by eXisor on 2006-12-27
Try using their ip's instead. I do that on the client side since windows is so case ambivalent.

---

### Post by nahham on 2007-01-11
OK I give up. ](*,) 

Here is the setup I have and what happened:

I have three computers: 2 desktops and 1 laptop.  1 of the desktops run Ubuntu 6.06 Server, the other runs windows xp sp2.  The laptop dual-boots to Ubuntu 6.10 (with Beryl) and windows xp sp2.  

For the past couple of weeks I've been trying to make the 2 desktops (win xp sp2 and ubuntu 6.06) use synergy to share the keyboard and mouse with no luck.  I've done everything that I can think of and whatever eXisor suggested.  

When I was finally fed up I tried to connect the Ubuntu desktop to Ubuntu laptop and it worked with no problem.  Tried either one as a server and it worked fine.  I then booted up the laptop to win xp and tried to connect to the server and that didn't work.  What happened what that the Ubuntu server (when running as a server) usually says the laptop is connected but I cannot control the mouse on the laptop screen.  After a couple of seconds it reports that the laptop connection is dead.  I tried each one as a server with no luck.  

Finally I tried to connect the two windows (desktop and the laptop booted up in win xp) and it didn't work either.  I have no clue what is wrong.  I have turned the win firewall off and opened the port required by synergy and I don't have any other firewall software running.  The synergy client on the windows machine usually hangs up and on the desktop basically crashing it.  I can CTRL-ALT-DEL on the laptop to forcefully shut synergy down. 

This is really frustrating and I am planning to jump off a really high 1 story building if it doesn't work :D

::_______________________________________________________________________::
Don't you just love Window$ ..

---

### Post by byoon on 2007-01-11
I have Synergy running with my two machines at work.

Server: Windows 2000 Professional
Client: Ubuntu Edgy Eft

I am having a problem which I can't find documented anywhere.

Keyboard repeat doesn't work on client.

Any settings that I can change to get this working?

---

### Post by nahham on 2007-01-15
Well, since I am disperate and thought it my problem had something to do with the connection I ran Ethereal on both win and Ubuntu computers and ran Synergy.  Turns out Ethereal believes there is a TCP checksum error on all the packets going from the win computer (192.168.0.3) to Ubuntu (192.168.0.2).  

I really don't know what to do next.  Should I report it to the Synergy guys?

Nahham..

---

### Post by eXisor on 2007-01-17
Hmmm... The checksum error is odd, but sounds like a red-herring. Perhaps there is a more fundamental problem.

Do you have basic networking going between the boxes? i.e. can you do file-sharing between Xp and Ubuntu?  If file-sharing works then the tcp checksum stuff is a red-herring.

What is your setup? Xp -> router -> Ubuntu,       or XP -> Ubuntu ?

---

### Post by nahham on 2007-04-14
Well .. 

It turns out that the language bar in XP conflicts with Synergy is some way (bug reported).  The only thing to do is remove the language bar and everything works fine.

nahham..

---

