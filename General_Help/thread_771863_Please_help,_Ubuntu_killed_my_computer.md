---
title: "Please help, Ubuntu killed my computer"
date: 2008-04-28
forum: General Help
---

### Post by Furbs on 2008-04-28
I have had my computer turned off for the last three days, and have all but given up on it. I would really appreciate any ideas for my problem, since I have many very important files on my PC that are not backed up and I currently have no way to access them. I have plentiful patience, just absolutely no idea what to do!

While trying to download and install a program via apt-get, my computer froze for no reason; frozen mouse, would not respond to any keyboard input (I have since discovered the wonders of alt-sysrq-b, yet even this has mysteriously stopped working by now). Upon reboot the problem kept repeating whenever I tried to access the internet, basically. However it even froze mysteriously when I tried to open the system monitor, of all things.

Eventually, my computer decided it didn't want to boot after restarting. No login screen even, it got as far as the GRUB loader then just blackness. I put in the installation CD and attempted to go into "rescue mode", yet i don't know what to do when it gives me a prompt. After random button-pressing it mentioned something about fschk or something like that, which i ran and it noticed that my file system was all out of whack. 

After fixing that to the best of its abilities I WAS able to boot my computer, yet the problems had not gone away and it kept crashing just like before. I finally got an error message this time though, an "input/output error" from Firefox when it crashed and didn't take the whole system down with it (though the whole system did crash with no programs running, thirty seconds later!)

Sure enough my computer decided it didn't want to boot again. But now when I try to go into rescue mode with the CD, fschk gives me warnings saying that I will severely damage my file system if I run it, so of course I won't do this. I've looked this up daily for the past three days, looking all over these boards, trying every option available on the installation CD with no luck whatsoever. I can give you any info on my computer if you need it, but really I just want my valuable files back! I would greatly prefer to run (a working installation of) Ubuntu on my computer, but if I can get my files and reinstall win XP I'd even settle for that. Thanks so much!

---

### Post by wannadumpwindows on 2008-04-28
First thing I would do is boot a LiveCD and use it to back up all of my files to some sort of external media. A USB thumb drive, or an external hard disk. Even CD's or DVD's will work. Always a good idea to back up anything important. After that, you can work from there, that way, even if you do kill something, you can always reinstall, and you'll still have your data!

---

