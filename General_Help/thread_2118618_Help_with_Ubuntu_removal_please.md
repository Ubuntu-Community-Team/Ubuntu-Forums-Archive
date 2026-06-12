---
title: "Help with Ubuntu removal please"
date: 2013-02-21
forum: General Help
---

### Post by Calv1n on 2013-02-21
I've been trying to do this all morning and I'm stuck. I'm beyond stuck and I'm frustrated so I'm really hoping someone can walk me through this.
 
First off all how I got into this mess.
 
I bought a used but new Panasonic Tough book CF-S9 from the daughter of the previous owner today after he passed away a few weeks ago. He had Ubuntu on the unit but his daugther removed all files from it before selling it to me. I have his user password which will get me into the ubuntu software but I do not nor can I get the password that will allow me into the BIOS of the Tough book (which is an issue I'll get to)
 
I have a brand new Windows 7 disk that I bought a few hours ago thinking I would just pop it in and install windows then move everything over from the laptop to the new toughbook. However that doesn't work. If I have the windows install disk in and boot up it doesn't see it as the BIOS is boot from the HD first where it finds Ubuntu and proceeds to boot it. As I can't get into the BIOS to change the boot order how on earth can I get windows installed?
 
Thanks for any help in advance I've tried going through the forums and I can't find anything like this situation. I've read online that I can as a last resort take out the HD and remove the power supply etc from the tough book which is supposed to reset the BIOS password but I'm loathe to take about a 2k + laptop I just bought as that is not my strong suit and I'm just as lost taking apart and putting back together a toughbook as I am with getting Ubuntu removed and windows installed!
 
Cheers
Calvin

---

### Post by JiuJitsu500 on 2013-02-21
For one thing, there is no such thing as a BIOS or UEFI that own't boot from CD, and all modern boot from USB as well, so something has to be disabled (which does not happen by default either).

So, regardless of this, you can boot from a live USB or CD by hitting f12 or whatever it is for your laptop to choose boot media (all modern laptops can do this), and then choose the dvd drive, usb, whatever.

default is normally the HDD, but you can select other media - CD will always be available. Check BBS priorities or other advanced boot options in the BIOS - there is NO WAY your laptop will only boot from the HDD (you may have to manually move the HDD below the other options however).

Check again please, and post back results. It's impossible for you to not be able to do it.

*EDIT - BIOS passwords are very difficult to crack though, you have to get this from the seller, period. You can force flash a new BIOS, but that's kind of risky and for another forum, but we'd help you through it. Ubuntu is not hard to uninstall - but without the BIOS password this may be a little hard.

---

### Post by Calv1n on 2013-02-21
JiuJitsu,
 
I don't want to argue with you and appreciate your help but there is a way trust me I'm looking at it. I've tried everything on the net and there is no way to get into selecting a boot device with out getting past the BIOS password which I've been informed by Panasonic Canada doesn't have a default and can't be reset. They told me I would have to send it in and pay 250 for a new HD as that is the only fix they can advise me of. These are designed as "military grade and have uber security" they've told me so that is why the traditional methods are dead ends :(
 
However I have removed the HD manually to see if it will boot from the DVD and it will but of course then I have no HD to install the Windows OS on so that doesn't really help me. Unless if this works that is

Could I, completely remove Unbuntu from the HD so when the laptop resets it finds no OS on the HD and then moves to the DVD for the windows install.
 
I can certainly show you screen shots if you'd like of the laptop on it's various screens but if you use F2 as the Panasonic manual states you get to the BIOS password which I don't know and can't reset and thus can't select the DVD drive or USB as priority. If I try the default F12 which works for many PC's as well I get a black screen that states
 
"Error:  No Desired Boot Device is available. Please turn off the system"
 
If you or anyone knows of anyway past this please let me know!
 
Thanks again
Calvin

---

### Post by JiuJitsu500 on 2013-02-21
ToughBooks are just ruggedized PC's, I'm in the US Army and we deal with them all the time, I've never had a problem :)

But, BIOS passwords do kind of screw things up. You can plug the HDD into an adapter in another computer, re-format it (or just empty all the space) from a live environment, then plug it back into the toughbook.

From there, the BIOS won't really matter - it'll see the HDD is empty, then boot from DVD.

This also means if you made a live DVD of ubuntu (I would do this), took the HDD out, booted from the live dvd or usb, then plugged the hdd back in when you get to a usable desktop - THEN reformat with gparted to all unallocated space....

Then shut down, and put your windows dvd in, and install from there. That pretty much all bypasses the BIOS password issue.

---

### Post by Mark Phelps on 2013-02-21
If it were me, I would pull the HDD, insert the installation DVD, reboot -- and see what happens.

It if works, you saved $250.

Normally, you can also remove the BIOS battery from the motherboard, short the BIOS pins (to reset the BIOS), reinsert the batter, reboot -- and all is OK.  But, given this is a ToughBook, that is likely to not work as well.

They don't call these "tough" for nothing, I guess.

---

### Post by JiuJitsu500 on 2013-02-21
Oh, when you do get windows installed though, I'd highly recommend re-flashing the BIOS.

If something goes very wrong ever, the only thing you ever want to work 100% of the time is the BIOS so you can get to a correcting environment, like a live linux usb or windows install dvd.

There are lots of tools out there for this, but for now, I'd use a linux USB to re-format that beast so you can install your Windows. That's kind of phase 1 lol.

*EDIT - To phelps... yup, the BIOS uses a tiny flash memory thing to store it's settings in that very event. The battery is designed to last longer than the motherboard, but removing the baattery or any other CMOS reset method is essentially not even possible because of this - it's meant to handle shock and all that lol, and why they generally come with VERY expensive 10,000rpm HDD's with uber-mega caching to prevent data loss in case of shoce, fire, or time travel or getting stomped on by dinosaurs. We use them on the road and in tanks. They are tough as hell, but not impenetrable.

*EDIT 2 --- Oops... windows does have it's own partitioning tool too, but theres a pretty big difference in the way windows and linux make a partition table. If you're afraid or hate linux, windows tools wwork too, just not as good :)

