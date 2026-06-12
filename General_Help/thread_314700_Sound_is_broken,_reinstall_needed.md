---
title: "Sound is broken, reinstall needed?"
date: 2006-12-07
forum: General Help
---

### Post by Mimsy on 2006-12-07
I am very frustrated. Unbuntu kicks @ss, no argument there, but it is incredibly frustrating at times.

Things should not be this complicated.

As of right now, I am stuck with horrible screen refresh rates on the monitor hooked up to the laptop docking station (I made another thread about that), and absolutely no sound whatsoever. I tried to follow the howto in the multimedia forum, and I followed the all guides I could find in the forums, and in the links in my signature, but ot no avail: I have no sound from the laptop anymore. I started out with the "only one application at a time can use the sound card" situation, and in my attempts to fix that, I completely killed all sound abilities of the poor Compaq Evo.

I admit, without reservation, that my own ignorance about Ubuntu and Linux greatly contributed to my frustrating situation.

Do I need to reinstall Ubuntu to solve this, or is there another way?

All help appreciated,
Mimsy

---

### Post by K.Mandla on 2006-12-07
Is there no sound whatsoever, or is there no sound while it's jacked into the docking station?

I had an old Dell Latitude CPi that I put in a Port II docking station and got no sound from the dock's ports (which made it completely irrelevant, since that was the laptop I use to serve music through the house and play tunes in one room).

Sound still worked out the laptop jack, just not from the docking station. I've heard that some other people had the same problem, but it seemed to be confined to Dells.

---

### Post by Mimsy on 2006-12-07
Thanks for the quick reply! :)

There is no sound whatsoever. The day before yesterday I was watching a movie on the bigger screen connected to the docking station, and I had sound in the headphones that I had connected to the laptop itself.

I spent a large portion of yesterday installing Skype and trying to set it up so I would have sound using it, and I think that tweaking is what killed sound completely. I now have no sound whatsoever; not even the drum sound that used to come at the login screen.

/Mimsy

---

### Post by Mimsy on 2006-12-08
Update:
I plugged in the headphones, directly into the laptop itself, so I would be able to tell when or if something happened as I continued to tweak. My plan was to track down and purge the sound drivers and reinstall them from scratch; maybe without the tweaking damage I had done they would work. So I put the headphones on and plugged them in. When I did, I heard some static through the headphones. Hm. This might be worth checking out. I put in the DVD again, and started the movie. Mplayer refused to play it, but gxine could... and in gxine it has both picture and sound.

So I have sound in gxine, but not in Totem Mplayer. This leads me to think that my sound configuration is all wrong. I will be experimenting with it this weekend. In the mean time, I remain open to suggestions.

/Mimsy

---

### Post by K.Mandla on 2006-12-08
Well that's hopeful, at least. I was going to suggest stripping out alsa and reinstalling it, but that's rather drastic.

---

### Post by Mimsy on 2006-12-08
I would rather not do that, if it can be avoided.

I noticed just a moment ago, as I was unplugging my headphones during the movie to see if I would get sound when they were plugged into the docking station, that I get a ***very*** loud squealing from my laptop speakers when I unplug the headphones. Not in the headphones themselves, thankfully, or I would be deaf now, but from the actual laptop. The other person in the room demanded to know what the h--- I was doing, and could I make it stop? Needless to say I shut things down as quickly as I could - the squealing was very loud.

I'm  now thinking that alsamixer may be messed up. Can I restore it to default somehow?

/Mimsy

---

### Post by Mimsy on 2006-12-08
New update:
The loud squealing became permanent. I shut down the laptop, unplugged the headphones, and rebooted, and the squealing begun almost before Ubuntu was fully loaded. I could hear it from the kitchen - that is one set of stairs and three rooms from where the laptop was! Quite naturally, the poor guy sitting in the room with the laptop, trying to get some late night work done before going to bed, was not happy. He shut the lid, hoping that would silence the darned thing, and fortunately for everyone it did. However, that doesn't change the fact that I am now on the Bad Girlfriend list for the rest of the night.

