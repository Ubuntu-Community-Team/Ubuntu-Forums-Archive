---
title: "Problem With Booting Ubuntu (Acer Aspire E1)"
date: 2015-03-08
forum: General Help
---

### Post by Marshall_Mason on 2015-03-08
I have an Acer Aspire E1 laptop with Ubuntu 14.04 LTS installed. I was happy with it until yesterday when I accidentally ran a dangerous command.
```
sudo dpkg --purge $(dpkg --get-selections | cut -d " " -f 1)
```
I accidentally forgot ```
grep deinstall
``` which, instead of removing config files for removed programs, started to remove all of my programs. I caught on after about a minute, but it was too late. I tried to do damage control by reinstalling some of the programs I thought it had deleted. After rebooting my system, Ubuntu opened up and asked me if I wanted to run in low-graphics mode. I couldn't use my mouse so I pressed enter. This led me to another screen with 4 radio buttons. I was able to select the buttons, but I could not select enter. I had the idea of switching to my tty terminals, but they wouldn't work. They would only ask for my login, do nothing for 3 minutes, and restart.

---

### Post by ajgreeny on 2015-03-08
Oh boy! What a pickle you got yourself into.

I wonder if this is one situation where a reinstall over the original OS, making sure you **DO NOT** **FORMAT** the partitions might just get you out of a really bad position.  This is now possible with 14.04 and later as far as I understand things, but I've never tried it and have no real knowledge of how successful it might be.

I was going to suggest you boot to a text command line and run ```
sudo apt-get install ubuntu-desktop
``` to try to add back whatever was removed but if you can not work in the tty terminals, a boot to cli will probably not work either, so I can not see any other way than a reinstall over the broken installation, or a complete clean reinstall.

---

### Post by Marshall_Mason on 2015-03-08
Thanks for the reply! I thought about what you said and I feel I should install Fedora on my laptop (I installed Ubuntu when I was a beginner) because I'm more of a novice now. I'm just worried about accidentally deleting my /home partition.

---

### Post by ajgreeny on 2015-03-09
It is years since I tried to install Fedora, and that was in the days when it used LVM as default, so I am not now in a position to give you any advice on installing that OS over your current Ubuntu.

I suspect you will just need to choose to use manual partitioning  in order to keep your /home partition safe and unformatted, but as with all OS installations I suggest very strongly that you have a backup of your /home just in case something goes wrong.

You might like to take a close look at [http://distrowatch.com/table.php?distribution=fedora](http://distrowatch.com/table.php?distribution=fedora) to see if that helps with your installation.  It is an excellent site for everything to do with Linux distros, and the reviews of the OSs available from the various site's links can be very informative.

---

