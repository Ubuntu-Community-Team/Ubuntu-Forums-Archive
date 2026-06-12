---
title: "bin/cue in cdemu wont work"
date: 2007-05-20
forum: General Help
---

### Post by rygar on 2007-05-20
i just installed cdemu so i could mount a bin/cue without converting it
here's what i get:

```
jeff@Jeff:/dev$ sudo mount /dev/cdemu0 /media/cdemumount: block device /dev/cdemu0 is write-protected, mounting read-only
mount: you must specify the filesystem type

```

so the cdemu webpage says to add "-t iso9660"...  and i get this:

```
jeff@Jeff:/dev$ sudo mount -t iso9660 /dev/cdemu0 /media/cdemu
mount: block device /dev/cdemu0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/cdemu0,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

```
jeff@Jeff:/dev$ dmesg | tail
[70496.896000] cdemu:257: cdemu_open: start cdemu0
[70496.896000] cdemu:266: cdemu_open: end
[70496.896000] cdemu:612: cdemu_block_media_changed: start cdemu0
[70496.896000] cdemu:616: cdemu_block_media_changed: going into cdrom_media_changed()
[70496.896000] cdemu:308: cdemu_media_changed: start cdemu0
[70496.896000] cdemu:320: cdemu_media_changed: end
[70496.896000] cdemu:572: cdemu_block_release: start
[70496.896000] cdemu:349: cdemu_lock_door: start
[70496.896000] cdemu:275: cdemu_release: start
[70496.896000] cdemu:282: cdemu_release: end

```

any ideas?

---

### Post by mlind on 2007-05-20
You could convert .cue/.bin to .iso image using **bcunk** and mount .iso image in loopback device. That's what I usually do.
cdemu did work for me too for some time, but not with all .bin/.cue files. Did you try UDF filesystem btw?

```

sudo aptitude install bcunk
bchunk foo.bin foo.cue foo
sudo mount -o loop foo.iso /mnt

```

---

### Post by rygar on 2007-05-20
hmmm
converting bin to iso didn't work either, i got the same problem on mount.

i tried to rename the bin to mpg and play it in vlc.  i get no sound.  i get video when i drag the window around but if im not moving it, its black.  what do i do?


edit: i think installing the multimedia codecs ala ubuntuguide.org might work, apparently i dont have some installed.  i thought i
didn't need it because i had installed "GStreamer ffmpeg video plugin" via add/remove programs...

edit x2! -- nope, codecs didn't help. :(

---

### Post by rygar on 2007-05-20
i did

sudo aptitude install totem-xine
sudo aptitude install xine-ui libxine-extracodecs

and xine player worked.  nothing else seems to, but whatevz.

---