I took the laptop as far from the home office as possible and plugged it into the docking station again (the docking station has the CD/DVD drive, without it the laptop can't read discs), and put in the Edge live CD. Thank all gods, there was blissful silence. I'm typing this from the Edgy live CD now, while I am trying to figure out where the horrible squealing is coming from.

I am deeply confused and very frustrated, but most of all I am incredibly grateful that the semester is over. This is the laptop I used to print my term paper and other assignment, and if this had happened last week, I would have been in deep, deep trouble.

/Mimsy

---

### Post by K.Mandla on 2006-12-08
That's very odd stuff. I was ready to write it off as a hardware issue, but if the live CD is coming through clear, then perhaps it's software after all.

I'd double check your sound control panel and make sure no bells or whistles are enabled. I have a laptop with some sort of 3D sound trigger that releases hideous static when I enable it. 

Aside from that, I guess you could purge out alsa and reinstall it. I really don't know if that would solve the problem, though. :-k

---

### Post by Mimsy on 2006-12-08
Purge out alsa sounds like it might work; it was after I started messing with alsamixer that the squealing started. Is the package name just "alsa", or is it called something else?

/Mimsy

---

### Post by K.Mandla on 2006-12-08
If I remember right, it's alsa-base and alsa-utils. That should completely rip the guts from your audio subsystem. You might have to pull ubuntu-minimal or ubuntu-standard too (I forget which one), since those are metapackages serving as stopgaps for the base-level stuff. They're harmless to yank out, though. I'd make a point of using *aptitude remove --purge* too, since you don't want any configuration files left over.

---

### Post by Mimsy on 2006-12-08
Surprisingly, and annoyingly, enough, the squealing is so loud and persistent that the laptop is unusable unless I run it from the live CD. So my next question is, can I purge those packages through the live cd, once I've managed to mount the hard drive?

I am fairly certain that the problem is that I have the microphone enabled in alsamixer, since the squealing sounds just like speakers do when you put the microphone too close. At least I know to keep it muted from now on! :)

/Mimsy

---

### Post by Mimsy on 2006-12-08
Hm. I don't think my live CD can see the hard disc drive of the laptop. I tried the command "sudo mount -t ext3 /dev/hda1 /media/recovery" with hda1 replaced by various "names" of eth drive that I could think of, but no luck. :(

I know that this can be done, and I'm frustrated by my own inability to make it happen. Off to the Ubuntu wiki to do my homework!

/Mimsy

---

### Post by scrooge_74 on 2006-12-08
Maybe start the laptop in safe mode and then uninstall everything it has to do with ALSA

Reboot and then install ALSA again

---

### Post by K.Mandla on 2006-12-09
I think it's possible to boot live, then uninstall, but I think you have to chroot into to the mounted drive, since aptitude is otherwise going to try to tamper with the live environment. 

I can't offer too many tips on that; I've only ever done that a few times, and the circumstances were unusual. I think you set up a folder in your live environment (like '/ubuntu'), then mount your hard drive to subdirectories of that folder (like '/ubuntu/root' for /, '/ubuntu/home' for /home, etc.), then chroot ... nah, I'd better not. I'm probably making things worse.

scrooge_74's suggestion might work too, but I don't know if safe mode will boot without sound.

Hey, if you have a headphone extension cord, you could plug it into the headphone jack, which would kill the sound output long enough to fix alsa. ... :-k

P.S.: Can you disable the sound through the BIOS?

---

### Post by K.Mandla on 2006-12-09
> **Mimsy said:**
> Hm. I don't think my live CD can see the hard disc drive of the laptop. I tried the command "sudo mount -t ext3 /dev/hda1 /media/recovery" with hda1 replaced by various "names" of eth drive that I could think of, but no luck. :(

I know that this can be done, and I'm frustrated by my own inability to make it happen. Off to the Ubuntu wiki to do my homework!

/Mimsy
Use *sudo fdisk -l /dev/hda* to list the partitions on /dev/hda.

---

### Post by Mimsy on 2006-12-09
I tried > sudo fdisk -l /dev/hda in a terminal, and to my great surprise it listed /dev/hda1 as the partition with Linux. I have lost count of how many times I have tried to mount that, in different ways, through the live CD. That was also the only partition that had an asterisk, *, in the "bootable" column, when I ran the command above.

I'm now going to plug in the headphone extension cord and see if that makes the squealing stop long enough to purge the alsa packages.

If that fails I'm going to try and disable sound in the BIOS, to see if that allows me to purge all alsa packages and get rid of the squealing. If it doesn't, I'm hoping it will at least keep the laptop quiet long enough for me to salvage the two files I need to copy before I can safely wipe the hard drive and do a fresh install of Ubuntu.

I'll be back with updates in a little bit.

/Mimsy

---

### Post by Mimsy on 2006-12-09
Okay, here goes...

I tried rebooting into safe mode, but the laptop spontaneously rebooted on me. Gah! Fortunately, I managed to plug in the headphone extension cord during the process, and it started up again without any squealing.That made me happy. :) Here's what happened once I went on to purge alsa packages:
> 
mimsy@Falcon:~$ sudo aptitude remove --purge alsa-base
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following packages are BROKEN:
  ubuntu-minimal
The following packages will be REMOVED:
  alsa-base
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 332kB will be freed.
The following packages have unmet dependencies:
  ubuntu-minimal: Depends: alsa-base but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-base
ubuntu-minimal

Leave the following dependencies unresolved:
alsa-utils recommends alsa-base (>= 1.0.9b-3)
libpt-plugins-alsa recommends alsa-base
Score is -1056

