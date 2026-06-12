---
title: "Removing Drives from RAID 5 and reverting cryptfs resize"
date: 2013-08-20
forum: General Help
---

### Post by osure on 2013-08-20
Hello everybody,

I have a nasty situation at hand:

The background:
I have a mdadm raid 5, with crypt_fs on top, and then ext4 on top of that, like this:
physical disks <-> raid 5 <-> crypt_fs <-> ext4.

Until now I was below the 16TB limit. I recently added 2 disks and added them to the raid accordingly.

Then I proceeded to resize the crypt_fs with
cryptseup resize /dev/md/raid.
It seemed successful since it immediately returned to bash prompt without error.
cryptsetup now tells:
$ sudo cryptsetup status /dev/mapper/decrypted
/dev/mapper/decrypted is active and is in use.
  type:    LUKS1
  cipher:  aes-xts-plain
  keysize: 512 bits
  device:  /dev/md127
  offset:  4096 sectors
  size:    41021864960 sectors
  mode:    read/write

Then, unfortunately I ran into the 16TB ext4 limit when trying to grow the filesystem: resize2fs returned:
$ sudo resize2fs /dev/mapper/decrypted
resize2fs 1.42 (29-Nov-2011)
resize2fs: New size too large to be expressed in 32 bits

Is there any way to revert the resizing of crypt_fs, so that I can remove the 2 new disks from the raid?
Does anyone have experience with such a situation?

Does the raid "know" what space is currently used and which not? I mean, after all, the raid does not interpret its content, right?
So, does the raid after the reshaping act like it's filled to the last bit (even the two new disks)?

can anybody help?

---

