---
title: "Failed to Initialize Hal...  Ubuntu 8.04..."
date: 2008-06-23
forum: General Help
---

### Post by casparov on 2008-06-23
Hi, Everyone...

This forum provided terrific help w/ a failed applications menu.  Now I can't seem to get things rolling because of an internal error: failed to initialize HAL.  

I am a new user and don't know what HAL is, precisely.  I have reviewed other posts on this topic and the remedies don't seem to apply (changing the logon to timed, for ex.) or using an older kernel.  Additionally, some of those which might are a bit beyond my comprehension.

I am currently booting to Windows via a separate disk. My booting into Heron w/ this error allows access to the administrative preferences but not the Net (Firefox can't find a server).  Also, The shutdown button is inactive. 

Does anyone have a link to a fix for this problem (or an explanation that involves a how to)?  

I appreciate any ideas anyone has,

Casp

---

### Post by |{urse on 2008-06-23
The HAL is your hardware abstraction layer.

please paste the output of

sudo lspci

you may have hardware going bad.

also paste the output of 

dmesg | tail

---

### Post by |{urse on 2008-06-23
at any rate your best bet is to 
1. try restarting the HAL
```
sudo /etc/init.d/hal stop
sudo /etc/init.d/hal start
```

(paste the output of step 1 if it gives you an error)

2. locate and replace the failing device (if it really is a failing device). Browse the content of 

```
dmesg
```

look for services that couldn't be started, this will usually help you sniff out the malfunction (paste the output of any errors of course so the community can help you determine their meaning)

3. IF ALL ELSE FAILS (in other words don't do this yet, I'm sure someone will give you an even better idea before you risk trying this)
*reinstall HAL.. (dangerous, may leave your system crippled, you know, like it already is)

```
sudo apt-get remove --purge hal
sudo apt-get install hal
```

---

### Post by casparov on 2008-06-24
|{urse... 

I tried doing things as you suggested w/ the following results:

1. Stopping and restarting HAL produced the following error upon restart: error while loading shared libraries: libpolkit.so.2

    Cannot open share object file: no such file or directory

2. dmesg produced a voluminous amount of recorded activity, which I cannot past because I cannot access the Net and cannot save and paste to my Windows disk for the following reasons: a. the Windows disk is NTFS, and b. the disk, suspiciously, does not appear in my Linux file structure--this could be the hardware error to which HAL refers.

I did get this much from the dmesg command results:

     Driver sd needs updating; please use bus type method
     Not locating disk.

I have always been able to locate my Windows disk within Linux and did nothing unusual prior to the boot which went wrong.  Moreover, I am using Windows now, and everything is nominal within W2000.   

So, I am indebted to your help.  Perhaps something here is usable.

All Regards,

Casp (Whit)

---

### Post by casparov on 2008-06-24
|{urse... 

I figured out what went wrong:  I did make a prior change to the system before this error plagued it. 

Just before logging off a couple of nights ago I got the bright idea to install a CD burning program located through Synaptic: K3b.  Well, I installed this, and it ran well from what I could tell from loading it for a preview.

But I am using Ubuntu and the program is KDE.  Somehow, it ruined the HAL initialization (so I surmised). 

I uninstalled K3b, and now everything is fine.  

Thank-you so much for your help.  I hope this will show other novices that mixing and matching Linux programs through Synaptic is not the best idea. 

All Regards,

Casp

---

### Post by |{urse on 2008-06-24
thats insane... but okies ^^ glad you got it sorted

---

### Post by casparov on 2008-06-24
...And you would know much better than I how insane...  

|{urse...  

I am pretty sure that's how HAL got screwed up.  Kubuntu-based applications must have some kernel differences (see, that's about all I know about Linux--just say kernel and something else; it's like saying something's wrong  w/ the solenoid in an electrical component) that can wreak havoc w/ different Linux flavors.  

I am always amazed, 

Casp

---

