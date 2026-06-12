---
title: "Coming Soon: MythTV w/PVR-250 Guide!"
date: 2005-04-10
forum: General Help
---

### Post by windexh8er on 2005-04-10
OK, so I got bored last night...  Did a fresh install of 5.04 and documented everything and anything it took to get MythTV working with the IVTV modules on my PVR-250.  There are a lot of intricacies of MythTV for the newb Myth user.  I figured since there are no good guides out there I'd help out...

Look for this soon, I'll post it up as soon as I'm done formatting it properly!

---

### Post by gab10 on 2005-04-11
Just want to encourage you and thank you in advance for this...I'm getting ready to set up a MythTV box and it seems a daunting task so I can use all the documentation I can get. Thanks!

---

### Post by sinbad782 on 2005-04-11
This sounds great - I built my system especially to be a MythTV PVR and so any help is much appreciated. 

I heard that support for DVB cards is now starting to be implemented in MythTV and this would be really great as I am in the UK and use Freeview cards like the Nebula DigiTV.

---

### Post by Nnyan on 2005-04-11
Anyone have a PVR-150 card?  I would love to see the guide include these cards.

---

### Post by windexh8er on 2005-04-11
Well, the new IVTV drivers support the PVR-150 I do believe...  So, your mileage may vary, but it shouldn't be much different.

---

### Post by MetalMusicAddict on 2005-04-11
Awesome man. Ive been a big HTPC guy now for years. I have a system now with FC2 as a base but a Ubuntu base would be cool also. ;)

---

### Post by Xenu on 2005-04-11
I eagerly await your howto. I have given up in frustration 3 times on installing MythTV. I pretty much gave up after KnoppMyth didnt work out of the box with my 250 card. My box is begging for XP to be removed. :) Thanks for the effort in advance.  \\:D/

---

### Post by windexh8er on 2005-04-12
Well - I'm *almost* done with it.  I didn't have as much time as I would have liked last night.  The only thing that won't be in it initially is the LIRC stuff - as I haven't gotten around to reinstalling that portion yet.  I will, however, add it later in the week or this coming weekend.  Other than that it's nothing too impressive, just what to do in what order!

---

### Post by dtranche on 2005-04-12
[QUOTE=windexh8er]Well - I'm *almost* done with it.  I didn't have as much time as I would have liked last night.  The only thing that won't be in it initially is the LIRC stuff - as I haven't gotten around to reinstalling that portion yet.  I will, however, add it later in the week or this coming weekend.  Other than that it's nothing too impressive, just what to do in what order![/QUOTE]
 Cool, MythTV is one of the uses I would like for this box.

---

### Post by water on 2005-04-12
I'm looking forward to trying this - I have a FC3 box alomst done following [Jarod's guide]("http://wilsonet.com/mythtv/fcmyth.php") but the complexity of that has held me back from pushing Mythtv on windows based friends.

Hopefully Ubuntu & Mythtv can now become a real alternative to all the windows based htpc aplications out there :mrgreen:

Has anybody tried the PVR-550 card?

:water

---

### Post by knathraak on 2005-04-12
[QUOTE=windexh8er]Well - I'm *almost* done with it.  I didn't have as much time as I would have liked last night.  The only thing that won't be in it initially is the LIRC stuff - as I haven't gotten around to reinstalling that portion yet.  I will, however, add it later in the week or this coming weekend.  Other than that it's nothing too impressive, just what to do in what order![/QUOTE]

Can't wait to see your guide.  I've been bouncing around from distro to distro trying to find one that plays nice with myth.  My preferred distro for everyday use is ubuntu, but couldn't find adequate guidance for myth on ubuntu (or debian for that matter).  Started with knoppmyth, then FC3, using Jarod's guide, then struck out on my own with (K)ubuntu.  Finally defected back to knoppmyth (by then I was satisfied that I understood enough of what it was doing behind my back).

I made a very long post on the ubuntu-users mailing list (name Zach) about my harrowing experience getting lirc going on ubuntu.  I can't wait to see the right way to do it.  Btw, in the universe (multiverse?) repo, the lirc-modules package doesn't seem to work right.  My hunch is that it was grabbed out of debian without really being looked at and hasn't really been maintained.  It makes 2.4-style modules (.o vs .ko).  Also couldn't get the lirc source to actually make either. 

