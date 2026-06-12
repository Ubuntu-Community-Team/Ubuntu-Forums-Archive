---
title: "Live CD Persistent changes"
date: 2021-02-21
forum: General Help
---

### Post by gus_zernial on 2021-02-21
I'm running Kubuntu 20.10. I created a Hirsute 21.04 development Live USB using Startup Disk Creator. The USB has an iso9660 filesystem, and is thus not writable(??), but has a Casper partition, which I understand is what is needed to be able to make changes to the live image persistent. But I don't know what to do from there, ie how to save changes and apply them during succeeding boots. Can someone enlighten me? And if I were to make and save large changes, can I expand the Casper partition (there's plenty of space on the USB stick).  Thx, Gus

---

### Post by C.S.Cameron on 2021-02-21
**A Startup Disk Creator USB is writable**
You just need to prime it every boot that you want to be persistent.

If your Live USB boots UEFI, at the grub menu press "**e**" and the menuentry should open for editing.
At the end of the "linux" line type "**persistent**" then press **f10** to boot.
The following Ubuntu session should be persistent.

If your Live USB boots using Syslinux in BIOS mode, press **Shift** when booting, then press **Esc** to get rid of the language screen, press **F6** and** Esc** again. Type a space and then the word "**persistent**". press **enter** to complete boot into persistent Ubuntu.

Any following session that is started the same way should also be persistent and retain programs and data from previous persistent sessions.

If you do not use the Persistent procedure when booting, the session will be a standard Live session with nothing retained from the previous sessions.

I have not tried this with 21.04 yet, please let me know if it doesn't work.

---

