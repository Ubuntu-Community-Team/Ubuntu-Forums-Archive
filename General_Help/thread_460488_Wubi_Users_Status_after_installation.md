---
title: "Wubi Users: Status after installation"
date: 2007-05-31
forum: General Help
---

### Post by Sushubh on 2007-05-31
A poll to see how many users faced problems with running Ubuntu after installing it using Wubi!

---

### Post by spaceship9 on 2007-05-31
I did

when shutting down or hibernating I am faced with a blinking cursor... and nothing else... doesn't really shut down or hibernate, just blinks at me....

occasionally a window freezes in ubuntu but the OS itself is still fine...

---

### Post by Sushubh on 2007-05-31
shut down does not work for me.

and my wubi installed ubuntu is at the moment totally unusable due to a bad system restart. am hoping to get a solution... posted the problem [here]("http://ubuntuforums.org/showthread.php?t=460424").

---

### Post by MikeM709 on 2007-05-31
i have some pretty big problems right now. any help would be appreciated.

i saw about wubi on download.com but unfortunately they did not say anywhere that it would break your vista boot manager. i jumped right to installing with out reading the fine print probably because i was bored and i love linux (and im daring, considering i only have one computer :P). so for now my family has to contend with ubuntu after the recent switch from xp to vista, which has still left them scratching their head. 

slight off topic, is there a way to uninstall wubi without starting up windows? like using a live boot cd of ubuntu and just basically doing the manual uninstallation?

---

### Post by omgDarkWillow on 2007-05-31
No problems. :D

---

### Post by varchar255 on 2007-05-31
> **spaceship9 said:**
> I did

when shutting down or hibernating I am faced with a blinking cursor... and nothing else... doesn't really shut down or hibernate, just blinks at me....

occasionally a window freezes in ubuntu but the OS itself is still fine...

Same problem with hibernation (shut down works for me though), but it has been acknowledged here: [http://ubuntuforums.org/showthread.php?t=436910](http://ubuntuforums.org/showthread.php?t=436910)

But sometimes Ubuntu freezes randomly for me, not just specific windows but the entire OS.

---

### Post by ago on 2007-06-01
Again can you please specify your wubi version? We expect no issues with test3 for instance.

---

### Post by minhmeoke on 2007-06-01
I've been using Lubi, the Linux Ubuntu Installer (to my knowledge, there is only one version), and had to hard-reboot several times due to the black-screen error that occurs with widescreen laptops like my Compaq V6000, see [http://ubuntuforums.org/showthread.php?t=457109]("http://ubuntuforums.org/showthread.php?t=457109") for the solution. As a result, I experienced a lot of random problems after installation, probably due to ReiserFS corruption.

Here are the errors I have found had so far:
1) Window borders don't appear when initially starting an Ubuntu session; I have to type in ```
metacity &
``` to get them back.

2) For about 2 minutes after I start up Ubuntu, I cannot get the "Run Application" prompt when I press Alt + F2. When I select System > Quit, the options also take about 2 minutes to appear. However, I can restart the computer any time from terminal with ```
sudo init 6
``` right after I start Ubuntu.

3) I was installing/removing packages in Synaptic when I started having problems with dpkg; first /var/lib/dpkg/available got corrupted with a newline character; then I tried ```
apt-get update
``` which caused missing headers and other problems, so now I can't change anything.

I'm going to try reinstalling (without hard-reboots); hopefully I'll have better results then.

---

### Post by hummingbird59 on 2007-06-01
I used an early May version (don't remember details) - and it was flawless!:D.  Convinced me to go Ubuntu full time!

---