Anyway, good luck, and can't wait for the guide.

---

### Post by Jon K on 2005-04-14
waiting for the guide.... I have a PVR 350 that I purchased last week and started building.  I have some things working and some not.  I'd love to add a section to a mythtv on ubuntu guide that includes getting the tv out on the pvr350 to funciton proeprtly.  Perhaps if you provided me a preliminary copy? :)

---

### Post by windexh8er on 2005-04-15
Well, here it is:

[http://www.slash32.com/ubuntu-myth.html](http://www.slash32.com/ubuntu-myth.html)

Sorry that the formatting is of crap right now.  I didn't have much of any time and things kind of fell apart a little towards the end.  If someone wants to reorganize it better, by all means!  :)

I'll be adding the LIRC stuff this weekend and a few other tips and tricks as well.

Sorry for the delay...  :)

Edit:
I wrote this in OOo and just saved as HTML.  That'll be something to fix eventually!  It was quick and dirty, oh well - at least it's a start.

---

### Post by knathraak on 2005-04-18
[QUOTE=windexh8er]Well, here it is:

[http://www.slash32.com/ubuntu-myth.html](http://www.slash32.com/ubuntu-myth.html)

Sorry that the formatting is of crap right now.  I didn't have much of any time and things kind of fell apart a little towards the end.  If someone wants to reorganize it better, by all means!  :)

I'll be adding the LIRC stuff this weekend and a few other tips and tricks as well.

Sorry for the delay...  :)

Edit:
I wrote this in OOo and just saved as HTML.  That'll be something to fix eventually!  It was quick and dirty, oh well - at least it's a start.[/QUOTE]


Nice guide.  Thanks for putting this together, as there is a lack of adequate Myth converage for Ubuntu.  You should get this listed over at pvrguide.no-ip.com.  There's a collection of howtos there for various distros.

Can't wait for the lirc stuff.  That was one of the things that really gave me troubles before I defected to KnoppMyth.

A couple of other sticky spots I ran into that you may want to mention [if these things are there already maybe i just overlooked them]:
--Make sure you don't already have a mythtv user before you install the myth packages.  If you do, the package configuration croaks when it tries to create the mythtv user.
--Maybe want to list the special code myth users are supposed to register with at labs.zap2it.com

Great guide and thanks again!

---

### Post by windexh8er on 2005-04-18
Thanks for the insight - I'll definitely update to reflect the mythtv user and Zap2It code, great catches!

So...  I went through my steps of getting the LIRC modules compiled and it works flawlessly every time.  :)  I had an issue the first go-round with my /etc/lircd.conf, but I figured it out using irrecord.

Anyway...  Does anyone want to help reorganize this - or have any formatting ideas?  Maybe use xalan and mark it all up with XML?  I'd really like this to turn out like the Fedora guide.  I could throw up a wiki on my site...  Lookin' for some insight or anybody who wants to help.

I see that 0.18 is released now, but an upgrade should be pretty easy and not affect any modules that were compiled.

---

### Post by dlpfmVfH on 2005-04-19
[QUOTE=windexh8er]Thanks for the insight - I'll definitely update to reflect the mythtv user and Zap2It code, great catches!

So...  I went through my steps of getting the LIRC modules compiled and it works flawlessly every time.  :)  I had an issue the first go-round with my /etc/lircd.conf, but I figured it out using irrecord.

Anyway...  Does anyone want to help reorganize this - or have any formatting ideas?  Maybe use xalan and mark it all up with XML?  I'd really like this to turn out like the Fedora guide.  I could throw up a wiki on my site...  Lookin' for some insight or anybody who wants to help.

I see that 0.18 is released now, but an upgrade should be pretty easy and not affect any modules that were compiled.[/QUOTE]
 got only one problem...did as you described in your guide...mythtv installed fine, without any problems..

but I can't run mythfrontend as my normal user,... did look in group video, and all users are present...?

and another thing...at boot it is complaining about an fw image not loading??

please can you help?

---

