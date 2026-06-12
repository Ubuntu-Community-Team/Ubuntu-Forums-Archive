---
title: "Crash diagnosis ideas?"
date: 2014-05-21
forum: General Help
---

### Post by blitheringeejit on 2014-05-21
Hello forum:

I'm using 12.04 LTS on a Acer Veriton core-i5  box, and I'm finding that the system crashes.  My usual desktop is Gnome Classic, but it does the same in Unity, and I've tried various older kernel versions but that makes no difference either.  

The problem has been intermittent for a couple of years, but in the last few days it's been happening within a few seconds of starting up.

The crash displays a screenful of terminal-style  white text on a black background. If I wasn't running anything or hadn't logged on, it usually begins with something like:

[   62.911342] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
[   62.911373] IP: [<ffffffff811b506b>] inode_lru_list_del+0x3b/0x80
[   62.911397] PGD: 0
[   62.911408] Oops: 0002 [#1] SMP
[   62.911425] Modules linked inL snd_hda_codec_hdmi snd_hda_codec_realtek pci_stub vbocpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) bnep rfcomm bluetooth coretemp_kvm_intel kvm ....

etc etc.

 Once the  machine has crashed the keyboard and mouse no longer work, and the  terminal text stays on the screen until I force a power-down by leaning  on the switch. It doesn't respond to Ctrl-Alt-Del.

Does anyone have any suggestions as to how I can find out what might be  causing the crashes?  Would it be useful to record the on-screen reports  and post them here, and is there something I could look for in the  system or other log which might provide a starting-point for diagnosis?  Should I be looking at hardware or some config issue?

Thanks!

---

### Post by dragonfly41 on 2014-05-21
Based only on the log info you provide .. a quick search 

> ubuntu BUG: unable to handle kernel NULL pointer dereference at 0000000000000008   Oops: 0002 [#1] SMP

through ubuntu bugs shows similar hits ..

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169652)

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1023916](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1023916)

As a guess I would look at your flash plugin as one possibility.

Do you access YouTube sites frequently (which use flash)?

Try to eliminate this possibility by trying different browsers or run time scenarios.

Do you get crashes when you login to a fresh account .. or when using live CD?

Have you run memtest?

---

### Post by blitheringeejit on 2014-05-23
Brilliant, solved.  I have removed the flash plugin and the crashes have stopped.  (Memtest showed no errors.)

A little more info - I don't think the crash was related to user activity or using a particular browser or content type, as it sometimes happened so soon after booting that the login screen never even appeared. I have no idea what a browser plugin would be trying to do at boot time, or when there was no browser running..?   I suspected something thermal, as it seemed to take longer to crash after initial switch-on - after it had crashed once, subsequent crashes happened much more quickly, until it was impossible even to log in.  But it looks like it was all down to the flash plugin.

Many thanks for your kind help and advice.

---

