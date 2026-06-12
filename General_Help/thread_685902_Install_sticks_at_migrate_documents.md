---
title: "Install sticks at migrate documents"
date: 2008-02-02
forum: General Help
---

### Post by chappell101 on 2008-02-02
Hi recently built a fresh system & wanted to put wubi back on alongside my windows install. Unlike my previous system which installed wubi correctly with wubi 7.10 rev385  and also worked on my hp laptop, i now get this error with both wubi 7.10 rev386 and 8.04rev397.

Warning: Unrecognised partition table for drive 80.  Please rebuild it using a Microsoft-compatible FDISK tool(err=115). Current C/H/S=16383/16/63

Then ubuntu starts loading and begins the live cd install but then gets stuck at the Migrate Documents and Settings install window where it see's my windows user account but the forward button stays greyed out if i click to import my user setting or not. 

I'm wondering if the problems are that I'm using the windows xp release candidate SP3 on my system, or that I'm using a Weston Digital 10000rpm Raptor drive.
as these are the only notable differences i would imagine would make any difference compared to my previous installs though i have read that my motherboard can be a bugger sometimes with ubuntu partition problems. This is my main problem is it safe to use ubuntu at all wubi or not on this pc as i can't risk loosing my windows partition.

If so i will have to come to terms with this but i have been a ubuntu user for over 2 years now and have it as the only operating system on 5 out of 7 systems, it will be a shame that my new workhorse is a linux no go!

Regardless here is my computer spec:
Motherboard Asus M2N-VM DH
CPU AMD Athlon X2 6000+
RAM Geil DDR2 Dual Channel 2GB 800MHZ
HD Weston Digital Raptor 10000RPM 150GB
GPU Nvidia X-Vision 8800GTX
Media Lite-On(lightscribe) DVDRW LH-20A1H

Anyway keep up the good work and i have been a very happy and thankful user of wubi since 7.04 to enable an easy install on a umpc, to see what Ubuntu is like without partitioning a very small hard disk.

Also I'm presuming there is no problem with wubi and setting up a dual boot for a hackintosh system as long as the Microsoft boot loader is still accessible after which ever boot loader i use to see Darwin.

Thanks M.Chappell

---

### Post by ago on 2008-02-02
You can disable migration-assistant by commenting out the respective section in /ubuntu/install/custom-installation/preseed.cfg (wubi 8.04).

But it would help if you could provide the log file in /var/log/syslog (press ctrl+alt+f2).

One thing I do not understand though is that there should be no forward button, you should only see progress bars (unless you are using kubuntu).

---

### Post by chappell101 on 2008-02-02
OK I've commented out the migration assistant section and I'm using standard ubuntu hardy alpha 4 but what do i need to type to save the log file say to a flash disk so i can attach here if i have to boot back into windows?

Sorry i've only learnt so much using it over the last couple of years as i've had a very easy ride with ubuntu till now on various platforms!

Also while i'm asking do you know if a remastersys image of a wubi system would still create a working live dvd image or does that have to come from a full partitioned install.

Thanks

---

### Post by ago on 2008-02-02
> **chappell101 said:**
> OK I've commented out the migration assistant section and I'm using standard ubuntu hardy alpha 4 but what do i need to type to save the log file say to a flash disk so i can attach here if i have to boot back into windows?
You need to install with an unedited preseed.cfg so that the error is repeated.

Pres ctrl+alt+f2 to get a console
sudo cp /var/log/syslog /host

now the log should be accessible from C:

> Also while i'm asking do you know if a remastersys image of a wubi system would still create a working live dvd image or does that have to come from a full partitioned install.

If you use wubi 8.04 should be good enough. Not so sure for 7.10.

---

### Post by chappell101 on 2008-02-02
I did  fresh install with an untouched preseed file and sudo copied the log directory to my host but all i can see in my c drive is wubildr.mbr,wubildr,.rnd is it any of these as they most are grub stuff or jibberish

anyway here is the 2 wubi files

---

### Post by ago on 2008-02-02
I need only the syslog

---

### Post by chappell101 on 2008-02-02
There wasn't one in my c: drive the first time, so i tried again and nano'd the folder first to see if it was even producing a log, it was, so here is the output! why it didn't produce one the first time i have no idea.

Thanks for any help.

---

### Post by ago on 2008-02-03
Thanks

---

### Post by NitroZZeLLo on 2008-02-03
Hello Ago,

I have the very same problem, I have tried to comment out the migrate section in the preseed.cfg and nothing happens.

I have used the three versions of Wubi and the problem remains the same.

Looks like there is another preseed.cfg somewhere but I have not been able to find it.

---

### Post by chappell101 on 2008-02-03
I also tried commenting out the migration assistant this morning on a fresh install again but it came to the same result as last nights without.

---

### Post by NitroZZeLLo on 2008-02-03
Dont worry,

Once you get to the migration page, cancel it, you will be taken automatically to the live installation of Ubuntu, once there open terminal and write "ubiquity --automatic" and that is all.

---

### Post by ago on 2008-02-03
Are you all using windows SP3 by any chance?

---

### Post by NitroZZeLLo on 2008-02-03
Hello Ago,

The actual sp3 package not quite but my windows have the latest patches, etc.. that comes from Micros... automatic updates.

---

### Post by ago on 2008-02-05
Can you please try with 8.04?
If you still have issues I will give instructions to produce a more interesting log (basically running ubiquity -d and looking into /var/log/installer/debug)

---

### Post by chappell101 on 2008-02-06
HI i just tried wubi 8.04 rev398 with today's live cd build and it installs on the windows side fine and adds itself to the Microsoft boot list but when i chose ubuntu it just makes my computer restart immediately. I'll try again later with alpha 4 as i knew that worked to get a you a debug file if needed.

---

### Post by ago on 2008-02-06
rev398 is broken, use rev397, you can reuse the same alpha-4 iso (note: requires manually editing menu.lst if target partition is not the first one)

---

### Post by chappell101 on 2008-02-07
Ok i tried the new 8.04 rev398 and today's live cd build and i still get the same issue, then when i tried running 'ubiquity -d' it started as if a normal live cd install with each page of the window for me to click and make choices through, i then did so and it finished to reboot leaving me no time to copy the debug log. I went to copy it after the reboot but the debug data wasn't stored. 

First do i need to copy the debug directory before starting 'ubiquity -d' as the system goes for a reboot upon completion.

Second is 'ubiquity -d' right as i got the live cd installer not the auto installer or should it be 'ubiquity --automatic -d' as 'ubiquity --automatic' works if i quit and then start it from terminal.

---

### Post by ago on 2008-02-08
> **chappell101 said:**
> Ok i tried the new 8.04 rev398 and today's live cd build and i still get the same issue, then when i tried running 'ubiquity -d'

Do the following, remove "automatic-ubiquity" from the boot menu (press esc at boot, then "e" to edit the line). You will boot in the desktop environment. Open a shell and run:

ubiquity -d --automatic

Then copy /var/log/syslog and /var/log/installer/*

---

