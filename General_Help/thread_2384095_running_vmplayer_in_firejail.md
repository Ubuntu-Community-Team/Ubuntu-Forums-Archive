---
title: "running vmplayer in firejail"
date: 2018-02-02
forum: General Help
---

### Post by rosika on 2018-02-02
Hi altogether,


I have a question concerning the use of firejail.


I want to run **VMwarePlayer** (terminal-command is "vmplayer") within firejail. But when typing "firejail vmplayer" I run into problems.
The "VWware Kernel Module Updater" presents itself and if I click on "intsall" the following message appears (in German):


> '/usr/bin/vmware-modconfig' --icon='vmware-player' --appname='VMware' konnte nicht als Anwender root ausgeführt werden:
 
 Failed to exec new process: Keine Berechtigung




The thing is: vmplayer doesn´t use the profile which already exists.


As there is no *vmplayer.profile* ( see [https://github.com/netblue30/firejail/tree/master/etc](https://github.com/netblue30/firejail/tree/master/etc) ) I tried the following:
**"firejail --noprofile vmplayer"**. This one worked. I could use my virtual machine (which by the way is bodhi linux).


My questions is: 
What is the security status of my application with the --noprofile-option? What exactly does it do? 
Or is there another/a better way of running vmplayer within firejail?


Thanks a lot in advance.


Greetings.
Rosika  :(


P.S.:
system: Lubuntu 16.04.3 LTS, 64 bit

---

### Post by TheFu on 2018-02-02
Running a complete OS in a sandbox with the default profile will limit many things that an OS needs to be ... an OS.  Much better to run the specific application in a way that meets your needs instead.

firejail has lots of example profiles in the /etc/firejail directory.  They aren't THAT hard to understand. Take a look, see what is available, see what works for your needs.

This video might help you understand what firejail is a little more when compared to using a full virtual machine: [https://www.youtube.com/watch?v=7mzbIOtcIaQ](https://www.youtube.com/watch?v=7mzbIOtcIaQ)  firejail is a sandbox, much like a linux container.

---

### Post by rosika on 2018-02-03
Hi [COLOR=#000000]TheFu,

thank you for your answer.
[/COLOR]> [COLOR=#000000]firejail has lots of example profiles in the /etc/firejail directory. They aren't THAT hard to understand. Take a look, see what is available, see what works for your needs.[/COLOR]
Right, I also read the man-pages. It might really be a good idea to take a look at the other profiles in order to see what could work.

Thanks also for the link.

Greetings and Have a nice weekend

Rosika :)

P.S.:
Just watched the video. It was quite awesome although I really understood a minor part of it. :redface:
In addition to that:
also interesting to watch: [https://www.youtube.com/watch?v=cYsVvV1aVss](https://www.youtube.com/watch?v=cYsVvV1aVss)  by the same speaker.

---

