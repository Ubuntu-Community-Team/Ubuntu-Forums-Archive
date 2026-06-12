---
title: "ubuntu won't boot up..."
date: 2008-04-11
forum: General Help
---

### Post by Mia_tech on 2008-04-11
I resetted my computer and now I'm left with the ubuntu black splash screen during bootup ... could anyone give me a hand to bring my machine to working condition....I'm using ubuntu 7.10

thanks

---

### Post by ibuclaw on 2008-04-11
Boot into recovery mode. (option 2 in the GRUB menu)

You'll be able to see all printed output of what is going on in the startup of ubuntu.

If you see any errors, or if a certain error gets printed recursively across the screen, take note of it and post back with what it is saying to be best of your description. (ideally, a near-identical version of the line that was printed would help alot).

If Ubuntu boots up correctly in recovery mode, type in **exit** to continue to the gdm login screen. As the error could be with X.

Regards
Iain

---

### Post by Mia_tech on 2008-04-11
well, I don't see any menu in grub during boot up... it goes straight to the ubuntu splash screen

thanks

---

### Post by ibuclaw on 2008-04-11
Oh. Okay then.

Try hitting:
```
 Alt+Ctrl+F1 
```
When Ubuntu is booting up then.

It should switch to the classic terminal startup view:
It should should something like this:
```

Running Startup Scripts                  [OK]
Mounting Devices                         [OK]
Detecting SoundCards                     [OK]
etc..

```

If that works you should be able to see where it is going wrong.

Regards
Iain

---

### Post by Mia_tech on 2008-04-11
it stops at 
```
Loading kernel modules...
Loading manual drivers...
```

does that tell you something..

thanks..

---

### Post by ibuclaw on 2008-04-11
An updated driver gone wrong?

In any case...
Do you have a LiveCD hanging around?

Because you'll need it to access the filesystem.

When you boot up into the LiveCD, chroot to your Linux Partition
ie: ```
 chroot /media/sda1 
```

Then there is one of two things I can think of you trying out.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
**A) ** Open up "/etc/modules" in a text editor.
Best hope is to hash out each line one by one. Then boot up as normal.
To see if we can isolate the erroneous driver.

To make sure that you are looking at the right file, here is a printed output of mine as a demonstrated example:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp

```
If you are frightened to hash something out, look it up on sourceforge.
Or google up **what is ##module name## linux**
You will find that it is OK to do so.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
**B) ** Update your system using the LiveCD.
The commands should work as normal.
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean

```
As the error could be fixed. And all you need to do is update the faulty package.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

If you have any queries, or run into any trouble. Just ask.

Regards
Iain

---

### Post by Mia_tech on 2008-04-11
yes I have a live cd, but what exactly do you mean by hash out...do you mean comment out one line at a time?

thanks

---

### Post by ibuclaw on 2008-04-11
Yes, comment it out.

ie:
To take my /etc/modules file as an example again.
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

#fuse   <---Hashed out, or Commented out.
lp

#          If you still get a freeze on startup, reload the LiveCD
#          And "un-comment" the above line.
#          Then "comment out" the next line.
#          So we have something that looks like this now:
[CODE]
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
#lp

```
[/CODE]
And try this again and again until you find it.

If you still can't get it to work. Comment out it all!

If still it doesn't work. Try updating your system through the LiveCD as I said above.

If all else fails, this may be beyond my knowledge, and I'm sorry for that.
I would then recommend considering backing up your precious data.

Also, make a note of all apps you have installed.
A time saving way would be to run this (while chroot'ed to your Linux Partition)
```
 dpkg --get-selections | awk '{if ($2="install") print $1" "}' | tr -d '\n' > instpackages 
```
That will save all your installed packages to a file.

Then doing a fresh clean install of Ubuntu.

Then to reinstall your programs.
```
 sudo apt-get install `cat instpackages` 
