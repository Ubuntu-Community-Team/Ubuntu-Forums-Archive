---
title: "Tvtime problems"
date: 2005-07-08
forum: General Help
---

### Post by dc2447 on 2005-07-08
Hi - I am trying to get [this tv card ](http://www.kworldcomputer.com/product/PVR-7134/PVR-7134.html) working under Hoary.

On fedora on a different PC, I just had to do:

> modprobe saa7134 card=43 tuner=2
modprobe bttv


And I'm up and runng, but on Ubuntu I can't scan for channels:

> davidcam@vader:~$ sudo modprobe saa7134 card=43 tuner=2
davidcam@vader:~$ sudo modprobe bttv
davidcam@vader:~$  tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Scanning using TV standard PAL.

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.



have I missed something?

Here are the relevant outpus:

> davidcam@vader:~$ lspci | grep SAA7134
0000:00:0a.0 Multimedia controller: Philips Semiconductors SAA7134 (rev 01)
davidcam@vader:~$


> Linux video capture interface: v1.00
saa7130/34: v4l2 driver version 0.2.12 loaded
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 18
saa7134[0]: found at 0000:00:0a.0, rev: 1, irq: 18, latency: 32, mmio: 0xde000000
saa7134: <rant>
saa7134:  Congratulations!  Your TV card vendor saved a few
saa7134:  cents for a eeprom, thus your pci board has no
saa7134:  subsystem ID and I can't identify it automatically
saa7134: </rant>
saa7134: I feel better now.  Ok, here are the good news:
saa7134: You can use the card=<nr> insmod option to specify
saa7134: which board do you have.  The list:
saa7134:   card=0 -> UNKNOWN/GENERIC
saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
saa7134:   card=3 -> LifeView FlyVIDEO2000                    5168:0138
saa7134:   card=4 -> EMPRESS                                  1131:6752
saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
saa7134:   card=6 -> Tevion MD 9717
saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
saa7134:   card=9 -> Medion 5044
saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI
saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
saa7134:   card=12 -> Medion 7134                              16be:0003
saa7134:   card=13 -> Typhoon TV+Radio 90031
saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226b
saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
saa7134:   card=18 -> BMK MPEX No Tuner
saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
saa7134:   card=23 -> BMK MPEX Tuner
saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b 11bd:002d
saa7134:   card=27 -> Manli MuchTV M-TV002
saa7134:   card=28 -> Manli MuchTV M-TV001
saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
saa7134:   card=32 -> AVACS SmartTV
saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
saa7134:   card=34 -> Noval Prime TV 7133
saa7134:   card=35 -> AverMedia 305                            1461:2115
saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
saa7134:   card=37 -> Items MuchTV Plus / IT-005
saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
saa7134:   card=39 -> LifeView FlyTV Platinum                  5168:0212
saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)
saa7134:   card=43 -> :Zolid Xpert TV7134
saa7134:   card=44 -> Empire PCI TV-Radio LE
saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
saa7134:   card=46 -> AVerMedia Cardbus TV/Radio               1461:d6ee
saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
saa7134[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
saa7134[0]: board init: gpio is 407f
saa7134[0]: Huh, no eeprom present (err=-5)?
saa7134[0]: registered device video0 [v4l2]
saa7134[0]: registered device vbi0


---

### Post by tristan on 2005-07-08
Can you post your exact TV card specifications, that would help a lot!

The the mean time I suggest you take 1/2 an hour to just try 

rmmod saa7134
modprobe saa7134 tuner=1

Then try tvtime

rmmod saa7134
modprobe saa7134 tuner=2

etc etc

For some reason a lot of card's tuners don't get properly recognised, so it might just be a matter of scanning through them til you chance on the right one.

---

### Post by dc2447 on 2005-07-09
Resolved my issue, I needed to edit /etc/tvtime/tvtime.xml and manually overide the tuner setting from 0 to 2, tvtime-scanner then worked:

So to recap, the procedure was:

> sudo apt-get install tvtime
sudo modprobe bttv
sudo modprobe saa7134 card=43 tuner=2

then edit /etc/tvtime/tvtime.xml

change this to the same value as tuner above
> 
<option name="V4LInput" value="2"/>

then tvtime-scanner works

---

### Post by tristan on 2005-07-09
Good skills dc2447 :) 
Next step - try recording stuff!

---

### Post by dc2447 on 2005-07-09
[QUOTE=tristan]Good skills dc2447 :) 
Next step - try recording stuff![/QUOTE]

Indeed, bit strange that mythtv doesn't seem to be in my repositories.

I'm also trying to work out the best approach for audio

---

### Post by tristan on 2005-07-09
To be honest mythtv seems to be a bit of overkill for what I want to do (eg record the occasional show when I'm not home). It's also fairly painful to set up...

I just use a few homebrewed **mencoder** scripts to record TV to divx avi (or mpeg2 for burning to vcd with **vcdimager**), using** at** to schedule them to start. Works a treat and is not exactly rocket science to set up. I can provide them if you're interested.

---

### Post by dc2447 on 2005-09-24
<apologies for bumping my own thread months later>

I have just rebuilt my workstation and I can't remember the syntax for /etc/modules to get the saa7134 module loaded:

Via the cli I use:

```
sudo modprobe saa7134 card=43 tuner=2
```

Have played with various options in /etc/modules but none seem to load the module when I run update-modules

---

### Post by Akli on 2006-04-01
My card works only with xawtv, I want it to work with tvtime,
 If someone can help

Pinnacle/Miro DC30+:
* Zoran zr36067 PCI controller
* Zoran zr36050 MJPEG codec
* Zoran zr36016 Video Front End
* Micronas vpx3225d/vpx3220a/vpx3216b TV decoder
* Analog Devices adv7176 TV encoder
Drivers to use: videodev, i2c-core, i2c-algo-bit,
		videocodec, vpx3220/vpx3224, adv7175, zr36050, zr36015, zoran
Inputs: Composite, S-video and Internal
Norms: PAL, SECAM (768x576 @ 25 fps), NTSC (640x480 @ 29.97 fps)
Card number: 4

Note: No module for the mse3000 is available yet
Note: No module for the vpx3224 is available yet
Note: use encoder=X or decoder=X for non-default i2c chips (see i2c-id.h)

---

### Post by bvidinli on 2008-05-08
same worked for me,
i use mythbuntu 8.04, i use avertv dvb-s hybrid+fm card, (A700-B)

sudo apt-get install tvtime
sudo modprobe bttv
sudo modprobe saa7134 card=43 tuner=2
then edit /etc/tvtime/tvtime.xml

change this to the same value as tuner above
Quote:
<option name="V4LInput" value="2"/> 


tvtime-scanner now started to scan channels, 
previously it was not starting scan, just giving error "no tuner found on input 0"

i try to use mythbuntu, on my tv card, avertv dvb-s hybrid+fm
after scan complete, i will try new frequency table with mythtv

after scan:
i found no channels, no output written.
i will try some other ways... if anybody helps, welcome...

i use AVerTV DVB-S Hybrid+FM

---

