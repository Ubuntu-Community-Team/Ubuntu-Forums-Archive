---
title: "Useful Linux Commands"
date: 2008-07-01
forum: General Help
---

### Post by unseend on 2008-07-01
[SIZE="2"]I think the following commands will be a usefull reference for future use and maybe a &#8220;cheat-sheet&#8221;. I list them in categories for easier access. If you have any suggestions, questions, want to correct something or want to add a command, feel free to comment below or @ my blog ([http://unseend.wordpress.com/2008/07/01/useful-linux-commands/](http://unseend.wordpress.com/2008/07/01/useful-linux-commands/)).
[B]
Networking Commands:[/B]

    * [COLOR="DarkRed"]ethtool eth0[/COLOR] Shows status of ethernet interface eth0.
    * [COLOR="DarkRed"]iwconfig eth1[/COLOR] Shows status of the wireless interface eth1.
    * [COLOR="DarkRed"]iwlist scan[/COLOR] Lists all wireless networks in range.
    * [COLOR="DarkRed"]ip route show[/COLOR] Lists routing table.
    * [COLOR="DarkRed"]netstat -tupl[/COLOR] Lists internet services on a system.
    * [COLOR="DarkRed"]netstat -tup[/COLOR] Lists active connections to/from a system.
    * [COLOR="DarkRed"]hostname -i[/COLOR] Shows localhost IP.
[B]
Windows Networking Commands (Samba):[/B]

    * [COLOR="DarkRed"]smbtree[/COLOR] Lists all Windows machines in a network. (See also findsmb)
    * [COLOR="DarkRed"]smbclient -L[/COLOR] windows_box Lists shares on windows machine or samba server.
    * [COLOR="DarkRed"]mount -t smbfs -o fmask=666,guest //windows_box/share /mnt/share[/COLOR] Mount a windows share.
    * [COLOR="DarkRed"]nmblookup -A 1.2.3.4[/COLOR] Finds the Windows (netbios) name associated with IP address.
[B]
Secure Shell (SSH):[/B]

    * [COLOR="DarkRed"]ssh $USER@$HOST command[/COLOR] Runs command on $HOST as $USER.
    * [COLOR="DarkRed"]ssh -g -L 8080:localhost:80 root@$HOST[/COLOR] Forwards connections to $HOSTNAME:8080 out to $HOST:80.
    * [COLOR="DarkRed"]ssh -R 1434:imap:143 root@$HOST[/COLOR] Forwards connections from $HOST:1434 in to imap:143.
[B]
Archives and Compression:[/B]

    * [COLOR="DarkRed"]gpg -c file[/COLOR] Encrypts a file.
    * [COLOR="DarkRed"]gpg file.gpg[/COLOR] Decrypts a file.
    * [COLOR="DarkRed"]cat /boot/grub/menu.lst > ~/Desktop/bootmenu[/COLOR] Outputs the contents of your boot menu to a file on your desktop. (The > will output the contents of cat to a file in the specified location)

**CDs:**

    * [COLOR="DarkRed"]gzip < /dev/cdrom > cdrom.iso.gz[/COLOR] Saves a copy of a data cd-rom.
    * [COLOR="DarkRed"]mkisofs -V LABEL -r dir | gzip > cdrom.iso.gz[/COLOR] Creates cd-rom image from contents of a dir.
    * [COLOR="DarkRed"]mount -o loop cdrom.iso /mnt/dir[/COLOR] Mounts the cdrom image at /mnt/dir (read only).
    * [COLOR="DarkRed"]cdparanoia -B[/COLOR] Rips audio tracks from CD to wav files in current dir.
    * [COLOR="DarkRed"]oggenc --tracknum='track' track.cdda.wav -o 'track.ogg'[/COLOR] Makes ogg file from wav file.
[B]
Disk Usage/Space:[/B]

    * [COLOR="DarkRed"]fdisk -l[/COLOR] Shows disks partitions sizes and types (run as root -> sudo fdisk -l).
    * [COLOR="DarkRed"]df -h[/COLOR] Shows free space on mounted filesystems.
[B]
Monitoring/Logging:[/B]

    * [COLOR="DarkRed"]tcpdump not port 22[/COLOR] Shows network traffic except SSH.
    * [COLOR="DarkRed"]last reboot[/COLOR] Shows system reboot history.
    * [COLOR="DarkRed"]free -m[/COLOR] Shows amount of (remaining) RAM (-m displays in MB).
