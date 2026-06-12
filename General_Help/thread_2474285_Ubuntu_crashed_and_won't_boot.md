---
title: "Ubuntu crashed and won't boot"
date: 2022-04-25
forum: General Help
---

### Post by slipslope on 2022-04-25
I think I had ubuntu 21.10 but I don't know because I can't access "about"

I am new to Linux and was trying to find out how to play Super Smash bros: Melee on my computer through an app called slippi. I was following a tutorial on YouTube called "Install Slippi Online on Linux". In the description there is a git hub link. In That github link under section "Ubuntu 20.04 LTS" had a command that I copied and pasted into terminal per the videos instructions. 

sudo apt install cmake pkg-config git libao-dev libasound2-dev libavcodec-dev libavformat-dev libbluetooth-dev libenet-dev libgtk2.0-dev liblzo2-dev libminiupnpc-dev libopenal-dev libpulse-dev libreadline-dev libsfml-dev libsoil-dev libsoundtouch-dev libswscale-dev libusb-1.0-0-dev libwxbase3.0-dev libwxgtk3.0-gtk3-dev libxext-dev libxrandr-dev portaudio19-dev zlib1g-dev libudev-dev libevdev-dev libmbedtls-dev libcurl4-openssl-dev libegl1-mesa-dev libpng-dev qtbase5-private-dev libxxf86vm-dev x11proto-xinerama-dev 

Typed my password in, it loaded a few things, asked y/n to use diskspace, I hit yes, then "installed". After installation I noticed my settings app and disk manager were auto removed from favorites. When I tried to open them nothing happened. Closed them and I couldn't find them anywhere. Looked through processes thar were happening after command (of which I now have a video of) and noticed a bunch of "removed ubuntu" "removed gnome tweaks" "removed gnome shell" and the list goes on. Tried finding how to reverse online and then tried sudo apt purge in front of same command. I tried rebooting and I'm in emergency mode now. Timed out waiting for device. Dependency failed for file system check. Dependency failed for boot efi. Dependency failed for local file system. When trying to boot from there I get "faules to start default targer: transaction for graphical.target/start is destructive (emergency. Target has 'start' job queued, but 'stop' is included in transaction).".  How boned am I? Any clues on what exactly did me in from that command line? Where do I go from here? Just trying to learn as much as I can

---

### Post by TheFu on 2022-04-25
Try
```
lsb_release -a
```
to see the version.

Following instructions for the wrong release is dangerous.
If you want to reverse stuff, we have these magical things in Unix/Linux called "backups."  They can put things back to the time when the backup was taken.
During installation, you could have selected an advanced file management system called LVM. LVM allows the admin to create something called a snapshot. What this means is technically simple, but hard to explain to someone new.  [https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)

Don't confuse LVM, ZFS, or BTRFS "snapshots" with what some backup tools call "snapshots", they are nothing alike.  For nearly all backup tools, when they say snapshot, they really mean "backup set".  Proper snapshots are nearly instantaneous - less than 1 second.  Backups using the snapshot term take 10-90 minutes, typically.

There is a tool that I've never used which can use btrfs snapshots to create backups as an integrated solution. I've never used it. BTRFS has some other issues which make it less-than-great for computers with multiple storage devices, but for a laptop with only 1 storage device, I think btrfs could be fine ... with some very important caveats like don't run virtual machines on the laptop and a few others.

If you don't have a backup, and if you are new, then troubleshooting is often too difficult. At this point, 21.10 support will be ending in 2-3 months and 22.04 would be what I installed if I were in the same situation as you today.  I am not.  None of my systems is newer than 20.04 and most are still running 18.04 Server which will lose support next year.  20.04 server will lose support in April 2025.  LTS Ubuntu desktop flavors typically have support for 3 yrs, so most people should move from LTS to LTS to LTS (18.04 --> 20.04 --> 22.04 --> ....)  Any other releases are NOT LTS and have effectively 6 months of support.

Since 21.10 support ends shortly, moving to 22.04 really isn't a choice. It has to happen before July. There's no real choice about that.

Some systems management tips:
[LIST]
[*]Make backups, at least weekly. If you can, you'll want backups that cover the last 90 days to fight malware attacks too.
[*]Test the backups to be certain you know how to restore them.
[*]Install only LTS releases and upgrade every 2 yrs. There's a 12 month overlap, so once you make the first change, the next upgrade isn't require immediately when the next LTS is released. We have some time.
[*]Don't install packages for the wrong release.
[*]Avoid directly installing .deb files.
[*]Use only trusted PPAs, not random PPAs.
[*]Patch weekly, not daily. Patching too often is a maintenance and security failure. Patching less often is bad too. In the world today, there are always - ALWAYS - unknown attacks that are in the wild and working.  If you work in an enterprise or NGO, your stance will need to be different, more nuanced for security. Those guys are constantly under attack.  I did some volunteer network design and deployment work for a monastery in a different country in central Asia.  Seems a specific govt didn't like that order of monks and has been attacking my systems for years now.
[/LIST]

So, do you have backups?