### Post by windexh8er on 2005-04-19
Well - your first problem is probably a segfault that I was running into as well.  If you run 'mythfrontend' from a terminal logged in as your user what output do you get?  I noticed that, for some reason, if the mysql settings do not exist within your .mythtv directory it *should* start the frontend and let you put those in.  In my case the frontend just segfaults.  I'm not in front of my Myth box, but if you copy the mysql settings (somewhere in .mythtv) to your user, all should be well in starting up the frontend.  Make sure you are owner of that file after you copy it as well...

The firmware thing - sounds like the extract didn't put those files in the right place.  Can you find them and tell me where they are?

EDIT:
The mysql file I was referring to is in: /home/mythtv/.mythtv/mysql.txt, just copy that to your other user .mythtv directory.

The firmware should be in: /lib/modules and there are two named - ivtv-fw-dec.bin &  ivtv-fw-enc.bin, make sure you have those!

---

### Post by bubbaz on 2005-04-20
Great HowTo  &  very much needed!!  

I've been struggling without this guide for the past two weeks.  I decided to convert my 1.6G P4, add two PVR-250 tuners, and a Gainward MX440 video card.  I have everything working (including sound & tv-out), but my live tv freezes.  I see & hear a few seconds of the broadcast before the tv freezes.  After a minute or so.. it kicks back to the MythTV main menu and isn't locking up the computer.  Any thoughts?
When I mocked it up initially with one tuner the live tv worked perfectly.  
  
I also appreciated how easy it was to get mysql running correctly.  I can't tell you how often I'd get mucked up root password permissions and grant privileges.  Your phpmyadmin/apache2/mysql method is really straightforward and simple. 

If it wasn't for the live tv freeze ups, I'm sure my initial configuration would be 100%.

---

### Post by windexh8er on 2005-04-20
Are you getting prebuffer pauses?

Thanks for the feedback!!!  :)

---

### Post by bubbaz on 2005-04-20
[QUOTE=windexh8er]Are you getting prebuffer pauses?

Thanks for the feedback!!!  :)[/QUOTE]

I'm not really sure.  It's about a second or two of image & sound before it freezes. A minute or so later.. I'm back at the frontend main menu.  

Two things I'm batting around..  

1) a problem with the nvidia glx.  The previous mockup install, I used a different video driver method.  Somewhere, I remember seeing something about nvidia-myth freeze problems when one method is used.  Of course, I can't find it now. [ugh!]

2) reload the ivtv drivers.  In the mockup, I used a current 'unstable' set.  This time, I used the latest stable driver.

---

### Post by windexh8er on 2005-04-20
Run mythfrontend from a terminal - you'll see the prebuffer pauses if that's part of what you're having.  I had the same problem in Gentoo when I didn't follow the nvidia-glx documentation.  Check out the unofficial UbuntuGuide for the proper way to install the nvidia driver...  I'm running the 0.2.0 IVTV stuff with no problems.

---

### Post by bubbaz on 2005-04-20
Ok.. Success!!   I think I fixed the problem when I changed the location of the live buffer cache and saved recordings.   My partition was a little too advanced for the defaults, so I created two new folders on a larger partition and the problem vanished.
So much for my ability to follow directions. :)

I'm still without lirc, but I have all the equipment.  I'd love to test & contribute what I can to this project.

---

### Post by windexh8er on 2005-04-20
I'll try and get you a rough draft to test possibly late tonight...

---

### Post by jovian on 2005-04-21
](*,) Unfortunately Im not as lucky as the others. i have followed your instruction verbatim with the only substution being change the 386 to 686 as thats the kernel im running. Everything goes fine until I try to watch tv when all i get is a black screen. Non of the keys work and I have to kill mythfrontend from another terminal in order to get the xdiplay back. Any suggestions on what to look for/ and or fix would be appreciated
heres some system info

p4 3.06GHz
2 Gig ddr
Nvidia gf4 ti4200 (with closed drivers installed via ubuntus way)
capture card is
bt878 video/audio capture from ati
SAA7310 Video Broadcast Decoder from Avermedia

