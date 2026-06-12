---
title: "Yakkety20160604 crypt backup and new Restore partition.. It is difficult... Help."
date: 2016-06-05
forum: General Help
---

### Post by oklokl on 2016-06-05
[https://errietta.me/blog/luks-clonezilla/](https://errietta.me/blog/luks-clonezilla/)

[https://en.wikipedia.org/wiki/Partclone](https://en.wikipedia.org/wiki/Partclone)
[https://wiki.archlinux.org/index.php/Dm-crypt/Device_encryption](https://wiki.archlinux.org/index.php/Dm-crypt/Device_encryption)




```
sudo -i

mount /dev/sdb1X /mnt
cryptsetup luksOpen /dev/sda3X crypt
modprobe dm-mod
lvscan
fsck.ext4 -a /dev/ubuntu-gnome-vg/root
partclone.ext4 -c -d -s /dev/ubuntu-gnome-vg/root -o /mnt/test.img

partclone.ext4 -r -d -s /mnt/test.img -o /dev/ubuntu-gnome-vg/root
```
It is normally very good. :)





but   ](*,)

I've created a new partition so broken.   (After changing the background  log... and.. -out stop pc..(I have no choice) Kill force pc .. so .. the newly created partition.)
[Story]

[SIZE=3]**but(PC has been operating normally.) ^^ I would like to try the following command:**[/SIZE]
add message... mkfs.ext4 -L "" /dev/ubuntu-gnome-vg/root (clean)
partclone.ext4 -r -d -s Normal recovery but.. End of an error dm-crypt(ubuntu)

After the shutdown message
[ATTACH=CONFIG]269448[/ATTACH]



[http://www.pavelkogan.com/2014/05/23/luks-full-disk-encryption/](http://www.pavelkogan.com/2014/05/23/luks-full-disk-encryption/)

[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)



```
dd if=/dev/zero of=/dev/sda3X

cryptsetup luksFormat /dev/xvdc


```YES 



```
parted -l  

cryptsetup luksOpen /dev/mapper/yourdevice crypt

mkfs.ext4 -L "" /dev/mapper/yourdevice

pvcreate /dev/mapper/yourdevice

vgcreate ubuntu--gnome--vg /dev/mapper/yourdevice

lvcreate -L 8G -n swap ubuntu--gnome--vg

lvcreate -l 100%FREE -n root ubuntu--gnome--vg

lvscan

cryptsetup close /dev/mapper/yourdevice


```reboot





..restore

```
mount /dev/sdX /mnt
```
# (D:\ HDD /dev/sdb or sdc?)

```
cryptsetup luksOpen /dev/sdX crypt
```
# me /dev/sda3

```
modprobe dm-mod
vgchange -ay
lvscan
```



# or Partition device( -d)

```
partclone.ext4 -C -r -d -s /mnt/test.img -o /dev/ubuntu-gnome-vg/root


```


reboot 
and Mount error 
```
mkdir -p /test
modprobe dm-mod
cryptsetup luksOpen /dev/sdX crypt
lvscan
mount /dev/ubuntu-gnome-vg/root /test

```

booting ubuntu crypt sda3 --No entry T^T..

Command is invalid.
Where 's the problem?

---

