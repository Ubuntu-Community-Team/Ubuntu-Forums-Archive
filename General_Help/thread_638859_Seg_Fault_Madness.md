---
title: "Seg Fault Madness"
date: 2007-12-12
forum: General Help
---

### Post by NielTown on 2007-12-12
Hey, Folks.  

So this morning I was trying to chmod a file and it started segfaulting.  Then the whole system started to inexplicably crap out.  I restarted and suddenly my network interface fails to initialize; I was able to re-activate it in order to surf the web, but I can't ssh into, ftp to it, and worst of all Apache is shot.  I can, however, ping the machine.

I then decided to do a slew of package upgrades through Synaptic.  That went fine until I looked at the terminal window:  segfaults everywhere!  Now it's been hung up for the past 15 minutes or so; the state Synaptic is in right now is "Preparing to configure libsmbclient."  Yes, it's said that for about 15 minutes.  I'm afraid to touch anything.

Anyone have any ideas?  I must note that this install is running on a virtual machine.

---

### Post by p_quarles on 2007-12-12
What file were you attempting to alter? That's an important detail here.

Anyway, do you have a snapshot of this VM? If so, that's the absolute easiest way to fix this.

---

### Post by NielTown on 2007-12-12
I do have a snapshot, but it's from since this problem occurred.  Any help you can offer?  I was chmodding a folder.  I tried to move_uploaded_file (PHP function) into this folder and I got "Permission Denied" in return.

This has to do with work, so it sucks especially badly.

---

### Post by p_quarles on 2007-12-12
I might be able to help if you get a little bit more specific about what you chmodded. If it wasn't integral to the system, then the chmod command wasn't the problem, and you'll have to start retracing your steps prior to that. If you chmodded a folder that contained a permissions sensitive configuration file, though, that could be the problem.

---

### Post by NielTown on 2007-12-12
It was a web folder, so it didn't have anything in it at all; it's purpose was to hold files uploaded by web users.  Thing is, I hadn't done anything outside of routine between when things were working fine and things were falling apart.  Also, all other suspects (co-workers) questioned maintain innocence.  I really, honestly have no idea what happened.  All I know is that I now have to manually start my ethernet connection, Apache doesn't work, and I can't start Postgres.

---

### Post by p_quarles on 2007-12-12
Hmm. Yeah, that's pretty puzzling. Not sure what to tell you, but I can suggest a couple directions to go in:

1) How "open" is the web folder? Can anyone upload to it, or just registered users? I ask just because something like this *could* be the result of giving a piece of malicious code the permission to execute. I know you said there's nothing in it, but just double-check for any hidden files.

2) The better bet is to scour through your system logs, starting with dmesg, messages, syslog and kern.log.

---

### Post by NielTown on 2007-12-12
Considering the site hasn't been deployed to the public yet, it's not really "open" at all, except to us here at our shop.

During boot I get this:

>Configuring network interfaces                  failed

Bad start.

Then I was getting some error messages as soon as I logged in and my desktop opened.  Here's what they say:

>Power Manager
>
>This program cannot start until you start the dbus system service.
>
>It is **strongly recommended** you reboot your computer after starting messagebus.

aaaaaand

>Internal error
>
>failed to initialize HAL!


Then when I try to shutdown/reboot (by clicking the ol' Quit button), I get the "Power Manager" error again.

I'm basically afraid to touch anything.

---

### Post by p_quarles on 2007-12-12
dbus strikes again. This is a rare, but perpetual, problem with Linux systems. 

To initialize it, run this:
```
sudo /etc/init.d/dbus restart
```
If you get an "already running" error message, do this:
```
sudo /etc/init.d/dbus start
```
This might repair the problem. If not, let me know what it tells you.

---

### Post by NielTown on 2007-12-12
[IMG]http://nieltown.freeshell.net/segFault.JPG[/IMG]

---

### Post by p_quarles on 2007-12-12
It looks like it's saying there's a problem with the syntax of the dbus initiatialization script. If you could open that file (/etc/init.d/dbus) in the text editor, you'll be able to look at lines 38 and 88. I'm fairly certain that these are simply the lines in that script that are called by "start" and "restart," but it's worth having a look.

---