edit:
I managed to pull this error:

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2005-04-21 09:32:55.829 mythfrontend version: 0.17.20050130-1 [www.mythtv.org](www.mythtv.org)
2005-04-21 09:32:55.830 Enabled verbose msgs : important general
2005-04-21 09:32:55.932 Switching to square mode (Titivillus)
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2005-04-21 09:32:56.317 Joystick disabled.
2005-04-21 09:32:56.332 Registering Internal as a media playback plugin.
2005-04-21 09:33:01.040 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2005-04-21 09:33:01.046 Using protocol version 14
2005-04-21 09:33:01.072 Using protocol version 14
2005-04-21 09:33:01.329 RemoteFile::Read() failed in RingBuffer::safe_read().
2005-04-21 09:33:01.538 RemoteFile::Read() failed in RingBuffer::safe_read().
2005-04-21 09:33:01.747 RemoteFile::Read() failed in RingBuffer::safe_read().
2005-04-21 09:33:01.956 RemoteFile::Read() failed in RingBuffer::safe_read().
2005-04-21 09:33:02.164 RemoteFile::Read() failed in RingBuffer::safe_read().
2005-04-21 09:33:02.373 RemoteFile::Read() failed in RingBuffer::safe_read().
Couldn't read file: rbuf://127.0.0.1:6543/var/cache/mythtv//ringbuf1.nuv
2005-04-21 09:33:02.390 LiveTV not successfully started
2005-04-21 09:33:02.400 Changing from None to WatchingLiveTV
2005-04-21 09:33:02.404 Changing from None to None

which then repeats from the "Using protocol version 14" until it is killed

---

### Post by windexh8er on 2005-04-22
Are you sure you setup your live TV buffer to a valid directory when doing the mythtv-setup?  It looks like it's choking on a missing file or directory...  Your mythtv user has to be able to write to that directory.  Also - it looks like you have an extra slash (which really shouldn't matter in a *nix filesystem, but, just in case) after your mythtv directory in your setup: /var/cache/mythtv//ringbuf1.nuv.  This may matter - again check your setup and take off that trailing slash...  I usually make a directory or complete partition to hold recordings / live TV buffer, I do believe the MythTV.org directions recommend that as well.

As for those who e-mailed me regarding the LIRC stuff - sorry, I haven't been getting home until after 11pm and have been too tired to transfer my documentation to something electronic.  Hopefully by Sunday sometime!!!

---

### Post by jovian on 2005-04-22
ahh the sweetness of mythtv is now known to me. here was the issue. After lots of digging found that my capture card an ati tv wonder ve was not supported by the typical bttv drivers and that the latest video 4 linux 2 was needed. after a couple failed attempts at trying to install the appropriate drivers from source i stumbled acrss System>prefrences>MultimediaSystems Selector and lo and behold it was defaulted to v4l I switched it two v4l2 and all is good with the world. I din't catch this right away because the chip on the card said 878 which i noticed was supported evidently though thats not the connextant 878 chip which requires the 8x8 driver which v4l2 has. so lesson is

You use a ATI TV Wonder card (note not the all in wonder)
System>Prefrences>Multimedia System Selector
change to Video 4 Linux 2 (I also switched to use sdl) in the video tab
follow this excellent guide

---

### Post by bubbaz on 2005-04-22
Congrats, Jovian!

---

### Post by scholzie on 2005-04-24
I've just completed most of my own guide, which I feel has some more information on the specifics of what needs to be done. Please check it out. I had started it a few weeks back, and when this thread was posted it lit a fire under my butt to complete it   :grin: 

[http://www.cs.rit.edu/~css8044/?q=mythtv](http://www.cs.rit.edu/~css8044/?q=mythtv)

---

### Post by windexh8er on 2005-04-25
MHO - it's a good guide, kinda bulky where it doesn't need to be, but definitely formatted a whole heck of a lot better than mine.  :)  Not sure you needed to post here regarding, but...  Hey, more power to you!

---

### Post by laurens on 2005-04-25
[QUOTE=windexh8er]MHO - it's a good guide, kinda bulky where it doesn't need to be, but definitely formatted a whole heck of a lot better than mine.  :)  Not sure you needed to post here regarding, but...  Hey, more power to you![/QUOTE]

Did you get round to put your lirc guide up, yet? Many people are eagerly awaiting it..

---

