---
title: "Static IP and 'An error occurred while mounting /files'"
date: 2015-03-20
forum: General Help
---

### Post by david355 on 2015-03-20
Not sure what's going on here. I've been running this box since I put it together just fine. That is, after I was finally able to access the files on the network..

But then I tried to change the server to run on a static IP.

Anyway, I made the changes to /etc/network/interfaces (based on [this guide]("http://www.sudo-juice.com/how-to-set-a-static-ip-in-ubuntu-the-proper-way/"))

```
# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
iface eth1 inet static
address 192.168.0.101
gateway 192.168.0.1
netmask 255.255.255.0
dns-nameservers 8.8.8.8 8.8.4.4

```

and restarted the network service (based on [this]("http://askubuntu.com/questions/441619/how-to-successfully-restart-a-network-without-reboot-over-ssh"))

```
sudo ifdown eth1 && sudo ifup eth1
```

When restarted, I had no network connection so I just rebooted. After doing so, I got the 'An error occurred while mounting /files' error while booting, and skipped the message by pressing 'S'. After I logged in, I still had no internet access, and the files of course were unavailable.

After commenting out the last line in /etc/network/interface, restarting the network, uncommenting the last line, then restarting the network again (usually it takes 2 times), I finally had network access.

Any help would be greatly appreciated.

Thanks

---

### Post by steeldriver on 2015-03-20
What is /files? is it a remote filesystem? You need an

```

auto eth1

```

---

### Post by david355 on 2015-03-20
> **steeldriver said:**
> What is /files? is it a remote filesystem? You need an

```

auto eth1

```

It's the directory where the hard drive which is getting the mount error is supposed to mount the files.

---

### Post by sandyd on 2015-03-20
can you post the outprt of 
```
cat /etc/fstab
```

---

### Post by steeldriver on 2015-03-20
My point was if /files is remote, then it's not surprising that it fails to mount at boot if your network interface is not configured at boot. 

I don't think there's anything more sinister going on here - you just need to add 'auto eth1'

---

### Post by david355 on 2015-03-20
> **sandyd said:**
> can you post the outprt of 
```
cat /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=0f868c91-ac6f-4730-bdc8-3383549a101c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=ee519be9-e55f-4240-9362-f357ccac528e none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=3c0fb09c-c534-4245-8ff5-bf5cc72bdfbe /files defaults 0 2
```

---

### Post by nerdtron on 2015-03-20
```
UUID=3c0fb09c-c534-4245-8ff5-bf5cc72bdfbe /files defaults 0 2 
```

Will this even work or did you made a typo? I don't the filesystem type on this fstab entry

---

### Post by david355 on 2015-03-21
> **nerdtron said:**
> ```
UUID=3c0fb09c-c534-4245-8ff5-bf5cc72bdfbe /files defaults 0 2 
```

Will this even work or did you made a typo? I don't the filesystem type on this fstab entry

It just says this when I type it in

```
-bash: /files: Is a directory
```

---

### Post by nerdtron on 2015-03-21
> **david355 said:**
> It just says this when I type it in

```
-bash: /files: Is a directory
```

I'm not asking you to run that on the terminal. Did you not read what I said? I said it won't work.

Why is that line on your fstab entry? who told you to paste that on your fstab?

---

### Post by david355 on 2015-03-22
No need to get touchy. bab1 is the one who helped me out when troubleshooting my last [problem]("http://ubuntuforums.org/showthread.php?t=2267066")

---

### Post by The Cog on 2015-03-22
steeldriver is right, but doesn't say where to put the requires line "auto eth1".
It needs to go in /etc/network/interfaces, preferably at the start of the eth1 configuration options. Like this:
```
# The primary network interface
auto eth1
iface eth1 inet static
address 192.168.0.101
gateway 192.168.0.1
netmask 255.255.255.0
dns-nameservers 8.8.8.8 8.8.4.4
```
Without the auto eth1 line, you can still bring the interface up with "sudo ifup eth1" but it won't be brought up automatically at boot time.

You should be able to see the state of eth1 with the command **ifconfig**, and see if it has an inet address.

Also, I suspect that you should be trying to use eth0, not eth1. If ifconfig shows that you have both eth0 and eth1, use the one that shows RUNNING because that's the one with the cable plugged in.

P.S.
I don't see any point in worrying about mount options etc. because we know it all works when the machine had a dynamic IP address. The mount options, mount point and all that side of things must therefore be correct already.

---

### Post by david355 on 2015-03-26
> **The Cog said:**
> steeldriver is right, but doesn't say where to put the requires line "auto eth1".
It needs to go in /etc/network/interfaces, preferably at the start of the eth1 configuration options. Like this:
```
# The primary network interface
auto eth1
iface eth1 inet static
address 192.168.0.101
gateway 192.168.0.1
netmask 255.255.255.0
dns-nameservers 8.8.8.8 8.8.4.4
```
Without the auto eth1 line, you can still bring the interface up with "sudo ifup eth1" but it won't be brought up automatically at boot time.

You should be able to see the state of eth1 with the command **ifconfig**, and see if it has an inet address.

Also, I suspect that you should be trying to use eth0, not eth1. If ifconfig shows that you have both eth0 and eth1, use the one that shows RUNNING because that's the one with the cable plugged in.

