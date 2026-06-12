---
title: "Permission and Directory Help"
date: 2013-12-24
forum: General Help
---

### Post by b.the.dyck on 2013-12-24
Hello. This is my first post, and my first week with any Linux distro, so I'd like to ask that all answers are in step-by-step format and have a little explanation of what I'm doing within the steps/terminal commands, if that is not too much.

A couple days ago I started looking at distros and decided on a bunch that I wanted to use. I didn't want to take my time learning them separately, so I decided to install them all at once. I'll use a different one every day at school. I've got thirteen 15GB partitions, one 3GB swap, and one 20GB shared /home partition. I've got Ubuntu 13.10, Mint-Mate Petra(16), Fedora-Gnome3(20), Antegros-Cinnamon, Crunchbang 11-Gnome3, and OpenSUSE-Gnome3 all installed. I'm working on Arch and Gentoo after I finish with my issues in this post. I don't know what else I'm gunna use. Maybe recommend in your posts.

The way I have formatted it is that all the distros share /home, but are split into a sub folder for their distribution. EX: Ubuntu's home is mounted on the /home partition, and then my user documents are in /home/Ubuntu (to get to Documents, the file path would be /home/Ubuntu/Documents), and then Mint is /home/Mint in the same /home folder. I've done this with only Mint so far. Still working on this with other distros. This preemptive is for compatibility issues.


The things I need help with are:
1. Read-write access to all /home documents and folders from every distro without sudo/root/admin rights. (This is the "Permission" part; this idea stemmed from trouble I was having with my .dmrc and discussion in posts that showed me how to fix it.)

2. To be able to see every distro's home folder from the /home folder. As in, when I click the /home folder in / in Antegros, I see Mint, Ubuntu, Fedora, etc. (kind of like user folders) and have the ability to choose which distro's document folder I want to access, rather than searching the devices that have whichever OS installed on them and going to the /home folder from their root. I also want the OS I am using in that session to only use the /home dir it is associated with.

4. To see the 20GB /home partition under 'Devices' and be able to access every distro's /home/<distro> from there.

3. Something went wrong on installs, and users weren't created in Fedora and OpenSUSE. I can totally figure out how to make my own in recovery console or whatever it's called, but I'd like to list it here if only to keep track of what I need to and have learned to do.

If any of this is default and I'm missing something, tell me. If any of this is impossible, let me know. If It's just nearly impossible, I will still give it a shot.

Thanks for your help in advance.

---

### Post by Bashing-om on 2013-12-24
b.the.dyck; Hi ! Welcome to the forum .

All that you are wanting to accomplish is doable.
Permissions is the big thing:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Then mounting what you want and where to have access to those respective /homes:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

That is the basics, and should get you well on the way.

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

### Post by b.the.dyck on 2013-12-25
Okay, I'll give those links a look. Thank you. 

I love having a question and then figuring it out just before you're gunna ask it.

---

### Post by sheldon-corey on 2014-01-06
how to change .dmrc to 644 after changing /home


situation: I have a tri boot ubuntu or mint / fedora / win7
only with ubuntu or mint do i have this issue

sda 250gb MBR
sda1 ntfs 40gb win7 
sda2 ntfs 12gb page
sda3 extended
sda5 10gb ext4 ubuntu (or ubuntu based system)
sda6 10gb ext4 fedora
sda7 12gb swap
sda8 ntfs home 

issue arises post install of ubuntu system I have pulled a copy of the .dmrc before repointing /home to sda8 (as install hates ntfs) and when I attempt to make 644 permission to /home (now on sda8) i can't revert back to username for u and g it always reverts back to root owner and group what am i doing wrong and how to fix (using ntfs for home as I can't stand any windows ext readers I've found)

---

### Post by steeldriver on 2014-01-06
You can't use ntfs for home for the reasons you are now discovering - it doesn't support the ownership and permission flags necessary to make *nix work

In fact, what you're trying to do seems bass-ackwards to me - there should be no problem sharing Documents, Music, Pictures etc between distros, but the things you need to separate are the (hidden) config files (like the .dmrc file) that may conflict between the different desktops/distros and live in the top-level of /home. So it would make much more sense to have a bunch of separate (small) partitions that you mount as sda1 --> /home (for distro1), sda2 --> /home (for distro2) etc and then symlink or bind-mount your (common) Documents / Music / Pictures directories into each of those - and *they* can be on ntfs if you prefer.

---

