---
title: "Ubuntu won't boot or load from CD"
date: 2007-08-14
forum: General Help
---

### Post by pikaia on 2007-08-14
First of all thanks ahead of time for any help given.

I recently became interested in giving Linux a try and downloaded and burned several Live CDs (ubuntu and Kubuntu among them).  I have to say that NO linux distribution I tried loaded on my desktop.  But I loaded them on my laptop without issue and also and old desktop I have.  This has been frustrating since, after some 'playing around,' decided I'd like to make a dual boot machine with the hopes of potentially becoming a (nearly) permanent linux machine (except for a few games I like to play).  

I build computers on the side and yesterday built a box for a family member and decided to install ubuntu on it.  It installed NO Problem.  I decided maybe it was an issue that would could be bypassed by using this new machine to install Ubuntu onto a backup hard drive and then connecting that to my machine.  

I did that and as it went to boot, I got the GRUB starting line and then the GRUB error 21.  

Why won't my box take ANY linux OS?
[LIST]
[*]AMD 64 2800
[*]Chaintech VNF-250 MOBO
[*]1.5 GB Corsair RAM
[*] using Feisty Fawn
[/list]
When I tried to boot it directly from the Ubuntu LiveCD it would *sometimes* get to just as the loading music would play and the 'loading desktop' bar would show up, then it would freeze.  Kubuntu wouldn't even load passed 77% on the Kernel loading screen.  

Any ideas?  Is there a BIOS setting I need to tweak?

Thanks again.

---

### Post by K.Mandla on 2007-08-14
I hope you don't mind if I ask some seemingly stupid questions.

[LIST=1]
[*]Are you using the 64-bit versions, or the standard i386 versions?
[*]Have you tried dropping back to an earlier version of Ubuntu, like 6.06?
[*]What kind of video card are you using in that machine? or is it onboard?
[*]Have you tried any other distros, other than Ubuntu-based variations?
[*]Can you boot into rescue mode? Does it get all the way to the root prompt?
[/LIST]
Grub error 21 means a missing drive or an invalid partition, I believe. This could mean that when you installed it on the other computer, it was assigned as a different drive. You might be able to get the machine to boot by editing the kernel boot line when the machine starts up. You'll have to tell us which drive the Ubuntu system is on, and the contents of your /boot/grub/menu.lst file.

---

### Post by pikaia on 2007-08-14
[LIST=5]
[*]I have both the 64 bit and 32 bit versions but am currently using the 32 bit version.
[*]I haven't tried using 6.06 yet, thats my next move.
[*]I just upgraded my video card to a 7600GS AGP but it also wouldn't work with an ATI 128MB PCI or an ATI 64MB TNT AGP
[*]I've tried Fedora, GoblinX, PClinuxOS, and freespire-NONE work.
[*]Also haven't tried Rescue mode.  I'll see what happens.
[/LIST]

Ubuntu is currently on the ONLY drive on the machine.  Jumper set to Cable select.  Cable connection is the master.

Again I'm a super Newbie when it comes to this stuff, I'm still extremely frustrated when trying to install some things.  (Mplayer - installed through Synaptic is giving me:  "error opening/initializing the selected video_out (vo) device."  But thats another issue).  How do I access that file?  I typed it into the terminal and it told me 'permission denied.'

Thanks.

---

### Post by logos34 on 2007-08-14
can you post your menu.lst as k.mandla suggested?  Because it may be that drive was designated '(hd1)' when installed on the other machine, but when you put it in your desktop (where it is the only hard disk) it is '(hd0)'.

Boot from the live cd and click your root partition to mount.  Then 

[B]cd /media/disk/boot/grub
cat menu.lst device.map[/B]

Post.

For Mplayer, you need to change the video driver ('vo_driver ='):

**gedit ~/.mplayer/gui.conf**

or just open mplayer, >Preferences>Video tab

---

### Post by pikaia on 2007-08-14
As far as the Live CD Boot goes, that'll have to wait until a bit later.  I have to run to work for a couple hours and then I'll post what I find.

As far as the Mplayer goes... thats a no go.  
The **gedit  ~/.mplayer/gui.conf** results in a No such file or directory.
When I look at the Video Tab on MPlayer the only configurable line is dxr3 -dxr3/H+ video out, but what am I supposed to change it to?  I've walked through most of the terminal codes posted online about updating the codecs and repositories for Mplayer, but have been fairly unsuccessful.  I keep running into issues.  I know this must be extremely newbish but I'm trying and am extremely frustrated.

