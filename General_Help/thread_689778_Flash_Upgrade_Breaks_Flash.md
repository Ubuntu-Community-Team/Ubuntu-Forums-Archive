---
title: "Flash Upgrade Breaks Flash"
date: 2008-02-06
forum: General Help
---

### Post by Frihet on 2008-02-06
I just did the upgrade to Flash pushed out by the upgrade service. Now flash objects result in an error message.

Is there a way to back the upgrade out and install a working version?

Thanks!!!

---

### Post by Yellowbelly on 2008-02-06
SAME exact thing happened to me too. I tried downloading flash and installing it manually but the executable doesn't want to run...which I can rarely get executables to run anyway. Linux does NOT make that easy.

---

### Post by Frihet on 2008-02-06
I got it. I uninstalled Flash.

Then I restarted Firefox and reinstalled from the Firefox Add-Ons dialog.

(Oops -- Correction)

The fix thet worked was here:

[http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html)

(End correction)

It works fine now.  I think the latest upgrade pushed out by Ubuntu is missing a few gears.

---

### Post by ORF1000 on 2008-02-06
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is quite a disappointment -- hope it will get fixed soon!  I have the AMD64 architecture.  Don't know if that's a factor.

---

### Post by aidanr on 2008-02-06
If you're on 64bit use [this method]("http://ubuntuforums.org/showthread.php?t=476924"). I updated earlier and firefox didn't recognise the updated version, so I ran that script and it worked a treat.

---

### Post by Yellowbelly on 2008-02-06
i have a 64bit proc but i don't use the 64 ubuntu os.

---

### Post by matchstich on 2008-02-06
am having the same problem.

package manager say i have flash 9.0

but about:plugins say 7.0

tried uninstalling and restart firefox

then reinstall,  no joy.

even tried a reboot--no joy there either

would like to have it working.

thanks

---

### Post by arsenic23 on 2008-02-06
A quick
```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```
fixed this issue for me in Firefox and Epiphany.  Opera is all of the not working though.  This is the first time I've had a flash issue since Breezy.

---

### Post by Chazall1 on 2008-02-06
> sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree 
That worked great, all Flash Functioning!!
Thanks
=D>

---

### Post by nucleararms on 2008-02-06
> **arsenic23 said:**
> A quick
```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```
fixed this issue for me in Firefox and Epiphany.  Opera is all of the not working though.  This is the first time I've had a flash issue since Breezy.

it kindof worked for me.. now i have crazy 0s that flash on every youtube video.. any thoughts? Also flash on other sites just doesn't work.

---

### Post by matchstich on 2008-02-07
[QUOTE=arsenic23;4284136]A quick
```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```


tried this , still getting the error that it is not installed.
thanks

---

### Post by likemindead on 2008-02-07
I generally figure patience is the key. A fix oughta come down in a day or two. I can wait.

---

### Post by Tanker Bob on 2008-02-07
Nevermind. I found the answer at this post: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890/comments/15](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890/comments/15). Purging the old package then installing the linked package worked fine.

---

### Post by legalizemeth on 2008-02-08
> **arsenic23 said:**
> A quick
```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```
fixed this issue for me in Firefox and Epiphany.  Opera is all of the not working though.  This is the first time I've had a flash issue since Breezy.
Fantastic!  This worked for me too.

---

