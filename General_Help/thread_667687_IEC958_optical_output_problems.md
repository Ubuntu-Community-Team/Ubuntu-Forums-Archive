---
title: "IEC958 optical output problems"
date: 2008-01-14
forum: General Help
---

### Post by RJ Hythloday on 2008-01-14
I had dapper for a day and managed to get the spdif working after installing alsamixer and changing the IEC958 as I had found in several forums.

I now have gutsy and am not able to figure out any sound, I tried the a.asoundrc file like Jennifer suggested also but still no luck.

I am using a turtle beach soundcard optical>reciever.

---

### Post by gobbles414 on 2008-01-14
RJ Hythloday,

I used this to get SPDIF output working on my laptop in Gusty... Here's the procedure for installing version 4.07a of the driver in Ubuntu 7.10. NOTE: Be careful not to paste commas or periods into the terminal.

1. Go System => Administration => Software Sources => Updates and put a checkmark next to Pre-released Updates. Check for and install any updates.

2. Then restart your computer, just to be safe.

3. Download the Realtek HD audio driver for Linux to your desktop (click on link). Interestingly, this driver is just an automatic version of what you and I tried to install on IRC.

4. Right-Click on the downloaded archive and choose Extract Here.

5. Open a terminal window and type sudo apt-get install linux-backports-modules-generic build-essential gettext libcunit1-ncurses libcunit1-ncurses-dev libncurses5 libncurses5-dev, and press enter.

6. Just to be safe, restart your computer again.

7. Open the terminal again and type cd /home/YOURUSERNAME/Desktop/realtek-linux-audiopack-4.07a, then press enter. Obviously, substitute your own username where I have written YOURUSERNAME. This will move you inside the driver folder.

8. Type sudo /etc/init.d/alsa-utils stop, then press enter. Then type sudo /etc/init.d/alsasound stop, and press enter. The first one should definitely work. The second may not work now, but it will eventually. NOTE: If asked to reload your speaker icon during either of these steps, say no.

9. Type sudo ./install, and press enter. Watch your computer as it installs the driver.

10. If there are not any errors in the installation process, you should be greeted by a screen asking you to select you audio device. Choose the one the talks about Intel HD Audio (ICH7), or similar.

11. Restart your computer.

12. Open the terminal again and type cat /proc/asound/card0/codec#* | grep Codec, and press enter. This should tell you what kind of sound you have. In my case, the result was Realtek ALC660-VD. WARNING: Your modem may also show up in these results. So be sure that you are about to choose the sound and not the modem by doing some research online.

13. Look at the list below to determine the abbreviation for your sound card. For example, my Realtek ALC660-VD is represented by 3stack-660-digout.

14. Type sudo gedit /etc/modprobe.d/alsa-base, and press enter. A file with some text should open.

15. Go to the last line of text and type options snd-hda-intel model=YOURMODEL. So for example, I have typed options snd-hda-intel model=3stack-660-digout. Be sure to save your changes by going File => Save!

16. Restart your computer so that your sound can reload itself.

17. I had to do steps 7-16 twice in order to get a successful installation of the audio driver.

18. To get your speaker icon back on your panel (also called a taskbar), Right-Click on the top panel and choose Add to Panel => System & Hardware => Volume Control => left-click on the Add button. Right-Clicking on a pane icon will allow you to move it around, or lock it into position.

19. THIS OPTION IS ONLY IF YOUR COMPUTER SUPPORTS SPDIF. Now, right-click on the speaker icon and choose Open Volume Control. The title of the Volume Control window should either have ALSA or OSS in it. Either way, go Edit => Preferences. If you are in ALSA, look for an option like IEC958. Choosing that will place on option in the Switches tab; placing a checkmark in the box there will activate SPDIF sound. It's fine to leave SPDIF on at all times if you want to do so. If you ever need to know about OSS, you can get there by going File => Change Device in Volume Control. On my computer, OSS calls SPDIF Digital-1. If selected, it will appear in the Playback tab of OSS.

