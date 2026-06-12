---
title: "Some Basic Questions (that I can't find working answers to)"
date: 2004-12-14
forum: General Help
---

### Post by LoneIgadzra on 2004-12-14
I did not realize that this was not the forum for questions, sorry.

---------------------------------

I've checked the "unofficial starter guide" and given these forums a cursory once-over, and was unable to find any solutions to my problems that actually worked. I am a complete Linux neophyte (except some prolongued exposure to Mandrake, during which I experienced many problems that generally boiled down to I couldn't figure out how to get anything to work).

Question #1: How do I make Windows XP the default OS in Grubb? With Lilo and Mandrake it was easy (relatively speaking, which really isn't saying much)...
Question #2: How do I mount my windows drives on startup, in such a way that they are easily accessible? I've tried adding several different lines to the relevant file (forget what it's called), to no apparent avail. Or rather, I can access one of them if I manually navigate to /mnt/windows which is a complete pain in the ass. One drive (hdb1) has all my music on it which I want to listen to in Linux, and the other (hda1) has all my documents. I just want them to show up as normal hard drives, I don't care if they're read only.

And while I'm at, anyone know where I can download an AAC plug-in for one of the audio players? My entire music library is made up of AAC (.m4a) files. A Google search only turns up a lot of cryptic confusing results that I don't know what to do with.

---

### Post by Daniel G. Taylor on 2004-12-14
1. Edit /boot/grub/menu.list. The thing you want to change is the default. It is a number that corresponds to the listed operating systems in the file, starting at 0 (so the first entry is 0, the second entry is 1, etc). You should only have to do this if savedefault isn't working for you (meaning that grub should save the last entry you choose from grub automatically). If you don't want the savedefault feature, remove it from the entries in /boot/grub/menu.list.

2. The file to edit is /etc/fstab if they aren't automatically added/mounted. What I'd do is create /media/windows and then /media/windows/c, /media/windows/d, etc for each Windows partition, and have them mounted there. The entries would probably look similar to:

/dev/hda1    /media/windows/c    vfat    defaults 0 0

You may want to change "defaults" to set the premissions (if you want all users to be able to read/write, for example, you can put "umask=000" I think). This is from memory so the commands might be slightly different, but you get the general idea.

After adding all the entries, you can "sudo mount /media/windows/c" and so on for each drive to get them all mounted. Next time you restart, it will be done automatically.

After they are mounted, I'd suggest creating a link to them in your home directory or desktop (via GNOME or by doing "ln -s /media/windows/c /home/name/c") for easy access. After that is done you can also add them to the file chooser's bookmarks to make life even easier.

3. If the files are DRM protected (i.e. from the iTunes music store) then you may be out of luck, but otherwise I've had great experiences with gst-ffmpeg. Since it's technically illegal in many countries because of patent and royalty issues, Ubuntu can't ship it. Note that the instructions below are NOT SUPPORTED and potentially dangerous and illegal. I have had great success with it and Hoary, so I cannot vouch for it in Warty (the current stable release). Here's one way to go about getting it:

Open Synaptic (the package manager GUI), and edit the repositories.
You want to add [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
Update (reload) the package view, then search for ffmpeg. Install it.

Grab this: [http://pkg-gnome.alioth.debian.org/debian/pool/g/gst-ffmpeg/gstreamer0.8-ffmpeg_0.8.2-1_i386.deb](http://pkg-gnome.alioth.debian.org/debian/pool/g/gst-ffmpeg/gstreamer0.8-ffmpeg_0.8.2-1_i386.deb)
Then, "sudo dpkg -i gstreamer0.8-ffmpeg_0.8.2-1_i386.deb" to install the package. All of this assumes you are using x86 compatible hardware.

From this point on you should be able to use any gstreamer-based application to play most any media file. This includes totem, rhythmbox, and others.

---

### Post by LoneIgadzra on 2004-12-15
Well, I did everything as you suggested. I haven't had a chance to play around with grub yet, though if it does indeed remember the last OS used instead of launching the hilighted entry (which is always Ubuntu) as it claims it's about to do, I guess I'll have gotten anxious for nothing. But I still need to test it. 

For the drive mounting I think I see what's going on, and instead of "defaults" I substituted "umask=0222" (thanks to the Ubuntu Unoffical Starter Guide for that one) because they were mounted as readable only by root. So now I have my Windows drives on my desktop, which is super cool, the only problem being that now I want the Ubuntu partition (/) and my home folder on the desktop as well, and don't know how to get them there. ;-)

I also followed your instructions for the gst-ffmpeg thing. I didn't really understand how to edit the repositories, but after fiddling for a bit it seemed to work and I was able to install everything as you described. However, totem remains incapable of playing AAC's (and the video channel of some mpg's that I have of Family Guy episodes for that matter).

---

### Post by Daniel G. Taylor on 2004-12-15
For the root partition and home directory on the desktop, you can create links using GNOME (middle click and drag the directory to the desktop), or "ln -s / /home/name/Desktop/Ubuntu" and "ln -s /home/name /home/name/Desktop/Home" replacing "name" with your user name.

Sorry my explanation about the repositories wasn't that good, I was in OSX. I'm glad you got it setup, though. I went ahead and did some testing of my own using some MPEG4+AAC rips I made of my Futurama DVD's and the video plays fine, but I get no audio so I thin you're right, ffmpeg can't decode the AAC audio. After a bit of digging I've found [faac](http://www.audiocoding.com), which is a free AAC decoder and I know a gstreamer plugin exists for it, but I need to see if I can find a package for it or see how to get it to work if it's already there. I'll let you know after I do a bit of experimenting.

---

