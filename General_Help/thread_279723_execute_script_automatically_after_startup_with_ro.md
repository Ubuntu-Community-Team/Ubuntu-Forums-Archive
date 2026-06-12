---
title: "execute script automatically after startup with root priviliges"
date: 2006-10-18
forum: General Help
---

### Post by mogliii on 2006-10-18
Hi,

I was looking around many googled pages looking for a way to start a script after startup with root priviliges.

My aim is the following: Have a small linux. When starting that linux, it boots up and after finishing to boot, instead of launching the x-window login screen or showing the login prompt, execute a script.

The script is supposed to backup the harddrives to a external harddrive and shutdown when finished. This means that from starting computer until shutting down after backup, there should be no user-action necessary.

My question is, where i put it and how I make it executed with root. I found a thread about startup scripts [http://ubuntuforums.org/showthread.php?t=277997&highlight=script+at+startup]("http://ubuntuforums.org/showthread.php?t=277997&highlight=script+at+startup")

But I am not sure if it is the right thing, cause I am afraid that if I put it there as discribed, it would start the backing up before the external harddrive is loaded or dd is ready?!?

Just I need your help where to put it and make it executed with root.

Thx

---

### Post by merkur2k on 2006-10-18
I believe rc.local is run after everything else, so that should be a good place to stick your script. You could also create a completely new init script like described, and make sure it has dependancies for any other services that need to be started first (such as hotplug for your usb drive).

---

### Post by mogliii on 2006-10-26
Hi,

have to get back to this thread as it didnt work as expected.

The script was started, but it was not possible to me to stop the script during execution (Ctrl+C). I wrote the script to it sleeps for 30 seconds at the beginning. This is intended to give a possibility to access the system for maintainance. The script will shutdown at the end.

So is there a key combination to abort the rc.local script? And if not, how can I make it execute automatically in a root-bash?

If i get everything running I will post my script or write a complete howto. Its already 90% functional.

Please help

---