20. Each program will behave differently with SPDIF audio. Movie Player (Totem) behaves very well. In Movie Player, you can activate full digital surround sound (Dolby Digital, DTS, etc) by going Edit => Preferences => Audio and choosing AC3 Passthrough from the drop-down menu. On the other hand, some audio-related options within the VLC media player can wreck the sound on your entire system! The good news is, you can always fix any damaged caused by VLC by repeating the above steps. Just be careful...

The following are webpages where I found all of this information:
<https://wiki.ubuntu.com/LaptopTestin...vo3000N100_FPG>
<http://ubuntuforums.org/showthread.php?t=616845>
<http://www.matusiak.eu/numerodix/blo...-toshiba-u300/>

Here is a list of audio devices:
Model name Description
---------- -----------
ALC880
3stack 3-jack in back and a headphone out
3stack-digout 3-jack in back, a HP out and a SPDIF out
5stack 5-jack in back, 2-jack in front
5stack-digout 5-jack in back, 2-jack in front, a SPDIF out
6stack 6-jack in back, 2-jack in front
6stack-digout 6-jack with a SPDIF out
w810 3-jack
z71v 3-jack (HP shared SPDIF)
asus 3-jack (ASUS Mobo)
asus-w1v ASUS W1V
asus-dig ASUS with SPDIF out
asus-dig2 ASUS with SPDIF out (using GPIO2)
uniwill 3-jack
fujitsu Fujitsu Laptops (Pi1536)
F1734 2-jack
lg LG laptop (m1 express dual)
lg-lw LG LW20/LW25 laptop
tcl TCL S700
clevo Clevo laptops (m520G, m665n)
test for testing/debugging purpose, almost all controls can be
adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y
auto auto-config reading BIOS (default)

ALC260
hp HP machines
hp-3013 HP machines (3013-variant)
fujitsu Fujitsu S7020
acer Acer TravelMate
will Will laptops (PB V7900)
replacer Replacer 672V
basic fixed pin assignment (old default model)
auto auto-config reading BIOS (default)

ALC262
fujitsu Fujitsu Laptop
hp-bpc HP xw4400/6400/8400/9400 laptops
hp-bpc-d7000 HP BPC D7000
benq Benq ED8
benq-t31 Benq T31
hippo Hippo (ATI) with jack detection, Sony UX-90s
hippo_1 Hippo (Benq) with jack detection
sony-assamd Sony ASSAMD
basic fixed pin assignment w/o SPDIF
auto auto-config reading BIOS (default)

ALC268
3stack 3-stack model
toshiba Toshiba A205
acer Acer laptops
auto auto-config reading BIOS (default)

ALC662
3stack-dig 3-stack (2-channel) with SPDIF
3stack-6ch 3-stack (6-channel)
3stack-6ch-dig 3-stack (6-channel) with SPDIF
6stack-dig 6-stack with SPDIF
lenovo-101e Lenovo laptop
auto auto-config reading BIOS (default)

ALC882/885
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack digital with SPDIF I/O
arima Arima W820Di1
targa Targa T8, MSI-1049 T8
asus-a7j ASUS A7J
asus-a7m ASUS A7M
macpro MacPro support
mbp3 Macbook Pro rev3
imac24 iMac 24'' with jack detection
w2jc ASUS W2JC
auto auto-config reading BIOS (default)

ALC883/888
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack digital with SPDIF I/O
3stack-6ch 3-jack 6-channel
3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
6stack-dig-demo 6-jack digital for Intel demo board
acer Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
acer-aspire Acer Aspire 9810
medion Medion Laptops
medion-md2 Medion MD2
targa-dig Targa/MSI
targa-2ch-dig Targs/MSI with 2-channel
laptop-eapd 3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
lenovo-101e Lenovo 101E
lenovo-nb0763 Lenovo NB0763
lenovo-ms7195-dig Lenovo MS7195
haier-w66 Haier W66
6stack-hp HP machines with 6stack (Nettle boards)
3stack-hp HP machines with 3stack (Lucknow, Samba boards)
auto auto-config reading BIOS (default)

