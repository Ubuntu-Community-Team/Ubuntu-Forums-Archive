---
title: "windows wol magic packet when requesting files from a samba server"
date: 2008-07-05
forum: General Help
---

### Post by BigNotch44 on 2008-07-05
First off, I'd like to say that this forum is AWESOME!  I've pretty much used it as my primary resource to set up my home server with Gusty.

Here's a brief summary of what I'm trying to do:
1) Samba server runs a share directory of my entire media
2) All other client computers are slaves and will request media from this server when needed.
3) The server will go to sleep when there is no activity.
4) When a client computer (windows XP or Vista machines) needs media, the server wakes up from its sleep state (S3) via wol and serves.

What I've accomplished:
1) Samba server is seen by all computers on the network.
2) I followed this thread [here]("http://ubuntuforums.org/showthread.php?t=234588") and got my server to wake up fine.  I used the wol.exe command line tool found [here]("http://gammadyne.com/cmdline.htm") to send the magic packets from my XP or Vista machines.

The problem is, I have technically illiterate (not saying I am entirely) kids and wife that will not want to run a magic packet to request media.  I'd like to find a way to send this request in the background, for instance when my family wants to watch a movie on my HTPC.

I haven't been able to find a clear solution, so I'm hoping someone has been able to accomplish this.

Thanks for the help!

---

### Post by coolaj86 on 2008-07-05
How about create a batch file on the desktop

Click-This-To-Get-File-Access.bat
"C:\path to\wol.exe"

Additionally I've noticed that viruses edit the registry to load and arbitrary executable (e.g. the virus itself) each time that a *.exe is opened.

You could probably do the same thing for any arbitrary file type - .mov, .mpg, etc. Maybe even for network access. You'd have to post in a windows forum about that.

If you open regedit the line is somewhere around /Current User/Windows/Current Version/Shell I think... but it's been a while since I messed with that stuff.

---

### Post by BigNotch44 on 2008-07-06
I've seen posts about people making batch files to send this packet to other computers on the network during start up, but I've never thought about having it coincide with another .exe  Good idea.

Another thing I noticed today.  When I run "sudo halt" and wake the server with a wol magic packet everything works fine.  However, when I manually tell the server to suspend or hibernate, the server will not respond to wol magic packets.  What's the difference between these three shutdown types that may prevent my NIC from being able to wake the server up?  Or is it due to my wol config?

Thanks for your help.  In the meantime I'll browse windows forums about linking batch files to other .exe's.

---