---

### Post by Calv1n on 2013-02-21
Mark,
 
 Thanks for the post but I did that and of course I'm ok with the fresh install of windows until the step of pick the HD you want the OS on then I'm dead in the water as the laptop only has a single 320 HD.
 
JiuJitsu500,

Thanks again for your post I really do appreciate the help. I do have some issues of course and those are my own ignorance when it comes to Ubuntu. I've never used it before today and coming from 20+ years of windows I feel like I've landed on another planet using alien technology.  
 
I tried downloading the Ubuntu OS - uninstaller I found on-line but I can't figure out how to get it to work from a USB drive or the DVD which I'm not sure if it can work anyways once Ubuntu has loaded or if I have to run it before the OS start up (in which case it won't work anyways as I won't be able to select either same as the windows problem)
 
I would be comfortable flashing the BIOS but I don't think I have any files to do so and their is no updated BIOS available for this model on their website...I'll certainly keep an eye open for such and update and do it as soon as it is possible but even then I have a sneaking suspicion that they would want the BIOS master password which I don't know to allow the update :(
 
I also don't have another laptop that I could format this drive from it appears that Panasonic has a unique cable for the also very unique looking HD's they have in this machine (I'm sure part of their we take your security very seriously don't worry about your data it's safe, no one but you will ever see it and thanks for the many thousands of dollars)
 
>  
This also means if you made a live DVD of ubuntu (I would do this), took the HDD out, booted from the live dvd or usb, then plugged the hdd back in when you get to a usable desktop - THEN reformat with gparted to all unallocated space....

Then shut down, and put your windows dvd in, and install from there. That pretty much all bypasses the BIOS password issue. 

 
This sounds like it may work but how would I do this exactly? Again I'm sorry I'm so new but I'm really have a hard time with this OS it's not at all like MS which is all I know and I've had zero luck so far with un-installing it or getting anything to run from the DVD or USB drives. They are appearing as ISO' files and I can't seem to get them to finish installation or extract. If I try to extract the Ubuntu 12.10 desktop file that is supposed to have the un-install built in I get this errror;
 
Error creating directory: Permission denied
 
I'm logged in as the only profile which is the administrator so i don't know how I'm supposed to install anything if I don't permissions at this level? 
 
Thanks again
Calvin

---

### Post by Cheesemill on 2013-02-21
If you have another machine you can connect the Toughbooks hard drive to then there is a solution, you can create a partition on the drive that will boot the installation files.

As I don't know if this other machine is a Windows box or a Linux box then I can't give exact instructions but the gist of it is this...


[LIST]
[*]First delete all of the existing partitions on the drive.
[*]Create a partition of around 8GB at the start of the drive and format it as NTFS (I can't recall exactly how big it needs to be, it just has to be large enough to hold all of the files from the Windows installation DVD).
[*]Set the boot flag on this partition, you can do this using gparted from Ubuntu or with the bootsect windows program (which can be found on the DVD).
[*]Copy the contents of the Windows installation DVD to this partition.
[/LIST]
When you plug the drive back into the toughbook and boot up, it will boot directly into the Windows installer you have just created on the hard drive, by using this method you don't ever have to force the Toughbook to boot from the DVD drive at all.

If you want to try this and need more help, just post back with any questions and tell us what OS you will be using to prepare the hard drive.

---

### Post by JiuJitsu500 on 2013-02-21
Hmmm...

Okay, from square one then :) Don't apologize so much either, linux distro's are all very different from Windows or Mac, I get it :)

