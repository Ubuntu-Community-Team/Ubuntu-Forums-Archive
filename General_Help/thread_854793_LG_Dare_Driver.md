---
title: "LG Dare Driver?"
date: 2008-07-09
forum: General Help
---

### Post by keenish27 on 2008-07-09
I did a quick search on the web but didn't find anything so I just figured I'd ask.  I just purchased an LG Dare and really don't want to use windows.  Are there any drivers out there so that I can connect my Dare to my PC and copy music and stuff over?  Or has anyone got it to work?

Thanks

---

### Post by hynd5224 on 2008-07-22
same here. i hate having to go to windows for stuff. if you want to just transfer like ringtones, bitpim has a linux version. i don't think it works with music though. 

-Charlie

---

### Post by RogueLeader on 2008-07-27
If your PC has a bluetooth adapter, you can transfer music, pictures, etc. easily.  I've used this method successfully with my Dare.  There are a few good guides floating around the Ubuntu forums about pairing a bluetooth phone with your PC, so I won't bother trying to rehash them here.  [https://help.ubuntu.com/community/BluetoothSetup]("https://help.ubuntu.com/community/BluetoothSetup") and [http://news.softpedia.com/news/Transfer-Files-With-Bluetooth-on-Ubuntu-47565.shtml]("http://news.softpedia.com/news/Transfer-Files-With-Bluetooth-on-Ubuntu-47565.shtml") are decent guides, for starters.

If you don't have a bluetooth adapter, they're not expensive.  I bought a cheap one for $1 off a Newegg special a few years ago for my tower.  My laptop (and most these days) came with one already.

As far as direct USB connections, I had some success using the development version of Bitpim.  (Actually, I just found out that you can even use the version 1.0.6 test release, there's a .deb for this on Bitpim's web site to make installation a breeze).  Within Bitpim, you need to manually set the phone as an LG-VX9100, then you will have access to the Phonebook, Calendar, Wallpaper, and Ringtone.  This is limited, obviously, as the Dare is a 9700, not a 9100, the two protocols just happen to be compatible.  Future version of Bitpim will almost surely have better support for the Dare, as it looks to be a popular phone, so you might as well at least install the program and poke around.

I've only used Bitpim to install user generated ringtones on my Dare and it works great.  It sure beats having to multimedia-message the file to yourself in order to save it as a ringtone.  For every other type of transfer (that is, regular music and photos), I found bluetooth file transfer sufficient.

---

### Post by Bladze DCOTL on 2008-09-05
I've tried setting it as the 9100, also the 9700 but the port is unavailable.  I am hoping that someone has found a fix for this, because all the posts I've been reading is that ppl are just plugging the dare in and having it auto recognize.  Here is a quick screen shot of what I'm seeing:

[ATTACH]84220[/ATTACH]

---

### Post by infinitelite on 2008-09-06
> **Bladze DCOTL said:**
> I've tried setting it as the 9100, also the 9700 but the port is unavailable.  I am hoping that someone has found a fix for this, because all the posts I've been reading is that ppl are just plugging the dare in and having it auto recognize.  Here is a quick screen shot of what I'm seeing:

[ATTACH]84220[/ATTACH]

I am having the exact same issue. It is not able to open the port. Not sure how to make it possible to open the port.

I keep trying things, tho. Hope to figure it out eventually...

---

### Post by infinitelite on 2008-09-06
Wait, no, just run it as root.

sudo bitpim

---

### Post by Kisil on 2008-10-24
I was able to get my Dare working by following some directions from Bitpim's website, with minor modifications.  I'm using the [latest version]("http://bitpim.org/#download"), not the Ubuntu version, so you'll have to download the .deb file and install manually.

You also have to create /etc/udev/rules.d/60-cell.rules  with the following contents (for a single user system):
```
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="cell_rules_end"

# LG Phone
SYSFS{idVendor}=="1004", SYSFS{idProduct}=="6000", MODE="0666"
LABEL="cell_rules_end"
```

Now if I follow these steps, my phone works:
1. plug in the phone
2. start bitpim
3. hit settings, then browse.  My phone appears in active devices; select it.
4. Now close settings and hit "Find Phone."  

Now everything works as expected, though I have some stability problems creating ringtones.

---

### Post by zstraub1 on 2008-11-24
see below (comp goofed)

---

### Post by zstraub1 on 2008-11-24
So I got Bitpim 1.0.6. I got Bitpim to recognize my phone (LG DARE Vx9700). Now I want to throw a playlist on the phone but Bitpim is having errors doing so. Apparently the format it uses is WPL, so I converted the playlist from M3U to WPL, and it still didn't work. 
Should I try getting Bitpim for windows, and run it on that side of my harddrive?
Basically what am I missing here?

---

### Post by rfurman24 on 2008-12-27
> **Kisil said:**
> I was able to get my Dare working by following some directions from Bitpim's website, with minor modifications.  I'm using the [latest version]("http://bitpim.org/#download"), not the Ubuntu version, so you'll have to download the .deb file and install manually.

You also have to create /etc/udev/rules.d/60-cell.rules  with the following contents (for a single user system):
```
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="cell_rules_end"

# LG Phone
SYSFS{idVendor}=="1004", SYSFS{idProduct}=="6000", MODE="0666"
LABEL="cell_rules_end"
```

Now if I follow these steps, my phone works:
1. plug in the phone
2. start bitpim
3. hit settings, then browse.  My phone appears in active devices; select it.
4. Now close settings and hit "Find Phone."  

Now everything works as expected, though I have some stability problems creating ringtones.


[SIZE="4"]To anyone who cares I used the above and the below to make my LG Rhythm work[/SIZE]

have the newest version of bitpim
make sure you have the drivers for the USB cable you are using.
open bitpim
let it find the phone(it will come up as other CDMA phone)
click FILESYSTEM on the left at the bottom
expand the folder
click dload
right click on lg_mysound.dat and save it to your desktop
after you save it right click lg_mysound.dat in bitpim and delete it
now click brew
click media
click lk
click ms

now drop the songs you want to use as ringers in this file. they will automaticlly load into your phone. it isnt the fastest process but it works.

after they are done loading onto the phone, unhook USB cable from computer, power the phone off and then back on.

the items you just transferred with now be in the my audio file where they need to be to assign them for individual ringers.

NOTE:

everytime you wnat to add new ringers to the phone you have to complete all the steps above, even the deleting that one certain file. not a very hard process and has worked well for me.

good luck and happy mp3 loading songs into the phone as ringers.

---

### Post by mjbauer95 on 2009-04-29
> **infinitelite said:**
> I am having the exact same issue. It is not able to open the port. Not sure how to make it possible to open the port.

I keep trying things, tho. Hope to figure it out eventually...

I'm having the same issue too. Anyone have anything else to try that might work?

---

### Post by merlin666 on 2009-09-04
Bitpim is not able to detect my Telus Lg-Dare in Ubuntu. It works fine in Windows. I am wondering if the USB driver is needed for this, but it seems there is no version available for Linux. Has anyone been able to connect a Telus Dare?

---

### Post by merlin666 on 2009-09-04
> **rfurman24 said:**
> [SIZE="4"]To anyone who cares I used the above and the below to make my LG Rhythm work[/SIZE]

have the newest version of bitpim
make sure you have the drivers for the USB cable you are using.
open bitpim
let it find the phone(it will come up as other CDMA phone)
click FILESYSTEM on the left at the bottom
expand the folder

Please let us know where to find drivers compatible with jaunty.

---

### Post by Nevermor7 on 2009-11-26
I am running Bitpim, but my phone does not connect.  I can connect it as a usb device, but I cant get the computer to recognize it as a phone, and thus, Bitpim will not find it... can't find any drivers... :cry:

---

