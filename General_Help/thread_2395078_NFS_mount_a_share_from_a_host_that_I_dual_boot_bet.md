---
title: "NFS mount a share from a host that I dual boot between Linux and Windows 10"
date: 2018-06-26
forum: General Help
---

### Post by ivan-samuelson on 2018-06-26
Okay, this sounds nuts but it's how I have to deal with it until I can get either new drives or a SATA controller for a machine I have running Ubuntu Server. On that server I'm running Plex media. I have all my media served on several different drives. One is a USB drive that is connected to the Plex Server. The rest are drives on my main PC that I have that I dual boot between Linux and Windows 10 (depending on what I'm doing at that time). As much as I'd LIKE to switch to full-time Linux, I just can't at the moment.

On the dual-boot machine, I have shares set up both in Windows and in Linux to the rest of my media that I will eventually migrate over to the Plex Server but I have to get new drives. I can't put them in the server right now because it currently has only one SATA connection and the drives in the dual boot are SATA only. 

I can mount the shares from the Plex Server when it's windows only with CIFS. If I reboot the dual-boot into Linux, I can only mount them as NFS and I understand why. I have it set up in my fstab but is there a way that I can set up fstab so that no matter which OS my host is booted into, it will figure out the right way to mount? I tried installing NFS services on my Windows box, but I couldn't get it to work.

I know it's a crappy way of doing things, but until I can migrate the drives/files to the Unbuntu Server, it's what I got. For now, I just don't use Plex when I boot into Windows and just only mount when my dual-boot is back in Linux so fstab is set up to only do nfs mounting instead of CIFS.

Please don't judge. :)

---

### Post by TheFu on 2018-06-26
You've shown enough remorse. ;)  Enough that I can admit to having Win7 physically installed on 1 machine here and inside 1 VM. I won't allow Win10 on my network over privacy concerns.  Anyways ... 

If I were you, I'd use CIFS/Samba on the Linux boot to make the media available to the media playback devices.  It would be ideal if you could provide exactly the same share-name from both the win and samba shares coming from the same machine.  Also, both should have the identical IP, which should be static.  From the client-side, the shares need to appear exactly the same.  That means, same IP, same share-name, same CIFS protocol version, same authentication level, same local mount on  the client-side.
Or
You could create a tiny script that mounts the CIFS/NFS storage to the client machine at the OS level.  I.e. don't use kodi/plex interfaces to mount it. As far as kodi/plex are concerned, the storage is just more local disk. This should be pretty easy.  Just need an easy way to determine which storage OS is running on the remote system that is scripted before the mount is attempted.  You won't be using the fstab for this to work.  You'll need for the script to perform the mount, which is probably easier than using the fstab.

I have another option for your consideration. Put Windows into a VM under the Linux host. This would work if the following are true:
a) Windows isn't being used for high-graphics needs.  Office productivity apps work fine inside VMs.
b) Your dual-boot system has sufficient CPU and RAM and supports VT-x
c) The Win10 license is retail (or you can get one) that isn't tied to the specific hardware. VMs hide the real hardware.

Once you can go full-Linux, then you should switch to NFS.

---

### Post by ivan-samuelson on 2018-06-26
Thanks for the reply. Unfortunately, Windows does need the high-graphic needs (sorry. Love to play Fortnite. lol). I do run Windows 10 in a VM for things like ripping my Blu-Ray collection so I don't have to boot to Windows, but when it comes to Fortnite, I need all the horsepower I can get natively. lol

I'll just keep "suffering" through what I have. I'm usually in Linux anyways unless I get the urge to play Fortnite. Plus, I have a valid Windows 10 key that I can use multiple times via my MSDN subscription, so that's good as well.

Just wasn't sure if there was a way to make it determine which way to mount. Otherwise, I have to switch the fstab on my Plex server from CIFS to NFS and vice versa depending on which OS my host is in. The shares are set up to be the same name, but I can't mount the shares via NFS if the host is in Windows and vice versa. Can't mount cia CIFS if the host is Linux. Tried installing different NFS services to run on Windows but they all came back with errors about the wrong NFS version or something like that.

Thanks for the tips though.

---

### Post by SeijiSensei on 2018-06-26
As TheFu said, you could run Samba on the Linux box and always use CIFS.

Another option might be to use Windows as the main host, and install Ubuntu server into a virtual machine on that system with VirtualBox.  Then there would be an instance of Linux running all the time.  Getting a VM to see the other devices is a bit tricky, but not that hard using the "Shared Folders" method in VirtualBox.

---

### Post by TheFu on 2018-06-26
> **ivan-samuelson said:**
>   Love to play Fortnite. lol).  

 Can't mount cia CIFS if the host is Linux.  

I never begrudge someone chasing their bliss, even if it requires Windows, cough. ;)

Why can't you mount via CIFS if the host is Linux?  Samba is the Unix implementation of CIFS and as been enterprise ready since the mid-1990s.  I know that I deployed it first around 1996 at work and it has mostly worked great all these decades, er ... for what CIFS is.

I'm running it on a 16.04 box here and while not the best, for a home setup, it is easier than trying to get NFS working from a Win7 Home install and faster than using WinSCP (sftp) for everything.

If your systems have static IPs, it should be pretty easy, really.

The "hard part" of a smb.conf file that allows 2 client computing devices to have access using userids that are in the /etc/passwd && smbpasswd DB specified in the global section. [homes] is a special area - it means the HOME directory for the valid userids.  You can make that a specific directory with a short name, like [Movies] and specify a directory (look up how to do that) and leave everything else the same.

```
[homes]
  comment = Home Directories
  hosts allow = 127.0.0.1 172.22.22.9 172.22.22.27
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S
```

Don't forget to run smbpasswd to add any users from Windows to the DB that samba uses.

Or as Sensei says, do the VM thing in the opposite way using vbox.

Or you can do PCI card passthru if you have 2 video cards in the machine and run Windows inside a KVM virtual machine.  Gamers claim this provides 95% of native graphics speed. While it isn't trivial to setup, in the last few days I've learned that it is about 75% easier than it was 5 yrs ago.

And there is 1 other option, which is how I have a plex server - spend about $130 and use a cheap MB, CPU Intel CPU, $25 in DDR3 RAM (look for used), and use old stuff you have lying around for the rest of the system to make a Plex + NFS + Calibre + Backup + about 5 other services box.  Mine is using an ATX case from 1999 and the OS boots from an old 320G SATA HDD that used to be in a RAID array I upgraded 10 yrs ago.  I already have a 4-port KVM-switch, so using the same keyboard and monitor and mouse was easy.

Of course, only you can know what skills and options make the most sense, not us.

One last thing, when you build out storage for the other system, please include backup storage too. I have a rule. If I can't backup the primary storage, then I won't bring it online.  About 15 yrs ago, I lost 80% of my data over only backing up my personal HOME and OS settings, but not the big data.  Think of all the effort put into that data. Backups are worth the cost, IMHO.

---

### Post by ivan-samuelson on 2018-06-26
Doh. Never thought of that. It's been awhile since I've set up Samba, but I'll do that instead. Thanks!

UPDATE:

I don't know why I never thought of this myself. Works like a charm. I don't even have to remount when I boot my host machine between Windows and Linux. Thanks again for the suggestion.

---

### Post by TheFu on 2018-06-27
Please mark the thread as "solved" to help others.

---

