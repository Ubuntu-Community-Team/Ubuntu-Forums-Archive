---
title: "Mount with -o loop as normal user?"
date: 2007-10-26
forum: General Help
---

### Post by tsg1zzn on 2007-10-26
Why can't I mount a floppy image that I own and have all permissions to onto a folder that I also own and have all permissions to without being root? Or is there a way I can do it that I haven't seen? (I don't want to add the floppy image to fstab.)

---

### Post by spd106 on 2007-10-27
Hmm, I thought [pmount]("apt://pmount") would work, but it doesn't seem to like loopback filesystems

This forum thread on LinuxQuestions.org might be useful [http://www.linuxquestions.org/questions/linux-general-1/how-to-give-not-root-user-ability-to-mount-devices-to-any-mount-point-374417/](http://www.linuxquestions.org/questions/linux-general-1/how-to-give-not-root-user-ability-to-mount-devices-to-any-mount-point-374417/)

---