From Ubuntu you can fairly easily make a bootable DVD. Once you download the .iso and have a blank dvd, find an app called "brasero" and open it. One of the options is to burn an image, which is what you need.

Once you choose that, then choose the image and put the blank dvd in. It'll burn it (assuming it's a dvd-r/w drive) and you'll be all set for part two.

Let's get the set up though - one blank DVD, make sure your drive is dvd-rw capable, and the .iso from ubuntu's website.

(EDIT - If you don't have a blank DVD, or the drive isn't DVD writable, then you have to use USB and pray to god the BIOS is set to use that as a boot device) - worse case you'll need another computer to burn the DVD if you can't on the toughbook, and USB doesn't boot... both of those options suck, but I promise you, we'll get this.

---

### Post by Calv1n on 2013-02-21
Cheesemill,
 
Thank you for the post. I do have a desk top close by that I'm using to post on these forums and search for answers that is a windows 7 64 bit system.
 
I have installed the OS uninstaller found here 
 
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)
 
this looks like it could work as well if I could just get a little direction perhaps...
 
I followed these instructions on the uninstaller to get it onto the machine
 
**>  **
[B]Download/Install OS-Uninstaller in Ubuntu :
either add ‘ppa:yannubuntu/os-uninstaller’ to your Software Sources via using a new Terminal session:

* sudo add-apt-repository ppa:yannubuntu/os-uninstaller
* sudo apt-get update && sudo apt-get install -y os-uninstaller [/B]
 
However when I run the program from the HD I get the error message "Please use this software in a live session (live-CD or live-USB) 
 
