---
title: "File system with errors in read only mode. Could be SSD problem?"
date: 2019-04-28
forum: General Help
---

### Post by soda-digitale on 2019-04-28
Hi everybody.

I'm pretty new out there and I'm having problems with Ubuntu, probably due to issues with an SSD.

The pc I'm using is a custom built desktop. I installed Windows 10 some time ago and it has issues of sudden peaks of 100% disk usage, freezing up almost the entire system. After some research seemed like it was a common issue and it was due to a bug in Windows. Since it wasn't bugging me out so much i left it as it was.

Then i decided to dual boot this machine with Ubuntu. Still had some freezing problems with Ubuntu. I've used it for two days since i had to reinstall the entire SO for the same problem i'm having now.

SSD: Kingston A400.
MoBo: AsRock AB350
Both Windows and Ubuntu are installed in UEFI mode

Ubuntu file system now is on read only mode. 
Reading other discussions on the topic i tried to run ```
mount -o remount,rw /
``` and didn't work.

I also updated the firmware of the SSD and seems like the usage peaks are solved.

Now i'm stuck with this during boot (see picture)

 [ATTACH=CONFIG]283122[/ATTACH]

Thank you for your time in advance

---

### Post by SeijiSensei on 2019-04-28
You don't have the right to use the mount command that way as an ordinary user.  You must preface the command with sudo.  However if the filesystem has errors, it's better to fix those fix.

Boot from the installation medium and choose the Try option. Then open a terminal and run "sudo blkid -l" to get a list of the available partitions. Pick the one you want to mount as root, let's say /dev/sda2, then run

```
sudo fsck /dev/sda2
```

to force a filesystem check. fsck will clean up any errors it finds.  You can check that it will mount correctly the next time by running the command

```
sudo mount /dev/sda2 /opt
```

If you don't get any errors, reboot and see how things go.

---

### Post by soda-digitale on 2019-04-29
Thank you very much, it works fine now

---

