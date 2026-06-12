---
title: "make a new filesystem.cloop"
date: 2005-03-20
forum: General Help
---

### Post by chungsijay on 2005-03-20
hello, I want to customize the hoary livecd,
and I delete the original filesystem.cloop and then use
debootstrap to build a new ubuntu sytem in /mnt/ubuntu.
and I install new kernel-image in it, 

then I use:
```
mkisofs -iso-level 4 -R -U -V "gnome" -P "gnome" -hide-rr-moved -cache-inodes -no-bak -pad /mnt/ubuntu | nice -5 create_compressed_fs - 65536 > filesystem.cloop
```
and put the resulted  filesystem.cloop into livecd/casper/

and burn it to try, but failed when "preparing live session" "Configuring Snapshot"
I dont know what is the correct method to make a new filesystem.cloop.

any suggestion will be appreciated  :-o

---

### Post by chungsijay on 2005-03-20
BTW, when I chroot to install new kernel,
to avoid mkinitrd failed? I did:
```

cat > /etc/fstab << "EOF"
/dev/hdd1       /               ext3    defaults,errors=remount-ro      0 1
EOF

apt-get install -y linux-image-386 linux-restricted-modules-386
cat /dev/null > /etc/fstab
```
but live CD dont need /etc/fstab,
I dont know if this step is wrong too much :(

---

### Post by Juanje on 2005-03-29
The problem is that the filesystem.cloop must be a **ext2**  image compress with cloop, not a **iso9660**  one.

try something like:
```

# TAM=`du -s /mnt/ubuntu | cut -f 1`
# let TAM=($TAM/1024)+20 # +20 is just in case, is not necessary
# head -c ${TAM}m /dev/zero > /tmp/ubuntu.ext2
# mkfs.ext2 -F /tmp/ubuntu.ext2
# mkdir /mnt/tmp
# mount -o loop -t ext2 /tmp/ubuntu.ext2 /mnt/tmp/
# cp -a /mnt/ubuntu/* /mnt/tmp/
# sync
# umount /mnt/tmp
# cat /tmp/ubuntu.ext2 | nice -5 create_compressed_fs - 65536 > filesystem.cloop

```

Good luck ;-) 

Juanje

---

