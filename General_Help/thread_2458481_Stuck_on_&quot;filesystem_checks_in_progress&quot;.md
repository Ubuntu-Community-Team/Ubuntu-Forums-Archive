---
title: "Stuck on &quot;filesystem checks in progress&quot;"
date: 2021-02-25
forum: General Help
---

### Post by alo12 on 2021-02-25
hello, i am facing a problem with a computer runing the latest ubuntu lts. After i turn on the computer and i put the password to unlock sdb6_crypt the system is stuck in the the "filesystem checks in progress" and it's not responding when i press ctrl+C to cancel. Does anyone has any idea about what is going wrong?

Thank you in advance.

---

### Post by TheFu on 2021-02-25
what is: > latest ubuntu lts?  Your idea and ours may not match.
**lsb_release -a** will say the exact version on a system.

Not enough information to guess anything else and I doubt the exact version of Ubuntu will latter. It usually doesn't for LUKS encryption, provided it is support. If you use encryption, having 100% know-you-can-restore backups is mandatory.

You'll need to boot from alternate media - use the same release - but it doesn't need to be EXACTLY the same, just the same major release.  Then you'll need to figure out which layout is used for the encryption.  Typically, it is something like this:  
```
# Assume: sdf5 is the partition to be opened (usually logical partition)
# Assume: LVM is used
# sdf                               8:80   0 119.2G  0 disk  
# &#9500;&#9472;sdf1                            8:81   0   243M  0 part  
# &#9500;&#9472;sdf2                            8:82   0     1K  0 part  
# &#9492;&#9472;sdf5                            8:85   0   119G  0 part  
#   &#9492;&#9472;c720 (dm-4)                 252:4    0   119G  0 crypt 
#     &#9500;&#9472;c720--vg-root (dm-5)      252:5    0  51.9G  0 lvm   /mnt/root
#     &#9500;&#9472;c720--vg-lv--swap (dm-6)  252:6    0   4.1G  0 lvm   
#     &#9492;&#9472;c720--vg-lv--Stuff (dm-7) 252:7    0    50G  0 lvm   /mnt/Stuff
# 
```
which shows an encrypted layout that uses partitions, LVM, LVs for root, home, stuff, and swap areas.  
Use this command to see a nicer view:
```
lsblk -o name,size,type,fstype,mountpoint
```

You may need to manually "activate" the VGs after the LUKS container is unlocked manually using cryptsetup.
```
 sudo cryptsetup luksOpen /dev/sdf5 c720
 sudo vgchange -ay
```
Then you can manually run fsck against each LV.  In the last few years, I think luksOpen has changed to something else. If it matters, the command should error. You can check the cryptsetup manpage for the new option, if needed.  The last "c720" was just the name of the machine when I took these notes. Yours will be different. I think that is set when the LUKS container is created. My encrypted laptop isn't booted, so I can't log into it from here and see if there's somewhere else to find that information outside the encrypted areas.  Perhaps luksDump?

That would use a command like this:
```
sudo fsck /dev/mapper/c720--vg-root 
```
for each LV.  You'll need to determine the actual device file on your system. For unlocked, activated, LVs, those devices should be in /dev/mapper/ somewhere. They usually have a name that looks like:
/dev/mapper/{hostname}--vg-{LVname}
The {hostname}--vg part is really the {VGname}. That really can be anything.
Run all the fsck commands you need. swap doesn't get fsck'ed.

Then you can try rebooting or mount the storage now, make backups, etc. if you like.
```
 sudo mkdir /mnt/root /mnt/Stuff
 sudo mount /dev/mapper/c720--vg-root /mnt/root
 sudo mount /dev/mapper/c720--vg-lv--Stuff /mnt/Stuff

```

If wouldn't hurt to learn these steps, so take careful notes as you do it someplace OUTSIDE the encrypted storage. If you don't have backups, GET SOME ASAP.
Please.

Good luck.  This stuff isn't really beginner-level stuff, but it isn't too hard either.  Use **tab-completion** to fill in all the file-paths correctly. No need go let guesses or misspellings frustrate anyone.

---

### Post by alo12 on 2021-02-27
hello, thank you for your answer. I tried to boot from a live usb but unfortynately in the begining it shows the ubuntu logo and after just a black screen. SO i guess it's a hardware problem? maybe somehting with the motherboard?

---

