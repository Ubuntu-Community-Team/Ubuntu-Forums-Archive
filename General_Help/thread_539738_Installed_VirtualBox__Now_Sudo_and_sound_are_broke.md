---
title: "Installed VirtualBox:  Now Sudo and sound are broken!"
date: 2007-08-31
forum: General Help
---

### Post by RChickenMan on 2007-08-31
Good day,

I installed virtual box, and now I cannot use Sudo ("Sorry, user <username> is not allowed to execute <binary path> as root on <machine name>."), and my sound card is no longer working (clicking on volume control icon gives a dialog box, "No volume control GStreamer plugins and/or devices found."  I discovered the Sudo problem almost immediately, and the sound problem a day or so later.  Chances are that other things are broken in my system as well.

I'm thinking the sudo problem has something to do with some user administration things I had to do in order to use virtual box.  The solution to the problem probably involves editing the sudoers files which, of course, requires root access.  Unfortunately I cannot login to the root account directly or boot into recovery mode since Ubuntu disables the root account by default.  Enabling the root account requires, well, root access.  So if I find out what is wrong with the sudoers files, I guess I can boot into a live CD and access the file system free of permission issues.

In addition to installing VirtualBox, here are some of the commands that happened around the time the problem happened:

```

  467  usermod -G vboxusers jeff
  468  sudo usermod -G vboxusers jeff
  469  VirtualBox 
  470  sudo usermod -Gvboxusers jeff
  471  usermod -Gvboxusers jeff
  472  sudo usermod -Gvboxusers jeff
  473  useradd -g vboxusers jeff

```

As you can see, I wasn't completely sure how to add the group to user jeff, so I tried a few different things.

Does anyone have any idea what went wrong and some ideas on how I could go about correcting them?

Thank you for your attention.

---

### Post by bodhi.zazen on 2007-08-31
Well, my guess is that in adding yourself to the virtualbox group, you removed yourself from other groups.

so, see this post :

[http://ubuntuforums.org/showpost.php?p=3282837&postcount=4](http://ubuntuforums.org/showpost.php?p=3282837&postcount=4)

Then reboot and add yourself to additional groups as needed (ie audio)

---

### Post by RChickenMan on 2007-09-01
Thanks, I booted into a live CD to get around the whole "security" business and added myself to the admin and audio groups.  Of course, I have a feeling that I kicked myself out of a lot more groups than just the two.  There are a bunch of groups that have no members at all, and I'm thinking I should be members of some of them.

So could anyone who is reading this please post their /etc/group file so that I can see what kinds of groups I should be a member of?

Thanks!

---

### Post by bodhi.zazen on 2007-09-01
The default groups for and admin user are :

1. your user name = primary group

2. adm, dialout, cdrom, floppy, audio, dip, video, plugdev, users, netdev, scanner, lpadmin, powerdev, admin

---

### Post by john8791 on 2007-09-01
> **RChickenMan said:**
> Good day,


I'm thinking the sudo problem has something to do with some user administration things I had to do in order to use virtual box.  The solution to the problem probably involves editing the sudoers files which, of course, requires root access. 

I know this doesn't help you now, but when you edit the sudoers file, you need to use "sudo visudo".  This makes a backup and checks for syntax errors.  Do not edit directly.

I have posted my group file for you.

---

### Post by brickbat on 2007-09-04
I think you can get around all these problems by using the gui in  System/Administration/Users & Groups/Manage Groups

---

