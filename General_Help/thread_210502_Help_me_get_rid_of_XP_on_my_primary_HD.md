---
title: "Help me get rid of XP on my primary HD"
date: 2006-07-07
forum: General Help
---

### Post by words1 on 2006-07-07
I have two hard drives in my PC, set up as dual-boot with XP (sda) and 6.06 (sdb), each 80 gigs.  I want to erase XP entirely from sda and use it for storage, converting the PC to Ubuntu-only.

1. How do I do this?  

2. How do I modify (or turn off) Grub so it just boots straight into linux?

3.  I have XP mounted at start-up so I can access files from within Ubuntu.  How do I disable that when XP is gone?

4.  How do I make sure I can read and write to sda after I get rid of XP?

Thanks.

---

### Post by Ptero-4 on 2006-07-07
1) Just unmount and format sda from within linux.

2) just type ```
sudo update-grub
``` and grub will recognize the absence of Windoze.

3) just change the filesystem for your XP drive in /etc/fstab.

4) linux will use it's filesystem and will be able to read/write easy.

---

### Post by jocko on 2006-07-07
**Get rid of windows:**
you can delete the partition it is installed to and create a new partition in it's place. There are probably many different programs for doing this, but the one I prefer to use is gparted. You can get it through synaptic, or by running 'sudo apt-get install gparted' in a terminal. You'll get a link to the program in System/Administration.
Use it to delete the partition windows is installed to (in your case I guess it is sda1) and create a new ext3 partition. Read the manual or ask people in the forums if you need help on using gparted.

**Modify grub:**
```
sudo gedit /boot/grub/menu.lst
```

1. Remove windows from the boot menu:
Find the section looking like this (the bottom of the file):
```
### END DEBIAN AUTOMAGIC KERNELS LIST

[COLOR="Blue"]title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1[/COLOR]
```
Delete the lines I have indicated with blue text.

2. Hide the boot menu:
Find this section (close to the top):
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Blue"]timeout		30[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Blue"]# hiddenmenu[/COLOR]
```
Remove the "# " in front of "hiddenmenu" and change the timeout value to a low number (I suggest 3 sec., shorter time may make it difficult to access the boot menu if you need to some day...)

[B]Getting access to the harddrive (I assume you created a new ext3 partition):
[/B]
You'll need to create a mount point:
```
sudo mkdir /media/[COLOR="Blue"]sda1[/COLOR]
``` (sda1 is just my example, name it whatever you like)
Now you need to add a line to /etc/fstab in order to automatically mount this partition at boot:
```
sudo gedit /etc/fstab
```
Add a new line looking like this:
```
/dev/sda1       /media/[COLOR="Blue"]sda1[/COLOR]    ext3    defaults        0       2
```
If there already is a line containing "/dev/sda1", put a # in front of it (or delete it).
See that it works by running "sudo mount -a" in a terminal.

Hope this gets you started!

---

### Post by words1 on 2006-07-07
Excellent!  That seems to have worked perfectly.  Thanks!

The only problem is that I need to have write access to that disk -- how do I do that?

---

### Post by aysiu on 2006-07-07
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by words1 on 2006-07-07
Excellent -- thanks.  I just substituted /media/sda1 for the /storage in the tutorial.  Is there a reason to do it in /storage?  

Also -- is there a way to prevent an sda1 icon from showing up on my desktop?

---

### Post by aysiu on 2006-07-08
I can answer both questions at once--when you mount something in the /media folder, it'll show up on your desktop.

---

### Post by words1 on 2006-07-08
Gotcha.  Thanks.

---