### Post by windexh8er on 2005-04-25
No - I must have written my excuse in the other thread.  :)  I ended up being out of town all weekend.  I *promise* tonight...  I'm in CST so, figure by 11:30pm - better give myself ample time!  If only I would have done this guide this past winter when I was over in Europe with a lot of extra time...  Excuses, excuses!

---

### Post by scholzie on 2005-04-25
[QUOTE=windexh8er]MHO - it's a good guide, kinda bulky where it doesn't need to be, but definitely formatted a whole heck of a lot better than mine.  :)  Not sure you needed to post here regarding, but...  Hey, more power to you![/QUOTE]
I didn't post it here to kick sand in your face or anything. I posted it here because the people who would be looking at yours are probably going to be interested in mine as well, and I felt it would be a waste of my hard work to let it go unnoticed. 

There is room for two guides. As far as being bulky...perhaps. I made it a point to cover every caveat I came across, as well as make a true "guide" for installing from scratch, rather than a few helpful pointers. I have been spoiled by the Gentoo documentation, and nothing aggrevates a linux user more than not knowing why something isn't working. I tried to cover all the bases, and I'm sure time will show that people appreciate it (at least, that's the plan).

---

### Post by windexh8er on 2005-04-25
Game on - no offense taken.  I just figured that why try try to encompass the world when all you're trying to do is one specific thing.  LIke I said in my doc - it's a Myth doc, nothing else.  There are plenty far better references for installing Ubuntu and getting things setup correctly (take the unofficial Ubuntu guide for e.g.).  If you really want to write Gentoo style docs you have to do everything - from start to finish.  That kind of doc would require a lot more maintenance and pages than just a few.  And I try not to make the user do extra things that have no relation to Myth (ssh, sources other than Ubuntu's, throwing stuff in modutils when you don't need it, etc...) when all they want is to watch TV.  :)

I guess that's difference on POV...  But.  Anyway.  The thread's about the guide - I'll quit rambling!

---

### Post by CompEngr on 2005-04-29
Many of you have been returning waiting for the lirc to appear.  I personally have been waiting for about two weeks now.  I finally have taken matters into my own hands and started a small howto.  It may be incomplete seeing as I am so new to linux, but it seemed to work when nothing else has.  Give it a read, apply it, and fix the errors.

