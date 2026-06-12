---
title: "How to mount a network location?"
date: 2012-12-13
forum: General Help
---

### Post by RED666 on 2012-12-13
Very simple question:

How do I get to a network resource in Ubuntu?

I'm trying to mount to a partition in my network, I'm running Ubuntu Live from a Usb pen drive.

This is what I tried:
root@ubuntu:~# sudo mount -t smbfs smb://192.168.0.10/disk_2 /mnt/raid
mount: unknown filesystem type 'smbfs'
root@ubuntu:~# mount -t cifs //192.168.0.10/Disk_2 -o username=xxx,password=xxxxx /mnt/raid
could not update mount table

I'm a solid MsWin user, but never tried this in Linux, so this is all new for me!

---

### Post by JRV on 2012-12-13
Try this:```

nautilus smb://HOSTNAME/SHARENAME

```

You can use an IP address instead of HOSTNAME.

---

### Post by RED666 on 2012-12-13
Thanks!

Tried it:
```

root@ubuntu:~# nautilus smb://192.168.0.10/Disk_2
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```No dice! I get an error msg (see bottom)

I tried a lot of other stuff, it seemed to be best to install the nfs package.. but I just got time outs and permission denied...

Finally I just went the Gui way (for some reason, even though I'm a MsWin slave, I always forget to use the GUI in Ubuntu) ... That got me the furthest. Via Ubuntu-> Go-> Network , I was able to read from the NAS but when I try to write it says "Permission denied!"
In Windows it works fine... So it's not the Nas that's the problem, I would say .

Any other idea's?

---

### Post by PinkFloyd102489 on 2012-12-13
> **RED666 said:**
> Thanks!

Tried it:
```

root@ubuntu:~# nautilus smb://192.168.0.10/Disk_2
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```No dice! I get an error msg (see bottom)

I tried a lot of other stuff, it seemed to be best to install the nfs package.. but I just got time outs and permission denied...

Finally I just went the Gui way (for some reason, even though I'm a MsWin slave, I always forget to use the GUI in Ubuntu) ... That got me the furthest. Via Ubuntu-> Go-> Network , I was able to read from the NAS but when I try to write it says "Permission denied!"
In Windows it works fine... So it's not the Nas that's the problem, I would say .

Any other idea's?

```
sudo apt-get install samba smbclient cifs-utils
```

Install those, then try again.

Also, you can mount the network drive at boot using /etc/fstab.

---

### Post by RED666 on 2012-12-14
Thx, via the GUI it's working now... read +write.

But... How would I do this using the terminal?


I chose the nfs package because it's a lot smaller.. the Bootable Pen drive is for emergencies, I'd like it to use as little resources as possible.

---

### Post by Mopar1973Man on 2012-12-14
Another way of doing it...

You could install SSH server on both machines and then use Filezilla to transfer between both. I tend to like this method of doing file management because I can also administrate the other machine on the network where Samba only shares files.

---

### Post by RED666 on 2012-12-14
I'm running Ubuntu of an USB pen drive!! Not interested in installing, thanks for the tip though. Also the other device is a Nas I haven't be able to get to it via SSH and I cannot run a different Os on it, I think, then the Linux system that's on it.

So, to reiterate my question:

How can I, via the terminal, mount a location on my Nas (preferably NOT using Samba)?

---

