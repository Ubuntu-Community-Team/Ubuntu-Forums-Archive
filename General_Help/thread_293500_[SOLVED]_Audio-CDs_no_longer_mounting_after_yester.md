---
title: "[SOLVED] Audio-CDs no longer mounting after yesterdays (kernel)update"
date: 2006-11-05
forum: General Help
---

### Post by Sokraates on 2006-11-05
The title describes everything, so to save myself some writing, here's the [bug-report]("https://launchpad.net/distros/ubuntu/+bug/70434")  I filed.If you suffer from this problem, please add a comment to the [bug-report]("https://launchpad.net/distros/ubuntu/+bug/70434"). You'll find the workaround at the end:

"[I]This happened on two fresh Edgy Final installs. One on my desktop (one CD-reader/writer, one DVD-reader), one on my laptop (HP nx6110, one DVD-reader):

Yesterday's updates included linux-*-2.6.17-10-generic (restricted modules and another one I don't remember) and some libs. If there's a log-file, please tell me and I post it.

After the update mounting an audio-CD will result in this error: 

$ sudo mount /dev/hdb /media/cdrom0
mount: block device /dev/hdb is write-protected, mounting read-only
mount: /dev/hdb: can't read superblock

If you don't mount the CD manually, mounting will fail without an error message. Data-CDs and -DVDs as well as movie-DVDs work fine.

This is not a problem with the audio-CD. I reproduced this on my desktop, which didn't have the update installed. Without the update, the cd mounted and played just fine, afterwards it produced the error seen above.

I didn't see any changes in /etc/fstab or /media/*.

The workaround with Kubuntu is pretty easy: in the app (tried it with KsCD or KAudioCreator) you need to select /dev/hd* or media:/hd* instead of the default /media/cdrom*.[/I]"

---