---

### Post by grahammechanical on 2022-04-25
Questions. As that command processed through the terminal did you see the word "autoremove?" Did you run the autoremove command? Oh, by the way, Slippi comes as an AppImage. Perhaps a safer way to install this application in Ubuntu.

[https://appimage.github.io/Slippi/](https://appimage.github.io/Slippi/)

I also think that this app is designed for KDE not Gnome. It includes a Dolphin emulator. It could be why so much of Gnome was removed.

[https://store.kde.org/p/1573268/](https://store.kde.org/p/1573268/)

Regards

---

### Post by Impavidus on 2022-04-26
To see the version, you can also look at the file /etc/lsb-release (which is where lsb_release -a gets its information).
> **slipslope said:**
> 
sudo apt install cmake pkg-config git libao-dev libasound2-dev libavcodec-dev libavformat-dev libbluetooth-dev libenet-dev libgtk2.0-dev liblzo2-dev libminiupnpc-dev libopenal-dev libpulse-dev libreadline-dev libsfml-dev libsoil-dev libsoundtouch-dev libswscale-dev libusb-1.0-0-dev libwxbase3.0-dev libwxgtk3.0-gtk3-dev libxext-dev libxrandr-dev portaudio19-dev zlib1g-dev libudev-dev libevdev-dev libmbedtls-dev libcurl4-openssl-dev libegl1-mesa-dev libpng-dev qtbase5-private-dev libxxf86vm-dev x11proto-xinerama-dev 
That command shouldn't be very dangerous. It installs a few software development tools (cmake, pkg-config and git) and the header files belonging to a large number of libraries, which you need to compile and install something from source. It will pull in the libraries themselves too if you don't have them already. On my Xubuntu 21.10 system it would remove only a single package, libjack-jackd2-0, as it gets replaced by libjack0.

Before hitting y to agree with installation, did you look at the list of packages that were going to be removed? It's a good idea to look at that list, always. And think twice before agreeing if that list isn't empty.

To see what happened exactly, you can look at the log files. Everything the package manager did is logged in /var/log/dpkg.log. If you can't get to a GUI session, it may be easier to access those logs using a live disk. If you use a live disk, make sure you look at the log files of the installed system, not of the live system.

I must add that the mess you appear to be in is far larger than would be expected from running a simple apt install command with some not-so-important packages, nor from running an apt purge command with the same packages. Something more may be going on. And as already stated, Ubuntu 21.10 is nearing end of life and its successor has been released, to which you have to upgrade in the next three months anyway, so the easy solution is a fresh install of 22.04. If you've got a separate /home partition, or keep your documents on a separate partition, you can keep those, else you have to restore them from backups. Make sure you've got those backups anyway. You can make them, if you haven't already, using a live disk. I suggest you wipe your user configuration, as that may be messy too.

So, do you want the quick fix, or do you want to investigate further? I can't guarantee that investigating this further will lead to a different solution than a fresh install. I don't expect so.

---

### Post by slipslope on 2022-05-02
Thanks for your response. I was correct, my version was 21.10. I do not have any back ups. I will probably update to 22.04 LTS as you suggested and make sure to back everything up using LVM. What is the proper route to start fresh from emergency mode? As in how I delete the skeleton of ununtu that remains through emergency mode?

---

### Post by slipslope on 2022-05-02
Looking back now I see that the autoremove command was run. I now know to look into what's being removed more carefully. Also, what information leads you to believe it's designed for KDE? I think I'm gonna try Kubuntu on my next go around anyways but I'm just wondering

---

### Post by TheFu on 2022-05-02
> **slipslope said:**
> Thanks for your response. I was correct, my version was 21.10. I do not have any back ups. I will probably update to 22.04 LTS as you suggested and make sure to back everything up using LVM.

If LVM wasn't added during install time, then it can't be added later, except where there isn't already data. Storage has layers. They are, in order:
[LIST=1]
[*]Disk
[*]Partitions
[*]Encryption (optional)
[*]LVM/LVs (optional)
[*]File systems
[*]Directories and Files
[/LIST]

File systems can be placed onto either the partition or an LVM-LV (logical volume).
Hope that helps.

LVM isn't a backup. It is a way to make better backups that won't be corrupted because files can be frozen in a 'snapshot' while they are backed up.  An LVM snapshot is really at the LV level. Create it using the snapshot term, then mount the snapshot somewhere else, read-only, and backup the important things in the snapshot to other storage.  There is little reason to backup the OS or swap or temporary files.  There are plenty of threads in these forums for what people backup. I've listed what I backup multiple times. I also explain my restore process.

---

### Post by Impavidus on 2022-05-03
Create a live disk of Ubuntu 22.04. Boot it. Then you can test 22.04 on your hardware and create backups on an external drive using the familiar GUI or the command line, if you prefer. Unmount and unplug the external drive with your backups, then install 22.04, wiping whatever is on your hard drive in the process.

Then reboot into your freshly installed 22.04 system, plug in the external drive with the backups and copy them back to the internal hard drive.

---

