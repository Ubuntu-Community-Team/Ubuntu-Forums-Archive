---
title: "How to Overide default behavior when Mounting Partitions"
date: 2015-05-10
forum: General Help
---

### Post by leegold on 2015-05-10
Hi,

Using Xubuntu 14.04. I have dual boot w/win7. I want to prevent auto-mounting of the ntfs partition. But while I can do that (prevent auto-mounting initially) one it's mounted and asks for my PW (good)  but, then I unmount then and from that point on it never asks me the Password again when I mount , it just mounts. So I tried uninstalling ntfs-3g, I tried all sorts of things in /etc/fstab, I tried commenting out lines in policykit files.

Nothing works, once it's mounted the first time asking for the PW and then unmounted - from that point on it will always mount w/no PW until I reboot.

I want asking for PW for this partition every time it's mounted and I can't seem to override the default behavior.

---

### Post by TheFu on 2015-05-11
NTFS doesn't have any protections, so why not encrypt it. Then it won't mount without the decryption key.

Or

Use autofs and mount it as a specific userid with 700 permissions so no other userid can see any of the files.

Just a few options. Doubt either are acceptable solutions.

---

### Post by leegold on 2015-05-11
if I encrypt it then what is the effect when I boot Win7 ?

I guess I don't understand. It asks for a PW the 1st time I mount it but never again till I reboot. Why can't I make it ask for PW every time I mount?

I don't understand. Thanks.

---

### Post by efflandt on 2015-05-11
Any Linux user with sudo or root access can mount any ntfs partition and read anything on it. If you want to make sure nobody gets on your X session, either logout, lock your screen when away, or have it your screen auto lock after a brief period. Typically if I have any text I want to keep private, if it is a Word file I encrypt it with a password, or I use LibreOffice Writer in Windows or Linux and do the same thing (encrypt it with a password). For example I keep my passwords for various sites in an encrypted file that requires a password to access.

Some drives are capable of encrypting the entire drive and requiring a password to access, but I have never done that, or encrypt partitions, because I have seen posts from people who are having trouble accessing such partitions after they do something wrong.

---

### Post by mc4man on 2015-05-11
Not sure why you are ever prompted for password, do you have an fstab entry?
As far as no prompt after that - 
1. commenting policies is not the way to go
2. does Xubuntu contain a .pkla override(s) like ubuntu? (in ubuntu it's in /var/lib/polkit-1/localauthority/10-vendor.d  in com.ubuntu.desktop.pkla
Specific to this would be likely be  one of the blue entries
```
[Mounting, checking, etc. of internal drives]
Identity=unix-group:admin;unix-group:sudo
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*;[COLOR="#0000CD"]org.freedesktop.udisks2.filesystem-mount-system[/COLOR];org.freedesktop.udisks2.encrypted-unlock-system;[COLOR="#0000CD"]org.freedesktop.udisks2.filesystem-fstab[/COLOR];
ResultActive=yes
```

---