How do I move the program onto the USB and run it as a live session? (is there a way I can just alter the command prompts above to have the OS-installer moved to the USB and how do I even find out what "Letter the USB has been assigned" or does it even matter in Ubuntu? There is no "my computer" area that lists everything that I can find like I would have in a MS OS...
 
Thanks again for the help

Cheers
Calvin

---

### Post by JiuJitsu500 on 2013-02-21
Oh, new edit real quick... "permission denied" is because though you are the 'administrator' of sorts, you are not the superuser.

sudo, su, gksu, or other commands like these invoke the "superuser" that can do anything to the computer. *nix system have this to stop unwanted users or viruses, etc from doing any damage at all. ONLY the su can change core files linux knows it needs (or any unix that doesn't automatically grant you this power).

More often than not, you'll get to a "root" shell by typing "su" as a command, or using sudo before most commands - gksu is often used for GUI apps, though isn't really as necessary as it used to be but still reccomended for things like file management and such.

---

### Post by Calv1n on 2013-02-21
> **JiuJitsu500 said:**
> 
 
From Ubuntu you can fairly easily make a bootable DVD. Once you download the .iso and have a blank dvd, find an app called "brasero" and open it. One of the options is to burn an image, which is what you need.
 
Once you choose that, then choose the image and put the blank dvd in. It'll burn it (assuming it's a dvd-r/w drive) and you'll be all set for part two.
 
Let's get the set up though - one blank DVD, make sure your drive is dvd-rw capable, and the .iso from ubuntu's website.
 
 
 
Great thanks again! You are a life saver their should be a way to send drinks through the internet! Ok I have a DVD that I burned the file called > Ubuntu 12.10- Desktop AMD 64.iso On. Is this the correct file or should have installed something else? Also not sure if it matter but under the properties of my system it says the current installed Ubuntu is only 32 bit?
 
Cheers
Calvin

---

### Post by Calv1n on 2013-02-21
Once I put in that disk it gives me this prompt:
 
Software package volume detected.
 
Would you like to open it with the package manager? (cancel or start pkg manager below two options available).

I assume I'm to start the pkg manager?
 
Cheers

---

### Post by JiuJitsu500 on 2013-02-21
Crap, hopefully you have a 64-bit processor, I forgot.

you should be okay though. Put the DVD in, take the HDD out, and reboot the computer. If things don't boot, it's because you have a 32-bit CPU and need the 32-bit .iso.

Sorry man, I kinda forgot to mention that. If it boots from the 64 bit one, we're well on the way :)

---

### Post by Calv1n on 2013-02-21
J,

I'm adding a second disk that is 32 bit just incase. I'm fairly sure it's a 64 bit system it is a fairly new laptop it's a Windows 7, intel i5 etc... but I'll have both ready just in case.
 
Once I pull out the hard drive and then restart I just follow the prompts on screen if I see them I assume?
 
Cheers
Calvin

---

### Post by Calv1n on 2013-02-21
Sorry probably a silly question but in Brasero it's asking me if I want to burn the Ubuntu ISO as Data or as image? I'm assuming Data?

Edit, NVM I found it online its supposed to be an Image. good thing I checked
 
Cheers

---

### Post by JiuJitsu500 on 2013-02-21
If it's an i5 then I guarantee it's 64 bit, that's actually awesome.

Once the dvd boots, you'll get to a screen that says "try ubuntu" and "install ubuntu"

Of course, pick "try" and let the desktop boot. Should look the same as yours with very little difference.

Now, plug the hdd back in and close any windows that come up if it opens. Then, find an app called "gparted" and open it. It will scan all of the drives and come up with a lot of cool jazz.

On the right will be a box that says /dev/sda or /dev/sdb or similar. Find the HDD in there (since it's the only drive, it should be /dev/sda and the only option).

Right click on the box in the middle showing the space used in the drive graphically, and click "unmount"

Once there, go to the top and click "device" and "new partition table" I believe. It'll warn you that it's going to rape and burn and pillage and kill the HDD, which is fine and what you want.

The box will then turn grey and say "unallocated."

Once that's it, you can now re-boot with the Windows dvd in the computer and install to the HDD :)

---

### Post by Calv1n on 2013-02-21
Thanks J I'll let you know how I make out in a few minutes after I catch up to you!

Cheers
Calvin

---

### Post by JiuJitsu500 on 2013-02-21
Oh, I told you the GUI way too, seemed easier and less prone to mistakes :)

The command for doing the same thing (if you know the drive's address) is:

dd if=/dev/zero of=/dev/sda

Making sure the "sda" is where the computer put it. Regardless, it kind of has to be, seeing as there is no other media in the laptop... but I guess it might mount at /sdb, but I can't see any reason it should.

Command is a lot easier :) It won't give you any progress though, just a blinking cursor until it's done, but it is the same result :guitar:

---

### Post by Calv1n on 2013-02-21
Ok I'm sad again. Just when I thought we had it. Your directions worked fine until I got to "plug the HD back in" as soon I did that the laptop dies instantly and when I restart it it's back to the OS on the HD :(

---

### Post by JiuJitsu500 on 2013-02-21
Dizzam.

There has got to be something off here! Try plugging it in then as soon as you see the ubuntu logo start to boot.

Maybe when the GUI is all loaded it's supposed to shut off if something is protecting the drive. This thing must be destroyed!

Don't mean to insult at all, but it IS plugged in, right? :)

---

### Post by Calv1n on 2013-02-21
I've installed the Gparted onto the HD is the way I can somehow work with this sofware to get ubuntu off?
 
This is what it's showing me 
 
[[IMG]http://i76.photobucket.com/albums/j14/Calv1n1/th_ubuntu.jpg[/IMG]]("http://s76.beta.photobucket.com/user/Calv1n1/media/ubuntu.jpg.html")
 
If I were to "unmount" the boot drive as you suggested in the previous post (if it'll let me that is) would that work or would I be in even worse shape?
 
Cheers

---

### Post by Calv1n on 2013-02-21
> **JiuJitsu500 said:**
> Dizzam.
 
There has got to be something off here! Try plugging it in then as soon as you see the ubuntu logo start to boot.
 
Maybe when the GUI is all loaded it's supposed to shut off if something is protecting the drive. This thing must be destroyed!
 
Don't mean to insult at all, but it IS plugged in, right? :)
 

Yep it's plugged in from what I can gather Panasonic has built this "Safety / security" feature into their new toughbooks to stop more or less what we are trying to do. Some clever folks at Panasonic. You have to remove the battery to get to the HD as well so you have no choice but to have the power cord plugged in with this model!

Cheers

---

### Post by JiuJitsu500 on 2013-02-21
In order to modify a drive's partitions or partiotn tables, formatting, etc you can't be on the drive you're booted from.

To answer you, no, you can't... you don't happen to have a seagate external drive do you? they have sata adapter that comes with them...

I would unplug the drive again, reboot with the DVD in there, and plug the drive back in as soon as you see it start to boot from the dvd. If it shuts off again then something is preventing you for real from getting into that drive.

I'm not sure of any way to reset the BIOS or a CMOS reset either on those... nor do I know if you can effectively flash the BIOS from ubuntu. Damn it man, if you can't get that thing hooked up like an external drive (separate from what you're booting)... then you might be in need of someone beyond me :(

If it fails again though, try booting from the Windows DVD and pluggin in the HDD while it's booted. Maybe that'll work?

---

### Post by Cheesemill on 2013-02-21
@JiuJitsu500

I don't think your technique is going to work.

To be able to hot-swap a hard drive (plug it in while the machine is powered up) successfully, you need a motherboard that supports hot-swapping. I have never seen this feature available on a laptop, only on high-end server hardware. This is probably because the added cost to the drive controller isn't worth it in a situation where it will never be needed (except in this particular niche case).

I think the only method available is if the OP can somehow get the hard drive plugged into a different machine.

---

### Post by Calv1n on 2013-02-21
What kind of Seagate external drive? I have a london drugs 5 minutes from my house I'll go pick one up? 
 
There is no way to reset the BIOS or CMOS is what Panasonic support has told me they stated point blank can't be done with the new tough books even they just throw out the old HD and put a new one in for $250 when I send it into them for "support" for this issue. 
 
I did try the booting from Windows and then plugging in the HD already but just as with the ubuntu CD it blacks out the second the drive connects and when I restart it loads from the HD... gah I'm in a love hate relationship with this thing. It's awesome in some ways but in others it's a disaster. This is a system you don't have to worry about having your data stolen on that is for sure (no password equals - nothing!)

cheers

---

### Post by JiuJitsu500 on 2013-02-21
Figures. Well crap.

I have a 1.5TB external Seagate (don't know the exact model) but you can probably get a SATA to USB adapter for cheaper. Make sure it's SATA (it really should be, anything with an i5 is likely not IDE or anything else like eSATA)...

$250 for "support"????? You can get a 750GB Hybrid Srive 7200rpm w/32GB SSD for less than $100!!!! Stupid as hell.

As for the hot-swapping thing, I know it was a long shot, but I have managed that in my laptop twice through a direct SATA plug-in while booted from a live USB (thanks to something in my BIOS temporarily not recognizing any drive) so I figure maybe it could work... Trying to save the man some dough!

Make sure the interface is SATA, or take the drive to the store and get a XXX-to-USB adapter. They are not expensive. This will I guess be the only guarantee to fix it besides buying a new HDD (and not from the company... but $250 isn't actually bad for a ruggedized, likely 10,000rpm HDD). You can't get to another pc at all you can plug it in to? This can re-format it easily from any OS as well...

---

### Post by Calv1n on 2013-02-21
I think I may have something. I grabbed my old sony laptop out of storage (well its only 2-3 years old) and swapped in the panasonic HD. I started it up and it said no OS detected. Put in the windows disk and now it appears to be loading!! Fingers crossed I'll let you know as soon as I confirm it's working back in the panasonic tough book!

cheers

---

### Post by JiuJitsu500 on 2013-02-21
Woah!

DON'T install windows from that!

If it's in any IDE mode or not ACHI like the toughtbook likely is, it'll configure wrong and be broken anyway. OR, it'll install and configure to that laptop.

Try pluggin it in to that laptop, and boot from the live DVD you made already (32 Bit), then format it like I told you through gparted.

Then, do the install on your toughbook :)

You may get lucky though... I'd re-format using that laptop, then once it's all unallocated space, plug it into the toughbook and install windows using that.

The system will install fine, but the congs can get screwed up if the SATA ports are configures for IDE mode, and the toughbooks are for ACHI - among other things windows congures itself. It can work like that, but it's ALWAYS better to install on the box you plan to use the drive in.

---

### Post by JiuJitsu500 on 2013-02-21
Oh, yeah... computers can be a pain :)

I recommend rum, or applecorn.

---

### Post by Calv1n on 2013-02-21
> **JiuJitsu500 said:**
> Woah!
 
DON'T install windows from that!
 
If it's in any IDE mode or not ACHI like the toughtbook likely is, it'll configure wrong and be broken anyway. OR, it'll install and configure to that laptop.
 
Try pluggin it in to that laptop, and boot from the live DVD you made already (32 Bit), then format it like I told you through gparted.
 
Then, do the install on your toughbook :)
 
You may get lucky though... I'd re-format using that laptop, then once it's all unallocated space, plug it into the toughbook and install windows using that.
 
The system will install fine, but the congs can get screwed up if the SATA ports are configures for IDE mode, and the toughbooks are for ACHI - among other things windows congures itself. It can work like that, but it's ALWAYS better to install on the box you plan to use the drive in.
 
It's not letting me install / or reformat sadly. 
 
This is the message...
 
[[IMG]http://i76.photobucket.com/albums/j14/Calv1n1/th_win7.jpg[/IMG]]("http://s76.beta.photobucket.com/user/Calv1n1/media/win7.jpg.html")
 
Is there another work around?
 
Cheers
Calvin
 
edit: Oh and both laptops are Windows 7 still so even my old one is comparable to the tough book (actually the old sony is far more powerful but it won't work for long in the welding shop we need it in thus the tough book). Although I don't know if that matters in regards to your concern about IDE and ACHI?

---

### Post by JiuJitsu500 on 2013-02-21
The driver screen... well we know that windows won't do it then.

Use the live linux media from that laptop to format it. At least from there more things can be done. INstructions are the same in the former post I made about gparted (unless you're comfortable with the command a couple posts after that, either way is fine).

From there, maybe it'll be recognized by windows.

As for a workaround, I've just rebooted a coupe times until it recognized the drive. It might be formatted in GPT and the media you have is booted from non-UEFI mode, which would be crazy and windows is usually okay at that recognition, but maybe not this time (wasn't with mine either).

Still, use linux to re-format. Once done, it should be windows from here on out.

---

### Post by JiuJitsu500 on 2013-02-21
IDE and ACHI mode just means the way windows configures itself based on how the BIOS tells the drive to act. Your issue doesn't reflect that I don't think. Not to mention, after windows installs, it configures (or profiles) itself to that specific hardware. It can run on others, but the configuration is meant for something else. If it's in IDE mode though, and moved to ACHI, it usually gives off insane no-booting crap and acts like a jerk.

You are still though closer to your goal :)

---

### Post by Calv1n on 2013-02-21
Ok I've tried that but again some issues.  Following these directions...
 
> **JiuJitsu500 said:**
> If it's an i5 then I guarantee it's 64 bit, that's actually awesome.
 
Once the dvd boots, you'll get to a screen that says "try ubuntu" and "install ubuntu"
 
Of course, pick "try" and let the desktop boot. Should look the same as yours with very little difference.
 
Now, plug the hdd back in and close any windows that come up if it opens. Then, find an app called "gparted" and open it. It will scan all of the drives and come up with a lot of cool jazz.

I get to here and then while it's scanning the drives it says 
 
 
"Libparted Bug Found!"
 
"Input/Output error during read on /dev/sda"
 
And no matter what I do it won't work from there. It does show the drive in the top right corner as you said and in the main "windows" it shows the drive as unallocated but I can't do anything with it as everything is greyed out but "new and information" for options.
 
>  
On the right will be a box that says /dev/sda or /dev/sdb or similar. Find the HDD in there (since it's the only drive, it should be /dev/sda and the only option).
 
Right click on the box in the middle showing the space used in the drive graphically, and click "unmount"
 
Once there, go to the top and click "device" and "new partition table" I believe. It'll warn you that it's going to rape and burn and pillage and kill the HDD, which is fine and what you want.
 
The box will then turn grey and say "unallocated."
 
Once that's it, you can now re-boot with the Windows dvd in the computer and install to the HDD :)
 

 
Or is it because I already tried to install windows on it that it's showing as unallocated and it is ready for a windows install if I put it back into the tough book?
 
Damn confusing
 
Cheers

---

### Post by Calv1n on 2013-02-21
> **JiuJitsu500 said:**
> 
Use the live linux media from that laptop to format it. At least from there more things can be done. INstructions are the same in the former post I made about gparted (unless you're comfortable with the command a couple posts after that, either way is fine).
 
Still, use linux to re-format. Once done, it should be windows from here on out.
 
Do I do that from the old Sony or put the drive back into Tough book to do so? I'm currently sitting with the tough book HD in the Sony laptop with the Trial Unbuntu running Gparted... rum is sounding mighty fine about now!
 
cheers

---

### Post by Calv1n on 2013-02-21
Ok something else I've just discovered. In Gparted if I go into Device it appears it will allow me to create a partition erasing everything on the entire disk / Dev/SDA. 
 
Do I want to do this and if so do I want to create an MD-DOS partition table or something else?
 
Cheers

---

### Post by JiuJitsu500 on 2013-02-21
If it shows up as unallocated you should be fine then. Go ahead and give windows a go and see what happens!

If you're still in the live dvd though, run:

dd if=/dev/zero of=/dev/sda

just to be sure. I/O errors are Input/Output, which is strange, maybe a security function. If the dd command doesn't work, something may be afoot...

---

### Post by Calv1n on 2013-02-21
silly question but how do I run the command in Ubuntu their is no command bar that I can find?

:/ sorry pretend I'm 4 years old if it helps as that is my knowledge base on Ubuntu ;)
 
Cheers

---

### Post by JiuJitsu500 on 2013-02-21
Oh, lol just look for the terminal app

Or CTRL+ALT+T opens it up :)

---

### Post by Calv1n on 2013-02-21
Ok I went into the command prompt and typed in the text string but it came back with:
 
dd: opening '/dev/sda': Permission denied
 
? Do I have another issue?
 
Cheers

---

### Post by JiuJitsu500 on 2013-02-21
oops, forgot again

sudo dd if=/dev/zero of=/dev/sda

The "sudo" missing is why permissions were denied :)

---

### Post by Calv1n on 2013-02-21
Ok so I think we have an issue after putting in that command it returns
 
dd: writing to '/dev/sda': Input / output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.0165946 s, 0.0 kb/s
 
So that means it did squat right?
 
cheers

---

### Post by JiuJitsu500 on 2013-02-21
Crap. that's exactly what that means.

Maybe this drive is copy-protected like a boss... anyone else have any input on this? dd and gparted are all very basic and can't really get past super-encrypted junk but I've never had a problem reformatting a hdd from a toughbook (though mine were older... maybe that's it).

I wanna know now... maybe something can remove the encryption, write protection, whatever. But seeing as how ubuntu was put on it in the first place, I don't see how that's still all extra tough.

But, seeing as how it was maybe secured or something, give it a whirl in the toughbook with windows 7 - maybe it'll let ou re install since it says it's all unallocated.

In the meantime? Anyone have an idea as to what's going on?

---

### Post by Calv1n on 2013-02-21
Should I still bother grabbing an external drive or do you think it won't matter? I could also check and see if there are any Laptop HD's that I could replace the existing one with maybe? What do you think?
 
Cheers
Calvin

---

### Post by Calv1n on 2013-02-21
Ok I bought another 320 GB HD from london drugs for $90 and it appears to be working. I'm doing the fresh install now. Thanks for the assistance everyone I wish I would have started with HD replacement many hours ago.
 
Anyone looking for a Ubuntu 320 GB HD for a laptop? I have one for cheap!

Cheers
Calvin

---

