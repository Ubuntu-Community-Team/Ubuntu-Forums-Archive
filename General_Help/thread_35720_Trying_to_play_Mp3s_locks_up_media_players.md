---
title: "Trying to play Mp3s locks up media players"
date: 2005-05-20
forum: General Help
---

### Post by crazeinc on 2005-05-20
I can load the file and it'll display the title, length, and so on, but when I press play all of the applications lock up. On the other hand, it plays CD's perfectly. Any ideas?

---

### Post by crazeinc on 2005-05-20
[QUOTE=crazeinc]I can load the file and it'll display the title, length, and so on, but when I press play all of the applications lock up. On the other hand, it plays CD's perfectly. Any ideas?[/QUOTE]
 anybody?

---

### Post by Zelut on 2005-05-20
Is this JUST for mp3s or do you get the same problem with .wma, .ogg, etc?  Also, have you installed the mp3 codecs?  They are not standard with the basic installation & need to be installed.  If you need the codecs let me know & I can send you a .deb.

---

### Post by crazeinc on 2005-05-20
[QUOTE=kuyaedz]Is this JUST for mp3s or do you get the same problem with .wma, .ogg, etc?  Also, have you installed the mp3 codecs?  They are not standard with the basic installation & need to be installed.  If you need the codecs let me know & I can send you a .deb.[/QUOTE]
 actually, it does appear to lockup with .wma and ogg as well. I ran through the ubuntuguide, but I don't remember if that installs the mp3 codecs. If it doesn't, I'd appreciate if you sent the deb to me. [email]pjhyett@gmail.com[/email]

---

### Post by Stormy Eyes on 2005-05-20
[QUOTE=crazeinc]I can load the file and it'll display the title, length, and so on, but when I press play all of the applications lock up. On the other hand, it plays CD's perfectly. Any ideas?[/QUOTE]

I've noticed this as well with Rhythmbox. I'm going to switch to BMP (sudo apt-get install beep-media-player)

---

### Post by dmccarney on 2005-05-20
Ok, I'm having a very similar problem with a slight twist.
I have a 160 gig external maxtor hard drive formatted in NTFS
To complicate matters futher this hard drive is in a USB 2.0 External kit that does not officially support Linux. Much to my delight when I installed Ubuntu it saw it right away. This is the primary location of all of my mp3s. Naturally I installed the mp3 drivers by following the ubuntu guide steps. I've been using Rythmbox for awhile now and it can play the mp3s no problem off of the external NTFS drive. Now here is where the trouble starts... Personally I've been using winamp for years and find the Itunes style interface of Rythmbox to be a pain in the ass, I found both XMMS and Beep Media Player to be alot more my style. They also can load my mp3 files off of my external NTFS drive and display all the tag info etc. BUT as soon as I click play on either, the application freezes and I have to kill it from console.

I'm pretty sure I have the correct mp3 drivers because as stated before, the default "media-player" plays them no problem. It is just XMMS and its derivative Beep that can't play them :(

Any help would be greatly appreciated.

---

### Post by dmccarney on 2005-05-21
I've managed to fix my problem with Beep Media Player. 
If anyone is interested this is how I did it:
1) Open Beep
2) Right click the beep gui
3) Click preferences
4) Click the Plugins tab on the right side of the screen (icon is a little electrical plug)
5) Choose the "output" tab on the top right of the preferences screen
6) Under "Current Output Plugin" change it from "OSS Output Plugin" to "eSound Output Plugin"
7) Rock out.

After that Beep could play all of my mp3's off of my external NTFS drive.  :) 

* Note: Step 7 is optional but recommended.*

---

### Post by himuraken on 2005-05-21
This seems to be a somewhat common/widespread issue. I had xmms locking up, mpg321 failing, and mplayer playing video but without sound. Obviously make sure you have the proper codecs installed. Check the multimedia systems selector. Uncheck the sound server startup option. Check to see if you are running ESD. Then get a command line/terminal window open and try:

killall -9 esd

This resolved my issue. It seems that ESD was hogging access to the /dev/dsp and wouldn't allow other programs to access it. I hope that this helps. By the way, my sound card is an onboard nForce2.

---

