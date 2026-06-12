---
title: "Help: Permissions &amp; Firefox after updates 8.04"
date: 2008-06-23
forum: General Help
---

### Post by Dubbed on 2008-06-23
Dear all

Please bear with me, as I'm a newbie to the world of Linux. 

I installed HH 8.04 a few weeks back - all good. It took me that long to get the wireless lan usb to work. I did learn a lot in that time, though, so it was a good curve. I will persist!

The wireless lan worked so well that I got the 250+ updates download in no time at all. Good stuff, untill installing the updates.

Reboot.

Now, Firefox won't start (save for the tab at the bottom saying Firefox is starting - then nothing).

Also, I go in to the Control Centre and I don't have permission/s to do anything. 

Any ideas?

Thank you in advance.

---

### Post by Darkade on 2008-06-23
what happens when you write this in a terminal
```

firerox

```
You can't access Control Center or you access and then certain items won't allow you to modify them?

---

### Post by Dubbed on 2008-06-23
Thanks for your quick responce.

Re code: "firerox" I will try that this evening.

I can access the Control Centre, but, for example - clicking on Network give me the message that I don't have permission to do that, or words to that effect.

---

### Post by Darkade on 2008-06-23
your example, Network, is an administrative task that can only be modified by an administrator. and there are several items of that kind in the Control Center, but all of them have an Unlock button at the bottom. There you just select you name from the list and use your password. That'll do the trick.

For firefox, after you write that in the terminal you will probably get an error, please copy/paste it

---

### Post by Dubbed on 2008-06-23
firerox - I'll be straight on to that, this evening, and will post the results.

I can't say that I noticed an Unlock botton. I say this, but bear in mind, my eyes were probably bleeding at this point! :) I'll be on to that, too. 

Many thanks for your help.

---

### Post by Dubbed on 2008-06-23
```
firefox
```
```
could not find compatible GRE between version 1.9 and 1.9
```

Also, I did not see and unlock button in Control Centre. Example:

Control Centre >> Sound - works ok.

Control Centre >> Network - pop up message:

The configuration could not be loaded.
You are not allowed to access the system configuration.

Also (sorry): Moving the pc upstairs - it was in the lounge while I set up the wlan0 - can not see my wireless network, but does see my neighbours.

---

### Post by Darkade on 2008-06-23
For your firefox problem I found [this]("http://ubuntuforums.org/showthread.php?t=570555") thread. What version of firefox are you using? 3.0? the final release or a beta?
If you don't know what version are you using, check it opening a synaptic (System>Administration>Synaptic Package Manager) search for synaptic and please post your version

the other problem I think it's a bit more tricky. could you please get this to a terminal
```

ls -lra > filelist

```
That will create a file named filelist in you home directory with the permissions for you files. I'm thinking that maybe you don't own you config files, I really can't think of another explanation. Also if you don't own some of your config files that may be the reason for your firefox not working

P.D. You didn't see an unlock button because it is in the network manager, and in the windows of some other admin tasks. And you can't even access this windows

---

### Post by Dubbed on 2008-06-23
ls -lra > filelist
cannot access lra: No such file or directory

ls
autopackage.31466146 ndis
autopackage.61686909 ndiswrapper-1.53
Desktop net8187.inf 
Documents Pictures
Examples Public
filelist rtl8187B_linux_24.6.1024.0822.2007
hardinfo-0.4.2.2-x86.package rtl8187B.sys
hardinfo-0.4.2.3 Templates
Music Videos



Edit:

Synaptic:

firefox >> 3.0+nobionly-0ubuntu0.8.04.1
then
firefox-2
firefox-2-dbg
firefox-2-dev
firefox-2-dom-inspector
firefox-2-gnome-support
firefox-2-libthai

then

firefox-3.0
etc

---

### Post by Dubbed on 2008-06-23
Please note - 

This desktop PC was borked by xp & vista

Since then, and why I have ubuntu, other OS can't be loaded. I was lucky to even get Ubuntu on this drive(after many install attempts). Mandriva wont even get past the first check/stage, Live or DVD. 

What annoys me is - yesterday, prior to all of the updates, Ubunto was running perfectly.

Note to self: Don't update (fix) if something is working well!

---

### Post by Darkade on 2008-06-23
Acctually updates work really great, I will not say I've haven't had trouble but thery are really great, I think nothing that does not works propertly makes it to the updates. and I'm sorry that command was my bad, just post the result of 
```

ls -la

```

I think that was a capital R instead :P it's just that I'm at work and not in front of my box LOL.

but that last piece of code will do

---

