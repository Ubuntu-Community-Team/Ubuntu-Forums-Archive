---
title: "Boot DOS in subdirectory on USB drive with Syslinux"
date: 2007-11-24
forum: General Help
---

### Post by Githlar on 2007-11-24
OK, I'm creating a multi-boot USB stick. I want to put FreeDOS as an option, but I don't want to have to use a large image that take forever to load. From what I understand, you can boot a .BSS boot sector file. I haven't tried it yet, but I imagine that .bss file loads all of the stuff from the root of the USB drive. If I have FreeDOS in a subdirectory, how can I tell it to use that subdirectory as its root? I'm sure I'll probably have to hex the bootsector, but I'm really not sure how I'd do that. In fact, I'm not really sure if I understand how booting a .bss file works...

Any help at all would be appreciated.
Githlar

---

### Post by Githlar on 2007-11-25
I tried something new and cool, but it didn't work =(

I used:
syslinux -d fdos /dev/sdc (/dev/sdc is my flash drive)

to install the ldlinux file into the fdos directory. 

I copied the bootsector into a file

Then I restored the backup I had made of my USB drive with dd

I then coped the fdos.bss file onto my flash drive's root and added this to my syslinux.cfg:

label fdos
  kernel fdos.bss
  append -

I emulated that menu and it came up with the loading screen and went straight back to the root menu. Odd. Perhaps I'm not copying all that I need to into that bootsector...

This is becoming such a pain. If I wanted to multiboot MSDOS and FreeDOS for some reason, their system files would overwrite eachother at my current state (where they're all in the root directory).

I guess what I'm looking for is a way to tell Syslinux where its root folder should be. I thought that loading the bootsector would tell it that, but apparently not. Anybody know some way to do this?

---

