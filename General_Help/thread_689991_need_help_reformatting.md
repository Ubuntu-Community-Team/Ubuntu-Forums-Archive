---
title: "need help reformatting"
date: 2008-02-07
forum: General Help
---

### Post by dzza on 2008-02-07
Hi, i've got 2 partitions, ubuntu and suse.  I don't use the suse at all, never really have.  I don't know linux beyond the basic user friendly environment, and that's been fine for a while but now I need to be able to do some analysis stuff that I'd feel more comfortable doing on windows for the time being.  

The problem is that my keyboard doesn't initialize until the ubuntu login starts up.  That means I can't press F2/F8/Del whatever to boot from a cd, can't change between partitions if i wanted to by selecting the alternative via up/down, and I can't "press any key to boot from cd" when I put in the windows boot cd.

I've posted a few places about the keyboard issue (its not a ps2/usb issue as i've tried both) and I've pretty much given up on it.

Can anyone suggest an alternative way to start up my xp install cd?  Any help is greatly appreciated.

---

### Post by kesman on 2008-02-07
Have you tried with another keyboard? This seems quite weird since you should be able to access the bios  if you need to.

---

### Post by dzza on 2008-02-07
Yes my keyboard is ps/2, i bought a usb keyboard and tried that and nothing changed.  Then I tried a friend's ps/2 keyboard, and nothing changed.

---

### Post by seventhc on 2008-02-07
What kind of computer is it...model etc...?
I think you might be trying the wrong keys to get into your BIOS. Keyboards are initialized fairly quickly, I have never seen a computer where you couldn't get access to the BIOS to make changes to boot priority or any changes in general.

If you have your ubuntu live cd, see if it boots to that or does it bypass that and boot to the default system.
When you try booting from the xp cd, do you actually see the screen that says press any key to boot from cd or does it just boot to default os?

If it boots to the live cd but not to the xp cd then your xp cd might have issues, if it doesn't boot to the ubuntu live cd or the xp, then you need to change your boot priority in the BIOS. Give the comp info and the correct key or key combo can be found easy enough.
try *<Esc>, <F1>, <F2>, <del>*...etc

---

### Post by osos on 2008-02-07
if your keyboard has leds for num lock, caps lock and scroll lock you see if it's initialized. never heard of a keyboard that wouldn't be either.

---

### Post by dzza on 2008-02-07
I tried the Ubuntu live cd, and the when the menu came up I was unable to move between the options, select an option, anything with the keyboard.  I basically could just watch the counter tick down til it booted up my system as the default option.  With the windows cd, I am able to see the actual message "press any key" and nothing happens.  During these no response times, toggling num lock does switch on/off the LED.  

As far as pressing the right key to access the bios, believe me i've practically face rolled on my keyboard in frustration, so i've probably hit every key.

I am willing to accept that I can't fix this, and that nobody has an idea what might be wrong.  I just need an alternative way then to boot from my windows cd.  I'm even willing to backup any existing data and restore my computer to the nothingness with which it came if only I had any idea how. 

Heres the comp info from when I purchased it (has had some upgrades like hard drive size, graphics card, but nothing too major):

CPU
: Intel Pentium 4 650 3.4Ghz CPU w/Fan
Motherboard : P23G VIA Chipset, 800FSB, 8X AGP, 3 PCI
Memory : 1GB DDR2 667Mhz Memory
Video Card : 64MB UniChrome Pro 3D Graphics (onboard)
Hard Drive : 160GB 7200RPM Ultra Fast Serial ATA300 Hard Drive
DVDRW/CDRW : 18X Samsung Dual Layer DVD+/-RW Drive w/NERO
Network Card : 10/100 Fast Ethernet Network Adapter
Sound Card : AC97 6-channel Sound Adapter
Case : Black Mid Tower 400watt Power Supply Power Supply
Ports : 6 USB 2.0 Ports, Serial, Parallel
Bundled Software : Nero CD Burning Software, all drivers for video,sound, and lan.

