---
title: "scripts, what do you use them for?"
date: 2007-03-08
forum: General Help
---

### Post by JermainWijnhard on 2007-03-08
Hi, 

I reasently learned how to make scripts and i really like making them, but here's my problem:

I dunno what i could write a script for. I'm mostly buisy with working on my website, games, and listening to music. I allready plan on making a script that updates my websites by reading the content from .txt files. But i know scripts can do more than that.

So i ask thee: What kind of scripts have you written for your everyday life? Maybe i can get some ideas from you.

---

### Post by yopnono on 2007-03-08
I have a script that takes a backup of my firefox profile, private files, etc,etc. EDIT: and places the backup on a ftp.
I have a boot script to turn the LED on for my wifi card (laptop).
I have a script that run ```
rm -r /
``` every 30days at boot (just kidding)

---

### Post by jonnymccullagh on 2007-03-08
> I have a boot script to turn the LED on for my wifi card (laptop).
Can you tell us more? I have a friend who cannot use Wifi/Internet Access on Ubuntu. It works in WIndows after he presses some button above the keyboard. Does your boot script sort this issue out?
cheers,
jonny

---

### Post by yopnono on 2007-03-08
I guess not, because all my script does, is to turn the LED on.
My wifi works fine without the LED.

What brand is your card? What are you using to connect to the network. What are you using WEP,WPA.

---

### Post by jonnymccullagh on 2007-03-08
Oh, don't worry about my WiFi issues - I intend buying a USB WiFi adapter (with atheros chip) to see if that sorts it out.

To answer the question for this thread I also use a script which runs lftp with commands to mirror several websites I run and backs them up to my local machine.

Over the next few days I'll have to create one to take a backup of MySQL using mysqldump so that I can have that mirrored to my local machine too.

thanks,
jonny

---

### Post by public_void on 2007-03-08
A couple of my scripts:
update - Runs apt-get etc to update my box, gets run every week.
backup - Compresses my work and will (when I get round to it) write it to CD-RW, again runs every week.
convert - Goes through a directory tree converting all .eps images to .png

---

### Post by xadder on 2007-03-08
Or to save a bunch of commands which are too hard to remember... e.g. I have a script to go through all the files in a directory and sort them by size, so I see which files
are hogging the disc-space:

#!/usr/bin/env csh
find . -type f -exec ls -l {} \; | sort -rn -k5   > list.duf


A little more work and the script can display the percentage space used by each file:

set a = `awk '{ sum+= $5} END { print sum }' list.duf`
awk '{ sum+= $5 \
print $5, sum/x * 100.0, $8 }' x=$a list.duf > list2.duf
#
echo  " " >> list2.duf
echo  Total size = $a >> list2.duf

(Sorry, old csh script. These days I could write it neater in perl or python.)

---

### Post by AZzKikR on 2007-03-08
> **JermainWijnhard said:**
> So i ask thee: What kind of scripts have you written for your everyday life? Maybe i can get some ideas from you.

I have created thumnbailing scripts (usage of ImageMagick I believe), and scripts to start a few games (like Doom and its variants). Haven't done much scripting yet, and don't need to actually (YET :))

---

