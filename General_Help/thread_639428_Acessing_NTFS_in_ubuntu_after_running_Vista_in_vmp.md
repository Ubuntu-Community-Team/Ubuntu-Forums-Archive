---
title: "Acessing NTFS in ubuntu after running Vista in vmplayer."
date: 2007-12-13
forum: General Help
---

### Post by tirithen on 2007-12-13
Hello, I'm running Gutsy and have installed vmware player and set it to run my windows vista install from my /dev/sda1 partition which is also my booting partition.

Vista runs fine in vmplayer but when I exited  vista and quit vmplayer I could no longer mount my ntfs partitions on my hdd sda, when I try to mount sda1 I get this:

```
tirithen@Minas:~$ sudo mount /dev/sda1
[sudo] password for tirithen:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operationen stöds ej
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/Windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/Windows ntfs-3g defaults,force 0 0

```
I have tried to reboot my system starting up vista and shutting it down but I did not change anything. Is it bad practice to run an installed OS in this way and how do I mount my two ntfs partitions on my sda drive?

Is it safe to use:

```
  mount -t ntfs-3g /dev/sda1 /media/Windows -o force
```or will I risk damaging the filesystem if I use the force option? Running vista both with regular boot and trough vmplayer still works fine and I would not want to risk that if someone can tell me of an alternative solution to this.

---

### Post by fjgaude on 2007-12-13
Gosh, Gutsy loads ntfs partition on bootup if you have placed that line in fstab, say without the force option.

```
/dev/sda1 /media/Windows ntfs-3g defaults 0 0
```

So do that then I think everything will be okay. Make sure you have, in Gutsy, setup the Shares in System/Administration/Shared Folders. When in Vista you have to go the Network, then WORKGROUP to get to all the files that are on your Linux filesystem.

Let us know how things go.

---

