---
title: "why is my 4gb MicroSD card only showing less than 2gb in Gutsy?"
date: 2008-03-03
forum: General Help
---

### Post by vibe666 on 2008-03-03
I use it in my Nokia N95, but although I've tried using both the direct usb cable to my phone and using a microSD card reader i only see less than half of the total capacity of the disk and i get 'disk full' errors if i try and fill the drive any more than that.

it works fine in windows though, soI guess it's just a linux thing.

any ideas if there's a way to fix this?

thanks.

---

### Post by phillips321 on 2008-03-03
my 4gb works fine in ubuntu (n95 as well)

how did u format the card? in nix or on the phone?

---

### Post by vibe666 on 2008-03-03
formatted it in the phone.  figured it would be the best way to get the most out of it on the phone itself.  hadn't planned on it not working in other devices so didn't even consider a different format.

how did you do yours?

---

### Post by jken146 on 2008-03-03
Check the deleted items folder.  If that's not the problem then browse to the top level directory on the card, press Ctrl+H to view hidden files, and delete any folder starting with .Trash-  

If you're still stuck, please post the output of ```
sudo fdisk -l
``` and ```
df -h
```

---

### Post by vibe666 on 2008-03-03
it's not full, it's showing full capactiy (inc. 2gb+ of free space) in the phone and on windows pc's, the only problem is with accessing the card from ubuntu and trying to copy data to it.

---

### Post by fragos on 2008-03-03
The phone may not support more than 2GB SD cards so it can't format for more than that.  Cards formated for higher capacity may still work in the phone but perhaps only recognize the first 2GB.

---

### Post by vibe666 on 2008-03-04
the phone does support more than 2gb AND has already had just under 4gb of data put on it temporarily to test the card via a windows PC.

---

### Post by phillips321 on 2008-03-12
have u got the latest version of symbian on your phone?
(*#0000# displays it i think)

Download the nokia update tool from nokia.com and it'll auto check/update for you.

My N95 with 4Gb card gives me
V 12.0.013
19-06-7
RM-159
Nokia N95 (F2.02)


Have you tried access the card via a standard card reader over usb?

---

### Post by vibe666 on 2008-04-16
well, I'd just about given up on this and just put it down to a one off, but it's happening on multiple devices now.
I have a 4gb usb flash disk (a sandisk cruzer micro) and I have the same problems mounting it if there is more than 2gb of data on it.

I've attached the error I get when I insert it.

I get the same error now when I insert my 4gb microSD in either my phone or in a usb card reader.

I alsoo have an 8gb flash based ipod nano (current generation) which was working fine in ubuntu until I had ore than 2gb of mp3's on it.

on the opposite side of the fence, I recently bought a 1tb 3.5" usb drive which currently has over 500gb of data on it and it works flawlessly.

again, all these devices are properly recognised in windows xp.

anyone?

---

### Post by fragos on 2008-04-16
The size of flash that cen be read by any device is a driver issue. Some handheld devices won't recogine more than 1GB or 2GB. There is also the issue of on disk format, e.g. FAT16, FAT32, EXT2, etc. Ubuntu should be able to read and write the full capacity regardless of format -- mine does.

---

### Post by vibe666 on 2008-04-17
I'm going to say it again for the people at the back of the room who haven't managed to read what I've been saying so far.

I don't have problems with my phone reading the card, that works just fine.  I don't have problems with my mp3 player, it can read _its own memory_ just fine and I reguarly use my usb memory stick in 4 or 5 different (windows) PC's and it works _just fine_.

what doesn't work fine is any of these devices in ubuntu once they are using more than 2gb of space.  until then it sees them, but once it's using more than 2gb of space on each device it fails to mount every single one of them.

---

### Post by cometa2k7 on 2008-04-21
> **fragos said:**
> The phone may not support more than 2GB SD cards so it can't format for more than that.  Cards formated for higher capacity may still work in the phone but perhaps only recognize the first 2GB.

Your phone is probably like mine, it only supports FAT16. FAT16 is limited to 2Gb.

However, I managed to use GParted to format my 8Gb card into 4Gb partitions which were FAT16. However, my phone can'y access on of them, so I have to leave it as free space.

---

### Post by vibe666 on 2008-04-24
**[SIZE="5"]_I DON'T HAVE ANY PROBLEM WITH MY PHONE READING ANYTHING!!!_[/SIZE]**

I'm having a problem with UBUNTU reading the memory card.  the fact the card is from a phone is TOTALLY irrelevent.

I'm not using my 8gb ipod nano inside my phone am I?

I'm not stuffing my 4gb USB drive inside my phone and then trying to read that am I?

NO I'M NOT, and none of these things will mount either.  

IT'S NOT THE PHONE, in fact I don't even have it any more, I upgraded to an 8GB N95.  Are you going to tell me that can't read more than 2GB either? 

my **_ONLY_** problem is that OO-FREAKING-BUNTU will not read any flash based storage over 2 freaking gigabytes **_AT ALL_** no matter how it's formatted.

my god I hope you people aren't the only thing keeping this project afloat.

---

### Post by fragos on 2008-04-24
> **vibe666 said:**
> **[SIZE="5"]_I DON'T HAVE ANY PROBLEM WITH MY PHONE READING ANYTHING!!!_[/SIZE]**

I'm having a problem with UBUNTU reading the memory card.  the fact the card is from a phone is TOTALLY irrelevent.

I'm not using my 8gb ipod nano inside my phone am I?

I'm not stuffing my 4gb USB drive inside my phone and then trying to read that am I?

NO I'M NOT, and none of these things will mount either.  

IT'S NOT THE PHONE, in fact I don't even have it any more, I upgraded to an 8GB N95.  Are you going to tell me that can't read more than 2GB either? 

my **_ONLY_** problem is that OO-FREAKING-BUNTU will not read any flash based storage over 2 freaking gigabytes **_AT ALL_** no matter how it's formatted.

my god I hope you people aren't the only thing keeping this project afloat.

Your attitude leaves a lot to be desired. Perhaps if you insult the members of forum more you'll find an answer.

---

### Post by vibe666 on 2008-04-24
An answer?

are you joking?

i've tried being nice and patient, but there's only so much a person can take.

perhaps if someone with a brain was looking at these forums I wouldn't have to repeat myself **_6 times_** and I wouldn't be so insulting.

every time I clearly explain the problem I'm having the same 3 or 4 idiots keep repeating the same irrelevent thing without even reading what's been posted.

and they say ipod users are sheep.

---

### Post by cometa2k7 on 2008-04-25
> **vibe666 said:**
> An answer?

are you joking?

i've tried being nice and patient, but there's only so much a person can take.

perhaps if someone with a brain was looking at these forums I wouldn't have to repeat myself **_6 times_** and I wouldn't be so insulting.

every time I clearly explain the problem I'm having the same 3 or 4 idiots keep repeating the same irrelevent thing without even reading what's been posted.

and they say ipod users are sheep.

It's an annoying problem, that not a lot of people get, and there isn't much that you can do to help it. But seriously, getting in a stress won't help. You say that you've tried being patient, just try some more.

I'm feling nice, so I'll give you a suggestion.

In a terminal

```
$ sudo gedit /etc/fstab
$ sudo mkdir /media/usb1
$ sudo chown user:user /media/usb1 (might be wrong, but I think you need to own it)
$ sudo gedit /etc/fstab