```
Though ironically, if it is a bad update of a driver, this may cause your bootup to crash again, so be careful.

Also, sorry for my terminology. I will keep that in mind next time I use the word. Thanks.

Regards
Iain

---

### Post by Mia_tech on 2008-04-11
lol....hey you fixed it!...now what?...there was only one line in my /etc/moudules file and it was fuse, by the way what is fuse?, and what kind of file is the modules file, also I have a question regarding the second method of your previous post, which involve updating the installation from a livecd....I don't think that's possible or I'm wrong?

any how how do I fix the bad fuse in the modules file

thanks

---

### Post by Mia_tech on 2008-04-11
by the way the first thing I'm doing is create an image of my hard drive with dd_rescue... :0)

thanks

---

### Post by Mia_tech on 2008-04-11
ok after doin a bit of googling around I found that fuse acts as an interface between the filesystem you wish to mount and the kernel...

---

### Post by ibuclaw on 2008-04-11
Hi, Sorry for my lateness.

Good. I'm glad it's fixed.
For more information of fuse, [read here.]("http://fuse.sourceforge.net/")
Whether or not it's a required module, is debatable, but it looks like an important feature.

Now that your system boots, I would recommend looking an update of fuse (or try downgrading it to it's previous version).

Open up synaptic. Click "Search". Choose to Look in the "Names". And type in "fuse".
Then click on the left-most tab to display all installed packages together.
[[IMG]http://img255.imageshack.us/img255/4560/screenshotsynapticpackags6.th.png[/IMG]](http://img255.imageshack.us/my.php?image=screenshotsynapticpackags6.png)

Try upgrading it, if an upgrade is there.
If not, click on the package and open up "Package" in the menu bar. If "Force-Downgrade" is greyed out, then you can't downgrade it.

So I would leave it uncommented in you /etc/modules file for the next few days.
File a bug at Launchpad. Then wait for an update of fuse to come through.

Other than that, there's not much else you can do at the moment.

But, as Hardy is no more than a fortnight round the corner. The issue will most probably be fixed as soon as you switch.

[EDIT]
I'm sure I've seen it work before. And it makes sense in my mind when I think it through logically. As using chroot to change the "/" root hierachy from that of the LiveCD to that of your Linux Partition, then you will get back all your programs and commands-line tools via LiveCD. Give me a minute to re-try this.

Regards
Iain

---

### Post by ibuclaw on 2008-04-11
Just thought that I might just confirm that upgrading your Distribution in LiveCD mode **does** work.

Here's how I did mine
```

# Now, I've just opened a terminal in the LiveCD
ubuntu@ubuntu:~$
# made a directory in media folder.
ubuntu@ubuntu:~$ **sudo mkdir /media/linux**
# mounted the root partition to the folder
ubuntu@ubuntu:~$** sudo mount /dev/sdb1 /media/linux**
# mounted my home folder to home in my root partition.
ubuntu@ubuntu:~$** sudo mount /dev/sdb3 /media/linux/home**
# chroot'd from the LiveCD to my Linux Installation
ubuntu@ubuntu:~$ **sudo chroot /media/linux**
# changed to my administrator account in Ubuntu. No password was needed.
root@ubuntu:/#** su administrator**
# Now I change to the home directory.
administrator@ubuntu:/$ **cd**
# And display my home directory.
administrator@ubuntu:~$** ls**
[I]Desktop    mbox                    packages    savelist
Documents  memory                  Pictures    Templates
E-Port  Music                   Public      Videos
Examples   nautilus-debug-log.txt[/I]

# I go into aptitude. 
administrator@ubuntu:/$** sudo aptitude**
# This generates a small LiveCD related error.
*sudo: unable to resolve host ubuntu*
# Now it asks for my password
*[sudo] password for administrator: *
# And I am able to update and upgrade my System!
# I won't display it all. But here is the last of it. I did a kernel upgrade.
[I]Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
cat: /proc/cmdline: No such file or directory
cryptsetup: WARNING: found more than one resume device candidate:
                     /dev/sdb6
                     UUID=196d1243-5322-47f6-a969-db99c7064a0d
Press return to continue.[/I]

# I'll now exit my user, since there's nothing more to do.
administrator@ubuntu:~$ **exit**
*exit*
# And by exiting again, chroot is unloaded and We are back to the LiveCD.
root@ubuntu:/# **exit**
*exit*
# Change directory back to LiveCD Home.
ubuntu@ubuntu:~$ **cd**
# And display the LiveCD contents.
ubuntu@ubuntu:~$** ls**
*Desktop  Documents  Music  Pictures  Public  Templates  Videos*
ubuntu@ubuntu:~$ 

```
And when I reboot, I **expect** to see a new line in my GRUB Menu.

Though I will report if I don't

Regards
Iain

---