---

### Post by seventhc on 2008-02-07
This is very weird...one thing I would try would be to unplug all devices leaving only the keyboard plugged in. (unplug the mouse too)
You said the num-locks key does turn on the led, I would also try that key as one of the "any keys" but press a bunch including combos.
But first I would unplug all  hardware other than what you need, that being the keyboard. 
If it does get past the initial screen and starts to install xp then you can plug the other stuff back in so it gets detected during the install.

edit: also if you have a different slot to plug the keyboard in (if it is usb) then I would try it in a different port.

---

### Post by dzza on 2008-02-08
I've tried unplugging everything but the keyboard, and it still does not respond just the same.  Also, I made an error in a previous reply- although the LED for numlock is on, I can't toggle it on/off until after passing the partition selection screen (at which point ubuntu begins loading and the keyboard behaves normally).

Any further suggestions for how to fix this, or better yet an alternative way to just completely wipe my comp and begin anew, are greatly appreciated.

---

### Post by The Saint on 2008-02-08
I have 2 possible options to help you.

1 ) If you  want to blank the drives so you can repartition it and start over/ load windows  then try Killdisk ([http://www.killdisk.com](http://www.killdisk.com)). It's free and resets the entire drive to zeroes. So you can start again. 

2) You might also try booting the Ubuntu live CD and starting gparted from the terminal. It will give you a graphical representation of the drives on your  computer and allow you do delete existing partitions and reformat them in a number of different ways, including FAT, FAT32 and NTFS.

Hope this helps. I was in a simillar boat a few days ago.

---

### Post by dzza on 2008-02-10
So I tried something that the above poster suggested with gparted.  I deleted the inactive Suse partition, and left only ubuntu and swap.  Then I loaded up the live disk, and I deleted the current ubuntu partion and swap and made a new primary partition / swap.  I should note here that at first the live disk had some issues:  The menu came up straightaway, but I still could not move up/down on the keyboard to select an option so it loaded the preexisting ubuntu at first.  After a reset, something failed with the preexisting linux so that the live cd was able to boot instead of starting up said linux partition.  

When the cd started, I made the new partitions.  Of course, as always, after the OS was loaded (even on live cd) the keyboard was fully functional and I could install feisty fawn no problem.  

Afterward, I attempted to boot xp from the cd.  Now it autumatically booted from the cd (did not have to worry about pressing any key to do so), but when I got to the very first option of the install, which is to set up the partitioning, I could not select any options with the keyboard nor move among options.  

Then things went awry.  After restarting again to just load/setup this new ubuntu, my computer hanged at the very first load screen, at the point where it says 'checking nvram'.  So, only option was to reset but the same thing happened.  Then, things got hairier when additional resets would result in either 1) the system hanging or 2) no visual output to the monitor at all, screen says the same thing it would if the computer were off, but it's audibly chugging away the same way it normally would. 

After many, many more attempts, the system finally passed the nvram check, and loaded 1) the xp cd, when it was in, which would now freeze before even getting to the options at which the keyboard wouldnt work, 2) the feisty fawn live cd, when it was in, which hung after the 30 second selection option (which couldnt be cycled through because of keyboard) countdown, 3) booted up the now new ubuntu install, but would often freeze trying to get there, or start up with issues like mouse lag.  

Now that I'm in option 3 with a seemingly steady grip on things, I'm at a loss of what to do and I'm scared to turn my computer off because it might take another hour to get it up to this point again.

Any help is greatly appreciated.  I would love to resolve this issue quickly, so if someone can say 'hey i know what's going on your motherboard is @#$#'d', or anyone has a temporary suggestion for how to deal with any of these issues, then you can be my valentine next week and i'll really appreciate it.  Thanks

---

### Post by seventhc on 2008-02-10
Have you made any changes to the BIOS?..ever??

---

