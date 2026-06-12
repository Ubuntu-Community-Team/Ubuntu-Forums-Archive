---
title: "Exporting list of installed programs/apps for a new install - possible?"
date: 2015-03-14
forum: General Help
---

### Post by mike248 on 2015-03-14
I have a system that I have fine tuned to where I really like the setup but there are some major issues that I'm not sure if it is in the kernel or other parts of the system.  After spending so much time installing and setting up the OS, I'd like to be able to "export" some kind of file that will show what is on the system and maybe a way to re-install them on a fresh install.  This is also because I want to duplicate this system on a number of other machines but they have different hardware.  

So I want to do a fresh install and then somehow re-install all the apps and such that are on the current system.  

It would be SUPERB if settings such as Dolphin configurations and such could be transfered over as well.  

Can anyone tell me if this stuff is possible and either where to look to find out how to do it, what to search for (if there is an app/feature name, etc), or any other info that may help here?

Any help is appreciated!

---

### Post by mörgæs on 2015-03-14
If you search [this post]("http://ubuntuforums.org/showthread.php?t=1946145") for the word *dpkg* you will see a method.

---

### Post by SeijiSensei on 2015-03-14
The dpkg command will let you save a configuration and later import it.  

To save the list of currently installed packages
```
sudo dpkg --get-selections > /path/to/some/file
```

To import the list
```
sudo dpkg --set-selections < /path/to/some/file
```

For the latter step, you would first install the base OS from the ISO image, then run dpkg with the list of selections to update it.

Configuration settings for things like Dolphin are stored in your home directory.  On a new installation, you might consider setting aside a separate partition for /home.  That way you can change the installed version of the operating system without touching your files and configurations.

---

### Post by sgage on 2015-03-14
Over the years of much testing and reinstalling, I have developed a simple .sh file that simply 'apt-get install's a long list of packages that I need/use/want. I actually have several of them - one for a gnome-based system, one for kde, one for unity, and a yum-based one for fedora. 

I also use grsync to save all my config files to an external drive on a regular basis. Again, I have a few different saved sets for various distros and releases, because settings sometimes move to different places, etc.  I also have a separate grsync config for data, which is distro-agnostic.

After I make a fresh install of, say, ubuntu-gnome, I simply copy over my config files  for the appropriate release (I currently have sets for trusty, utopic, and vivid), my data directory, and run my 'post-ug.sh' script, and in no time I'm up and running with all my programs and all my config just the way I like it. Makes it real easy to experiment with various distros and whatnot.

---