[B]
System Information:[/B]

    * [COLOR="DarkRed"]uname -a[/COLOR] Shows kernel version and system architecture.
    * [COLOR="DarkRed"]head -n1 /etc/issue[/COLOR] Shows name and version of distribution.
    * [COLOR="DarkRed"]cat /proc/partitions[/COLOR] Shows all partitions registered on the system.
    * [COLOR="DarkRed"]grep MemTotal /proc/meminfo[/COLOR] Shows RAM total seen by the system.
    * [COLOR="DarkRed"]grep "model name" /proc/cpuinfo[/COLOR] Shows CPU(s) info.
    * [COLOR="DarkRed"]mount | column -t[/COLOR] Lists mounted filesystems on the system (and align output).
    * [COLOR="DarkRed"]hdparm -i /dev/sda[/COLOR] Shows info about disk sda.[/SIZE]
    * [COLOR="DarkRed"]lshw[/COLOR] Shows hardware information of your PC and mounted devices.
    * [COLOR="DarkRed"]lspci[/COLOR] Shows information about all PCI buses in the system and all devices connected to them.

---

### Post by WRDN on 2008-07-01
This [Command Sheet]("http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/") can also be very helpful.

---

### Post by unseend on 2008-07-01
> **WRDN said:**
> This [Command Sheet]("http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/") can also be very helpful.
oh nice! tagged it in del.icio.us :)

---

### Post by Sealbhach on 2008-07-01
One I learned recently:

cat /folder/folder/file > /folder/filenane

The **>** will output the contents of cat to a file in the specified location. 

e.g

```
cat /etc/boot/grub/menu.lst > ~/Desktop/bootmenu
```

This will output the contents of your boot menu to a file on your desktop.  Kinda handy if you you want to look at it at leisure without fear of changing something by mistake.



.

---

### Post by unseend on 2008-07-01
> **Sealbhach said:**
> One I learned recently:
cat /folder/folder/file > /folder/filenane
The **>** will output the contents of cat to a file in the specified location. 
e.g
```
cat /etc/boot/grub/menu.lst > ~/Desktop/bootmenu
```
This will output the contents of your boot menu to a file on your desktop.  Kinda handy if you you want to look at it at leisure without fear of changing something by mistake.

I'll add it :)

---

### Post by ChronoSphere on 2008-07-01
Here's one I use to get a better look at my path:

[COLOR="Red"]echo $PATH | tr ":" "\n"[/COLOR]

---

### Post by caljohnsmith on 2008-07-01
> **unseend said:**
> 
    * [COLOR="DarkRed"]cat /etc/boot/grub/menu.lst > ~/Desktop/bootmenu[/COLOR] Outputs the contents of your boot menu to a file on your desktop. (The > will output the contents of cat to a file in the specified location)

I think that must be a small typo, because the menu.lst is actually in /boot/grub and not /etc/boot/grub, so the command should be:
```
cat /boot/grub/menu.lst > ~/Desktop/bootmenu
```
Thanks for sharing your useful list of commands!

---

### Post by anemptygun on 2008-07-01
I just bought an o'reilly pocket guide for 10 bucks

---

### Post by steveneddy on 2008-07-01
**cowsay** is my favorite linix command

---

### Post by ghostdog74 on 2008-07-01
> **ChronoSphere said:**
> Here's one I use to get a better look at my path:

[COLOR="Red"]echo $PATH | tr ":" "\n"[/COLOR]

don't have to use echo too
```

tr ":" "\n" <<<$PATH

```

---

### Post by qpieus on 2008-07-01
For system information try```
lshw
```
and
```
lspci
```

---

### Post by unseend on 2008-07-02
> **caljohnsmith said:**
> I think that must be a small typo, because the menu.lst is actually in /boot/grub and not /etc/boot/grub, so the command should be:
```
cat /boot/grub/menu.lst > ~/Desktop/bootmenu
```
Thanks for sharing your useful list of commands!
corrected it :-D
thank you guys for your feedback :-D

---

### Post by unseend on 2008-07-02
> **qpieus said:**
> For system information try```
lshw
```
and
```
lspci
```
added them too.:)

---