### Post by dzza on 2008-02-10
Not that I can think of.  Like i've mentioned, i'm very lacking with computer knowledge, so I don't think I'd even know how to change anything important.  Since this trouble started, I haven't been able to access the BIOS at all because of the keyboard issue.  IIRC, this all began after adding a Suse partition.  I vaguely recall that it would let you choose between the partition bootup options (suse/ubuntu), then it would do so every other time, and then it finally just got to the point where it was stuck on Suse and the keyboard wouldn't respond to anything until an OS booted up.  The only changes I made at that point were 1) increased the boot menu time in hopes that the keyboard just needed a bit longer to initialize, and 2) changed the boot order so that it loaded ubuntu by default. 

Nothing with the BIOS.

I appreciate your interest in this problem,

---

### Post by seventhc on 2008-02-10
It's really difficult to say what exactly is causing this, I know you have tried different keyboards, so it isn't the keyboard. But I am starting to think that there is some bad hardware somewhere internally. There really is no reason that your keyboard shouldn't be one of the first things initialized. :confused:
I haven't ever come across this particular problem before, so I don't have a previous experience to reference. I am fairly confident that it's an internal hardware issue though. (Unless it's your BIOS) which you can't  access now.
Wait for more feedback, but If it is a tower, the BIOS can be reset by taking out the battery ( It should look like the kind you see in watches)
Once that is out, the BIOS resets to default values, you do however have to leave the battery out for a while so it resets. Some will reset right away, others can take up to an hour, In your case...if you do try this, I would give it the full hour just to be certain.

---

### Post by dzza on 2008-02-11
Mixed results.  I pulled the battery and put it back in an hour later.  I can now access the bios!  Presumably, the keyboard problem is fixed.  However, I can't try it out because now the system hangs so frequently that it doesn't seem likely i'll make it far enough to get to a selection screen  for either windows install or the live cd options.

It took me maybe 8 resets before normal ubuntu started.  I tried an equal number of times to boot from cd after leaving bios (gives me option of where to boot from) and each time it just froze after i selected the option for cd (but finally i could choose among options!).  

This new problem with the system freezing is completely new, and must be a result of something I've done in the last 24 hours trying to straighten up my comp.  When I say it hangs or freezes, there are several things that may actually occur:

I enter the bios when the computer first starts up.  No problems here.  No matter how long I spend in here, all is well until i leave the bios and select a boot option (hd/cd/floppy).  Immediately it freezes when I select one.

Also, it may be that the system froze so I restart, but now nothing happens, I just get a blank screen and the monitor power light dims, signifying that there is no input being read in.  

Finally, and most frequently, the system begins to load up at the initial screen and hangs at 'checking nvram.'   

At this point it looks like the keyboard issue is resolved!  For this you have my greatest appreciation.  Honestly I didn't think I'd get past that issue, and I've been on this forum more than once trying to resolve it.  Thanks very much!

I'm still unable to install xp, or run the ubuntu live cd.  As always, help is very much appreciated.  Thanks

---

### Post by seventhc on 2008-02-11
When in the BIOS, each one is different..example, I had to change boot priority not to long ago. At the menu I had to use the *arrow keys* to navigate then highlight the boot from cd using *-/+*. The* -* moved it down, the + moved it up. My other computer I had to use *page up/page down*.
There should be a menu in the BIOS telling you what keys to use, again this seems strange ,I have never seen a computer freeze in BIOS either. Hopefully when we are finished, everything will be working as it should be. :D

---

### Post by dzza on 2008-02-11
It doesn't exactly freeze when in the BIOS.  In the BIOS menu, i can use the arrow keys to navigate perfectly.  Let me try to be more specific in what exactly is going on now.

Let's first say the computer is powered down.  If I start it up, it will likely load the fresh install of ubuntu just fine.  If, however, I need to restart, or if i restart for any reason, on the subsequent load the system will freeze when it gets to the point 'checking nvram' at the very first load screen (the screen where it displays the slave/masters and at which point you may press a key to enter the bios). 

