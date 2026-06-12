---
title: "Beep Media Player - problems playing audio cd's (.wav)"
date: 2005-08-25
forum: General Help
---

### Post by 5-HT on 2005-08-25
Hi, just installed Beep Media Player and while I can play music (.wav) from a cd if the files are on a data cd (containing files of other formats), I cannot play any .wav's from an audio cd.

It seems as though the data cd appears as a CD-ROM (on the desktop) and mounts as: /media/cdrom0, whereas the audio cd appears  as "Audio CD" and mounts as: cdda:///dev/hdc.

(So I'm thinking this may have something to do with it?)

I tried unmounting the audio cd and mounting it on /media/cdrom0, but with no luck (gave an error of needing file type, and when I specified -t iso9660 still a no go).

I have no problems playing the cd's with CD Player, but would like to have Beep handle everything if possible.

I'm wondering if anyone has any ideas on how to get this to work?
Thanks for any help.

---

### Post by vruum on 2005-08-25
hi. actually audio cd's are not mounted, but besides that, you're probably right, beep looks for audio cd's in /dev/cdrom two ways to solve this.
1: make beep look for the cd in /dev/hdc. in beep go to preferences / plugins choose cd audio plugins, settings and change /dev/cdrom to /dev/hdc.
2: a more universal solution would be to create /dev/cdrom as a symlink to /dev/hdc:
    sudo ln -s /dev/hdc /dev/cdrom
   (make sure you don't already have a /dev/cdrom)

---

### Post by 5-HT on 2005-08-25
Thanks for the input.

Tried both methods, and definitely making some headway but still unable to play any audio cd's with beep.

Under the CD audio plugin preferences, I changed the device to /dev/hdc (default /dev/cdrom) and directory to /media/cdrom0 (default /mnt/cdrom). 

When I click on the "Check drive" button on the preferences page, I get a popup showing the tracks on the disk, length, and a message saying both that "Digital audio extraction test: OK" and directory ok...so at some level beep is communicating with the disk.

However, when trying to play the disc, still no tracks show up to select.

I've tried looking under the "Audio CD", /media/cdrom0, /media/cdrom, and even /dev/hdc for the fun of it.

I have noticed one strange thing though, in nautilus there's "Audio Disc" in the directory tree (and showing up on the desktop). If I open that directory I can see the files, but If I try to look in /media/cdrom0....they're not there.

I guess that's what you said about audio cd's not mounting (never knew that before), but they do show up in that "Audio Disc" directory...so there has to be someway to point beep to that directory (cdda:///dev/hdc) but I get an error (when trying that in the audio plugin preferences in Beep).

I'm not sure if this is a common issue or just an isolated one (doesn't seem as if this should be problem, maybe it is though).

Thanks for the help though.
Maybe I'll try xmms and see if I have the same issue with it.

---

### Post by vruum on 2005-08-25
maybe you've already done this, but instead of trying to add the seperate track of the cd, what happens if you choose add cd in the playlist menu?

---

### Post by 5-HT on 2005-08-25
[QUOTE=vruum]...instead of trying to add the seperate track of the cd, what happens if you choose add cd in the playlist menu? [/QUOTE]

Ha! Beautiful, works great. 
Can't believe I didn't try that before...
Thanks a lot.

---

