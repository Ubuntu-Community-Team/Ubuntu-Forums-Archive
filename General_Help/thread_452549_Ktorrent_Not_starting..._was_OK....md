---
title: "Ktorrent Not starting... was OK..."
date: 2007-05-23
forum: General Help
---

### Post by hatman on 2007-05-23
Got a problem with ktorrent, was working ok until the last upgrade/reboot and suddenly it's not working... If I click the app link nothing shows up but when I run it in terminal I get te following error message...
> andy@Downstairs PC:~$ ktorrent
/usr/bin/iceauth: /tmp/dcopPfMg8b:1:  bad "add" command line
/usr/bin/iceauth: /tmp/dcopPfMg8b:2:  bad "add" command line
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
kdeinit: DCOPServer could not be started, aborting.
ERROR: KUniqueApplication: Can't setup DCOP communication.

Looked though Synaptic for ICE/DCOP and found zilch.. must admit I'm running it under gnome but as I say, had no problems before... anyone any ideas?

---

### Post by Tamara on 2007-05-23
I'm having a similar problem. ktorrent was working just fine. All of a sudden, it did not start anymore.  However, it seems to eat up all my CPU power and it takes minutes to even open a terminal window. 

if I do this: ps -C ktorrent, I get the following. Once I kill the processes, my CPU power is back. 

  PID TTY          TIME CMD
10074 pts/0    00:00:00 ktorrent
10075 pts/0    00:00:04 ktorrent

If I start it from the command line, this is what I get:

kbuildsycoca running...
kio (KMimeType): WARNING: KServiceType:: offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType:: offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType:: offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType:: offers : servicetype ThumbCreator not found

And then nothing.  Any idea what went wrong and how to fix this?

---

### Post by hatman on 2007-05-23
Also happening with k3b.. so assuming it's something to do with me using gnome and not kde...

---

### Post by Tamara on 2007-05-25
I'm relatively new to Ubuntu. Still no clue what's going on. I also couldn't get Azareus to work, but this seems to be a port issue as discussed in different threads. Bittornado works, but I don't think you can shut down you computer and resume the download later on. Right now I am using the Bittorrent Client for Windows with Wine.  Until now it works, but I would still like to go back to ktorrent.  It is definitely the client I like best so far. I am not sure if it has to do something with not using kde, because at first it worked just fine.

---

### Post by hatman on 2007-05-26
So far fro msearching round it appears that it may be a problem with permissions, but I've not got round to changing them yet... You can always try deluge as your client, thats what I'm using at the moment myself (as I cant get Az to run either...)

---

### Post by hatman on 2007-05-28
Well, I've changed the owner/permissions of ICEAuth as well as DCOP, dcopserver and dcopclient from root to me and still get the same error message.. someone must have come across this before... Neither k3b nor ktorrent will work in gnome where they were working before...

---

### Post by hatman on 2007-05-30
If it helps the output from ls -lah ~ | grep kde is

> drwx------  3 andy andy 4.0K 2007-05-22 18:14 .kde

Trouble is I dont know what they're supposed to be... I just seem to be going round in circles at the moment....

---

### Post by hatman on 2007-06-01
Oh well...  looks like a back everything up and do a re-install... thought I'd got away from having to do this **** when I left Win9x behind.... *sigh*

---

### Post by hatman on 2007-06-10
OK, dont know if it helps anyone but my pc's host name was changed to "downstairs pc" (as opposed to "upstairs" and "laptop") on my home network and after getting an error in a couple of other apps as I was backing up ready to reinstall I changed it to "downstairs" and lo! everything is running again... just a pointer to check the host name has no "illegal" characters in it... woohoo... no reinstall needed...

---

