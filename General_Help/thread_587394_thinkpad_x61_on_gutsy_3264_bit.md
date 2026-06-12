---
title: "thinkpad x61 on gutsy 32/64 bit"
date: 2007-10-22
forum: General Help
---

### Post by zorkerz on 2007-10-22
I have recently done a fresh install of both 32 bit and 64 bit Gutsy Gibbon. Most things have worked fine for me here is what I have had to play with so far.

[B]Both in 32 and 64
[/B]->desktop effects (compiz): the intel x3100 graphics driver GMA 965 chipset has been blacklisted due to problems playing video. [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) Besides video not working all else seems to be ok in my brief test. The blacklist can be bypassed with this command 'SKIP_CHECKS=yes compiz'
[B]
->[/B]GNOME volume applet is set to mic instead of PCM by default

->Third mouse button does not scroll vertically:  [http://forum.thinkpads.com/viewtopic.php?p=346779&sid=8d853d569e97021a17e1604cd7fe1628](http://forum.thinkpads.com/viewtopic.php?p=346779&sid=8d853d569e97021a17e1604cd7fe1628)
    --> then it scrolls back and forth in firefox with too much sensitivity:         [http://ubuntuforums.org/showpost.php?p=3265283&postcount=31](http://ubuntuforums.org/showpost.php?p=3265283&postcount=31)

->back/forward keys on keyboard do not work. this thread provides a solution but I have gotten erratic behavior from it. how bout you? [http://ubuntuforums.org/showpost.php?p=3265183&postcount=30](http://ubuntuforums.org/showpost.php?p=3265183&postcount=30)

[B]32 bit
[/B]-resume from suspend and the screen is extremely dark due to the backlight being off -> a work around that i use is to switch to a different screen (what are the actually called) with ctrl + alt + F1 (or any F* except 7) then switch back with ctrl + alt + F7  
--> an alternate solution to this is to the install uswsup package which provides different suspend and hibernate commands but I have found this to cause new problems for me (in gutsy the hibernate command s2disk remains but the suspend command s2ram has been replaced with s2both which is supposed to suspend but also save an image of the ram to disk, people have reported problems with this)
[B]
64 bit[/B]
->keyboard volume keys go to system->preferences->sound select pcm in the bottom scroll box under default mixer tracks
->CONFIG_NO_HZ kernel config option for power saving is not yet out for 64 bit linux -> expected in 2.6.23

Two Threads that have most and link to just about everything else I have needed.
[http://ubuntuforums.org/showthread.php?t=523022](http://ubuntuforums.org/showthread.php?t=523022)
[http://ubuntuforums.org/showthread.php?t=503233](http://ubuntuforums.org/showthread.php?t=503233)
hope this is helpful
cheers

---

### Post by PhantamaroK on 2007-10-24
I've been runny 64bit Gusty on my X61 and, for the most part, absolutely love it.  My one qualm is that I can't quite seem to get rotation working with xrandr.  Whenever I enter a command it just returns the help menu.  Is this a conflict with Compiz Fusion?

---

### Post by zorkerz on 2007-10-24
afraid i know nothing about xrandr I might try the feisty thread linked at the bottom of the first post that has had many people responding.
cheers

---

### Post by victorgreen on 2007-10-29
Hey guys, I just did a fresh install of gutsy on my x61. 

I have the same suspend problem at you do Zorkerz.I can sometimes get the cntrl alt f1/f7 combo to work and not at others.

Also, when I hit the fn f4 suspend to ram keys, it takes about 30 seconds and has tons of hdd activity, I think its trying to hibernate instead [not cool, I hate hibernate and never do it]. 

I really need to be able to close the lid and have it suspend instantly like xp does. Im really starting to miss xp... thats a bad thing. 

Has anyone been able to get the internal mic to work with skype? I had it working fine with older version of skype and alsa 1.0.15rc3 in fiesty. Ive compiled 1.0.15 release version already on gutsy but I havnt had any luck.

---

### Post by victorgreen on 2007-10-29
Oh, and I have added all the resume acpi_bios=3 thingies to grub menus, it hasnt done anything.

---

### Post by victorgreen on 2007-10-29
This guide should work with the default gutsy alsa (1.0.14) but I compiled the newest stable alsa release [1.0.15 at this time]

Go to system ==> prefs==> sound
   set sound capture  to  ad198x analog

open gnome volume control by double clicking on volume applet in gnome panel 

    file change device- HDA intel alsa mixer
      edit ==> preferences - select pcm, internal mic, internal mic boost, capture , capture 1, and both options called 'input source'
 and  whatever else looks good

Then go to playback tab and jack up/unmute internal mic volume and internal mic boost if you want [note- do not max out internal mic in this menu, going over ~65% will cause a godawfully loud and painful beeping noise, I dont know why] 

under recording tab jack up capture and capture one to max [I dont know which one controls it so I jacked up both]

under switches tab  select both headphones and speaker 

under options tab make the first input source internal mic, I left the second one on Mic 

close gnome volume control 

In skype go options ==> sound devices and set sound in to HDA Intel (hw:Intel,0)

Make a skype test call to make sure its recording you. You should be good to go. 

I have noted that skype test call will record me whether I have internal mic muted in gnome volume control or not. It was also a fairly faint recording, it sounded better in Fiesty, but Im glad it works.

---

### Post by zorkerz on 2007-10-29
> victorgreen:  under options tab make the first input source internal mic, I left the second one on Mic 
What do you mean here? I do not have an options tab under gnome volume control.

Also when I turn up the volume op on internal mic I get a high pitched ringing.

I have not at this point installed skype so I did not go that far through your post.

For suspend problems i don't know too much its not an important feature for me. If my comp is on im using it. 

Have you installed the uswsusp package. I believe this provides alternate commands from the default (s2ram, s2disk, s2both). In gutsy s2ram has been removed and is replaced by s2both. What is supposed to happen with the s2both command is that it suspends like normal but also writes an image to disk in case you run out of power. A good idea in theory I think but I have had worse luck with these than the defaults. There are many threads around of people trying to get suspend and hibernate to work.

Is there a specific reason you did not install 64bit gutsy. Out of the box this has given me the bust suspend and hibernation I have gotten in ubuntu. Once it told me it failed to suspend after I resumed but never again.

good luck

---

### Post by victorgreen on 2007-10-31
The options menu should be there if youve enabled enough things under edit preferences. Skype is the only way I know of testing whether or not a microphone works.

Thanks for the tip on it suspending to both ram and disk, thats why it was taking so long and blinking the hdd light! [duh...]

Ill look into the other package because many times Im using this somewhere and I have to pack up and go and dont have time to turn it off. 

By setting in the power manager to suspend when the lid closes, upon reopening the backlight comes back on no problem. Some of those edits to the menu.lst must have done something. 

The high pitched beep will happen if you turn up the volume to max, I have mine on the lowest setting that doesnt cause that godawful noise. Sorry for not noting that before. I have no idea what the beep is. 

I didnt want to have to deal with additional software issues on this thing so I didnt go 64 bit. I have friends who use and havnt noticed any increase in speed or anything else except more hoops to jump through to get things like flash videos open. This is my only computer and it must be in good working order 100% of time. I dont have as much time as I would like to mess with it.

---

### Post by zorkerz on 2007-10-31
I was worried about 64 bit also but if anything it has worked better than 32 bit for me. I definitely notice slight performance increase. It starts up a little faster but nothing important enough my computer was plenty fast in feisty.

The options tab comes when at least one input source is checked. Although even when I check both I don't see a second input source under options.

For the internal mic there is slight sound distortion even when it is unmuted. It does not get loud or become the killer screech until I turn it up a ways. I have left it muted until I install skype. Something I need to get around to.
Cheers

---

### Post by victorgreen on 2007-11-01
Well its good to know that the mic worked for you, one of my friends with an X61s was having issues. Ill be using 64 bit Ubuntu on the next install I do, but hopefully I wont have cause to reformat/reinstall an OS on this thing for a while. Its on its 2nd set of 2 OS's. 

I was wondering what file system you use/ recommend for a laptop. I had been using ext3 on Feisty and decided to try reiserfs on this install. I notice quite a bit more frequent hdd activity.

---

### Post by zorkerz on 2007-11-02
I have always stuck to ext2 or 3 for linux distros mostly going with the default. someday i would love to do the research and actually understand the differences. I don't yet have a clear idea of  how the filesystems differ from eachother.

---

### Post by Antioch on 2007-11-03
Hi. I have a fresh install of Gusty on my X61s and was  bummed out that the desktop effects didn't work by default as I expected them to.

I ran "SKIP_CHECKS=yes compiz" and got the following errors:

abirkel@Acheron:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


Also, my right palmrest is incredibly hot - too hot to use. It was never this hot in Vista (I've actually NEVER felt it this hot, even when downloading the 700mb gusty gibbon iso at 1Mbit/sec), with or without the WiFi turned on (I have the Intel agn card). It seems linux still does a horrible job at power management. Has anyone been able to fix this?

All in all I'm disappointed with 7.10. I thought it would be a lot better than it is. At this point it doesn't seem like Linux is a viable option for the X61s. As I write this my right hand is just killing me. This is ridiculous. Of course, this makes my fan run at max speed... I'm so thoroughly disappointed. Hopefully someone has good news.

---

### Post by nattjakt on 2007-11-03
Antioch>

Yeah, my X61s also gets crazy hot around the Fingerprint scanner (to the right of the mouse buttons). I checked the System Monitor, and found that whenever work was being done on the computer, the 2 cores would alternate between 0% and 100% respectively, and when there was no more work to be done the 2nd core got stuck at 100%. That was scary, so I launched Powertop, which didn't help. So i moved the mouse pointer round-and-round (a tic, not an attempt to solve the problem), and the 2nd core stopped running amok all of a sudden. Now they both behave nicely, but my right hand side is still getting hella hot. It's scary, and I don't know what to do either. 

So... sorry about that rant =)

---

### Post by Antioch on 2007-11-03
My cores idle at 800MHz most of the time, no bouncing around.

I think the problem is that there is no WiFi power management. Vista lets you manage the power, I have mine set of medium power, medium throughput and the palmrest is only faintly warm to the touch. In Linux it just burns up.

---

### Post by fazen on 2007-11-05
If I turn off my wifi it doesn't burn.

---

### Post by victorgreen on 2007-11-05
I have the same problem with the wifi being hot, but if you enable manual cpu frequency scaling, the temps decrease somewhat if you cap the cpu at 800mhz. See [this]("http://forum.thinkpads.com/viewtopic.php?t=50949") guide for cpu scaling and other tweaks [http://forum.thinkpads.com/viewtopic.php?t=50949](http://forum.thinkpads.com/viewtopic.php?t=50949) 

The wifi does get hot though. I leave mine off 90+% of the time though. 

I went through hell with fiesty on my x61 originally, and I absolutely love gutsy on it [most everything worked out of box this time 'round]. 

I cant get powertop to give me wattage use estimates, does anyone know if that'll only show values if you are actually on batt power?

---

### Post by zorkerz on 2007-11-06
I only get wattage estimates from powertop when on battery power. Otherwise the battery is not being drained and there is no numbers to estimate from I would imagine.

I guess my laptop does get pretty hot on the right side around the thinkfinger, I never noticed this before. Computers can get pretty hot. Should I be worried?

---

### Post by nattjakt on 2007-11-06
Damn, I'm not using WiFi, and still it gets hot. I've also set the CPU @ 800mhz, and Powertop reports an average of 20-50 wakeups-per-second, which is really low. System Monitor reports a 1-5% utilization of CPU...  and still the damned computer is as hot as day one with Linux. Never noticed it at all on Vista. Also, the fan is running at 4000rpm all the time.

Oh yeah, the temp never rises above 51 degrees celcius, but that's high enough for a computer that not doing -anything-.

---

### Post by zorkerz on 2007-11-06
wow 20-50 wakeups a second. Did you do anything to get it this low?

---

### Post by nattjakt on 2007-11-08
No, nothing much at all =) Just the suggestions given by powertop, and also staying away from the 64-bit version of Ubuntu, which does not yet have support for that nice tickless kernel stuff.

That is on battery power, mind, since that allows powertop to suggest the "laptop mode" whatever that is, and when I plug in the power cord the wake-ups get up to 100-300 again, usually.

---

### Post by victorgreen on 2007-11-11
Ok well I have 32bit gutsy cause I didnt want any more issues than I already had with this machine. I dont like making work for myself. 

Anyways, I found the old posts on the fiesty x61 forums and other places about modifying /boot/grub/menu.lst My menu.lst is at the bottom of this, but I added acpi_sleep=s3_bios according to these two instructions:

First set of instructions [Thinkwiki]
   1.  In the file /boot/grub/menu.lst, find the line beginning with "# kopt=". This is where grub sets the options for your kernel. Append to this line the following: " acpi_sleep=s3_bios". (That is, these words should be preceded by a space separating them from the existing options. Do not remove the initial "#" from the line.) 

2. Run the command update-grub as root. 

Second Set of Instructions- MB Sullivan on Feisty on x61 thread
      Perhaps the most intelligent way to do this is to add it to the "additional options" section, as follows:

Code:
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash acpi_sleep=s3_bios

This will automatically insert it into each kernel's option list when update-grub is called. Otherwise, you would have to manually re-add it each time you update your boot list.

Those two things might do the same thing, im not sure, but I did both and backlight is fine if I suspend when close lid but not ok when I hit fn f4. Go figure. 



 # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## Splash image!
splashimage (hd0,2)/boot/grub/images/grub_skull.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0502f3fe-028d-49c4-a317-1a9cd717bcf1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash acpi_sleep=s3_bios

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0502f3fe-028d-49c4-a317-1a9cd717bcf1 ro quiet splash acpi_sleep=s3_bios
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0502f3fe-028d-49c4-a317-1a9cd717bcf1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		M$ Winturd Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by skier on 2007-11-12
This works perfectly Victor, thanks.

---

### Post by nattjakt on 2007-11-12
Oh my, I didn't get much of that, victor... the what goes where now? Did the last part of your config succeed in making the backlight function after a Fn+F4 or not?

---

### Post by victorgreen on 2007-11-13
Sorry, nattjakt.

The relevant portion of the post was the beginning part (rewritten here). 

Get into /boot/grub/menu.lst
find the line that starts with # kopt=
add acpi_sleep=s3_bios to the end of whatever kopt equals

I also found the section of the file that looks like this:
# defoptions=quiet splash acpi_sleep=s3_bios

Then run 
sudo update-grub 

I cant recall if a restart is required or not at this point.

Anyways then backlight was fine after:
-  telling computer to suspend in the menu that opens when you click the power icon the upper right hand corner of the top gnome menu

-telling  the computer to suspend when the lid is closed

The backlight still has issues when you suspend with fn f4

Also, we are all still plagued by the little change they apparently made to gutsy- it no longer just suspends but both hibernates and suspends in case you run out of power while you're suspended. Its really dumb, I hate hibernate, and there is no easy way to just get it to suspend to ram.

---

### Post by sheol on 2007-11-17
Pg_back and Pg_forewards work by default in Kubuntu, and are easily remapped.in KDE's Keyboard Shortcuts by simply hitting the key (I mapped them to switch my desktops).

The code for them is: XF86Forward and XF86Back

I'm not sure why you guys are having trouble mapping them in Gnome.

---

### Post by zorkerz on 2007-11-17
If your referring to the two keys to the left and right of the up arrow I have also set them to XF86Forward and XF86Back and this works well for most things. However firefox does not like it. In another thread mbsullivian gave directions for how to change the keys in firefox this unfortunately has created erratic behavior for me.

---

### Post by zorkerz on 2007-12-11
hello,
so im trying to access an external hardrive. It belongs to my friends older mac laptop. I am assuming it has hfs+ as a filesystem (any reason to think otherwise). It uses firewire. When I plug it in nothing happens. gparted does not see it. If i boot into vista it detects the device but has no drivers for it. I am thinking it as a problem with firewire or I don't krow how to deal with hfs+. Anyone have any ideas?
cheers

---

### Post by ritzdank on 2007-12-27
My X61s gets terribly hot as well under fingerprint reader. Is there any working power management for intel wifi chipset out there?

Suspend/Hibernate works fine!

My harddrive is driving me crazy at the moment. It seems that it is spinning up/down every second when the computer is idle. I have a 100Gb 7200rpm sata drive. I tried suggested things from this thread [http://ubuntuforums.org/archive/index.php/t-531866.html]("http://ubuntuforums.org/archive/index.php/t-531866.html")
without any success?

```

sudo vim /etc/init.d/local_settings

Add this line:
hdparm -B 254 /dev/sda

sudo ln -s /etc/init.d/local_settings /etc/rc2.d/S99local_settings

```

Thanks, indeed!

---

### Post by Dynaflow on 2007-12-30
> **ritzdank said:**
> My X61s gets terribly hot as well under fingerprint reader. Is there any working power management for intel wifi chipset out there?

Suspend/Hibernate works fine!

My harddrive is driving me crazy at the moment. It seems that it is spinning up/down every second when the computer is idle. I have a 100Gb 7200rpm sata drive. I tried suggested things from this thread [http://ubuntuforums.org/archive/index.php/t-531866.html]("http://ubuntuforums.org/archive/index.php/t-531866.html")
without any success?

```

sudo vim /etc/init.d/local_settings

Add this line:
hdparm -B 254 /dev/sda

sudo ln -s /etc/init.d/local_settings /etc/rc2.d/S99local_settings

```

Thanks, indeed!

Given that it's a SATA hard drive and the way you describe your problem, you may be suffering from the load-cycle issue and may want to read through [this stuff]("http://ubuntuforums.org/showthread.php?t=591503") thoroughly and see if you need to apply the ["ugly fix."]("http://ubuntuforums.org/showpost.php?p=3675960&postcount=26")  It seems that the (stupid) BIOS/firmware-level settings on a lot of laptop hard drives basically cause the things to slowly self-destruct when not tightly controlled, and that Gutsy's kernel isn't set to exercise that kind of control by default.

---

### Post by zorkerz on 2008-01-02
OOPS Apparently I replied to a post much earlier in this thread.
this post can be deleted

I have stuck to ext3 as it is default. I the past I have read a bit about the differences between various filesystems. It seems they all have strong points and weak points. I have never found anything important enough for me to try anything different out.

---

### Post by palustris on 2008-01-17
I'd like to thank you all for the help you have provided ...your posts have helped me get my x61 up and running.  I am completely new to Linux and have been grateful for all the ready lessons these posts provide which have helped yield a capable platform to conduct my work.  That said, I have a problem and need some help...

I have had a strange thing happen after I have plugged in a usb mouse.  After using the usb mouse my red finger track mouse has been rendered mostly useless.  By mostly useless I mean that the arrow just hops around the screen but I effectively have no control. This persists (though intermittently) after a restart with or without the usb mouse plugged in.  I have also lost the ability to use my center button to scroll through a page.

In addition, at times my laptop keyboard lags in typing or simply won't type at all.  The most perplexing thing about all this is that these symptoms are not constant or even directly attributable to any certain action, I notice that they tend to occur when I have a  lot of  tabs open in firefox...and that the keyboard never works when the computer returns from being suspended.  Also it seems the symptoms get worse the longer the computer is running  after I am eventually forced to restart though the memory and cpu use are all about normal...never maxed out. 

please help.

---

### Post by zorkerz on 2008-01-17
My first question I guess is if this is a software (ubunut) problem or some weird hardware thing. Are you dual booting with any other os? Or do you have a live cd and a cd drive (for the x61) to test out? If these work fine then something has gone wrong with ubunut. Unfortunately I think thats as far as my knowledge will be able to help.
good luck

---

### Post by palustris on 2008-01-17
I only have Ubuntu on the computer...have had it running for 3 months now, these issues have developed in the last week.  The hardware had been working before so I think it is a software issue....that I somehow messed it up.
thanks

---

