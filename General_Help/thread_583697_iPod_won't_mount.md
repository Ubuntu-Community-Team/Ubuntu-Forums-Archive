---
title: "iPod won't mount"
date: 2007-10-20
forum: General Help
---

### Post by Old Pink on 2007-10-20
[img]http://img145.imageshack.us/img145/323/screenshotgnomemountef1.png[/img]

Just started randomly. Tried rebooting both devices, and putting the iPod in disk mode. No luck.

dmesg | tail:> [  269.276000] sda: assuming drive cache: write through
[  269.288000] SCSI device sda: 14651280 2048-byte hdwr sectors (30006 MB)
[  269.292000] sda: Write Protect is off
[  269.292000] sda: Mode Sense: 68 00 00 08
[  269.292000] sda: assuming drive cache: write through
[  269.292000]  sda: sda1 sda2
[  269.328000] sd 1:0:0:0: Attached scsi removable disk sda
[  269.328000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[  270.808000] FAT: Unrecognized mount option "usefree" or missing value
[  292.412000] spurious 8259A interrupt: IRQ15.

---

### Post by Old Pink on 2007-10-20
Tried on an old XP computer, works fine.

---

### Post by DagonX on 2007-10-20
I have the same problem with Gutsy X32. The IPOD does mount without problems ih Gutsy X64. Is there a bug in Gutsy X32?

---

### Post by Old Pink on 2007-10-21
This only happens in the 2.6.20-16 kernel.

In the newer one it's fine, but I need to use the old one in order to get Gutsy to see my laptop battery. :(

---

### Post by Old Pink on 2007-10-21
Launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/155436](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/155436)

---

### Post by eosyn on 2007-10-21
I get the same problem on  2.6.22-14-generic. It seems that whatever the system is for automounting usb storage is failing to run properly (and not logging any errors @%^). I did..

mkdir /media/ipod
mount -t vfat /dev/sdb1 /media/ipod

and it mounted fine, so thats not a problem. Just no program picks up the new drive and mounts it automatically


Bleh

---

### Post by Perpetual on 2007-10-21
I just tested my Ipod for the first time on Gutsy and it mounted fine and launched Exaile (as I configured it to for this type of device).  Not sure why it wouldn't work for others.  

Did you upgrade to Gutsy or clean install?

---

### Post by eosyn on 2007-10-21
This is a clean instal. I also notice that actually none of my drives (cdrom, storage) will automount and since I just checked back, I see refrences to 'nothing automounts in gutsy'

so were not alone!

---

### Post by Neovos on 2007-10-21
Same exact pop up error (cannot mount volume), same dmesg output

```

[20658.502914] usb-storage: device scan complete
[20658.503411] scsi 10:0:0:0: Direct-Access     Apple    iPod             2.70 PQ: 0 ANSI: 2
[20658.504886] SCSI device sde: 495616 2048-byte hdwr sectors (1015 MB)
[20658.505505] sde: Write Protect is off
[20658.505510] sde: Mode Sense: 64 00 00 08
[20658.505514] sde: assuming drive cache: write through
[20658.507127] SCSI device sde: 495616 2048-byte hdwr sectors (1015 MB)
[20658.507748] sde: Write Protect is off
[20658.507753] sde: Mode Sense: 64 00 00 08
[20658.507756] sde: assuming drive cache: write through
[20658.507760]  sde: unknown partition table
[20658.531981] sd 10:0:0:0: Attached scsi removable disk sde
[20658.532047] sd 10:0:0:0: Attached scsi generic sg6 type 0
[20659.071390] FAT: Unrecognized mount option "usefree" or missing value

```

and this is on gutsy (just updated from feisty) running 2.6.20-15-generic with an ipod shuffle.

I manually mounted as said by eosyn and it worked for me as well also. But I've been able to auto mount external hard drives and cd's so far without problem so it's not an automount issue, for me at least. Looking at the dmesg output, it seems like that "usefree" option is in some config file somewhere and needs to be taken out. I wouldn't know where to look though, maybe fstab?

---

### Post by Old Pink on 2007-10-22
Everyone please comment with your experiences and errors (inc. dmesg | tail) on the launchpad page aswell, should help this get fixed sooner.

Interesting to see you can manual mount (apparently) and that it does happen with other devices.> **Old Pink said:**
> Launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/155436](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/155436)

---

### Post by DagonX on 2007-10-22
In reference to the post by Bleh

I get the same problem on 2.6.22-14-generic. It seems that whatever the system is for automounting usb storage is failing to run properly (and not logging any errors @%^). I did..

mkdir /media/ipod
mount -t vfat /dev/sdb1 /media/ipod

and it mounted fine, so thats not a problem. Just no program picks up the new drive and mounts it automatically


Bleh

When I execute sudo  mount -t vfat /dev/sdb1 /media/ipod I get the same error as when I plug the IPOD in.

Charles aka Dagon

---

### Post by Alpensepp on 2007-10-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/155436](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/155436) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi.

I got the same Problem with an USB-Memory-Stick

It seems as if the old Kernel doesn't know "usefree"

So i started "sudo gconf-editor" in a Terminal and erased the "usefree" option in

System - storage - default_options - vfat -- mount_options

and it works fine now :)


sepp

---