P.S.
I don't see any point in worrying about mount options etc. because we know it all works when the machine had a dynamic IP address. The mount options, mount point and all that side of things must therefore be correct already.

Changing the config file fixed my connection issues. And yes, I have two ports, and the one I use is eth1. It just happens to be the first port I plugged into.

Somehow, though, my HDD still won't mount. Getting the same message on boot

---

### Post by bab1 on 2015-03-27
> **david355 said:**
> ...Somehow, though, my HDD still won't mount. Getting the same message on boot
What is the message David?

FYI: The mount configuration in the /etc/fstab should have the file system type defined.  The system will make a best effort guess and most of the time it is correct, but it can also fail.

Refresh our memories.  Post the output of ```
cat /etc/fstab 
```...and also this```

sudo blkid -c /dev/null -o list

```

---

### Post by david355 on 2015-03-27
> **bab1 said:**
> What is the message David?

FYI: The mount configuration in the /etc/fstab should have the file system type defined.  The system will make a best effort guess and most of the time it is correct, but it can also fail.

Refresh our memories.  Post the output of ```
cat /etc/fstab 
```...and also this```

sudo blkid -c /dev/null -o list

```

The message:

```
An error occurred while mounting /files.
keys:Press S to skip mounting or M for manual recovery
```

...and then more boot progress messages

cat /etc/fstab
```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=0f868c91-ac6f-4730-bdc8-3383549a101c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=ee519be9-e55f-4240-9362-f357ccac528e none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=3c0fb09c-c534-4245-8ff5-bf5cc72bdfbe /files defaults 0 2
```

sudo blkid -c /dev/null -o list
```
device     fs_type label    mount point    UUID-------------------------------------------------------------------------------
/dev/sda1  ext4             /              0f868c91-ac6f-4730-bdc8-3383549a101c
/dev/sdb1  ext4             (not mounted)  3c0fb09c-c534-4245-8ff5-bf5cc72bdfbe
```

---

### Post by bab1 on 2015-03-27
Add the part in red (see below) to the last line in the /etc/fstab file```
UUID=3c0fb09c-c534-4245-8ff5-bf5cc72bdfbe   **[COLOR="#FF0000"]ext4[/COLOR]**   /files defaults 0 2
```

The use this command ```
sudo mount -a
```

You can check to see if the HDD is mounted successfully with this command```
df -h
```...look for the line with /files at the end.

If all of that works, try rebooting the system.  The error should be gone.

For those interested the **/files** is a directory (the mountpoint) created by the OP at **/** on the local file system.

---

### Post by david355 on 2015-03-27
> **bab1 said:**
> Add the part in red (see below) to the last line in the /etc/fstab file```
UUID=3c0fb09c-c534-4245-8ff5-bf5cc72bdfbe   **[COLOR=#FF0000]ext4[/COLOR]**   /files defaults 0 2
```

The use this command ```
sudo mount -a
```...

After modifying the file and running

```
sudo mount -a
```

I got the message

```
mount: mount point ext4 does not exist

```

---

### Post by bab1 on 2015-03-27
> **bab1 said:**
> Add the part in red (see below) to the last line in the /etc/fstab file```
UUID=3c0fb09c-c534-4245-8ff5-bf5cc72bdfbe   **[COLOR="#FF0000"]ext4[/COLOR]**   /files defaults 0 2
```

The use this command ```
sudo mount -a
```

You can check to see if the HDD is mounted successfully with this command```
df -h
```...look for the line with /files at the end.

If all of that works, try rebooting the system.  The error should be gone.

For those interested the **/files** is a directory (the mountpoint) created by the OP at **/** on the local file system.

My mistake.  It should be this
```
UUID=3c0fb09c-c534-4245-8ff5-bf5cc72bdfbe   /files **[COLOR="#FF0000"]    ext4  [/COLOR]**defaults 0 2
```

Run the other commands again.

---

### Post by david355 on 2015-03-27
Once again bab1, you are a miracle worker. Running smoothly now! :D

---

### Post by bab1 on 2015-03-27
Not sure what happened,  I guess the /etc/fstab file should have stopped us originally.  The static IP address issue had nothing to do with the mount of a partition at the /files mountpoint.

---

### Post by david355 on 2015-03-27
I didn't think so. It was especially strange though, because I saw that message on boot before this and it seemed to mount fine. Maybe my memory is hazy. Anyway, it works now, so I'm happy

---

### Post by bab1 on 2015-03-27
> **david355 said:**
> I didn't think so. It was especially strange though, because I saw that message on boot before this and it seemed to mount fine. Maybe my memory is hazy. Anyway, it works now, so I'm happy

I'll bet it did not mount at all.  Check to see if the data you moved to /files is still there.  Let me know  If the data is missing I'll show you where it is.

---

### Post by david355 on 2015-03-27
It's all there

---

### Post by bab1 on 2015-03-27
> **david355 said:**
> It's all there

Good.  That means the drive was mounted when you transfered data.  If it was not mounted it would have put the data in the /files directory and when you mounted the drive later on it would hid the date in that directory.  Since the data is there we have nothing to worry about.  Yeah!

---

