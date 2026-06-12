---
title: "Error while trying to encrypt partition: Incompatible libdevmapper 1.02.07"
date: 2006-11-17
forum: General Help
---

### Post by felixj on 2006-11-17
Just installed a brand new harddrive and put an ext3 filesystem on it. Then I was following the instruction in the wiki for harddrive encryption:
[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

But when I do 
```
sudo cryptsetup -y create 400gb_crypt /dev/sda1

```
I get the error message:
```
Aufruf fehlgeschlagen: Incompatible libdevmapper 1.02.07 (2006-05-11)(compat) and kernel driver 
```

I searched the forums and there is a workaround for already existing encrypted partitions (just fill in the missing options in /etc/cryptab manually), but not for newly encrypted ones.

Thanks,
felixj

---

### Post by felixj on 2006-11-21
In case somebody stumbles across the same problem: Installing the package libdevmapper-dev helps.

---

### Post by ograndedienne on 2007-11-02
> **felixj said:**
> Just installed a brand new harddrive and put an ext3 filesystem on it. Then I was following the instruction in the wiki for harddrive encryption:
[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

But when I do 
```
sudo cryptsetup -y create 400gb_crypt /dev/sda1

```
I get the error message:
```
Aufruf fehlgeschlagen: Incompatible libdevmapper 1.02.07 (2006-05-11)(compat) and kernel driver 
```



I had this problem in gusty. Solution: just load dm-crypt kernel module. ):P

Valerio aka O(n)

---

### Post by jakswa on 2008-02-23
> **ograndedienne said:**
> I had this problem in gusty. Solution: just load dm-crypt kernel module. ):P

Valerio aka O(n)

Thank you!  Worked like a charm.  If any other noobs like me don't know how to load a module, I hunted it down:

To load the 'dm-crypt' module manually:
```
sudo modprobe dm-crypt
```

---

