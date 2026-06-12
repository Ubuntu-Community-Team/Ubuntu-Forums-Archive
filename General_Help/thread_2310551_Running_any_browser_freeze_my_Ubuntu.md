---
title: "Running any browser freeze my Ubuntu"
date: 2016-01-20
forum: General Help
---

### Post by Odense on 2016-01-20
Not sure when it exactly started - but it must be caused by one of the updates.
I am running dual boot Windows10/Ubuntu 14.04.3 on an old desktop and have been using Firefox an Chromium as my browsers.
Now as soon as I start Firefox the computer freeze and I have to shut it down the hard way to get out of the freeze. With Chromium I can browse some seconds but then the same happens.

Any ideas how I can fix it - and logs I can check/submit to assist with fault finding (and how to get to the logs when frozen or are they still there are a hard reboot ?).

Windows 10 is running OK on the old HW so I think Ubuntu should be able to as well ;-).

---

### Post by Odense on 2016-01-22
Damn - 219 views - not a single suggestion - let alone a solution :-D
Would reinstalling Ubuntu perhaps work ?

---

### Post by howefield on 2016-01-22
You could try renaming the ~/.mozilla folder (with Firefox closed) forcing Firefox to create a new default profile. If you use any extensions, add them back one at a time.

---

### Post by dragonfly41 on 2016-01-22
Your reported symptoms seem to occur across both Firefox and Chromium Web Browser.

I would try start a new account (or guest account) and test if you see same symptoms.

If not, then return to main account and launch Applications > System Tools > System Monitor to inspect running processes and memory usage.
Do you have enough memory?  Do you have a swap partition?

Perhaps reboot and try a full memory check (takes a long time to run though).

---

### Post by Odense on 2016-01-30
Thanks guys - I must have switched off notifications - so I did not think I had any replies.

I have tried uninstalling both Firefox and Chromium and reinstalling them but that did not give any improvements.
Would a full reinstall of Ubuntu help - and will it "only" clear the Ubuntu installation - NOT the Win10 part or my documents ?

How do I find the profile (~/.mozilla) ?
 
How do I do the full memory check ?

---

### Post by howefield on 2016-01-30
> **Odense said:**
> I have tried uninstalling both Firefox and Chromium and reinstalling them but that did not give any improvements.

That wouldn't do any good with the hidden configuration folders are left behind.. (eg, ~/.moziila)

> Would a full reinstall of Ubuntu help - and will it "only" clear the Ubuntu installation - NOT the Win10 part or my documents ?

Might do, but it is a bit of a sledgehammer approach and you are not at that stage yet :)

> How do I find the profile (~/.mozilla) ?

Open the Files manager (Nautilus) which should open in your /home folder, then press the Ctrl + h keys to show hidden files, scroll down till you see .mozilla. The period before a file or folder name signals that it is a hidden file, Ctrl + h toggles viewing hidden files. (PS. ~/ is a shortcut to your home folder)

---

### Post by Odense on 2016-01-30
Thanks howefield - I will try that but I don't think that folder is involved with Chromium - so I am guessing the problem lies somewhere else ?
Anyway - I ran both the memory checks in the boot menu with no errors.

---

### Post by dragonfly41 on 2016-01-30
I didn't ask if you are viewing the same websites with both browsers, and both browsers are freezing?
Consider the common factors.
Could be you need to explore flash plugins used by both browsers (e.g. if you are viewing YouTube videos).
Did you try guest account when you first login to Ubuntu to see if problem persists with fresh guest (or other new user) profiles?

---

### Post by howefield on 2016-01-30
> **Odense said:**
> Thanks howefield - I will try that but I don't think that folder is involved with Chromium - so I am guessing the problem lies somewhere else ?

The ~/.mozilla folder is for Firefox, the chromium folder is ~/config/chromium

> Anyway - I ran both the memory checks in the boot menu with no errors.

To be honest, you seem to have gone from saying the browsers freeze the computer freezes the minute you start it. That's a completely different story.

---

### Post by Odense on 2016-01-31
[URL="http://ubuntuforums.org/member.php?u=186490"]Thanks guys.
[B][COLOR=#990303][B]
howefield[/B][/COLOR][/B][/URL]
Unfortunately I am inclined to agree with you somewhat - it seems to be a worse problem that just the browsers - but it started with freezing as soon as I started Firefox - then I tested if Chromium did the same and it did just after a few minutes instead of immediately.

I now renamed the ~/.mozilla folder and it has helped. The computer did however freeze when I finding another program in the software center.
It seems the whole Ubuntu installation is not really "stabile" (like it used to be) and I wonder if there is a way to fix it or even reinstall/repair it WITHOUT clearing the whole harddrive(s). It is running in a dual boot with Windows10 (which have never frozen) and I don't want to mess up the dual boot (it was a bit of a hassle to set up - MS don't like sharing :-D)