ALC861/660
3stack 3-jack
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack with SPDIF I/O
3stack-660 3-jack (for ALC660)
uniwill-m31 Uniwill M31 laptop
toshiba Toshiba laptop support
asus Asus laptop support
asus-laptop ASUS F2/F3 laptops
auto auto-config reading BIOS (default)

ALC861VD/660VD
3stack 3-jack
3stack-dig 3-jack with SPDIF OUT
6stack-dig 6-jack with SPDIF OUT
3stack-660 3-jack (for ALC660VD)
3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
lenovo Lenovo 3000 C200
dallas Dallas laptops
hp HP TX1000
auto auto-config reading BIOS (default)

CMI9880
minimal 3-jack in back
min_fp 3-jack in back, 2-jack in front
full 6-jack in back, 2-jack in front
full_dig 6-jack in back, 2-jack in front, SPDIF I/O
allout 5-jack in back, 2-jack in front, SPDIF out
auto auto-config reading BIOS (default)

AD1882
3stack 3-stack mode (default)
6stack 6-stack mode

AD1884
N/A

AD1981
basic 3-jack (default)
hp HP nx6320
thinkpad Lenovo Thinkpad T60/X60/Z60
toshiba Toshiba U205

AD1983
N/A

AD1984
basic default configuration
thinkpad Lenovo Thinkpad T61/X61

AD1986A
6stack 6-jack, separate surrounds (default)
3stack 3-stack, shared surrounds
laptop 2-channel only (FSC V2060, Samsung M50)
laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
ultra 2-channel with EAPD (Samsung Ultra tablet PC)

AD1988
6stack 6-jack
6stack-dig ditto with SPDIF
3stack 3-jack
3stack-dig ditto with SPDIF
laptop 3-jack with hp-jack automute
laptop-dig ditto with SPDIF
auto auto-config reading BIOS (default)

Conexant 5045
laptop Laptop config
test for testing/debugging purpose, almost all controls
can be adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y

Conexant 5047
laptop Basic Laptop config
laptop-hp Laptop config for some HP models (subdevice 30A5)
laptop-eapd Laptop config with EAPD support
test for testing/debugging purpose, almost all controls
can be adjusted. Appearing only when compiled with
$CONFIG_SND_DEBUG=y

STAC9200
ref Reference board
dell-d21 Dell (unknown)
dell-d22 Dell (unknown)
dell-d23 Dell (unknown)
dell-m21 Dell Inspiron 630m, Dell Inspiron 640m
dell-m22 Dell Latitude D620, Dell Latitude D820
dell-m23 Dell XPS M1710, Dell Precision M90
dell-m24 Dell Latitude 120L
dell-m25 Dell Inspiron E1505n
dell-m26 Dell Inspiron 1501
dell-m27 Dell Inspiron E1705/9400

STAC9205/9254
ref Reference board
dell-m42 Dell (unknown)
dell-m43 Dell Precision
dell-m44 Dell Inspiron

STAC9220/9221
ref Reference board
3stack D945 3stack
5stack D945 5stack + SPDIF
intel-mac-v1 Intel Mac Type 1
intel-mac-v2 Intel Mac Type 2
intel-mac-v3 Intel Mac Type 3
intel-mac-v4 Intel Mac Type 4
intel-mac-v5 Intel Mac Type 5
macmini Intel Mac Mini (equivalent with type 3)
macbook Intel Mac Book (eq. type 5)
macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
macbook-pro Intel Mac Book Pro 2nd generation (eq. type 3)
imac-intel Intel iMac (eq. type 2)
imac-intel-20 Intel iMac (newer version) (eq. type 3)
dell-d81 Dell (unknown)
dell-d82 Dell (unknown)
dell-m81 Dell (unknown)
dell-m82 Dell XPS M1210

