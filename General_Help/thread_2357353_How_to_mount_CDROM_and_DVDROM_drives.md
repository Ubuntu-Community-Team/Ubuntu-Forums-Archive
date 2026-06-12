---
title: "How to mount CDROM and DVDROM drives?"
date: 2017-04-01
forum: General Help
---

### Post by lysander6662 on 2017-04-01
I have one CDROM and one DVDRW drive but I do not know how to mount them so I can play disks. Ubuntu sees the drives, this is the output of** sudo lshw -C** disk for them:

```

  *-cdrom:0
       description: DVD reader
       product: DVD+RW ND-2100AD
       vendor: _NEC
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/sr0
       version: 103D
       serial: [
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: DVD writer
       product: DVD_RW ND-2510A
       vendor: _NEC
       physical id: 0.1.0
       bus info: scsi@4:0.1.0
       logical name: /dev/dvdrw
       logical name: /dev/sr1
       version: 2.15
       serial: [
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc


```

I have tried to mount them in the Disks utility with no luck. Here's what they look like in there:

[ATTACH=CONFIG]274390[/ATTACH]

[ATTACH=CONFIG]274389[/ATTACH]

Any idea what I'm doing wrong?

---

### Post by Impavidus on 2017-04-01
It says "No Medium". When no disk with a file system is present, it cannot be mounted. Are you talking about audio cds? I don't think they have a proper file system, the player would read /dev/sr0 directly and process it itself.

---

### Post by lysander6662 on 2017-04-01
Primarily the problem is DVDs and DVD ROMs. I changed the jumpers on the back of the drives and hooked the IDE cable up correctly so the right drive was on the master/slave connector. CDROM I have as slave, DVD RW as master.

I managed to get the cdrom drive [which is actually confusingly a DVD reader drive!] to mount with the command

```
sudo mount /dev/sr1 /mnt/cdrom
```

This drive now loads software CDs and can play audio CDs. It also autoloads, which is excellent. This hasn't been the case for years [this is a drive I got with my first Dell in 2004, amazed it still works]. However, it cannot play DVD ROMs or DVD videos [and it used to], which I want as its main purpose - that's the important thing.

The other DVD drive cannot do anything at present! Even with the same software CD in that I mounted the other drive with I still get

```
lysander@psychopig-xxiii:~$ sudo mount /dev/sr0 /mnt/dvdrw
mount: no medium found on /dev/sr0

```

---

### Post by ajgreeny on 2017-04-01
Excuse the obvious but possibly seemingly rude question, but in a machine from 2004, are you 100% sure that the drive is actually able to read DVDs and is not just a CD drive?

Is it just commercial DVDs videos that can not be seen or is it the same with data DVDs?

---

### Post by lysander6662 on 2017-04-01
> **ajgreeny said:**
> Excuse the obvious but possibly seemingly rude question, but in a machine from 2004, are you 100% sure that the drive is actually able to read DVDs and is not just a CD drive?

Is it just commercial DVDs videos that can not be seen or is it the same with data DVDs?

Yes indeed, it could play DVD videos, but that's a fair question. It was set to region 3 since I used to play a lot of videos from Hong Kong. The other drive was set to region 0. However, last time I remember using either drive they would both pretty much play anything, no matter the region [this was in Windows].

And yes, it cannot play data DVDs either. But CDroms and audio CDs are fine, for some reason.

---

### Post by lysander6662 on 2017-04-01
Anyone have any clue? This is driving me mad, I have been doing it all day. The first serious problem I've had so far. I'm wondering if this would be easier in other distros [probably not] but I'm astounded that I'm coming up against so many problems with it.

---

### Post by Geoffrey_Arndt on 2017-04-01
And just to be sure, in all cases (CD or DVD & all physical optical drives) . . . . . you are inserting the media first . . . and then, if the system does not see the media and auto-mount, then you are trying the manual mount process?

Also,  have you read this recent info on optical media under Linux?    [https://linuxconfig.org/how-to-mount-cdrom-in-linux](https://linuxconfig.org/how-to-mount-cdrom-in-linux)

---

### Post by mc4man on 2017-04-01
No longer have desktop machines so just a comment or two based on past..
Both of the drives are dvd drives that can do read & writes. The ND-2100AD is likely less capable &  Dell oem.

So which device is the problem one (model, not what you term cdrom/dvd) and what is it jumpered as?
The Dell desktops I had way back when typically shipped dvd/cdrom devices with a cable select ide cable and devices jumpered as such. So what cable type do you have? (40 pin, cs cable, 80 pin
You might want to browse thru various logs like syslog or does & see if any errors or warnings on the devices and/or dma, ultra dma

---

### Post by lysander6662 on 2017-04-01
> **Geoffrey_Arndt said:**
> And just to be sure, in all cases (CD or DVD & all physical optical drives) . . . . . you are inserting the media first . . . and then, if the system does not see the media and auto-mount, then you are trying the manual mount process?

Also,  have you read this recent info on optical media under Linux?    [https://linuxconfig.org/how-to-mount-cdrom-in-linux](https://linuxconfig.org/how-to-mount-cdrom-in-linux) Yes indeed, this is the output of attempts to mount the currently non working DVD drive. 

```
sudo mount /dev/sr0 /mnt/dvdrw
[sudo] password for lysander: 
mount: no medium found on /dev/sr0
```

This is strange because there is media in the drive, and the same media that was detected and playable by sr1!

---

### Post by lysander6662 on 2017-04-01
> **mc4man said:**
> No longer have desktop machines so just a comment or two based on past..
Both of the drives are dvd drives that can do read & writes. The ND-2100AD is likely less capable &  Dell oem.

So which device is the problem one (model, not what you term cdrom/dvd) and what is it jumpered as?
The Dell desktops I had way back when typically shipped dvd/cdrom devices with a cable select ide cable and devices jumpered as such. So what cable type do you have? (40 pin, cs cable, 80 pin
You might want to browse thru various logs like syslog or does & see if any errors or warnings on the devices and/or dma, ultra dma 

Sorry, missed this since I had the page idle for a while. 

Yes, one of those would be Dell OEM I think from way back. Both devices have problems, but thinking of the answers to your questions cedes confusing results, here is why. The drive which is the Dell, DVD+RW ND-2100AD, is currently sr1 [or mounted as such], but the output in the OP shows it as sr0. Very weird, maybe I did something wrong. This drive can play audio CDs but not DVD ROMs or videos. It is jumpered as slave and on slave IDE 40pin which is a shared IDE cable with the master.

The other drive, DVD_RW ND-2510A, is sr0, even though the output says sr1 in the OP! This drive currently can't do anything. This is jumpered as master and on the master part of the same IDE cable as the slave.

---

### Post by mc4man on 2017-04-01
Myself always replaced the Oem 40 pin cable with an 80 pin Ultra Dma one so only from memory - i think if the 40 pin is a csel cable then master is middle connector & slave is the end one. On a 'normal' 40 pin it's the opposite. So maybe try switching the jumpers or switching cable positions

---