Accept this solution? [Y/n/q/?] y
The following packages will be automatically REMOVED:
  ubuntu-base ubuntu-minimal
The following packages will be REMOVED:
  alsa-base ubuntu-base ubuntu-minimal
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 414kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 107372 files and directories currently installed.)
Removing ubuntu-base ...
Removing ubuntu-minimal ...
Removing alsa-base ...
mimsy@Falcon:~$ sudo aptitude remove --purge alsa-utils
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following packages are BROKEN:
  gdm gnome-control-center
The following packages will be REMOVED:
  alsa-utils
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1872kB will be freed.
The following packages have unmet dependencies:
  gnome-control-center: Depends: alsa-utils (>= 1.0.10-1ubuntu10) but it is not installable
  gdm: Depends: alsa-utils but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
gdm
gnome-applets
gnome-control-center
gnome-panel
gnome-session
gnome-terminal
nautilus
ubuntu-desktop

Downgrade the following packages:
nautilus-data [2.14.3-0ubuntu1 (dapper-updates, dapper-updates, now) ->
2.14.1-0ubuntu9 (dapper, dapper)]

Leave the following dependencies unresolved:
gnome-system-tools recommends gnome-control-center (>= 1:2.10.1-1)
nautilus-data recommends nautilus (= 2.14.1-0ubuntu9)
capplets-data recommends gnome-control-center (= 1:2.14.2-0ubuntu1)
gnome-panel-data recommends gnome-panel (= 2.14.3-0ubuntu1)
gnome-terminal-data recommends gnome-terminal
Score is -3848

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

This is the part that concerns me:
> Remove the following packages:
gdm
gnome-applets
gnome-control-center
gnome-panel
gnome-session
gnome-terminal
nautilus
ubuntu-desktop


I suppose I could do a "sudo aptitude install ubuntu-desktop" immediately after reboot, but all the same, I'd like to know before I choose yes, what is the worst thing that can happen?

/Mimsy

---

### Post by K.Mandla on 2006-12-09
Oh nuts, I forgot that Gnome would rely on some of those packages. My fault; I haven't worked with Gnome in so long.

Seems to me that the worst that could happen is that you end up rebooting in safe mode as root, and reinstalling ubuntu-desktop. I would keep a scribbled list of what got removed as a result of yanking alsa, just so nothing gets discombobulated on reassembly.

By the way, any time now would probably be a wise time to back up important stuff. In the off case that something becomes completely unusable, I'd feel responsible. :shock:

---

### Post by Mimsy on 2006-12-09
> **K.Mandla said:**
> By the way, any time now would probably be a wise time to back up important stuff. In the off case that something becomes completely unusable, I'd feel responsible. :shock:

And while you do that, I'll be over here feeling smart that I actually paid attention to the terminal output, and asked questions about it instead of mindlessly say "yes" to anything that popped up. ;)

I have back-ups of everything important on the hard drive, as far as I know anyway, which means that since I am ignorant about configuration files, probably none of them. I care less about that than about my documents and media files anyway.

Worst case scenario, I can always put in the live CD again and search here for more solutions.

Now, off to purge things. Hehe. :twisted: 

/Mimsy

---

### Post by Mimsy on 2006-12-09
Alsa-utils was successfully purged from the laptop, along with my  entire desktop environment. I then restarted the laptop, and waited for it to finish booting, and leave me at a command prompt that apparently wanted me to log in. So I did, and all I found was a blackscreen and a command line, so whatever was removed obviously was fully removed.

I was a little bit surprised to find that if you type in "sudo aptitude install ubuntu-desktop" it installs the two alsa packages as well, but I was going to do that anyway, so I said yes to installing all the packages that were previously removed, rebooted again, and found all my desktop settings right were they used to be. Nice.

Best of all, after reboot I unplugged the headphone extension cord, and there is no squealing at all. The sound is back to what it was before I started all my tweaking!

Thanks for all the help!

/Mimsy

---

### Post by scrooge_74 on 2006-12-09
Happy Ubunting !!!

---

### Post by K.Mandla on 2006-12-11
> **Mimsy said:**
> Best of all, after reboot I unplugged the headphone extension cord, and there is no squealing at all. The sound is back to what it was before I started all my tweaking!

Thanks for all the help!
Fantastic! That's great! Cheers! :KS

---

### Post by Mimsy on 2006-12-11
The high irony of it all is that about an hour after I made my cheerful post, the horrible squaling started again! fortunately the headphones were close by, and I managed to plug them in before anyone had a migraine attack...

When I looked at alsamixer, to see if it would let me mute the speakers, I noticed that the microphone was set to maximum input.  That explained quite a lot...! The microphone is now muted.

/Mimsy

---

