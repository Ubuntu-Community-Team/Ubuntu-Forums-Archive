---
title: "Recommended things to try"
date: 2007-10-22
forum: General Help
---

### Post by kamasabi on 2007-10-22
So my journey into linux/ubuntu begins. :)  

I've been your typical windows user who has been risen since windows 95 all the way up through XP (refuse vista, many reasons why, but yeah).  Frankly, I'm looking for something different.  I tried Mac for a while when I was working at my previous college in a recording studio, and I liked the UI on it, very easy to use, pretty much everything handed to you, however it's not exactly what I want.  I like the idea of making my computer do what I want it to do, not just what it was pre-programmed to.  So, I heard a lot of ruckus about ubuntu, so I figured I would give it a shot.  So far, I'm very impressed with it, it beats the pants outta windows when it comes to startup times and dexterity.  My main original purpose was to have it running as a file server, and yet again, it also seems to do a much better job than windows.  Even just browsing through the files seems exponentially faster than windows ever seemed to be like, transfer times are faster, not to mention the great access control capabilities!!!  Samba is frickin awsome!  Just using a series of guides here I learned how to set a few things up, like samba, hamachi,etc. (thank god for gusty, I don't have to deal with my video drivers :), although I would still like to figure out how to do it properly anyway).  

Now as for the reason for my post: I have just started reading this glourious post about just basically installing ubuntu/other.

[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

While I'm reading through this, what kinds of things do you think I should try doing, just to help familiarize myself with it?  Setting up samba was a walk in the park as far as setting it up, but it's the command line where I have most of my problems, and knowing where to go.  Setting up my fstab and smb.conf were pie, considering the syntax's and format were all simply listed in the smb.conf, and another post I found just searching around about how fstab works.  

However its things like "apt-get", "aptitude", and parts of my commands that I don't fully understand how they work.  Maybe that'll come later in that post, dunno, haven't gotten there yet.  I'm just not 100% sure on some things I should be looking for.  For instance, I was messing around with the Synaptics Package Manager, and there are tons of programs that are available.  But what if there are some programs that aren't available?  I have a game server that had been previously running windows, but I wanted to try linux and see how it worked out.  I ran a search for the UT3 Beta in there and found nothing, so looking around on google I found it, but I have no idea how exactly to install it.  Again, going back to the command line :(, as well as knowledge on file types used in linux.  How does ubuntu handle installing those packages?  windows was nice because it just went straight through the microsoft installer and just click a bunch of options and whala, but just not used to this quite yet.  

Also, the GUI is interesting in the respsect for the whole super admin idea.  In windows, you can create directories very easily just by right clicking where you want, making a new folder, naming it to whatever, and you're good *or the various other methods*.  You can also easily create shortcuts from one place to another.  In ubuntu, you have to **unless there is a different way** be logged into root in order to be able to use a lot of those options through the GUI.  I kinda cheated when I'm really desperate and log into root when I get really irritated, but I'm trying not to as much as possible.  

I plan on continuing to use ubuntu, so far, aside from the uniqueness learning curve, it's very nice.  I'll be taking a class in operating systems probably next fall, hopefully I can find one specifically for linux, but hoping to gain as much knowledge here as possible!

Please post your suggestions, they would be much appreciated!!!

Thanks,

Kama

---

### Post by Sunforge on 2007-10-22
The "Ubuntu way" is to not set a password for root, although you can set one yourself by using the command
 
sudo passwd root
 
Generally though it's best to stick with sudo and after some inconvenience you'll get used to it. 
 
The general principle is that you can do what you like in your home folder but are severely restricted outside that area.
 
If you're in Gnome you can launch nautilus as root by using the command:
 
"gksudo nautilus"
 
Once you've input your normal password you have root: just be careful what you get up to as you can cause a lot of damage.
 
If you're really new to Linux here's a guide to what all those top level directories are there for:

[http://www.neowin.net/forum/lofiversion/index.php/t64329.html](http://www.neowin.net/forum/lofiversion/index.php/t64329.html)
 
The Ubuntu repositories are arranged as follows:
Main - completely free FOSS binaries, supported via Ubuntu/Canonical
Universe - unsupported FOSS binaries
Multiverse - unsupported non-FOSS binaries
Restricted - non-FOSS binaries which are nonetheless supported by the Ubuntu team due to frequent use eg: NVIDIA drivers.

Programmes like UT3 are I think outside the scope of the repositories because there are components that you cannot freely redistribute.

---

### Post by mali2297 on 2007-10-22
Here are a collection of links about using the command line:
[https://help.ubuntu.com/7.04/basic-commands/C/ar01s07.html](https://help.ubuntu.com/7.04/basic-commands/C/ar01s07.html)

If you've got a game from the project's web site, you often need to compile it from source. Here's one tutorial that I found:
[http://jucato.wordpress.com/2006/09/04/ubuntu-classroom-basic-compiling/](http://jucato.wordpress.com/2006/09/04/ubuntu-classroom-basic-compiling/)

Also, often there are files called README or INSTALL in the downloaded package. They contain information on how to install and use the program.

Sometimes a .deb file is provided. In that case you can simply install the program by
```

sudo dpkg -i filename.deb

```

Have fun. :-)

---