### Post by quixote on 2008-04-28
(I'm not sure it's entirely fair to say that Ubuntu killed your computer.  That pattern sounds more like a hard disk failing.  :( )

I'd suggest *stop* trying to boot your computer off that disk.  If it is failing, this will only make it fail faster.  Boot from a liveCD.  Try to mount the partition (or drive, whatever word you prefer) that has the files you want, and get them copied to a removable medium.

Then start trying to revive your hard drive again.  How to diagnose the actual problem, I have no idea.  

Suggestions from others?

---

### Post by Furbs on 2008-04-28
Thanks for the LiveCD idea, but what is that exactly? I only had Ubuntu up and running for a week before it died, so I still know very little about Linux. I had to use the installation disc that lets you install without internet connectivity, since I don't have a direct ethernet connection to the internet with this computer (also, the installer cannot recognize my wireless card, which uses the madwifi drivers, so I cannot use any internet-necessary installation disc). Do I already have the live CD? How can I tell what I have? Also I have no idea how to copy files from my hard drive to an external thumb drive (which I have) using the installation disc. I'm pretty sure an option like that wasn't on my installation disc, but not 100% positive. Where would I find it?

Significantly, behavior like this NEVER HAPPENED UNDER WINDOWS.  My computer is only a few years old too, and I'd only had Ubuntu installed for a week before this happened. Which is what leads me to believe this is not a hard disk failure. Also note that 90% of the time my computer crashed it was trying to access the internet (downloading files, plugin-intensive websites etc), and Firefox did give me an "input/output error" once, whatever that means. Thanks for setting me on the right track, now what's next?

---

### Post by mhmjr on 2008-04-28
A live CD would allow you to run Linux from off of the CD itself without need to use your hard drives. Once you have your important data backed up you should then unmount your drive and try running fsck while the drive is unmounted. The warning you mentioned about fsck ruining the filesystem sounds very much like the warning fsck will give you when you attempt to fsck a drive that is mounted.

Knopix is a very popular LiveCD and if I am not mistaken any Ubuntu CD is also a LiveCD that you can use as a LiveCD or to install from. Its been awhile since I have had an Ubuntu cd though so I may be mistaken.

---

### Post by agim on 2008-04-28
First off, I am sure we can get the files off of your computer. A live cd is the cd you booted into rescue mode with. It should boot with a menu of a few options. Boot or intstall, recovery mode, check cd for errors... a few others.

When you see that menu, just press enter at the top one. It will boot you into a live cd. Get that done and we can go from there.

---

### Post by wannadumpwindows on 2008-04-28
My Atheros wireless card uses the madwifi drivers as well, and it worked "out of the box". I'd imagine yours should be the same, unless it's something really new that's unsupported at this time. Using network-manager with a static ip is a different story . . . . .

---

### Post by Bari on 2008-04-28
Run Gparted (Download it and burn to disc) its a live disc so you should be ok there you can select your hard dive and run a check to see if its ok it will tell you if its failing. If I remember right you can right click on the entry for your drive and check properties. Not 100% sure as I haven't had to do it for a while.

---

### Post by quixote on 2008-04-28
Hi Furbs-

As others have said, the "LiveCD" is the term used for that disk you installed from.  When it starts booting, there's the list of choices beginning with "try or install ubuntu."

Select that one.  Once your computer has booted up from the CD, start the file manager (leftmost icon on the menu bar, then "places", then "computer").

That will bring up a list of all drives, including unmounted ones.  Right-click on the one you think might have your data. (Usually size is your only cue because the naming is based on how the machine sees it.) An option toward the bottom says "Mount Volume."  Select that. ("mount" basically means "make available.")

Then look at what's on it. If it doesn't have your files, close that folder, right-click on the drive, and select "Unmount Volume."  Then try the next plausible-looking drive.

Once you've found the drive that has your data, you're ready to copy.  

I don't know what you have available, but let's say it's an 8GB USB thumbdrive.  Stick it in the slot, and it'll show up in the list of available drives as something like "8GB-USB" Usually those are mounted by default.  Check by right-clicking.  If the option at the bottom says "Unmount" that means the drive is currently mounted.  If not, just mount it.

After that, it's just a matter of selecting the files or folders you want from your old drive, and copying them to the removable medium.  You can do that by dragging, but often it's easier to select them, go up to "Edit" then "Copy" on the menu bar of the file manager, switch to the folder where you want it copied to, and select "Edit" then "Paste".

Once you have your data, *then* we can all start worrying about fsck ... :D

---

### Post by Furbs on 2008-04-29
Hi quixote, thanks for the response again. The first option when I boot from the installation CD is "install in text mode", which just brings me to the same installer that I've been running repeatedly and getting stuck with this whole time. Except now, I eventually end up at a partitioner that shows me the partitions on my single hard drive and asks me to resize them, or "write changes to disk and continue". I just wanted to run the LiveCD, not write partitions to my disk. How do I do this? Do I have the wrong CD? It's a Xubuntu 7.10 Gutsy CD, by the way.

---

### Post by Furbs on 2008-04-30
I just ran the Gparted Live CD and I'm doing the MemTest86 right now. It's 5 minutes in and already 45,000+ errors! What does this mean? Any idea what happened/how to fix it?

---

### Post by Nunu on 2008-04-30
> **Furbs said:**
> I just ran the Gparted Live CD and I'm doing the MemTest86 right now. It's 5 minutes in and already 45,000+ errors! What does this mean? Any idea what happened/how to fix it?

I think memtest is only a memory testing app. If your getting that sort of error on memory then i would suspect that the memory module is on its way out.

That might actually be the cause of your problem.

---

### Post by ryanhaigh on 2008-04-30
The means that there are defects in at least on of your memory (RAM) modules, if you know how to you could try removing one at a time and see if the issue is specific to one stick. Ram is cheap to buy but make sure you get the right type (just take the old one in if you don't know) or check the manufacturers website it could be covered by warranty.

---

### Post by Furbs on 2008-04-30
I just bought 512 MB of new RAM a week or two ago, I sure hope it isn't broken already! I'll do what you guys said and take out the old 128 MB stick and attempt to run on the new RAM only. Wish me luck...

---

### Post by Nunu on 2008-04-30
> **Furbs said:**
> I just bought 512 MB of new RAM a week or two ago, I sure hope it isn't broken already! I'll do what you guys said and take out the old 128 MB stick and attempt to run on the new RAM only. Wish me luck...

Good luck 

I know some systems don't really like it when memory banks are mixed and matched. I Had two 1Gig DIMMs in mine from two different vendors and that was enough to make my machine unstable.

---

### Post by quixote on 2008-04-30
Sure sounds like you have a memory problem.  Probably, as the Nunu said, a mismatch.  But possibly that new set of RAM you got has some bad elements and you should get your money back!

Just remember that if it is memory chips, your data is safe even if the problem makes it -- temporarily! -- hard to get at.

Chips tend to fail intermittently and have increasing problems over time until they fail completely.  If you want to try to get your data to removable media, do it sooner rather than later.  Try the process of booting from a LiveCD, and when you're lucky enough to get a "good" boot, get your data before you do anything else.

Is there a reason why you're using Xubuntu?  It's a smaller-footprint version that works on machines with less memory.  It has somewhat fewer ease-of-use features than the usual version because those take more memory.  If you don't actually need it, and if you'd like as simple a user experience as possible, get the plain-vanilla version, i.e. straight "Ubuntu". We're up to 8.04, Hardy Heron now, and you probably want to get that, rather than 7.10, Gutsy Gibbon, because there have been several usability improvements (easier bluetooth, for instance).

---

### Post by vexorian on 2008-04-30
Hi, as a guy who has had memory problems and done (re)installations of software while unaware of it. I must advice you that it is URGENT that you replace the failing memory chip, don't boot the computer, don't backup the files, don't use the hard drive until you fix this. Alternatively (if you are an advanced user) you can remove the hard drive from your computer and install it somewhere else to do the backups (first run some checks for physical integrity since bad RAM is likely to have messed up your hard drive)

After you get a new RAM chip, run memtest again to make sure it is correct, if it is , you might procceed trying to fix your computer.

Just saying that, now that it is confirmed you got a bad RAM chip, you must avoid to use your computer since it will keep breaking more and more until this is fixed.

---

### Post by Furbs on 2008-04-30
Well, time for another update! I tried running my 128MB RAM chip and it got no errors, but it wasn't enough RAM to even run Gparted to fix the file system, let alone backup files. So I tried the (new) 512mb chip by itself and it kept getting errors, but it still worked at least. So I ran Gparted to check for errors in my filesystem, but while checking my filesystem it got stuck. All night! This morning I press the "cancel" button and it warns me that doing so may SEVERELY DAMAGE MY FILESYSTEM. Yay! I have no other choice, so I cancel it and attempt to exit. This does not work, and I get numerous "segmentation faults". This is where I'm at right now.

My computer seems almost unrecoverably broken. I burned a Live CD of plain-vanilla Ubuntu 8.04 LTS (passed md5sum check and everything), yet when I tried to check the CD for errors on my computer it found 1 file was corrupt. This happened with every single copy I burned of the LiveCD, and I burned four copies! I tried to run the disk anyway (with the first option, "try Ubuntu and don't change anything on my computer") and all four disks failed while loading each time.

At this point I am just amazed that my computer could somehow get this broken. I have tried literally dozens of remedies for the past six days and none of them have worked, my valuable files are still inaccessible. It looks like I have lost for good all my most important files from the past four years!

---

### Post by bodinux on 2008-04-30
Hi

Sorry to hear that your bad RAM lead to such a corrupted state. I would definitely do what vexorian advised (i.e. remove the hard drive from your computer and get it backed up on another computer if it is still readable). This is not too technical, if you can't do this alone I am sure you can find someone who will do it for you. As Vexorian wrote : avoid booting on a corrupted system, anything you do may add corruption to your disk.

As for your live cd, I myself have never had this problem. I would advise getting and burning a copy somewhere else.

As for your RAM, there are bad batches of RAM. If one is not good, there are chances that the other ones in the shop are bad also.

As for your data ... save what you can. 


My sister lived a scary story, one day she unplugged her computer because she needed the plug for something else; then she pluged her computer back and there was a shortcut somewhere in the power supply frying EVERYTHING in her computer! She brought her computer to a technician who replaced the power supply, but then the drive was not seen by the bios. He then dismounted the drive and put it in another computer to backup, sadly the drive was dead from the shortcut (all her professional files from the last four years were blown away). The technician gave her another computer. She came home plugged the screen, the keyboard and the mouse. Result : the keyboard and the mouse where shortcuted also !!! real life story!

Just don't boot your computer again before you make a backup of your data and never ever think that your computer is reliable hardware.

---

### Post by Furbs on 2008-04-30
Some great news! Turns out that it WAS bad RAM that killed my filesystem. Thankfully I have my computer up and running and am posting this from a LiveCD of Ubuntu Hardy right now. Also, the Live CD I burned was fine, I guess the bad RAM was making it think there were errors present. I see what vexorian meant, keeping my computer off and waiting till I had new RAM to install was very important. The new DIMM passed memtest86 and I'm trying to backup files now to a USB drive.

I'm just running into a small problem, I don't know how to change permissions! I want to use the GUI on the Hardy LiveCD to drag&drop files to my USB drive (which connects fine), but many of my files are in folders that I currently don't have permissions to view. How do I do this?

After my files are backed up I figure I'll just format & repartition the drive and install Hardy off the Live CD, since it seems to work fine 8)

---

### Post by jimv on 2008-04-30
I hate bad ram.  I bought 2 gigs of ram for this laptop earlier this year, and it would have problems with lockups and compiling code sometimes errored out.  It took me awhile to diagnose, because the problems didn't always happen.  I finally noticed that whenever my memory usage got near a gig, that's when problems started.  So I ran memtest86 and yep, both sticks were bad.

---

### Post by quixote on 2008-05-01
Furbs: re:
> I'm just running into a small problem, I don't know how to change permissions! I want to use the GUI on the Hardy LiveCD to drag&drop files to my USB drive (which connects fine), but many of my files are in folders that I currently don't have permissions to view. How do I do this?
I assume you mean that on the LiveCD you're user "ubuntu", but your files are owned by "furbs" and it won't let "ubuntu" access them?

The problem with becoming root and copying your files that way is that then they will be owned by root.  You'll have to remember to change the ownership back to you later on!

Another problem is that you can do literally anything to your system as root, and if you don't know what you're doing, you can get some very strange effects.  So be super-careful!

In a terminal (under Start -->Accessories -->Terminal), type 
```
$sudo nautilus
```
it'll ask for your password.  Since you're a generic liveCD user there is none and you just hit return.  Then a GUI file manager appears with you as root.

But do be careful!  I'll feel awful if I hear I've aided and abetted a disaster!

---

### Post by quixote on 2008-05-01
And you'll have to become root to change the ownership back to you, since root will own those files.

---

### Post by Marcus Atilius Priscus on 2009-02-10
Bumping this in the spirit of the thread title -- not necessarily the same specific problem.

System information/backstory:
Dell XPS 400 that I found on CL a couple of years ago.  Got it on a steal b/c it had Windows Media Center on it.

Originally had 2 gigs PC-4200 and a 256 ATI Radeon (x600?) in it.  I put a GF 8600GT and expanded to 4 gigs PC-5300 recently -- this was all before installing Ubuntu 8.10.

Also, the boot disk in this rig is a 60 gig.  I've had a 160 gig installed in the other SATA slot since I bought it.  It was in this 160 gig that I partitioned 20 gigs for Ubuntu.

8.10 was my first install and it was only a couple of weeks ago.  I had no major issues besides learning the basic functionality of the terminal.

Here's where it gets interesting...

Over the weekend, I was browsing CHUD.com and queueing up the new Riddick game trailer when the whole thing went to ****.  I turned away from the monitor for about 30 seconds to check on my dog (chewing on the coffee table leg) and, when I turned back, Firefox was minimized.  I cocked an eyebrow and tried to maximize it again -- no luck.  I tried opening another instance of Firefox...it opened minimized.  I was upset since I'd had something like half a dozen tabs open and didn't want to lose my place in a bunch of forums, but I rebooted, anyway.

Ubuntu booted to the sign in screen.  After I put in id and pass, it went blank.  Just that background from the sign in was showing...no UI at all.  The normal sign on music track plays, but it cuts off prematurely.

And that's it.

Nothing else.

Booting Windows resulted in an almost immediate blue screen.

Win Safe Mode refuses to do anything but show a steady black screen.

The 160 gig that contains the Ubuntu partition also has most of everything I care about on it...so if I need to just relocate that to another rig and recover those files, that's not a big deal.  The 60 gig is mostly Windows-boot-related, although it does have the full Office 03 on it and some productivity files I would prefer not to have to say goodbye to...

I still have all of the original RAM sticks that came with this rig and I will, upon returning home later, immediately pull out the new RAM and see if that's the issue.

If not...where does that leave me?

---

### Post by stalkingwolf on 2009-02-10
here are a couple things I have learned about RAM.  When upgrading RAM
there are several pieces of information that are crucial. the normal
stuff like type and speed , DDR, DDR2 etc, pc2700, 5300 etc..  The most
crucial element I have found is density.  You have high density and Low density.  Some boards will not accept high density ram.  other things
to watch for are ECC or non-ECC and if it is buffered or unbuffered.

I use crucial.com to check my Ram before buying.  A note however , their 
"scan my system" only works with IE or at least the last time I tried it.
If you have any doubts about if RAM will work buy LOW DENSITY . IT is almost
100% compatible with everything.

For OP,  before you reinstall try this,
when Grub first starts hit ESC, this should bring up the menu.  Select
recovery mode.  after it runs a window will open, Select fix broken packages
when that finishes select reboot normally.

Hope that helps.

---