```

Add this line to the bottom of you FSTAB

```
/dev/sdb1 /media/usb1 vfat auto,sync,rw,user 0 0
```

N.B.
Your device might not be sdb1.
You need to change "vfat", to whatever filesystem your device uses.
The "chown" part of the code may be wrong, I'm not too used to that.


This may not work, but it seemed to help my problem.

---

### Post by orethrius on 2008-04-25
I'm just wondering out loud here, does Gutsy even support SDHC yet?  As I recall, 2GB is the limit from the older, non-highcap SD format.

---

### Post by Tux.Ice on 2008-04-25
navigate to your card so you can browse the files then hit ctrl+h if there is a .trash-[COLOR="Black"]*USER*[/COLOR] delete it.

---

### Post by vibe666 on 2008-04-26
> **cometa2k7 said:**
> It's an annoying problem, that not a lot of people get, and there isn't much that you can do to help it. But seriously, getting in a stress won't help. You say that you've tried being patient, just try some more.cometa2k7, thank you for one of the first helpful intelligent posts in this thread (yes I know, including my own!).  I really really trying to be patient, but for yet another 2 examples of the kind of thing I'm talking about, check out the two posts sitting between your last post and mine.

over and over again I've tried to clearly explain what my problem is, but over and over aain, people do not read what I've said (well, past the title of the thread at least) and post stupid comments that have absolutely nothing to do with the problem.

if the thread was 75 pages long and someone had skipped through then yeah, no problem nobody wants to read 75 pages of posts, but there's less than 20 posts here, it's hardly like having to read the bible.

I've been on the net for years, in dozens of forums with thousands of posts and I don't think I've ever encountered such a large percentage of brainless posts in one place before.  seriosuly, I'm not trolling or name calling, just stating the truth.  i know there's the odd troll in most forums, but i don't even think that's what this is.

don't get me wrong, I'm sure all these people are very nice in real life, they just don't seem to be able to think (or read) before they post and when I constantly have to repeat the most basic things over and over again  my tolerence for muppetry drops right down to zero.

when the shoe is on the other foot, i'm more than happy to help anyone out whenever I can, but having to constantly repeat myself because people refuse take a moment to read a few lines of posts and then post irrelevent nonsense themselves thinking that they're helping when in fact they're doing the opposite, just gets on my tits.

---

