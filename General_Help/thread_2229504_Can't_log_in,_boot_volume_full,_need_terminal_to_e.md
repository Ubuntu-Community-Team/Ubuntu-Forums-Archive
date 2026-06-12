---
title: "Can't log in, boot volume full, need terminal to edit and fix kernels"
date: 2014-06-13
forum: General Help
---

### Post by sewbiz on 2014-06-13
Is it too late for me? I had to boot my computer with Grub2 disc I downloaded from website and
uploaded onto a usb drive. (Against my rules...should always use synaptic.)
Is there more I need to do with it? I can't log in to get to the terminal and type in the command
line. "Login failed". I read the tutorial on ibm.com

I need the terminal to remove kernals so more space can be had on my Boot partition.
I am fairly new at this but have been doing some research. Is there a way I can get in.
Had warning messages that the boot volume was getting full...removed programs, etc. 
and for a couple days the message went away...thought I fixed it. Nope, then it finally
did not let me even do the boot. : (   Please help or let me know the bad news.

Will installing more boot programs do the fix? Clueless!

---

### Post by Impavidus on 2014-06-13
Can you boot an older kernel, or boot into recovery mode? If you can manage, run these commands and show us the output:```
df -h
ls /boot
dpkg --list linux-image*
```Else you'll need a live disk and chroot into your install.

---

### Post by sewbiz on 2014-06-13
Failed to load session "ubuntu" is the error message I get after the boot....I can't log in to get to a terminal. : (

---

### Post by sewbiz on 2014-06-13
> **Impavidus said:**
> Can you boot an older kernel, or boot into recovery mode? If you can manage, run these commands and show us the output:```
df -h
ls /boot
dpkg --list linux-image*
```Else you'll need a live disk and chroot into your install.


Can I get a terminal on a windows OS...using daughter's laptop....and then somehow upload a command to a usb then to my computer?  Hopeful.

---

### Post by sewbiz on 2014-06-13
How to make a command without a terminal? I can't get beyond the log in page.

---

### Post by sewbiz on 2014-06-13
Ok...so I have at least a black GUI screen (is that the term) and could put in some commands, and when I did ls /boot initially it ran quite a while and filled my screen with a lot of information. When I entered these last commands you gave me "as you have them written...3 separate lines....I get no response.

---

### Post by sewbiz on 2014-06-13
It tells me....after I clicked "TAB"....
Display all 121 possibilities? (y or n)......I then typed in y.
Now what....perplexed....been at this all day! Welcome to UBUNTU world of Linux or vice versa. I am new at this, can you tell?

---

### Post by Impavidus on 2014-06-13
OK, you found the console using ctrl-alt-Fsomething and it works. When ready, you can return to the graphical login page with ctrl-alt-F7. The fact that ls /boot gave a lot of ouput suggests that a full boot partition could indeed be the problem.

Go to the console, login with your username and password, and type this command, followed by enter:```
df -h
```It will show a list of all your file systems. If your boot partition is full, the line belonging to the boot partition will show 100% (or something close to that). I'd like to see that line.

Not being able to login is not a typical symptom of a full boot partition, so there may be something else going on (too).

The command```
dpkg --list linux-image*
```(mind the * at the end of the line) should give you a list of all installed or partially installed kernels. I like to know how many there are.

I've got no idea what you had typed before you hit tab.

By the way, which Ubuntu version are you running?

---

### Post by sewbiz on 2014-06-13
I did finally get a terminal on my screen and don't ask me how. I think because I had a usb in with Grub2 on it and Ubuntu Tweak. The terminal comes up automatically after I type in my password, yet my hidden password stays on the screen and nothing opens up.
I did the command you said already and I have a TON of old kernals. NO WONDER....but not being successful removing anything because
it tells me it can't find them.

---

### Post by sewbiz on 2014-06-13
I am running Ubuntu 12.04 LTS

---

### Post by sewbiz on 2014-06-13
I have 33 linux-image-3 kernels on the list.

---

### Post by sewbiz on 2014-06-13
I get error message: E: Unable to locate package
                               E: Regex compilation error - invalid content of \{\}
                               E: Couldn't find any package by regex

I don't know what regex is or means...but wonder if it is on the Grub2 or Ubuntu Tweak thing. Was I suppose to configure them?

---

### Post by yancek on 2014-06-13
If you have the Ubuntu Live DVD or installation medium you used to install Ubuntu, you could boot that then open a terminal and mount your boot partition.  You haven't indicated which partition it is so it's not possible to be any more detailed.  Once you have done that, if you are more comfortable using a file manager open a terminal and type:  sudo nautilus
That should open the file manager and you can go to the mounted /boot partition and delete what you want.

---

### Post by sewbiz on 2014-06-13
I am getting 3 error messages that I can't figure out...after reading pkg lists, building dependency tree, reading stateinfo, note selecting..

E: Unable to locate package
E: Regex compilation error-Invalid content of \{\}
E: Couldn't find and package by regex

I don't know what regex is...could it be something on those things I put on my usb drive? (Grub2 or something in Ubuntu Tweak)
Maybe something in there needs to be configured...I did nothing to them...did the download and saved to the usb.

---

### Post by steeldriver on 2014-06-13
What is the exact command you are typing that produces the errors?

---

### Post by sewbiz on 2014-06-13
I have the live DVD but I don't want to install it and have it overwrite things I didn't save. I didn't have a chance to find a fix before it was too late and my boot volume was full. Also...the disc is a different version....earlier.
where is the mounted/boot partition? In the boot folder...then...I have abi. ,config., initrd.img, memtest,system map,vmcoreinfo,vmlinuz, kernals......what are they and which are important? Also in the grub...a ton of music....  .mod  kernals.  : (
I don't see anything about a partition.

---

### Post by sewbiz on 2014-06-13
The errors come up after I try to remove the kernels. YOu would have to go to the beginning of this thread. My boot volume 100% full....couldn't reboot (fixed with Grub2 disc manually)...getting further...didn't have terminal (fixed..not sure how/maybe Grub2 helped)...yet still can't login to my program....got to remove all the stuff so there is room in the boot.

I might be typing something wrong, but my gut tells me it has more to do with config. the Ubuntu Tweak or finding out what regex is...what is REGEX anyway?

---

### Post by sewbiz on 2014-06-13
Yancek had the best idea yet....I like nautilis and file manager...but don't want to remove something I should keep. Will wait for answers to my questions about the "extensions" definitions.

---

### Post by Impavidus on 2014-06-14
You can use the live disk to fix your system. It won't reinstall Ubuntu and wipe your files unless you tell it to do so. Just run the live session. It doesn't matter if it's an older version of Ubuntu. Not too old, but I think a 10.04 live disk should still work.

In Nautilus, running from the live disk, you should see a list of partitions on your system on the left side of window. One of them must be the /boot partition of your installed Ubuntu, but it may not have an obvious label. You may have to find out by looking at the contents. Mount it by clicking and remove some old kernels. Keep at least a few of the kernels with recent version numbers. It's not the cleanest way of solving this, but it's the easiest way.

Next you have to reboot without the live disk and boot into recovery mode. Select recovery mode from the grub menu. It may be hidden in the advanced options submenu. At the next menu, choose to fix packages. This will run some default commands to fix your packages. Hopefully your computer will then work again. If so, boot and login in the normal way and uninstall the old kernels using synaptic.

There is one alternative. You can use a different computer to create a 14.04 live disk and then boot from that. You should be able to access your hard drive from the live session. Make backups of all vital files to an external drive, disconnect the external drive with the backups and do a clean install of 14.04

---

