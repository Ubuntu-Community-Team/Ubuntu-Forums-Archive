---
title: "IS there a good stable 7.10 release?"
date: 2008-02-05
forum: General Help
---

### Post by nintennuendo on 2008-02-05
Not 8.04.  I just tried the most recent alpha of wubi 7.10 and it crashed trying to download the iso.. so is there something I don't know?

---

### Post by ago on 2008-02-05
> **nintennuendo said:**
> Not 8.04.  I just tried the most recent alpha of wubi 7.10 and it crashed trying to download the iso.. so is there something I don't know?

The only stable release is 7.04. For anything more up-to-date, 8.04 is the preferred route, since 7.10 had other issues that cannot be fixed. I'd encourage you report detailed information on any error so that I can resolve it. If you type %temp% in the windows file manager you will see a log of wubi.

---

### Post by nintennuendo on 2008-02-05
Heres the log I got.  So, It would be smartest to try the 8.04alpha instead of 7.10?

---

### Post by ago on 2008-02-05
Do you have a file called C:\ubuntu\install\metalinks\ubuntu-desktop-i386.iso.metalink? 
What URL is in there? Also what does happen to the downloader? Do you use an http proxy?

A workaround is to download the ISO (see the URL in the metalink) separately and put it in the same folder as wubi.

---

### Post by nintennuendo on 2008-02-05
I'm already downloading the 8.04 alpha.  Should I stop and try to get the other one?  

this is what that metalink file says when opened in Notepad.
<?xml version="1.0" encoding="utf-8"?>
<metalink version="3.0" generator="Metalink Editor version 1.0.0" xmlns="http://www.metalinker.org/">
  <publisher>
    <name>Package resources</name>
    <url>http://www.packages.ro</url>
  </publisher>
  <license>
    <name>GPL</name>
    <url>http://www.gnu.org/copyleft/gpl.html</url>
  </license>
  <identity>ubuntu-8.04-desktop-i386</identity>
  <version>8.04</version>
  <description>Ubuntu Linux Live CD</description>
  <files>
    <file name="hardy-desktop-i386.iso">
      <os>Linux-x86</os>
      <resources>
        <url type="http" location="us">http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-i386.iso</url>
      </resources>
    </file>
  </files>
</metalink>

The installer just crashes like any other windows program.  And no proxies for me.

---

### Post by ago on 2008-02-05
alpha-4 ISO is good for wubi-8.04 (any version), the daily-build is almost identical to the alpha-4 anyway and relevant wubi patches are not yet in. So use alpha-4.

---

### Post by nintennuendo on 2008-02-05
I downloaded the recent 8.04 alpha, and it installed.  I restarted my pc, chose Ubuntu on the boot menu, it wanted me to go through the standard setup, so I chose my location, then it said it was booting up the partitioner, then errord, and Asked if I wanted to cancel, continue anyway, or try again, so I tried again, then nothing happened.

I canceled the location map which was still open, then it went into the desktop halfway, closed, then went back into the desktop.  It now says I am using 7.10 and am a Live Session user, as if I were booting from the LiveCD.  What did I do wrong?

Edit:  It is slow to display and do things, just like the LiveCD, if that matters.  I had wubi and a genuine ubuntu dual-boot setup before, and they both were much faster than this.

---

### Post by ago on 2008-02-05
> **nintennuendo said:**
> I downloaded the recent 8.04 alpha, and it installed.  I restarted my pc, chose Ubuntu on the boot menu, it wanted me to go through the standard setup

Did you boot with the CD in the tray? 

Wubi installer is supposed to be non-interactive after reboot, if you are asked any question or have to press any button then there is a bug. If not reinstall press esc for verbose mode and submit any log + the output of "cat /proc/cmdline" (press ctrl+alt+f2 to get a shell).


> It now says I am using 7.10 and am a Live Session user, as if I were booting from the LiveCD.
Did you use 7.10 or 8.04 ISO? Did you use a CD? And with what wubi version?

> Edit:  It is slow to display and do things, just like the LiveCD, if that matters.  I had wubi and a genuine ubuntu dual-boot setup before, and they both were much faster than this.
That probably is the LiveCD environment

---

### Post by nintennuendo on 2008-02-05
I did not use a cd.  I downloaded the ISO that the 8.04 alpha downloaded.  It asked me the things it asks if you want to install from a LiveCD.  and I have no idea how to get that stuff you said to submit and log.

---

### Post by ago on 2008-02-05
Uninstall and reinstall
If you get to the point where you see  a country selector, press ctrl+alt+f2

and type:

cat /proc/cmdline

sign down the output exactly on a piece of paper and post it here.

Also see if the windows drive is under /host with

ls /host

If it is, copy the log files with the command:

sudo cp /var/log/syslog /host

Now you should be able to see the log file in windows and can post it here.

---

