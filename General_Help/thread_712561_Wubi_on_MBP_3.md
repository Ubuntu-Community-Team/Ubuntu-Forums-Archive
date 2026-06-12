---
title: "Wubi on MBP 3"
date: 2008-03-01
forum: General Help
---

### Post by new_11 on 2008-03-01
I only ask this since I've tried wubi before on my Leopard/XP with bootcamp install and it's worked (I had to change where grub was looking to boot from, but it was a relatively straightforward and easy process cause it only involved pointing it to the third partition, instead of the first). 
When I install now though, it boots into the installer, it does some checking, fires up the partitioner and within about 45 seconds the procedure stops and says Installation failed and says there are logs saved in a directory on my C drive and that its going to reboot now.
Is there any reason for this, or some way I can fix it? (Windows is on bootcamp and is the 3rd partition)
I've tried rev444 with hardy alpha5. (My problem is that I don't remember which previous rev worked, and its a real hassle trying all revs)
Any help would be appreciated. and Thanks in advance.

---

### Post by ago on 2008-03-02
Look at /var/log/syslog, in the zip file. If you see some migration assistant messages at the end of the log, then we are aware of the issue, and it is being worked on. Otherwise feel free to attach the logs.

---

### Post by new_11 on 2008-03-04
It seems it is a migration assistant problem. (I tried rev 446, and that still had the same problems...)
Thanks for your response... and I was wondering if you had any idea when you might fix it by?...

---

### Post by ago on 2008-03-05
> **new_11 said:**
> It seems it is a migration assistant problem. (I tried rev 446, and that still had the same problems...)
Thanks for your response... and I was wondering if you had any idea when you might fix it by?...
Migration assistant is a component external to Wubi, Evan wrote it. And he already submitted a fix, but the ISO are frozen by other packages at the moment so the fix did not appear, should be there any day now.

---

### Post by ago on 2008-03-05
New ISO as of today should have the fix.

Can you please try it out? You will have to redownload the ISO from 

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

and possibly use latest Wubi version from

[http://www.wubi-installer.org/devel/minefield](http://www.wubi-installer.org/devel/minefield)

---

### Post by new_11 on 2008-03-05
its working!.. 
the installation had one more issue.. basically at the migration assistant screen i had no option to go forward(there was an option to go forward, but it was greyed out and unclickable)... so i clicked cancel, and it booted me into a live cd desktop.. and i installed from there... and the settings were all already automatically detected(it was going to install on the loop without my telling it to)... (btw, this problem also occured the first time i tried this)...
the os itself is slow and crashes quite a bit.. though i suspect thats due to ubuntu itself and not wubi... 
there are a couple of issues though... grub gives me an error message.. i can't remember what it says..but it tells me to run an ms compatible fdisk tool... 
and another thing.. ubuntu doesn't shut down!! i have to power the computer off to turn it off.. 
either way.. this is a great app... and thanks a lot for it... a triple boot osx/windows/ubuntu is a lot easier now...

---

### Post by ago on 2008-03-06
Can you please provide the exact errors you see?
I'll give instructions later on how to debug shutdown issues
It will help if you can zip /etc/init.d and post the list of files in rc6.d
+ the usual logs such as syslog and dmesg

---

### Post by new_11 on 2008-03-06
the error says:
Warning: Unrecognizable partition on table 80. Please rebuild using a Microsoft compatible FDISK tool. 


(i think thats the error.. it occurs after i select ubuntu in NTLDR)

and attaching files in these forums are a pain... it just keeps failing... any other way of doing it?

---

### Post by new_11 on 2008-03-06
it seems something DID attach.. lol...

---

### Post by ago on 2008-03-07
init.d seems fine but there is not enough info there, what do you see if you type

cat /var/run/sendsigs.omit

---

### Post by new_11 on 2008-03-11
hi... sorry for the late reply... but i tried booting into ubuntu and it just gave me an initramfs prompt... i didn't really know what to do after that.. 
i can't provide any more info cause i deleted ubuntu.. will be re-installing soon, but for now, its gone..

---

### Post by ago on 2008-03-13
> **new_11 said:**
> its working!.. 
the installation had one more issue.. basically at the migration assistant screen i had no option to go forward(there was an option to go forward, but it was greyed out and unclickable)... so i clicked cancel, and it booted me into a live cd desktop.. and i installed from there... and the settings were all already automatically detected(it was going to install on the loop without my telling it to)... (btw, this problem also occured the first time i tried this)...

It would help if you could provide the logs when you get shown the migration-assistant dialog.
Boot in verbose mode, then when you see the dialog, press Ctrl+alt+f4 and zip /var/log into the windows drive (which will be accessible as either /isodevice or /host, you'll have to check). Then attach the logs here.

---

