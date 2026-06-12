---
title: "Terminal commands for data recovery on remote server"
date: 2016-09-04
forum: General Help
---

### Post by naris2 on 2016-09-04
Long story short a black out totally screwed my NAS.  I'm trying desperately to get data off of the drive without paying for it, as I can't afford it.  I'm able through the software to reinstall, but obviously I want the data, so the good news is I probably still have a NAS.

Anyways, I tried to retrieve data on Windows and no go.  The people that manufactured the NAS suggested I try Linux.  I have some experience with Ubuntu because it is more GUI friendly, so I put a live cd in.  The GUI doesn't detect the server either, but I was wondering if I would have better luck with the terminal.

The problem is I can't find any documentation through google on my specific situation.  I'm hoping someone could give me commands that I could use to find the server if it is responsive, and retrieve the data.  You don't have to spell out step by step, but commands I can get information about in the terminal.  What's the command for help in Linux?

I also wanted to say I love Ubuntu, the concept of Ubuntu, but as I understand it games don't work really well with Linux.  If games worked well with Linux, I would be onboard with Linux anyday.  Specifically Ubuntu.

Well I would really appreciate this help.  It would really help a person  out.  I appreciate your time.

---

### Post by steeldriver on 2016-09-04
What kind of NAS is it (make, model)? What is "the software" through which you are given the option to re-install (are you referring to some kind of web interface?)

I have some experience with helping people recover data from NAS disks - but that involves removing the disks physically from the unit and connecting them directly to the Linux system. But let's not go there yet.

---

### Post by naris2 on 2016-09-04
If I was a billionaire I would buy you something.  Holy crap.

Here is the make and model:[SIZE=3]  [SIZE=2]Seagate STBN2000100 2TB Business Storage 2-Bay NAS.

As I understand it, the OS went into "basic" mode, and when I connect to it through the browser, there is no username and password which is strange.  There is only one page.  That page is to wipe the drives and re-install.

I am willing to try anything to get the data off of this drive.  Have you been able to retrieve data from the drives and still have the NAS work when it reinstalls?

THANK YOU.[/SIZE]

[/SIZE]

---

### Post by steeldriver on 2016-09-05
Well - don't get your hopes up too high

If the device has reset to some kind of default state, then almost certainly the only way to get data off the disk(s) will be to remove them and connect them directly to your Linux system (e.g. in an external SATA enclosure)

[Some NAS boxes support - usually unofficially - low-level access such as SSH - but that's something you would have had to have set up in advance - and would probably be disabled again in the default state]

---

### Post by naris2 on 2016-09-05
So I have one of the hard drives hooked up to an adapter that I have that takes any internal hard drive and plugs it in the USB port.  I tried Linux first and it didn't see a thing.  Windows sees 9 partitions, simply because the file system is all screwed up.  I'm using a Windows based program right now to see if the data is recoverable (taking 8+ hours to scan), however it says in its documentation that NAS systems use a Linux based file system, and may make things unrecoverable on that specific program's end.

With the hard drive attached locally to my computer...

What are some commands that I should look up?  Because the GUI on the Live CD does not pick anything up.

Thanks.

---

### Post by steeldriver on 2016-09-05
What "GUI on the Live CD" are you referring to exactly? did you try gparted?

From a terminal, I'd start with

```

sudo parted -l

```

(that's a lower case L - for 'list' - not a 1)

---