[**[COLOR=#000000]dragonfly41[/COLOR]**]("http://ubuntuforums.org/member.php?u=1261878")
There did not seem to be much relation to what site I was on
I could not see any common factors.
Flash IS suspected but it also happened when I visited pages with no video (and I want to be able to view YouTube videos).
I did not try a guest account but the deletion of the ~/.mozilla folder seems to have helped. Unfortunately it seems there is an additional problem with the Ubuntu installation itself.

---

### Post by dragonfly41 on 2016-01-31
[COLOR=#000000]> I did not try a guest account but the deletion of the ~/.mozilla folder seems to have helped. Unfortunately it seems there is an additional problem with the Ubuntu installation itself.

Testing with a virgin guest or new user account might help to establish if you have a faulty Ubuntu installation .. ***or*** .. only a faulty Ubuntu user profile (which contains all the user apps).
It is a process of elimination of factors.
e.g. Does your normal user desktop freeze when you try (say) Opera browser?


[/COLOR]

Further thought. Here is another test .. try disabling hardware acceleration ..

[https://support.mozilla.org/en-US/questions/1030156](https://support.mozilla.org/en-US/questions/1030156)

---

### Post by Odense on 2016-02-03
> **dragonfly41 said:**
> [COLOR=#000000]

Testing with a virgin guest or new user account might help to establish if you have a faulty Ubuntu installation .. ***or*** .. only a faulty Ubuntu user profile (which contains all the user apps).
It is a process of elimination of factors.
e.g. Does your normal user desktop freeze when you try (say) Opera browser?


[/COLOR]

Thanks - Firefox seems to be running OK just now - without disabling the HW acceleration - but I had Ubuntu freeze when I tried starting a program (not a browser but cannot remember what it was) while Ubuntu was checking for system SW updates. I do things simultaneously like this all the time on my low powered old Samsung laptop without a hitch.
I have just installed Opera browser also.
I will see if it help to log in as guest (I should not create a new guest account while I am logged in as admin right ?) if I get another freeze.
And if it goes back to being mostly Firefox I will try out Opera.

---

### Post by RobertoRecordo on 2016-02-03
This sounds exactly like a problem I have on an older system with NVidia 6150SE hardware.
Every time I do an update (Ubuntu, mint, puppy) the nouveau driver gets installed, the desktop works, but any browser crashes the system - I get all kinds of colorful patterns on the screen, but the system is dead and I need to pull the plug to shut down. Also, if I let it go to sleep, when I wake it up it crashes.

One of these might help you figure out what driver you need:
```
$ sudo lshw -c video
$ glxinfo | grep -B 2 version
```
Getting the correct driver from NVidia solves my problem!

Good Luck

-Rob

---

### Post by Odense on 2016-02-09
Thanks Rob - I will try that.
It is a very strange problem - sometimes it is working reasonable well and this morning it just froze the whole computer again as soon as I tried to run Firefox. Good that I can boot the PC up with Win 10 too (which runs stable just as Ubuntu used to do) - but it IS annoying that I have to.
Maybe I should give up fixing it and try a reinstall - IF I can reinstall only Ubuntu without messing up my files and also not ruining Windows 10 and the dual boot ?

---

### Post by Odense on 2016-02-18
The last 3 times I booted up in Ubuntu mode the PC froze immediately when I tried starting a browser Firefox/Opera.
It also happened when I was logged in as guest (with Firefox).
I think solving this the "easy way" might be too difficult for me.

Can I reinstall Ubuntu WITHOUT deleting my contents (documents/downloads and such) and WITHOUT compromising the Windows 10 installation I have in a dual boot menu with the Ubuntu ?
 If there is too big a risk for the Win 10 installation I might just have to skip the Ubuntu part for now.

If I CAN do this safely I would like to know how ? And should I just close this thread and perhaps open a reinstall thread ?

---

### Post by dragonfly41 on 2016-02-18
Another idea I would try ... boot up a Live USB or Live DVD and see if you hit the same problems in "Try Ubuntu" mode.

And do you have enough free end space on your disk to try a "triple boot" .. i.e. adding another partition for a second installation of Ubuntu.
Or you could run Ubuntu on an external USB drive.

---

### Post by Odense on 2016-02-19
Thanks again dragonfly41,

I have a USB stick with Ubuntu - I will try that.
Not eager to make a triple boot - but how would I do it (if it comes to that) ?

---

### Post by dragonfly41 on 2016-02-19
I would try the USB stick first .. but it may run slower than internal Ubuntu.

I'm sure there is advice on this forum on installing multiple versions of Ubuntu .. triple boot .. if you have sufficient disk space.
Or you could install VirtualBox (on either Windows or Ubuntu) and install another Ubuntu VM in Virtual Box). That might be an easier option.

I keep Windows + Ubuntu 14.04 + earlier Ubuntu on different partitions setup by GParted (I have 12 different partitions on an ageing laptop).
You would first backup your entire disk. This is important.
Then using GParted resize the end partition to free up space for third OS partition.
Then create ext4 partition.
Then install Ubuntu into that newly created partition using Live USB (being absolutely sure that you target the correct partition).
Then apply boot-repair to recognise the three operating systems.

Hopefully you can track down the problem in current OS before resorting to such extreme measures.

---

### Post by Odense on 2016-04-02
I apologize for being too slow in progressing. I have been busy and mostly used the Win 10 partition.
I am writing this logged in via Firefox running (pretty slowly) on an older USB stick.
This probably indicates that the problem is in the Ubuntu installation on my PC.
Is there way I can clean it up and verify that the programs & settings are workable ?
I know that a new clean install will probably solve it - but I am running it in dual boot with Win 10 and I really do not want to mess that up.

---

### Post by Odense on 2016-04-07
I hope I did not loose the chance to get help because of being slow :-(
But so far it does not look good :-k

Still nobody willing to help ??

---