The new thread is at [http://ubuntuforums.org/showthread.php?p=152456#post152456](http://ubuntuforums.org/showthread.php?p=152456#post152456)

---

### Post by paulhoy on 2005-05-13
[QUOTE=scholzie]I've just completed most of my own guide, which I feel has some more information on the specifics of what needs to be done. Please check it out. I had started it a few weeks back, and when this thread was posted it lit a fire under my butt to complete it   :grin: 

[http://www.cs.rit.edu/~css8044/?q=mythtv](http://www.cs.rit.edu/~css8044/?q=mythtv)[/QUOTE]


I think it's great that you posted here, and the extra detail is great for newbies. Now, get that lirc doc. out :)

Thanks

---

### Post by paulhoy on 2005-05-14
Hi,

Newbie question here - you mention knoppmyth a few times. Did you install Knoppmyth onto Ubuntu?

Thanks




[QUOTE=knathraak]Nice guide.  Thanks for putting this together, as there is a lack of adequate Myth converage for Ubuntu.  You should get this listed over at pvrguide.no-ip.com.  There's a collection of howtos there for various distros.

Can't wait for the lirc stuff.  That was one of the things that really gave me troubles before I defected to KnoppMyth.

A couple of other sticky spots I ran into that you may want to mention [if these things are there already maybe i just overlooked them]:
--Make sure you don't already have a mythtv user before you install the myth packages.  If you do, the package configuration croaks when it tries to create the mythtv user.
--Maybe want to list the special code myth users are supposed to register with at labs.zap2it.com

Great guide and thanks again![/QUOTE]

---

### Post by frkstein on 2005-05-14
windexh8er, I tried using your Howto but I have a problem loading the modules into the kernel.  This is the output I get from dmesg. Any ideas?

May 14 12:31:00 localhost kernel: ivtv: ==================== START INIT IVTV ====================
May 14 12:31:00 localhost kernel: ivtv: version 0.2.0 (rc3j) loading
May 14 12:31:00 localhost kernel: ivtv: Linux version: 2.6.10-5-386 preempt 386 gcc-3.3
May 14 12:31:00 localhost kernel: ivtv: In case of problems please include the debug info
May 14 12:31:00 localhost kernel: ivtv: between the START INIT IVTV and END INIT IVTV lines when
May 14 12:31:00 localhost kernel: ivtv: mailing the ivtv-devel mailinglist.
May 14 12:31:00 localhost kernel: ivtv: Autodetected WinTV PVR 250 card
May 14 12:31:00 localhost kernel: ivtv: Found an iTVC16 based chip
May 14 12:31:00 localhost kernel: PCI: Found IRQ 9 for device 0000:00:0b.0
May 14 12:31:00 localhost kernel: ivtv: Unreasonably low latency timer, setting to 64 (was 32)
May 14 12:31:00 localhost kernel: ivtv: VIA PCI device: 0x3189 vendor: 0x1106
May 14 12:31:00 localhost kernel: tveeprom: Hauppauge: model = 32062, rev = C182, serial# = 7913781
May 14 12:31:00 localhost kernel: tveeprom: tuner = LG TAPC H791F (idx = 82, type = 39)
May 14 12:31:00 localhost kernel: tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
May 14 12:31:00 localhost kernel: tveeprom: audio_processor = MSP3445 (type = 12)
May 14 12:31:00 localhost kernel: ivtv: i2c attach [client=tveeprom[0],ok]
May 14 12:31:00 localhost kernel: ivtv: Tuner Type 39, Tuner formats 0x00001000, Radio: yes, Model 0x008d1612, Revision 0x00000000
May 14 12:31:00 localhost kernel: ivtv: NTSC tuner detected
May 14 12:31:00 localhost kernel: ivtv: Radio detected
May 14 12:31:00 localhost kernel: tuner: Ignoring new-style parameters in presence of obsolete ones
May 14 12:31:00 localhost kernel: saa7115: starting probe for adapter SMBus Via Pro adapter at e800 (0x0)
May 14 12:31:00 localhost kernel: saa7115: starting probe for adapter ivtv i2c driver #0 (0x10005)
May 14 12:31:01 localhost kernel: ivtv: Encoder mailbox not found
May 14 12:31:01 localhost kernel: ivtv: Decoder mailbox not found
May 14 12:31:01 localhost kernel: ivtv-iTVC15_16_mpg2_encoder_card: probe of 0000:00:0b.0 failed with error -12
May 14 12:31:01 localhost kernel: ivtv: ====================  END INIT IVTV  ====================

---

### Post by frkstein on 2005-05-14
Solved my own problem. Turns out I didn't have the card complete installed in the pci slot. Go figure. ](*,)

---

### Post by Drain on 2005-05-17
I found the ubuntu/mythtv install guide at [http://www.cs.rit.edu/~css8044/?q=mythtv](http://www.cs.rit.edu/~css8044/?q=mythtv) by searching google a while ago, but having the other two guides ([http://pvrguide.no-ip.com/](http://pvrguide.no-ip.com/)  and [http://www.slash32.com/ubuntu-myth.html](http://www.slash32.com/ubuntu-myth.html)) have also been useful. I've had Ubuntu on my new computer for all of 3 days now, and been playing around with a couple of different aspects of it, but now I'm ready to get down to putting Mythtv on it. 

So here are the big challenges: 
1. Different tv card. The HD-3000 from [www.pchdtv.com](www.pchdtv.com). 
2. I'm running it on an AMD64. 

Good documentation on either one of those seems to be pretty sparse, and I'm perfectly willing to help by writing up my process as I go through them. But I figured I would seek out any advice from the community as I go through the ordeal ;-) I know it's do-able ([http://www.krose.org/~krose/freesoftware.html](http://www.krose.org/~krose/freesoftware.html) has used a similar setup, but there is not a whole lot there on the "how" so much as the end result). 

So any suggestions? ;-)

---

### Post by atezun on 2005-08-04
i installed everything exactly as instructed except when i try to open iot it seg faults, os i tried the previous advice for seg faulting but all i get is 

```
2005-08-04 14:57:54.914 Switching to square mode ()
2005-08-04 14:57:54.927 Unable to connect to database!
2005-08-04 14:57:54.928 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

couldn't open db
2005-08-04 14:57:54.929 Switching to square mode (blue)
Segmentation fault
```

any ideas?

---

### Post by tom-ubuntu on 2005-08-09
Looks like you have no permissions to access mysql with the mythtv users. I am not a mysql expert, so can't give you exact steps. Check somehow the hostmaks which is allowed to use mythtv user. Perhaps is is just 192.168.x.x instead of 127.0.0.1.

---

### Post by kkvenkit on 2005-08-16
The password for MySQL's root account differs from what you provided during the mythtv-setup script (off-hand it's this script). 

If you never set the MySQL root password:
1. run *mysql -u root mysql* from a command-line.
2. then run *UPDATE user SET Password=PASSWORD('<your password here>') WHERE user='root'; FLUSH PRIVILEGES; quit*, replacing <your password here> with the password you gave to mythtv during its setup.

If you don't recall the password you gave to mythtv during its setup choose any password above. Then run *mythtv-setup* and provide the new MySQL password.

Hope that helps.


[QUOTE=atezun]i installed everything exactly as instructed except when i try to open iot it seg faults, os i tried the previous advice for seg faulting but all i get is 

```
2005-08-04 14:57:54.914 Switching to square mode ()
2005-08-04 14:57:54.927 Unable to connect to database!
2005-08-04 14:57:54.928 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

couldn't open db
2005-08-04 14:57:54.929 Switching to square mode (blue)
Segmentation fault
```

any ideas?[/QUOTE]

---

### Post by Footer on 2005-08-21
Thank you - Thank you - Thank you!

Just finished setting my MythTV box using this guide ... I had previously run it on Fedora Core 2 and it worked fine but my main desktop is now Kubuntu so I figured the Myth box should be Ubuntu as well!  I had LIRC working on it before so I guess it's time to try getting it to work under Ubuntu now ...

Thanks again for all the hard work!  Couldn't have done it without this guide (at least not as quickly and easily!).

 :)

---

### Post by luiska on 2005-10-03
Hi

Thanks for the guide!!! I end up with one little problem. After the initial myth configuration when I started the frontend, there is only a background. There is no text whatsoever. Common sense says that it might be wanting a font that I dont have installed.

Any suggestions, or at least, where and in what conf do I change the theme back to default. 

I used the myth packaged in hoary as there is some dependecy problems when using the repo in the guide, those seem to be to new.

Thanks again
Luiska

---

### Post by triplep on 2005-10-15
Just a quick thank you for this(both) HOWTO(s).

I've just had a really nasty experience with another distro and myth, not to mention mysql, destructing of md devices and some kernel panic. we'll just say that --unmerge can become your friend. This is a fairly beefy box with 700GB to play with... who needs to delete?

Now if if the iso would just finish downloading I'd be all set.

---

### Post by mimsmall on 2005-10-31
Will this procedure work with a 350 card and Ubuntu 5.10?

---

### Post by maino82 on 2005-11-13
I'm having some problems configuring mythtv. When I run /etc/cron.daily/mythtv-backend I get the following error:

> Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2005-11-13 21:17:06.597 Unable to connect to database!
2005-11-13 21:17:06.598 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

couldn't open db
Would you like to configure the database connection now? [yes]  y
Database host name: [localhost]
Database name: [mythconverg]
Database user name: [mythtv]
Database password: [********]
Unique identifier for this machine (if empty, the local host name will be used): [my-unique-identifier-goes-here]
Would you like to use Wake-On-LAN to retry database connections? [yes]
Seconds to wait for reconnection: [0]
Number of times to retry: [5]
Command to use to wake server: [echo 'WOLsqlServerCommand not set']
2005-11-13 21:17:33.474 Writing settings file /home/mythtv/.mythtv/mysql.txt
2005-11-13 21:17:33.475 Unable to connect to database!


I'm not sure what to do to fix this or where to even begin. I'm fairly new to linux and am a complete neewbie when it comes to mysql, so any help you can offer would be greatly appreciated. Also, when I run mythfrontend or mythtv all it does is run me through some setup stuff. I can never get to a place where I can watch TV or setup recordings. What else might I be doing wrong?

Thanks,

Dave

---