One solution is to power down the computer totally, and start it up like that (doesn't seem to like resets much).  Alternatively, I can enter the BIOS before it gets to that point in the load screen.  If I wait til it hangs on 'checking nvram' I can't do anything, system is frozen I must restart.  If I entered the BIOS and I then exit, there is a chance that it will start up the system that way. 

To try to clarify this:  the system will probably hang at the load screen, entering the BIOS and exiting it gives the choices of which device to boot from and there is a chance that it will then load up normally or just freeze at the point when I make the boot device selection.  

If I choose to boot from the XP cd, it will start the install process.  The general scheme of things with the install process is that it loads up a windows blue screen with the windows name in the left corner and an emptry grey toolbar will span the bottom of the screen and display what's going on.  IE it'll first say press F6 to install 3rd party RAID drivers.  Then it'll say Press F2 to start windows auto-recovery.  Next, if no option is pressed, it should automatically begin to load up windows/install.  If I make it to this point, and I let the process go by unperturbed.  It will get to the 'press F2' part, then it'll hang after this option is gone but before any other status is shown.  It's frozen at this point, as I tried leaving it for more than enough time to see if it was just taking a while to load. 

The weird thing is if I select, say F2, to start up the recovery, and then I cancel this option, it will start to load windows pretty much at the point where it would freeze if unperturbed.  However, after it is finished loading all the devices and is ready to start the installer, it freezes again and I'm stuck again. 

This problem with frequently freezing at random points has never been an issue.  I could reset my computer all day long if I wanted to prior to deleting my partitions and starting a fresh install and nothing would come of it, no freezing at all.  This also occurred before the BIOS was reset, and now after, so it seems to be unrelated to whatever was keeping the keyboard from functioning. 

Any thoughts/ideas on this?

---

### Post by seventhc on 2008-02-11
I am starting to think that there must be bad hardware somewhere.
Have you replaced anything lately?? Maybe it isn't compatible??

If it isn't hardware, it is very difficult to say whats causing all of this confusion.
If it were me, I would probably wipe the entire hard drive(gparted), starting fresh.
I would create a partition for windows, then try installing it. If it installs successfully I would then try installing Ubuntu choosing  "*Use the Largest continuous free space*" during install.
Sadly though I am really not sure what else to try, I'll be trying to think of something. ;)
It's also possible someone else might have a better idea/solution
but at this point, if it were me, I would wipe the drive completely.
Start from scratch.

---

### Post by dzza on 2008-02-11
Thank you for the reply.  The initial keyboard issue led to someone suggesting the use of gparted or kill disk, at which point I did indeed wipe the drives.  Then these new issues arose.  I suppose I'll try making a new post that addresses specifically these new concerns.  Thanks a bunch for your help through this whole mess.  At least the keyboard now works.  It probably is a hardware problem somewhere, but it's very weird that it didn't start happening until after i wiped the drives and put up a fresh ubuntu install.  Oh well.

Thanks again you've been a great deal of help!

---

### Post by seventhc on 2008-02-11
OK, I wasn't to sure if you had wiped the entire drive, or just deleted some partitions.
Well, I do hope everything works out for you and if I come up with any ideas, I'll be sure to let you know.
Good Luck:)

---

### Post by dzza on 2008-02-11
I believe I fully wiped them.  When I had Ubuntu/Suse originally, I deleted the suse partition using gparted while on ubuntu.  Then using the live cd I deleted all currently used/partitioned space and set up a new partition on which the new ubuntu install was to be placed.  I'm a newbie, so maybe something in those steps didn't amount to wiping the whole drive.  If there's a better way to do it let me know and I'll give that a shot.

---

### Post by seventhc on 2008-02-11
That sounds like you wiped it if you had to install Ubuntu.
If it is wiped completely, then there is no operating system or data on the hard drive, but I think that is what you did.

---

