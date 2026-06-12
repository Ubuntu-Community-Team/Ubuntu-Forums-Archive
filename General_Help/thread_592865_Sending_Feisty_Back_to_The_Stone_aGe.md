---
title: "Sending Feisty Back to The Stone aGe"
date: 2007-10-26
forum: General Help
---

### Post by mike_302 on 2007-10-26
OK, I've had ENOUGH of Feisty doing waht it has been. I'm pretty sure most of the problems I'm having are because I got a little carried away once in uninstalling stuff from the synptic manager and ... MAYBE one of those were importnat files or something... And I edited parts of the system as well. What I want to do is find out how to reset all the files, settings, installed stuff, back to the original state (preferablly keeping the stuff I DID install).. Basically al I want to do is reenable everything that was enabled when it was installed.

IF that Isn't possible, then I guess what I'm looking for is how to wipe the feisty partition and re install it... The only reason I'd prefer my first method is that its a laptop and theres parts id prefer not to lose as they'd take a bit to get working again.

The problems are insanely stupid and include the following:
-Cannot get compiz-fusion working (which is when I started uninstalling things from synaptic manager by my on free will)
-Wireless randomly stop working and when using Wireless manager, I click on my connection/network and it INSTANTLY just says connection failed
-Cannot get simple movies to play properly, such as HD movie trailers from the Mac site... They are very standard web pages setup for people that just want to see a movie trailer so, why isn't it as easy for ME to watch them???

Anyways, i want to get my ubuntu feisty 64 back to its original state. Thanks in advance

---

### Post by zorkerz on 2007-10-26
Im with you that this is a feature that would be pretty handy but i think the logistics of how it would work get tricky. What do you keep and what do you revert. If you revert everything back to default and just keep a users home directory that is the same as reinstalling (at least installs can be done this way). 
I don't even know where to begin after that.

As for your specifics. First i don't know if you know but gutsy has recently come out it might be worth downloading a cd of it and trying the live cd to see if it works better than feisty did. compiz is enabled by default for most hardware.

by wireless manager I assume you mean network manager?
It works sometimes but not all the time? 
I have problems with networkmanager (i have in gutsy 0.9.5 yours should be 0.9.4) and I restart my computer because I don't know any other way to get it to restart.

for your movies you should try and find out what formate they are. If its just flash embedded in a web page you can download the appropriate codecs for that again

hope something here helped

---

### Post by mike_302 on 2007-10-26
If I download and make a lived cd of gutsy
will it reinstall over this feisty, and bring it back to life again.. by that i mean revert back to the ORIGINAL, default settings. When i really get to thinking about it, there wsnt much i installed that cnat be installed again easily. 
About the movies on the websites, theyre just MOV 's ! go to any apple webpage for amovie, choose the resolution u want to use, adn on a Windows, Quicktime pops up and plays it... I understnad it wont be as compatible with Linux but... I'm sure theres a way to get it this fast...

anyways, most importnat question is the original one.

---

### Post by Perpetual on 2007-10-26
I personally would not suggest doing an upgrade to Gutsy.  If your system is messy, you will just end up with a messy Gutsy.  Much better to download the Live cd and do a clean installation.

---