STAC9202/9250/9251
ref Reference board, base config
m2-2 Some Gateway MX series laptops
m6 Some Gateway NX series laptops
pa6 Gateway NX860 series

STAC9227/9228/9229/927x
ref Reference board
3stack D965 3stack
5stack D965 5stack + SPDIF
dell-3stack Dell Dimension E520

STAC9872
vaio Setup for VAIO FE550G/SZ110
vaio-ar Setup for VAIO AR

Does this help?

---

### Post by RJ Hythloday on 2008-01-14
Thanks, 

It works up to step 12

then I get 

cat: /proc/asound/card0/codec#*: No such file or directory


I'm   trying again from step 7 to 11 and am about to restart.

still getting the same message, 

Thanks for the help, I will try searching some more myself, lmk if you think of any thing else I should try.

btw when I got to the install there was nothing about a hd ICH7 my choices were via or legacy, I installed the VIA chipset, I looked  at lagacy and it said it would make the system unstable.

---

### Post by gobbles414 on 2008-01-15
RJ Hythloday,

**It works up to step 12 then I get *cat: /proc/asound/card0/codec#*: No such file or directory*.**
I believe that all step 12 does is tell you information that you will need to know to complete step 15. If you know the exact model number and capabilities of your audio card, then step 12 is unnecessary (see my next answer for more info). By the way, a similar "No such file or directory" error is mentioned [here]("http://ubuntuforums.org/showthread.php?t=545750") and [also here]("http://ubuntuforums.org/showthread.php?t=202555&page=5"). I didn't see a solution in either thread. But I am quite tired so it might be worth your time to read them for yourself! ;-)

**...when I got to the install there was nothing about a *HD ICH7* my choices were *VIA* or *Legacy*, I installed the VIA chipset, I looked at legacy and it said it would make the system unstable.**
I am actually working with some VIA motherboards and Ubuntu 7.10 as part of a job that I am doing! Is your entire motherboard made by VIA? Look in *System => Preferences => Hardware Information* to possibly discover the answer. Click [this]("http://www.via.com.tw/en/initiatives/empowered/pc3500_mainboard/index.jsp") for an example of a VIA motherboard. IMPORTANT: Notice how the specs for that motherboard list *Realtek ALC883 HD audio eight channel*? If you know that kind of information about your audio configuration, then step 12 should be unnecessary and step 15 should go smoothly. Go to [VIA Arena]("http://www.viaarena.com/") to maybe find drivers for your specific audio hardware. NOTE: Google provides sub-results underneath the VIA Arena homepage. One of them is supposedly for audio drivers.

Please keep me posted on your progress!

---

### Post by RJ Hythloday on 2008-01-15
When I tried step 14 last night it didn't find the file. Should I been in home/desktop/or realtek-linux-audiopack-4.07a? Just doing some reading during lunch, I'll try to get back to this tonight.

The wife has really been getting upset so I plugged the windoz boot drive back in for her. 

Do all versions of ubuntu have this problem or just kde? I might have to look at redhat again, I really want to get away from windoz!

---

### Post by gobbles414 on 2008-01-15
RJ Hythloday,

Did you discover any more details about your audio hardware and/or motherboard?

**Do all versions of Ubuntu have this problem or just KDE?**
Well I'm using GNOME. So my guess is that all versions of Ubuntu have this bug. I have read reports that this wasn't a problem for as many of us in earlier versions of Ubuntu. But I wouldn't know since I never tried SPDIF before Ubuntu 7.10.

**When I tried step 14 last night it didn't find the file. Should I been in home/desktop/or realtek-linux-audiopack-4.07a?**
The *gedit* part of the command is a queue to launch the default GNOME text editor in Ubuntu. Does KDE have the same text editor? I have only experimented with KDE. But typing *gedit AND kde* in Google results in a lot of hits for a program called *Kate*. Is that the default text editor in KDE? Type *cd /etc/modprobe.d* in the terminal. Then type *dir*. Hopefully, *alsa-base* will be one of the results in the list. If not, use the default desktop search tool in KDE to find *alsa-base*. In GNOME Ubuntu, I can also find the correct file by typing *locate alsa-base* in the terminal. This may be a GNOME-only thing too. But it's worth a try. **NOTE:** You need root privileges in order to properly save the *alsa-base* file. Hence, to modify the file either use *sudo* in the terminal, configure your text editor to launch as root, or login as root.