Thanks.

---

### Post by logos34 on 2007-08-14
> **pikaia said:**
> As far as the Live CD Boot goes, that'll have to wait until a bit later.  I have to run to work for a couple hours and then I'll post what I find.

As far as the Mplayer goes... thats a no go.  
The **gedit  ~/.mplayer/gui.conf** results in a No such file or directory.
When I look at the Video Tab on MPlayer the only configurable line is dxr3 -dxr3/H+ video out, but what am I supposed to change it to?  I've walked through most of the terminal codes posted online about updating the codecs and repositories for Mplayer, but have been fairly unsuccessful.  I keep running into issues.  I know this must be extremely newbish but I'm trying and am extremely frustrated.

Thanks.

You should have more video drivers listed.  (ie x11, xv, gl, xvidix, dxr3, etc).  The [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats?highlight=%28RestrictedFormats%29") page will hopefully get you sorted.
[https://help.ubuntu.com/community/MPlayer#head-ef33a9443d32283f48f446547a38b21bd635184b](https://help.ubuntu.com/community/MPlayer#head-ef33a9443d32283f48f446547a38b21bd635184b)

The Mplayer config files are normally in your home dir in a hidden '.mplayer' folder.  Try:
[B]
locate gui.conf[/B]

Or search for mplayer in synaptic and check the 'installed' files tab

---

### Post by pikaia on 2007-08-14
okay.

I've tried a few things and still haven't gotten much farther.  I still can't get Mplayer to play a dvd, the ONLY drivers listed in the Preferences tab are:
[LIST]
[*]xmga
[*]xv
[*]x11
[*]gl
[*]gl2
[*]dxr3
[*]xvidix
[*]xvmc
[/LIST]

I've installed medibuntu through the terminal as well as the 'restricted' formats.  But it will not play a DVD.  (Neither Mplayer or Totem)  MPlayer gives the video out device error, Totem says it doesn't have the proper plug ins.

As far as the main issue.  I couldn't get the hard drive to boot on my pc no matter how I had it set up.  I bounced the jumper around, changed the cable connection and every time it gave me the GRUB error 21.  I reconnected it back to the computer I installed it on initially and it continued to give the same error... had to reload the LiveCD and reinstall.  

I put Ubuntu on another HD and got it to boot up to past the load bar and then locked up, tried it a second time and it made it to the next screen before erroring out.  I tried booting in recovery mode and it told me that there was no screen detected, and the graphics device was unsupported.  I'm going to retry an old AGP card I have sitting around here but I don't have faith.  I tried booting the LiveCD in graphics Safe mode several times to no luck.  

I appreciate all the help.  Sorry for my extreme newbish-ness.  (I'm sure that doesn't help)

Just for reminder, my graphics card is Nvidia GeForce 7600GS AGP.

Edit:  Swapped Nvidia Card for an old ATI and still the same issue, and gives the 'No Nvidia driver support'  (something like that) and gives the Server X screen which says NO SCREENS.

On the DVD front, I got Totem to play the dvd but not Mplayer, I had to install Automatix2 and the codecs associated.  MPlayer is still being a pain in my butt.  I like the Windows version, but this is getting out of hand.  Thanks.

---

### Post by logos34 on 2007-08-14
DVD playback requires [libdvdcss2]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").  I use totem-xine (better than the gstreamer engine).  

Your mplayer video driver tab looks like mine.

As for installing ubuntu:

--try flashing the bios if you haven't already--it's the first thing you should do after building a pc (there's a recent update for the VNF3-250 [here.]("http://www.chaintechusa.com/eng/a2111_product_download.php?serno=320"))
--double check that the Bios is correctly seeing the hard disk (should be set for 'auto' detect, not 'user' defined, LBA, CHS, etc)
--make sure onboard video (if applicable) is disabled, since you're using AGP card
--try F1 help on the LiveCD for [kernel boot parameters]("https://help.ubuntu.com/community/BootOptions?highlight=%28boot%29") 
--run memtest86+ from livecd menu to check your RAM
--try installing using the text-mode ubuntu alternate CD

---

### Post by pikaia on 2007-08-15
I'm checking into flashing.  I've downloaded the file and its full of a dozen different BIOS versions with the latest being from September 2005.  

-BIOS sees HD without issue.
-There is no Onboard Video.
-The PC I'm using is an established one, (the one I built yesterday runs Ubuntu with no problems) and so    the RAM is good (last ran memtest in March).
-Would installing using the alternate CD somehow bypass this issue?  I've got a drive with Ubuntu already installed, and it still errors out and loads non-graphical based Linux after the Server X failure.

I'll try to get libdvdcss2 installed, but why is one player working and not the other?  

Thanks again.

Also, I'm getting a series of error messages at the end of each install/update of any file.  The messages refer to OpenOffice even though the updates/installed programs do not... do I need to update Openoffice?

---

### Post by logos34 on 2007-08-15
> **pikaia said:**
> I'm checking into flashing.  I've downloaded the file and its full of a dozen different BIOS versions with the latest being from September 2005.  

-BIOS sees HD without issue.
-There is no Onboard Video.
-The PC I'm using is an established one, (the one I built yesterday runs Ubuntu with no problems) and so    the RAM is good (last ran memtest in March).
-Would installing using the alternate CD somehow bypass this issue?  I've got a drive with Ubuntu already installed, and it still errors out and loads non-graphical based Linux after the Server X failure.

I'll try to get libdvdcss2 installed, but why is one player working and not the other?  

Thanks again.

Also, I'm getting a series of error messages at the end of each install/update of any file.  The messages refer to OpenOffice even though the updates/installed programs do not... do I need to update Openoffice?

Oh, so you have dvd playback, just not on mplayer or totem?

The bios update: so that's why it said 'bios all'--they just threw everything into that archive recently.  Looks confusing--just forget it.  You probably already have the latest.  (What happened to Chaintech?  Was it bought out by this Walton company or what?  Because that's the site for 'chaintechusa'.)

I suggested the alternate install because frankly I'm out of ideas.

Try adding some boot options/kernel parameters. 

Maybe it's solely a graphics problem.  Try booting into recovery mode on the ubuntu hard disk and running the interactive xserver config (maybe you did this already). 

dpkg-reconfigure xserver-xorg

Choose 'vesa' driver and go thru the steps accepting defaults for the most part. 

Or try to download and install the nvidia driver:

sudo apt-get install nvidia-glx

sudo nvidia-glx-config enable

---

### Post by pikaia on 2007-08-15
Again, thanks a lot for sticking with me.  Its frustrating.  

I don't know what happened to Chaintech.  I've been real happy with the board up until this point.  

I do have DVD playback with Totem now (although only with a burned disc, haven't tried commercial copy).  I thnk I'd prefer MPlayer, but I'm sure I'll figure out all the MPlayer problems in time (along with installing in general).  I'm trying to remember that Windows hasn't always been comfortable to navigate so Ubuntu should just take some time.  Quick question.  Will the Terminal codes become easier?  Will I know to download/install something I just need to type: sudo apt-get install 'something'?  Or is it different all the time.  Because some of it seems like the learning curve isn't so bad (like the line I just posted) and then some seem to have seeming endless lines of code.  Or will I just have to do searches online to figure out how to install something whenever I can't find it in Synaptic or Automatix?  

I have to admit a lot of it has been confusing (and more than a little frustrating) when trying to do something I think shouldn't be this complicated.  (but I guess this is part of the reason I went with Ubuntu and not something more commercial like Xandros or Linspire, so I could actually learn a few things).  I still have problems when I see instructions to goto home directory, change location, rename... I guess I'm confused more with the terminology than the actual process.  Do I do this in the file system screen or in the terminal?  If its in the terminal, HOW do I do it?  I also don't fully understand some of the other instructions I've seen like:
Boot from the live cd and click your root partition to mount. Then

cd /media/disk/boot/grub
cat menu.lst device.map

Was I supposed to do this from the partition screen?  In the terminal?  As I write all this I realize I sound as inept as they come.

You suggested adding boot options or parameters, How do I do that?

I'll give the code you listed a try next time I boot up.  Its gotta be the board because I've swapped everything else into other machines that have had no problems at all.  I just can't figure out why it is still listing the Nvidia issue when I replaced it with the old ATI card?  I *sometimes* can get it to boot to the text version, but probably 50% of the time it errors to the server X error screen (blue and choppy), and sometimes it boots to terminal and asks for password.  (and sometimes that becomes frozen too.  

Sorry for the unloading my irritation here, I get this way when i can't figure something out.  (I'm a scientist...)  Maybe its time for Ubuntu for dummies...

Any thoughts on the Openoffice errors that are being thrown up everytime I install/update something?  I'll try and post the actual error messages tonight.  They appear at the end of the install/update series of terminal codes, probably about 10 or so lines worth of Openoffice errors.

---

### Post by logos34 on 2007-08-15
> **pikaia said:**
> ...Quick question.  Will the Terminal codes become easier?  Will I know to download/install something I just need to type: sudo apt-get install 'something'?  Or is it different all the time.  Because some of it seems like the learning curve isn't so bad (like the line I just posted) and then some seem to have seeming endless lines of code.  Or will I just have to do searches online to figure out how to install something whenever I can't find it in Synaptic or Automatix?

Like anything new it just takes some time getting used to, especially  coming fresh from windows or osx where everything is done for you as if you were an idiot.  Yes, the directory (tree) structure and the command line can be intimidating (or exasperating) at first, but after a little reading and hands-on usage it's not all that bad.  Personally it was perhaps easier for me than most because I built my first desktop box specifically with linux in mind (I was determined to be free of the Microsoft grip and these PC makers with their shoddy tech support!) and I did a fair amount of research into both the hardware and linux OS--I actually spent much more time than was necessary because everything 'just worked' (well, almost everything).  But I nevertheless consider it time well-spent because I learned a lot about systems and components and how the OS and hardware interact.  At any rate, you'll be installing most software as .deb pkgs (debian packages) straight from the ubuntu repositories using synaptic/apt, and any other stuff you put in will likely have its own installer (you just do './<pkgname>.bin,  or 'sudo sh <pkgname>.run', etc.) or be easily compiled from source by unpacking a tarball and simply running ./configure, make, sudo make install commands. (dependencies can cause frustrations though).  I still have a lot to learn but I can handle most of the stuff I run into.  But there are times you will have to google around for more info.  (Like I'm doing right now to figure out how to compile the HelixPlayer from source using the latest GCC version that my FF browser build uses in the hope that I can get the plugins to work as they should with RealPlayer--I seem to be cursed with buggy playback of .rm video streams) 

There are a zillion good links you could check out but here's a good, concise overview (besides they're ubuntu-specific):

"Using the Command Line":
[https://help.ubuntu.com/7.04/basic-commands/C/](https://help.ubuntu.com/7.04/basic-commands/C/)

"Installing Software":
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

Be sure to check out this amazing reference link:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

> 
I also don't fully understand some of the other instructions I've seen like:
Boot from the live cd and click your root partition to mount. Then

cd /media/disk/boot/grub
cat menu.lst device.map

Was I supposed to do this from the partition screen?  In the terminal?  As I write all this I realize I sound as inept as they come.

You suggested adding boot options or parameters, How do I do that?

Forgive me if I assumed you knew to use the terminal for those commands, most have no problem (I read a lot of these threads and they all start to run together in my head).  I should have said 'Then open a terminal and type...'  But surely you know what the root partition is--you set it up during install!  All you have to do in Feisty live cd (using the other machine of course--I should just told you to boot the hard disk) is click on a partition and it mounts.  Then you can navigate/change directory ('cd') to access files.  'cat' = concatenate (print files menu.lst and device.map in terminal together).

As for the boot options/kernel parameters, I spelled it out in post #8 (link and all).

Yeah, I agree it's gotta be something to do with the mobo (I mean, what's left?).  Maybe someone else has some ideas on this....

---

### Post by pikaia on 2007-08-15
SO CLOSE!!!

I went through the 'vesa' set up and got through to the load bar screen (brown Ubuntu background and then the Ubuntu bar comes up and starts loading apps... then it froze!!)  I'm going to try again and see if I missed something.  

I'll let you know.

---

### Post by pikaia on 2007-08-15
We're Close!!  Very Close!  

I installed the Nvidia driver and got through the boot and everything posted and then it locked up.  I'm looking at the main screen right before the Ubuntu background loads.  (light tan background right now)  Any other options?

Thanks again, and if nothing else, you've been very very helpful in dealing with my frustration.

Edit:  Okay, it seems like it might have been a one time teaser.  I got just passed the Nvidia logo this time and then it locked.  I'll keep trying until I hear something.
Edit2:  Second try gets me to the desktop, files appear, background loads... and freezes... (using vesa drivers)  I'm at a loss.  Any help?

---

### Post by pikaia on 2007-08-16
I'm not sure if I did something right or just managed a fluke here.  But it booted up and loaded.  What I did was disable APIC in the BIOS and then went into the boot menu and added the lines acpi=off and nolapic and then rebooted.  

I'm not sure what video drivers I'm currently using, but I don't think its the nvidia since I didn't get the splash screen.  

I'm going to reboot and see if I can't see what the settings are.

---

