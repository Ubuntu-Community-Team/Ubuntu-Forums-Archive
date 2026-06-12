---
title: "GGM Issue, Login Impossible [Resolved]"
date: 2007-05-28
forum: General Help
---

### Post by Gibran on 2007-05-28
Hello everyone,

I got today's (or last night's) kernel update this morning, I did not reboot and left the PC on downloading torrents while I ran some errands, but when I left all it needed was a restart. When I returned I saw the desktop was loaded but every icon had a red "x" next to it, like when it's read-only or it's not available, and there was no theme or background image. I restarted and then I got this:

> GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator

I tried entering in recovery mode, I deleted around 100MBs from the OS partition to no avail (I don't know if they go to trash with the "rm" command, but I doubt it) I also uninstalled a couple of games and a music player to free around 30 megs. I know I was low on space on that partition because I had my torrents downloading to it (though I have 100-something GB free), but even after freeing this space the log in message persists:(. Please advice.

Thanks in advance!

---

### Post by aysiu on 2007-05-28
Have you tried booting into recovery mode and doing ```
chown -R gibran:gibran /home/gibran
chmod 644 /home/gibran/.dmrc
reboot
``` and then seeing if the error message goes away?

---

### Post by Gibran on 2007-05-28
Thanks so much for the prompt reply! I just tried that and the error persists. I am also getting:

> modprobe: WARNING: /etc/modprobe.d/alsa-base line 41: ignoring bad line starting with 'snd-hda-intel'

In case that is a problem

---

### Post by aysiu on 2007-05-28
That is probably an unrelated problem. All my lines begin with either *options* or *install*: ```
cat /etc/modprobe.d/alsa-base 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
``` For the GDM issue, another thing to try: Can you try creating a test user and logging in as the test user? In recovery mode: ```
adduser testuser
adduser testuser admin
reboot
```

---

### Post by Gibran on 2007-05-28
Okee...I saw a "fail" when it was loading on failsafe and I think it was the kernel or had something to do with it. How could I reinstall/repair the kernel? And how can I see a list of installed programs so I can clean up the disk a little more? Thanks!

---

### Post by Gibran on 2007-05-29
Alright!! I'm into the system now. The problem was the disk was still too full to operate properly. I hadn't realized you had to use autoremove to get rid of the packages you deleted. The interesting part now is that my other two hard drives are not being mounted as they were before...  But with your kickass site [http://www.psychocats.net]("http://www.psychocats.net") I managed to mount them again. So all is well that ends well, and I learned a lesson: Do not set torrents to download on your main partition!:D

---

### Post by aysiu on 2007-05-29
Well, actually *autoremove* removes the dependencies of applications you've already removed.

If you want to delete the installer files themselves, you use ```
sudo apt-get clean
```

---

### Post by Gibran on 2007-05-29
Yet again you have saved me from the fires of insanity :D  Thank you very much, kind sir! *bows*

---