### Post by Old Pink on 2007-10-25
>            [FONT=monospace]Unfortunately the method Alpensepp posted didn't fix the problem for me, with dmesg still showing:
 [  161.472000] FAT: Unrecognized mount option "usefree" or missing value
 Maybe I need to remove it elsewhere? I'll investigate further. Glad to see we're making progress on this.
[/FONT]
              


Let me know if this works (or doesn't) for you. And remember to check/update the [launchpad page](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/155436). 

Hopefully this works as a fix and I'm doing something wrong, or at least puts us on the right track to finding a fully working fix. 

I'm yet to try a USB stick. I'll give it a shot now.

---

### Post by Old Pink on 2007-10-25
USB sticks don't work either. 

Removing "usefree" from:  "System - storage - default_options - vfat -- mount_options" in sudo gconf-editor

Does nothing.

---

### Post by Old Pink on 2007-10-25
... and why would it? It's sudo! It's only going to affect the root.

So, to fix this:
[LIST=1]
[*]Run gconf-editor as a user, NOT in sudo
[*]Click into sytem > storage > default_options > vfat on the left folder menu
[*]Right click the "mount_options" key on the right and choose "Edit Key"
[*]An "Edit Key" dialogue will appear. Highlight "usefree" by clicking it, and hit "Remove"
[*]Click "OK" and close the gconf-editor
[*]Insert the device of your choice.[/LIST]

---

### Post by Old Pink on 2007-10-25
OK, final fix uploaded. 

See launchpad page: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/155436](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/155436)

You basically have two fix options:

Download [this file](http://launchpadlibrarian.net/10169796/%25gconf.xml) and put it in "/home/USER/.gconf/system/storage/default_options/vfat" overwriting the current file.

**OR**

Download and run [this .sh script](http://launchpadlibrarian.net/10169832/fix.sh) which will backup your current configuration and replace it with the working configuration, therefore fixing your system and allowing you to undo the changes.

---

### Post by Alpensepp on 2007-10-25
Hey.. sorry.. the sudo was a mistake made by me... :KS

i was a little too quick writing... 

sepp

---

### Post by bluehue on 2007-10-29
> **Old Pink said:**
> OK, final fix uploaded. 

See launchpad page: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/155436](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/155436)

You basically have two fix options:

Download [this file](http://launchpadlibrarian.net/10169796/%25gconf.xml) and put it in "/home/USER/.gconf/system/storage/default_options/vfat" overwriting the current file.

**OR**

Download and run [this .sh script](http://launchpadlibrarian.net/10169832/fix.sh) which will backup your current configuration and replace it with the working configuration, therefore fixing your system and allowing you to undo the changes.
Here's the output I got after running your script:
```

spiral@spiral-desktop:~/Desktop$ sh fix.sh
cd: 1: can't cd to /home/spiral/.gconf/system/storage/default_options/vfat
mv: cannot stat `%gconf.xml': No such file or directory
--12:04:02--  http://launchpadlibrarian.net/10169796/%25gconf.xml
           => `%gconf.xml'
Resolving launchpadlibrarian.net... 91.189.90.235
Connecting to launchpadlibrarian.net|91.189.90.235|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 720 [text/plain]

100%[====================================>] 720           --.--K/s             

12:04:03 (47.61 MB/s) - `%gconf.xml' saved [720/720]

spiral@spiral-desktop:~/Desktop$
```
Problem is that the directory "/home/USER/.gconf/system/storage/default_options/ vfat" does not exist for me. These are the contents within my /.gconf directory:
```

spiral@spiral-desktop:~/.gconf$ ls -l
total 12
drwx------ 14 spiral spiral 4096 2007-10-29 11:28 apps
drwx------  3 spiral spiral 4096 2007-10-28 13:44 desktop
drwx------  3 spiral spiral 4096 2007-10-28 23:45 GNOME

```Notice that I do not have a "system" folder nor any of the other subdirectories for that matter. Each of the above directories does contain a "%gconf.xml" file however. Is there anywhere else I should place the modified "%gconf.xml" by any chance? I'm having the mounting problem with a 3rd gen. Ipod btw.

---

### Post by bluehue on 2007-10-30
Well, after using the gconf-editor the directory "/.gconf/system/storage/default_opti ons/ vfat" was created. I then successfully ran Old Pink's fix.sh script:
```

spiral@spiral-desktop:~$ cd ~/Desktop
spiral@spiral-desktop:~/Desktop$ sh fix.sh
--12:28:23--  http://launchpadlibrarian.net/10169796/%25gconf.xml
           => `%gconf.xml'
Resolving launchpadlibrarian.net... 91.189.90.235
Connecting to launchpadlibrarian.net|91.189.90.235|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 720 [text/plain]

100%[====================================>] 720           --.--K/s             

12:28:23 (46.25 MB/s) - `%gconf.xml' saved [720/720]

spiral@spiral-desktop:~/Desktop$
```My Ipod, however, only auto-mounts if it is detected at start-up after shutting  down the system. If I plug it in after the system has booted, then it no longer auto-mounts. I'm connecting via firewire, however, not usb.

---

### Post by misterbeetz on 2007-10-30
> **bluehue said:**
> 
]My Ipod, however, only auto-mounts if it is detected at start-up after shutting  down the system. If I plug it in after the system has booted, then it no longer auto-mounts. I'm connecting via firewire, however, not usb.

I also have a firewire ipod and have this same issue except my external USB hard drive is also doing the same thing.

I dunno what commands to use to troubleshoot this though so any help would be greatly appreciated.

- misterbeetz

---