### Post by mike_302 on 2007-10-27
allrighty then. Guess thats my only option. 
when i get it setup, ill be installing the following (this is as a grocery list to myself, and... i guess, if there's any conflict someone can point out, that would be great):

-wireless manager (to see the wireless networks
-uninstal totem, replace with VLC
-get compiz fusion working
-install audacity
-

Anyone see how any of this may start to mess things up?

---

### Post by zorkerz on 2007-10-27
compiz is enabled by default in gutsy and can be found under the visual effects tab in system->preferences->appearance for extra effects you should get this package compizconfig-settings-manager
```
sudo apt-get install compizconfig-settings-manager
```

Network Manager is installed by default its likely your best bet. What wireless card do you have?

I would recommend leaving totem installed. Install vlc if you want i agree its good but with the right codecs you can play everything with totem also. ubuntu-restriced-extras in the add/remove menu used to have most things covered.

Is audacity KDE based? I have heard many good things but have not actually used it myself. If it is based on kde and you install gnome then keep in mind you will have to install many libraries for that single applicatio

Make sure to back up you data if you really get into it I recommend making a separate partition for your home directory so that you ca install and never have to loose any of your home data.

---

### Post by mike_302 on 2007-10-27
I DO have a seperate partition that I made FAT32 for switching between windows and ubuntu... I don't think I was smart enough to make the other one for home... Don't think I knew how to sepearte that home directory when I made it.

I'll definatly be doing this all when I get the chance (probably NEXT weekend). 

My network card is a Belkin .. Can't remember the exact model but I believe its a common one. The model of the laptop is Gateway MX6425. The problem with network manager is that, at least with Feisty, you cant "scan" for the wireless networks and choose which one to connect to... At least not in mine because it just plain wouldn't connect to the net when I only had network manager, so I went to add/remove and searched Wireless Manager and I've been using that, but even that is being annoying because sometimes it just plain refuses to connect or to even try to connect even though it see the network.

---

### Post by adamorjames on 2007-10-27
If you don't have home as a separate partition there is a way to make it separate without reinstalling or anything like that.

---

### Post by mike_302 on 2007-10-27
the thing is, I'm going to reinstall anyways because of all the crap im being forced to put up with since i played around with too many things that I shouldn't have.  So, without repartitioning everything, how do I make a seperate home partition? what are reasonable sizes for the partitons? The following is what I personally figure but correct me if I need more:

Swap (1gb)
Home (my personal files? correct? 12 GB)
Ubuntu install files (where all the programs get installed to, including future onesthat I add) 8GB
FAT32 (switch between linux and microsoft) 5 GB

(is the "Ubuntu install files" partition I'm referring to the /root section??? just clarifying)

---

### Post by adamorjames on 2007-10-27
> **mike_302 said:**
> the thing is, I'm going to reinstall anyways because of all the crap im being forced to put up with since i played around with too many things that I shouldn't have.  So, without repartitioning everything, how do I make a seperate home partition? what are reasonable sizes for the partitons? The following is what I personally figure but correct me if I need more:

Swap (1gb)
Home (my personal files? correct? 12 GB)
Ubuntu install files (where all the programs get installed to, including future onesthat I add) 8GB
FAT32 (switch between linux and microsoft) 5 GB

(is the "Ubuntu install files" partition I'm referring to the /root section??? just clarifying)

What I meant was, without backing up, reinstalling(wiping the root partition with home folder in it) and then making a home partition and putting files back into home. You can do it all inside Ubuntu that is on your HD instead. There isn't a way to make a separate partition for your current home when you reinstall unless you backup and do all the annoying steps like mentioned. So I'd go for the easy way. I'll see if I can find the tutorial for the easy HD way that I used a long time ago.
EDIT: Here is the tutorial - [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by mike_302 on 2007-10-27
I'm slightly confused... Let me reexplain what I'm now willing to do:

I'm going to wipe the Linux part of my HD (leave the XP) and reinstall it ALL. I don't care about any of those drivers because frankly, I realize now that I KNOW what I need to do so it wont take as long. All I'm wondering now is if those partition sizes I explained were correct, and how to go about setting up my Ubuntu (Gutsy) to install /root to one partition, and /home to another UPON formatting and reinstalling it all.

---

### Post by louieb on 2007-10-27
I like that attitude  "***if it ain't broke tweak it till it is***" .
One suggestion thought. If you have an external drive lean how to use **partimage  **[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

That way when you screw it up beyond repair you can restore it to a working state. The link above is a pretty good. If you burn a  [SystemRescueCd]("http://www.sysresccd.org/Main_Page") you can start at step 4.   And in step 5 instead of running **sudo partimage** its just  **partimage**.

BTW: Your partition scheme looks good. And yes you have it right the / (root) partition is the  main install partition. /home is for personal files.

I just loaded Gutsy on my laptop and Desktop. Think your going to like it.

---

### Post by zorkerz on 2007-10-27
Here is what I would do. I would use gparted (install it from the repos if its not). Use gparted to resize my current partitions to the way I want them

Mike_302 I would get ride of your vfat partition. I used to use one of these to switch between windows and ubuntu also, but now gutsy comes with ntfs read and write support out of the box so you can just leave thins in windows and ubuntu can add or grab others. I would say your sizes look pretty good.

So a good basic layout would be 
-swap (i don't know what sizes are recommended here depends on your ram ubuntu wants at least 512 mb I think)
-windows ntfs (as small as I can get away with)
-home (as big as I can make it)
- / (for ubuntu install files) at least 5 gigs but that can get tight depending on how much extra stuff you add


Once you have created a partition for your home documents separate from all the ubuntu install files I would backup or copy your home over here. You cannot just copy and past I have been using this command for some time with success.
```
 find . -depth -print0 | sudo cpio --null --sparse -pvd "/backup/dir"
```
This takes the contents of your home and copies them to where you specify

Lastly when you do the new install choose manual partitioning and it will show you all of your partitions. You edit each one giving them labels as "/" and "/home" Then install as normal. 

As a side note if your going to reinstall anyway and have the bandwidth it might be fun to try the upgrade and see what happens. I have had very successful upgrades most of the time.

---

### Post by mike_302 on 2007-10-28
so if i rename the partitions to / and /home, then ubuntu will recognize that and automatically send my home folder to its respected partition? Or will I still have to move it over with that command?

I'll download it today, burn to dvd and install tonight if i can, definatly following all of your advice for ntfs, getting rid of the FAT partition, etc.
As for the / partition, I'm still not 100% sure what size to put it at yet. Maybe I need a little more consultation-- I'm not using ubuntu as my MAIN OS, but I will be adding quite a few of the smaller programs if I can, from the Repos, if i find them useful (like audacity which I REALLY found to be powerful), and if support comes out in the future, I would REALY like to use photoshop on ubuntu so I'll need space to install stuff like that (as a nexample). My only question to this I guess is: When I install stuff from the repos, I know it goes to the root directory, but when I install stuff that I need to run through WINE for example, or programs that were made more for Windows, do those go to the root as well, or to the home partition?

---

### Post by zorkerz on 2007-10-28
Nameing the partitions / and /home at the beginning of the installation does not move your current home files over make sure you do that with the command before you install. If your really worried also copy them over to another hardrive then there is no chance of anything going wrong.

I have a slightly less that 5 gig partition for all my ubuntu system files and applications. It is my main OS but I do not install too many extra packages. It has gotten a little full before (at one point I only had 500 mb left) but this was because it was storing all the package for updates to beta gutsy after they had been installed.

If you ever run out of space you can always throw in a live cd with gparted on it and resize partitions as needed.

The packages for wine itself will be installed however normal packages get installed from the repos in ubuntu. Not really all to one place is my understanding be parts here and there according to some organization I never needed to learn. Wine can run programs from wherever they are. If you install them to with wine they go into your wine folder by default (.wine in your home directory) The period makes it hidden press ctrl + h to see hidden files in nautilus.

The advantage of this for wine is that you can setup all your windows programs with wine then when you want to upgrade or reinstall ubuntu all of your wine setup will remain intact.

I think I covered your questions shoot more if they come or anythings unclear. Good luck

---

### Post by mike_302 on 2007-10-28
So, how do I go about telling the installerthat code?... When do I say "Stop, I want to tell oyu to do something before oyu install" ... And How exactly do I use that code? I'm a newb basically with code so, based on that box of code you gave me originally, what would I be changing/altering to make it all work? My hard drive is now partitioned as follows:

hda1 (Windows) 64 GB
hda2   (/    the root directoy , about 7 GB)
hda3 extended
     hda5 (Linux swap, 1 GB) 
     hda6 (home, 17 GB)


EDIT: Actually, what I TRIED to do is install and, when I selected Manual for how I wnat to partition, and i told it which section to mount everything in, in the drop down list, /home was given as an option so I slected that for my 17 GB home partition and... I unno if thatll work but if not, I read that oyu can move the home partition after install anyways so, no big deal.

---

### Post by zorkerz on 2007-10-28
Sorry I was unclear.

First: use gparted (system->Administration->partition editor) to create a partition that will become /home
-->NOTE: depending on which partitions you are trying to resize you may want to do this with a livecd rather than in your current ubuntu install

Second: login as the user who's home folder you want to backup. Then copy and past this command into a terminal window. Be sure to replace "/backup/dir" with the location of your newly created home partition. ```
find . -depth -print0 | sudo cpio --null --sparse -pvd "/backup/dir"
```Finally: Throw in an ubuntu live cd and start the installation. In the partition section select manual and then specify the appropriate partitions. ie / and /home

* use the same login name or rename the home backup to your new login name before installing.

*keep in mind the command you enter above only creates a backup of the contents of home the new partition does not become home until you have completed a new install.

I hope thats a little clearer I working on using less words i think they tend to confuse. If your on an IM network feel free to contact me.

You can move the home after install. Its always looked like more of a complicated procedure than i wanted to do but there are good walk throughs out there.

---

### Post by mike_302 on 2007-10-28
added u to msn. 

I don't really have anytihng in my home folder CURRENTLY that I want to move t hte new setup. So I didn't bother copying anything over, instead I just set the mount point as /home in the installler. And, I DID use gparted to partition everythign and move stuff all aroudn tom the liking that I described in my last msg.

---

### Post by mike_302 on 2007-10-28
And-- now I'm trying to boot Gutsy and does its kernel alive kernel direct mapping tables crap, then goes black, but hte fan on my computer is still running constant, and the loading light flashes fairly frequently, but nothing happens.. ive left it for 5 minutes and nothing.

---

### Post by zorkerz on 2007-10-28
hmm i don't like the sound of that. I assume the livecd booted fine which means to me  that the kernel should work. Your getting no error message which makes it hard to diagnose. 
This is the first time you started gutsy?

---

### Post by mike_302 on 2007-10-28
yep. No error message, nothing... The LiveCD worked fine.

---

### Post by mike_302 on 2007-10-28
This is WEIRD, for sure. There are on errors in recovery mode either. Everything worked fine in feisty too so, why would any drivers be missing in gutsy? The only thing I DID get in installation was a message that said some securtiy files could not be accessed (probably from an internet source) and to check in oun that later, but everything would be fine... IT only said to check that once I got the system up and running. Should I simply try to reinstall?

---

### Post by zorkerz on 2007-10-28
I got the same security message you are right about that one its not your problem. Also you know all the drivers work because the live cd worked and is the same just on a cd rather than your harddrive.

I would start searching the forums there must be someone else with your problem. Or its possible the install had some problems and needs to be run again. Or maybe there is a problem with your livecd itself.

You could throw the cd in and one of the options is to check for defects.

---

### Post by mike_302 on 2007-10-28
going t do a disk check now. I'll let you know if anything else turns up...

The only problem with searching the forums for a similar problem is: what IS the problem? What do I search for? "screen goes black on boot" "no error at boot" the thing is, whatever I search for is probably the symptom of 100 other problems people are having, specific to their setup. :s none the less, I'll look.

---

### Post by mike_302 on 2007-10-28
AHA, ok.. I'm going to retry this over.. But I rebooted (no errors on the disk) and when it did hte black screen thing, I started mashing at ctrl alt bckspc and ctr alt f1 and... maybe it was delayed but ater I hit the f1 key pattern, the disk sorta started to move, then stopped, then a command line opened and tried to do some stuff and then the system started up.. no problem. I'm going to see if i can redo that.

---

### Post by mike_302 on 2007-10-28
kinit: no resume image, doing normal boot

thats what one of the lines said when I started mashing hte buttons again. I couldnt get it to load when i tried just clicking one of the pattersn or another, so i started mashing agian under impatience, and BAM it appeared so quickly.

---

### Post by mike_302 on 2007-10-28
allright. Upon ANOTHER restart, I just let it sit at the black screen for a few minutes, then INSTANTLY upon hitting ctrl alt f1, the lines came up and it booted again.. Clearly I can make gutsy work now, but CLEARLY I dont want to do this all just to boot eery time. What now?

---

### Post by zorkerz on 2007-10-28
wierd

Im not sure of the correct terminology for this but pressing ctrl + alt + an F key switches between consoles (correct term needed).

By default f7 is where x window runs. ie all your gui stuff. All smaller F keys should provide you with a command line ready to be logged into.

What happens when you switch between these (F1 through F7). Is your gui on F7 also.

I honestly don't know enough about what is happening to be much help. Without an error Im pretty useless. I would search around both here and google (i don't like ubuntuforums search much).

---

### Post by mike_302 on 2007-10-28
It doesnt work with f7.. only f1. Anyone else able to read this and help out?

---

