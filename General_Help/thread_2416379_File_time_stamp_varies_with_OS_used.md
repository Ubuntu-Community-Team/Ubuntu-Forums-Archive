---
title: "File time stamp varies with OS used"
date: 2019-04-09
forum: General Help
---

### Post by bateybates on 2019-04-09
When connecting a digital voice recorder to computer via USB, the WMA files it creates have a different time stamp, depending on what Operating System I use to view it. This is a problem as saving the files to hard drive creates a file with the wrong time - it is an hour ahead.

I have a file on the recorder created at 10:16 today and the time shows up correctly on the recorder as 10:16

If I view the file via the computer using Mint 17.1 (Linux Mint 17.1 features Cinnamon 2.4, MDM 1.8, a Linux kernel 3.13 and an Ubuntu 14.04 package base.) ,  the file time shows up correctly in file browser and also with stat :

Viewing the file with stat on Mint 17.1 (time shows up correctly):
username/WS_650S/RECORDER/FOLDER_D $ stat WS651938.WMA
  File: &#8216;WS651938.WMA&#8217;
  Size: 282314        Blocks: 576        IO Block: 32768  regular file
Device: 831h/2097d    Inode: 100         Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/   username)   Gid: ( 1000/   username)
Access: 2019-04-09 00:00:00.000000000 +0100
Modify: 2019-04-09 10:16:52.000000000 +0100
Change: 2019-04-09 10:16:34.000000000 +0100
 Birth: -

(and if saved to hard drive it saves with correct time)

Viewing the same file via Ubuntu 18.04.2 - the time shows up as 11:16 instead of 10:16 :
username/WS_650S/RECORDER/FOLDER_D$ stat WS651938.WMA
  File: WS651938.WMA
  Size: 282314        Blocks: 576        IO Block: 32768  regular file
Device: 831h/2097d    Inode: 101         Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/   username)   Gid: ( 1000/   username)
Access: 2019-04-09 01:00:00.000000000 +0100
Modify: 2019-04-09 11:16:52.000000000 +0100
Change: 2019-04-09 11:16:34.000000000 +0100
 Birth: -

I've noticed this problem with more than one type of digital voice recorder, but it does not show up when saving files from a camera via USB.

I'd be grateful if anyone can shed light on this problem.

---

### Post by SeijiSensei on 2019-04-09
Do both OS's have the right timezone? Compare /etc/timezone to see. Daylight savings time?

---

### Post by bateybates on 2019-04-09
I've just checked and the entire contents of that file (/etc/timezone), in all the operating systems, is "Europe/London"  (without the quotes).

You may be onto something with the mention of Daylight saving time - it is something I've never had to think about before and have never looked into, but however it works, surely it should not be changing the time of a file from an external device? (The digital voice recorders don't have a time zone setting - they simply stamp the file with date and time as far as I can see and I've never noticed a problem with this being read wrongly before)

---

### Post by Impavidus on 2019-04-09
Undoubtedly timezone confusion. What's the used filesystem? What's your timezone? I think one the systems assumes the file modification time as stored in the filesystem is local time, the other OS thinks it's UTC.

It looks like Mint correctly assumes the time is stored as local time, whilst Ubuntu assumes it's UTC. Stat then shows it in local time (which, according to stat, is UTC+1).

Of course, UTC works better. Imagine you use local time, make a recording in Calais, take the train to Folkestone and plug the recorder in your computer. The files will be from the future.

Edit: Didn't read your last post before I posted this.

---

### Post by sisco311 on 2019-04-09
Is the output of:```
timedatectl
```identical on both OS's?

---

### Post by bateybates on 2019-04-09
Local time - identical
Universal time - identical
RTC - not shown on older OS
am not sure about the others - can you take a look?

timedatectl results

================
Ubuntu 18.04.2 (adds 1 hrs to external device time)
(at 17:30 local time)

:~$ timedatectl
                      Local time: Tue 2019-04-09 17:30:11 BST
                  Universal time: Tue 2019-04-09 16:30:11 UTC
                        RTC time: Tue 2019-04-09 16:30:11
                       Time zone: Europe/London (BST, +0100)
       System clock synchronized: no
systemd-timesyncd.service active: yes
                 RTC in local TZ: no


===========================
Mint 17.1 [based on Ubuntu 14.04?]  (shows external device time correctly)
(at 17:25 local time)

 ~ $ timedatectl
      Local time: Tue 2019-04-09 17:25:13 BST
  Universal time: Tue 2019-04-09 16:25:13 UTC
        Timezone: Europe/London (BST, +0100)
     NTP enabled: yes
NTP synchronized: no
 RTC in local TZ: no
      DST active: yes
 Last DST change: DST began at
                  Sun 2019-03-31 00:59:59 GMT
                  Sun 2019-03-31 02:00:00 BST
 Next DST change: DST ends (the clock jumps one hour backwards) at
                  Sun 2019-10-27 01:59:59 BST
                  Sun 2019-10-27 01:00:00 GMT


==========================
Mint 19.1 [based on Ubuntu 18.04?]  (adds 1 hr to external device time)
(at 17:16 local time)

:~$ timedatectl
                      Local time: Tue 2019-04-09 17:16:52 BST
                  Universal time: Tue 2019-04-09 16:16:52 UTC
                        RTC time: Tue 2019-04-09 16:16:52
                       Time zone: Europe/London (BST, +0100)
       System clock synchronized: yes
systemd-timesyncd.service active: yes
                 RTC in local TZ: no

===========================

File system on all Operating systems is ext4
File system on USB external device is fat16

---

