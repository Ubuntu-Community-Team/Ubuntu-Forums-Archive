---
title: "cannot delete files (read only file system)"
date: 2018-01-10
forum: General Help
---

### Post by jgw on 2018-01-10
I have two files.  They were originally owned by root.  I changed that and now the files look like (from disks):
drwxr-xr-x  3 greg greg    4096 Jan 10 12:51 snap
drwxr-xr-x 17 greg greg    4096 Jan 10 10:45 snapd


I tried to remount them but were told they were busy.  I have no idea what they are doing and 
When I try and delete them, using sudo or su, I am told that they are in a read-only file system
I also failed to change the ownership of those files that are read only 

I finally figured out how to get rid of the files and then I did a search for 'snap' and 'snapd' it seems that there are a LOT of files (snap or 'snapd' included in name.  I think these were already on my machine so I won't delete unless somebody tells me to do that. 

All this occurred when I decided to by a cheap endoscope and see if it would run on my machine - BAD mistake!  I think, however, that I have stopped and deleted all the offending machine.

Now, I wonder if anybody could tell me if I am in trouble.  As far as I know my machine is running without a problem but I get a bit antsy when I do something obviously not good <G>

---

### Post by TheFu on 2018-01-10
The file system is read-only. Nothing on it can be changed. That's sorta the point of a read-only file system.

This happens for a few reasons. If you didn't do it on purpose, then those reasons usually aren't good.  Check the log files, see what shows up as errors or warnings.  I assume you rebooted it and the read-only has come back. I've seen it for a bad sata cable or failing disk controller.

Would be smart to check the SMART tests for the HDD too.

The OS moves a file system from read-write to read-only when it sees bad things are possible, like data corruption.

---

### Post by jgw on 2018-01-12
I was able to deal with it.  I did it with sudo nautilus and then changed ownership, and permissions, of all the files involved.  Then I had to move them out of the trash. Those that were running I killed.  Took me a while but, finally, it got done.  I was a bit of a pain <G>

---

### Post by cruzer001 on 2018-01-12
Not a good idea to " sudo nautilus", better to "sudo -H nautilus".

---

### Post by TheFu on 2018-01-12
> **cruzer001 said:**
> Not a good idea to " sudo nautilus", better to "sudo -H nautilus".

Yep. May have made some config files owned by root, which will cause issues doing that.

---

### Post by DuckHook on 2018-01-12
> **cruzer001 said:**
> Not a good idea to " sudo nautilus"&#8230;&#8593;&#8593;&#8593;+1

The "official" way to invoke root nautilus is to install the following:```
sudo apt install nautilus-admin
```&#8230;which installs the Policy Kits for both nautilus and gedit. This will give you root nautilus and also root gedit. It is invoked with:```
pkexec nautilus
```&#8230;or:```
pkexec gedit
```Alternatively, you now get a new right-click menu option in regular nautilus which allows you to open a root nautilus or root gedit.

A word to the wise: I've found that it is not a good idea to use *any* GUI app as root even if this functionality can be enabled. This is because I have run into problems mistaking a root file manager which was carelessly left open for a regular one and causing myself immense grief. Therefore, I find it better to monkey around with root only in the command line. If new users want some pseudo-graphical hand-holding, then consider Midnight Commander in root mode:```
sudo apt install mc
``````
sudo mc
```

---

### Post by cruzer001 on 2018-01-12
> want some pseudo-graphical hand-holding, then consider Midnight Commander in root mode

I'll drink to that; even has dual pane :D

---

### Post by sudodus on 2018-01-14
You can run GUI programs in 17.10 with Xorg with elevated permissions with

```
sudo -H gui-program
```

But it does not work in Wayland, which is designed to only allow text mode programs with elevated permissions (for security reasons). In other words, the developers of Wayland (and many other people too) think that *it is a good idea to use text mode programs for tasks that need elevated permissions.*

There is a workaround, that works in many cases, for example with Nautilus and Gedit,

```
xhost +si:localuser:root
sudo -H gui-program
```

This is described with more details at this link,

[Why don't gksu/gksudo or launching a graphical application with sudo work with Wayland?](https://askubuntu.com/questions/961967/why-dont-gksu-gksudo-or-launching-a-graphical-application-with-sudo-work-with-w/96xhost +si:localuser:root1978#961978)

---

### Post by cruzer001 on 2018-01-14
Thats good info on wayland.  I will be taking the dive in a few months.  Thanks

---

### Post by DuckHook on 2018-01-15
> **sudodus said:**
> …There is a workaround, that works in many cases…This is described with more details at this link…
Thank you so much for this sudodus.

At the risk of digressing a little, I'm of two minds about the direction that Wayland devs have chosen:

[LIST=1]
[*]This forum is filled with hundreds, maybe thousands, of identical recurring problems from new users who bork their systems because they did a:```
sudo nautilus
```A big part of me gets why the devs said: "we will not tolerate any more monkeying around with sudo and graphical apps." As helpers on these forums, it will make our lives a lot easier not having to dig unsuspecting victims out of such messes.
[*]However, the bigger part of me is really irritated that we are prohibited from doing some really useful things. *gparted* is a good example of a highly useful app that will be nerfed. There's no other app like it, and even though *parted* is very powerful, this is one area where a graphical representation is far superior to the numerical obscurity of the CLI.
[/LIST]
Thanks for giving me *gparted* back.

---

### Post by sudodus on 2018-01-15
You are welcome, Duckhook :-)

I agree that ***gparted*** is a good tool. ***Synaptic*** is another good GUI tool, that needs elevated permissions.

---

### Post by cruzer001 on 2018-01-15
This has me wondering about "sudoers" and how well it will play with wayland.

---

### Post by sudodus on 2018-01-15
I think ```
xhost +si:localuser:root
``` is the main difference for running with elevated permissions in Wayland. A second thing is that gksu and gksudo do not work.

I think (but am not sure) that "sudoers" will play like before (in Xorg).

---