**The wife has really been getting upset so I plugged the windoz boot drive back in for her.**
What else can I say but BOO! Question though... Is your sound totally not working? Or is is just SPDIF that is not working. You can always plug some analog speakers into your computer until the SPDIF has been solved, yes?

**I might have to look at Red Hat again, I really want to get away from windoz!**
I have never been a fan of Red Hat (or Fedora Core) because a significant amount of command line syntax is different in Red Hat than in other Linux distributions. So I chose to try Ubuntu instead of buying an expensive Red Hat book. I've never regretted it!

**Just in case you missed them in my original post, some further reading:**
<[https://wiki.ubuntu.com/LaptopTestin...vo3000N100 _FPG]("https://wiki.ubuntu.com/LaptopTestin...vo3000N100 _FPG")>
<[http://ubuntuforums.org/showthread.php?t=616845]("http://ubuntuforums.org/showthread.php?t=616845")>
<[http://www.matusiak.eu/numerodix/blo...-toshiba-u300/]("http://www.matusiak.eu/numerodix/blo...-toshiba-u300/")>

You've gotten me really intrigued! So please, keep me informed regarding your progress.

---

### Post by RJ Hythloday on 2008-01-15
I have a turtle beach catalina the xp driver I am using is 5.12.1.3615 and it is a via chipset

my mobo is a foxconn K7S741GXMG I really don't like it cause there is no bios oc options and no sw option to oc w/ *nix. also no onboard sata so that will be another thing for me to figure out the driver for my promise card.

Yeah I guess I could have googled gedit, kate is the .txt editor in kde, I do have some analog surround speakers it would just be a pain to get them out of my desk they are pretty much wired into to bring them to the front room.

Thanks for all of your help so far, I hope to get this kicked soon, the wife canceled her trip to the gym tonight so I won't have much chance for more trouble shooting.

---

### Post by gobbles414 on 2008-01-15
RJ Hythloday,

Well, [your sound card manufacturer's official stance on Linux]("http://support.turtlebeach.com/site/kb_ftp/586515094.asp") is ZERO support. So don't expect any help there. Furthermore, I have done some more research and concluded that the Realtek audio drivers in my instructions will most likely NOT work with your sound card -- I wasn't able to find any evidence that Turtle Beach (a.k.a VTB) hardware uses any parts from Realtek.

You could try manually installing the latest ALSA drivers. But a look at [ALSA's list of supported Turtle Beach devices]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Turtle_Beach") doesn't make me very optimistic that a manual installation of ALSA drivers would result in success. Catalina is not in the list. Isn't Catalina from like 2003 or 2004? In those years, Linux drives of all kinds were still quite limited. The driver situation in Linux has improved tremendously in recent years. But as your problems illustrate, there is still a long way to go driver-wise.

If you have some extra money that you've been saving for a rainy day, **I would recommend just buying a different sound card at this point. SPDIF-capable sound cards are available for as little as 30USD -- sometimes even less.** Check the ALSA website for a list of sound cards whose SPDIFs are known to work in Linux.

As always, I would love to learn how you are progressing with this issue.

---

### Post by gobbles414 on 2008-01-16
RJ Hythloday,

Just remembered that you said your SPDIF worked in Dapper... Do you still have a Dapper LiveCD? If so, why don't you load it into your computer and see how your sound card is identified in Dapper. That might help us to get it working for you in Gusty. But since "time is money" as they say, it might still be the best option for you to shell out 30USD or so for a new sound card. "Whatever makes you happy..." :)

---

### Post by RJ Hythloday on 2008-01-16
I can see if it will work in the live cd, I had dapper installed and searched and read about turning off iec958 in alsamixer so I did that after I installed alsamixer, I don't think I can do all that from the live cd. I wonder if the onboard optical out might be a better choice for me?

---

### Post by gobbles414 on 2008-01-16
RJ Hythloday,

I would try the built-in audio option first, for sure! Any idea what audio chipset your Foxconn K7S741GXMG motherboard uses? I imagine that you will need to remove your sound card too. You're probably right about Dapper LiveCD not working.

---

### Post by RJ Hythloday on 2008-01-17
I think it's probably realtek ac97. I just realized there was a second page here. Do you think this is something that ubuntu will fix? I'm thinking I might just pull the other speakers over here for the pc.

---

### Post by gobbles414 on 2008-01-17
RJ Hythloday,

**I think it's probably Realtek ac97.**
I think that Realtek also has Linux drivers for ac97 hardware -- same download page as the HD drivers, but a different file to download. I assume that the installation procedure will be similar to the one I posted in my original response. Be sure to remember to allow for KDE as you use my instructions. For example, use *kate* instead of *gedit*. EDIT: Items 12 and 14 might require different commands in Kubuntu than in Ubuntu (GNOME). Visit the [Kubuntu Support webpage]("http://www.kubuntu.org/support.php") if you need to do KDE-based research.

**I just realized there was a second page here.**
Yes, when I was new to the forums I missed some valuable replies because of that. I assume that threads are split into pages to keep load times down. I personally would prefer on long page. But for those still on dial-up (yikes) multiple pages makes more sense.

**Do you think this is something that Ubuntu will fix?**
As you mentioned in your original post, SPDIF used to work much more easily in Ubuntu. The difficulties could be the result of a modification that has been made to Ubuntu by the programmers. Or, it could be the result of a bug in the Linux Kernel itself. I hope that Ubuntu's programmers will be kind enough to fix this issue in time for Ubuntu 8.04. EDIT: This issue could also be caused by version 1.0.14 of the ALSA drivers, which are currently used by Ubuntu Gusty (and I think Feisty too). Almost all of the solutions to SPDIF problems that I have read involve installing version 1.0.15 of ALSA. The Realtek drivers should contain some form of version 1.0.15.

**I'm thinking I might just pull the other speakers over here for the PC.**
My feeling would be to take out your Turtle sound card and attempt to install the ac97 driver for your motherboard's built-in sound. Just out of curiosity, why did you purchase the Turtle sound card if your motherboard already supported digital audio output? Aren't they both 5.1?

Always a pleasure to reply to your posts! Please keep me informed about your progress.

---

### Post by gobbles414 on 2008-01-22
RJ Hythloday,

Have you been able to make any progress getting the built-in SPDIF on your motherboard to work?

---

### Post by RJ Hythloday on 2008-01-22
> **gobbles414 said:**
> RJ Hythloday,



**I'm thinking I might just pull the other speakers over here for the PC.**
My feeling would be to take out your Turtle sound card and attempt to install the ac97 driver for your motherboard's built-in sound. Just out of curiosity, why did you purchase the Turtle sound card if your motherboard already supported digital audio output? Aren't they both 5.1?

Yeah, early in my pc buillding I thought I might get better sound this way or less cpu strain I dk I'd definitely get an M-Audio w/ coax for my next build which will be an htpc. The turtle beach really doesn't serve any purpose right now.

---

### Post by gobbles414 on 2008-01-22
RJ Hythloday,

So is the built-in SPDIF working now? If so, how did you get it working?

---

### Post by RJ Hythloday on 2008-01-23
> **gobbles414 said:**
> RJ Hythloday,

So is the built-in SPDIF working now? If so, how did you get it working?
I guess I was thinking of my old mobo, this one doesn't actually have it. I'm currently using the analog output of the soundcard w/ some logitech spkrs, I'd much prefer to get the receiver working through the digital. 

Next job is the dual output and getting the plasma to display at the proper resolution.

---

### Post by gobbles414 on 2008-01-23
RJ Hythloday,

***I guess I was thinking of my old mobo, this one doesn't actually have it.***
Hmm... If your motherboard is A Foxconn K7S741GXMG, then you should have 5.1 digital sound output (according to a Google search).

***I'm currently using the analog output of the sound card w/ some Logitech speakers, I'd much prefer to get the receiver working through the digital.***
As I see it, here are the possibilities: It might be worth waiting for Ubuntu 8.04 (or experiment with the current alpha build). I imagine that it will automatically include ALSA 1.0.15, which seems to solve the problems that many have been having with SPDIF output. Or, you might be able to get SPDIF working again in Ubuntu 6.06 (Dapper) or Ubuntu 6.10 (Edgy). Furthermore, you can purchase a new Linux-compatible sound card that supports SPDIF output. And of course, you can always buy an RCA to mini adapter to output analog "surround sound" to your home theater from your computer. Those cables are really inexpensive nowadays. If your receiver supports Dolby Pro Logic II -- or the DTS equivalent -- this will yield acceptable results with most movies and TV shows.

***Next job is the dual output and getting the plasma to display at the proper resolution.***
I've got a 720p LCD myself. At least without going into the command line -- which I haven't tried, by the way -- I haven't been able to get my computer to output to my HDTV's native resolution of 1366x768. I have been using a DVI to HDMI cable to connect, since my computer does not have and HDMI out. I can get other 16x9 resolutions, but not full 720p. I have not tried 1080i because I'm guessing that such a resolution would be difficult to achieve. I assume that these issues are being worked on for 8.04 as well, because each of the recent Ubuntu updates have had better graphics support than previous releases..

---

### Post by RJ Hythloday on 2008-01-24
> **gobbles414 said:**
> RJ Hythloday,

***I guess I was thinking of my old mobo, this one doesn't actually have it.***
Hmm... If your motherboard is A Foxconn K7S741GXMG, then you should have 5.1 digital sound output (according to a Google search).

It sure isn't there physically :lol:

***I'm currently using the analog output of the sound card w/ some Logitech speakers, I'd much prefer to get the receiver working through the digital.***
As I see it, here are the possibilities: It might be worth waiting for Ubuntu 8.04 (or experiment with the current alpha build). I imagine that it will automatically include ALSA 1.0.15, which seems to solve the problems that many have been having with SPDIF output. Or, you might be able to get SPDIF working again in Ubuntu 6.06 (Dapper) or Ubuntu 6.10 (Edgy). Furthermore, you can purchase a new Linux-compatible sound card that supports SPDIF output. And of course, you can always buy an RCA to mini adapter to output analog "surround sound" to your home theater from your computer. Those cables are really inexpensive nowadays. If your receiver supports Dolby Pro Logic II -- or the DTS equivalent -- this will yield acceptable results with most movies and TV shows.

I figure I can live w/ this till the next os release, A new soundcard is in order for the mythbuntu box I want to build eventually, Maybe the sound card could be the first purchase.

***Next job is the dual output and getting the plasma to display at the proper resolution.***
I've got a 720p LCD myself. At least without going into the command line -- which I haven't tried, by the way -- I haven't been able to get my computer to output to my HDTV's native resolution of 1366x768. I have been using a DVI to HDMI cable to connect, since my computer does not have and HDMI out. I can get other 16x9 resolutions, but not full 720p. I have not tried 1080i because I'm guessing that such a resolution would be difficult to achieve. I assume that these issues are being worked on for 8.04 as well, because each of the recent Ubuntu updates have had better graphics support than previous releases..
I've found a couple post about xorg.conf and hope to get the flat screen hooked up soon, I started messing around w/ superkaramba last night and then the wife never went to the gym so I didn't get to finish. I try to limit my time in front of the pc to keep our marriage happy. :KS

---

