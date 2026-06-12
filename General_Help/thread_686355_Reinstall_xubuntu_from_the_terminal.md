---
title: "Reinstall xubuntu from the terminal?"
date: 2008-02-03
forum: General Help
---

### Post by sumsa on 2008-02-03
My installation of xubuntu isn’t going that well. 

The resolution is wrong, I have tried using the graphics and display to alter the resolution to 1024x768 16 bit, but it will only use 800x600. I tried altering the xorg.conf file, forcing it into 16 bit mode, but to no avail. 

The toolbar doesn’t show up half of the times I reboot. I have to run xfce4-panel manually which usually brings up the toolbar, but not all the time.

After setting up the connection manager to automatically be assigned from the DHCP server from my wired connection to my rooter, I ping google, everything seemed to work.. but then I restarted the computer and now I  get a warning message every time I log in saying

Could not look up internet address for (none),
This will prevent Xfce from operating correctly.
It may be possible to correct the problem by adding 
(none) to the file /etc/hosts on your system.

So after looking at the forum I tried to pico the /etc/hosts which is empty except for an comment. I hesitate to write anything here because I don’t think adding-> “10.0.0.1 localhost (none)” will correct the problem.
Xfce is so slow.. I tried using the connection manager to alter the configuration, I can ask it to activate the wired connection, but if I quit the manager it deactivates itself. 

On the lighter note the terminal works fine, in recovery mode that is =)

I was thinking about reinstalling xubuntu from scratch or going for another distro of Linux

I don’t have an internal cdrom drive but I have a USB cd drive, this means I cannot simply boot my computer with any live disk on it since it will fail to launch form the bios.  So my question is, is it possible to reinstall xubunto via a command from the terminal (something like “apt-get reinstall xubuntu”) 

Or can I copy the CD onto the harddisk and configure grub to start it up?

---

### Post by solar george on 2008-02-03
For the hosts isssue /etc/hosts should contain
```
127.0.0.1 localhost
127.0.1.1 *HOSTNAME*

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Where *HOSTNAME* is the hostname in /etc/hostname

You may be best just reinstalling.

---

### Post by sumsa on 2008-02-03
My rooter is configured to  assign Ip adresses in the range 192.168.0.2-255 via  NAT. I dont have a domain name.

should i still use 127.0.0.1?

---

### Post by solar george on 2008-02-03
> My rooter is configured to assign Ip adresses in the range 192.168.0.2-255 via NAT. I dont have a domain name.
You will still have a hostname - that is just the name of your computer look at
```
less /etc/hostname
``` that will give you your hostname - if there is nothing there just edit it to include a name that you have made up - ubuntu - is the default

> should i still use 127.0.0.1?
Yes this is the loopback - it always refers to your own computer.

---

### Post by sumsa on 2008-02-03
less /etc/hostname turned up empty .. so i've edited it to contain the name - a -

then added the name to /etc/hosts 
so it looks like this:

127.0.0.1 localhost
127.0.1.1 a

now the error message has changed to 
could not look up adress for ,
this will.....

---

### Post by solar george on 2008-02-03
Reinstall

---

### Post by sumsa on 2008-02-03
Lol... thx fot the anwser 
That really brings me back to my first question... 
since i cant boot with cd-rom support because of an older computer with external USB cd drive, 
is there a way to reinstall from the terminal?
or should i try to copy the xubuntu cd to the hd and then use grub to load it?

---

### Post by solar george on 2008-02-03
If you don't mind using the text menu based installer then you could try this (I always use this method),

[COLOR="Red"][SIZE="5"]>>>>Remember to backup your data first this will wipe your harddisk<<<<[/SIZE][/COLOR]

Download the linux and initrd files to your / directory,
```
cd /
sudo -s
wget http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/linux
wget http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/initrd.gz
```

Setup grub to boot from these files,
```
nano /boot/grub/menu.lst
```
Look for an entry like,
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
**root            (hd0,2)**
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=abb5e602-801e-4a53-a22e-ae717662db75 ro splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```
and remember what is on the line starting root.
Add an entry above the ### BEGIN AUTOMAGIC KERNELS LIST line
```
title Network install
**root            (hd0,2)**
kernel             /linux
initrd              /initrd
boot

```
Making sure you change the line in bold to match the one in your other root line.

Reboot into the Network install option (press esc to get to the menu)

Go through the installer (this will download all the files it needs as it goes along) and select the "Xubuntu desktop" option from the select and install software menu.

Reboot into your new xubuntu installation

---

### Post by sumsa on 2008-02-03
Wow.. This is absolutely fantastic help.. You practically spelled it all out for me!. Thank you so much! I&#8217;ll get to it right away!

---

### Post by dgray_from_dc on 2008-02-27
I have the *_[COLOR="Blue"]Could not look up internet address for . . .[/COLOR]_* problem too.

The solution didn't quite work for me though.  My /etc/hosts file had my hostname in it with a domain attached to it.  I added another line without the domain name and it cleared up.

```

127.0.0.1  host.domain host.DOMAIN
127.0.0.1  host                     <-----------------added

```

I'm posting here in the hope this helps someone.

---

### Post by Jerry N on 2008-02-27
In reference to the Xubuntu resolution problem:  In working with an older computer I had to change the depth in xorg.conf from 24 to 16 and I added the following two lines in the "monitor" section:
   Horizsync   30-70
  Vertrefresh 50-160

After reboot, this gave me a much wider choice of resolutions

Jerry

---

