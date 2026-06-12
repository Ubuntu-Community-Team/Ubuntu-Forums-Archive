---
title: "Ubuntu Freezes"
date: 2006-12-05
forum: General Help
---

### Post by ghepardo on 2006-12-05
Hi.
My ubuntu freezes. Sometimes, when I am working with my pc, it freezes. Only the mouse works and I can't do anithing, nor close gnome (ctrl+alt+backspace) nor change tty (ctrl+alt+f1 or f2 etc). The only thing I can do is reset my pc.
I had the same problem with kububtu, I thought it was kubuntu and I installed ubuntu, but I still have the problem now.

Is this a known bug?

I hope someone answers me.

---

### Post by Forceflow on 2006-12-05
Did you customize something to your X-window sysem ? (xorg.conf)

Try running memtest86. Could be something with your RAM.

---

### Post by 3rdalbum on 2006-12-05
There's absolutely no pattern to it? It doesn't, for instance, only happen when you try opening certain folders in Nautilus?

I would try opening a terminal window when you start up and running the 'top' command in it. Keep it on top of all other windows, just so you can see the first couple of lines of the process list. Maybe you'll see a pattern there when the machine freezes.

A tip for dealing with crashes: If the computer becomes unresponsive, don't just turn off the power or restart. First, press Alt-PrintScreen-S to sync your disks. (wait a few seconds). Now press Alt-PrintScreen-U to mount all disks as read-only. Now reboot by pressing Alt-PrintScreen-B or your reset switch.

Those steps can minimise the possibility of data corruption.

---

### Post by ghepardo on 2006-12-05
Well, my ram is ok. In fact Windows xp never crashes, and memtest does not shows any problem.
Well there isnt a pattern to these crashes... In fact, just few mins ago it crashed when I was choosing screen saver. yesterday crashed when I was surfing the web with opera. 

I tried to use the open nvidia drivers ("nv") in spite of the NVIDIA ones, but the crashes still comes. So now I am trying to not use ntfs-3g. If someone has some more advice give me tnx. 

Maybe there is some software that saves the system log constantly!?, so when I reboot I can see what happened ?!

And using the "top" command, for what should I search when my system hangs!?

---

### Post by ghepardo on 2006-12-05
Ok, I tried again to work with screensavers, and the system crashed again.
What happens when the system freezes is that the screensaver preview starts going slow, and I have no control on my pc. The mouse works, I can use the alt+printscreen+b to reboot my pc, but I cant interact with the GUI.
I had the console opened with the TOP program running, but I didn't saw anithing strange. Should I search for something particular there!?

Someone of you have something to suggest me to find why this happens!?

---

### Post by yopnono on 2006-12-05
Have checked the logs?

---

### Post by ghepardo on 2006-12-05
> **yopnono said:**
> Have checked the logs?

Tell me precisely what logs should I check tnx.

---

### Post by tuskal on 2006-12-05
> **ghepardo said:**
> Hi.
My ubuntu freezes. Sometimes, when I am working with my pc, it freezes. Only the mouse works and I can't do anithing, nor close gnome (ctrl+alt+backspace) nor change tty (ctrl+alt+f1 or f2 etc). The only thing I can do is reset my pc.
I had the same problem with kububtu, I thought it was kubuntu and I installed ubuntu, but I still have the problem now.

Is this a known bug?

I hope someone answers me.

Check [here]("http://ubuntuforums.org/showthread.php?t=311927"), [here ]("http://www.ubuntuforums.org/showthread.php?t=221320")or [here]("http://www.ubuntuforums.org/showthread.php?t=221313&highlight=nvidia+driver")

btw, what are your computer specs? Mine seems to be working now, though I haven't used it as much yet...

edit: and oh, where do I find the logs in ubuntu? I'd like to see those aswell... some command in the console perhaps?

---

### Post by yopnono on 2006-12-05
Check all logs for error or anything strange for that specific time the machine freeze.

You have the log under menu system / administration
Or you will find it at /var/log

---

### Post by ghepardo on 2006-12-06
I ran memtest86 for 5 hours, it did 16 pass and I had these errors:

tst pass failing address good bad err.bits count
8 1 001fcd9fb0-508.5mb 00000000 00400000 1
8 2 0000fce3fa0-252.1mb 00000000 00400000 1
8 11 0000dc00f80-220.5mb 00000000 00400000 1
8 11 002dccbfc0-nonhosegnato 00000000 0040000 1

are they normal (I mean, is normal that some error can occur in 16 pass) or my ram/mobo are damaged !?

Is possible that the crash are due to nvidia drivers !? I installed the ones in repos.

---

### Post by ghepardo on 2006-12-06
up

---

### Post by ghepardo on 2006-12-07
I think the problem is the nvidia driver, same if is the one from repos or the one from nvidia website. Someone can help!?

---

### Post by jk_warrior on 2006-12-15
I have exactly the same problem. My system freezes randomly. It are the same symptoms as the topic starter has.

I'm using Gnome and have Beryl running on an Ati card. So a totally different driver then the topic starter has! When it freezes (sometimes after 2 hours, sometimes after 5, sometimes working in the terminal, sometimes browsing in Firefox), everything keeps working, but I cant click or type anything. Animated gifs keep moving and stuff, but everything becomes unresponsive. 

I just can't figure out witch program is causing this! 
Thanks in advance for your help.

---

