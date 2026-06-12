---
title: "dd command finished but where is the output?"
date: 2017-08-27
forum: General Help
---

### Post by onlineaddy on 2017-08-27
Hi,
I wanted to make an .iso image of my USB drive (/dev/sdb) to another USB drive (/dev/sdc). The result I got: 

```
ubuntu@ubuntu ~ $ sudo dd if=/dev/sdb of=/dev/sdc bs=64K conv=noerror,sync62640+0 records in
62640+0 records out
4105175040 bytes (4.1 GB, 3.8 GiB) copied, 1493.43 s, 2.7 MB/s
ubuntu@ubuntu ~ $
```

It seems to me it has completed successfully, but the problem is I don't know WHERE to look for the output. Where did dd copy my dev/sdb drive to?? How do I access it?

```
ubuntu@ubuntu /dev $ cd /dev/sdc
bash: cd: /dev/sdc: Not a directory


```

---

### Post by onlineaddy on 2017-08-27
Anyone please?

---

### Post by SeijiSensei on 2017-08-27
/dev/sdc represents the entire drive. You cannot cd into it.  You must first mount any partitions on the device into the filesystem.  If there's only one partition, try using
```
sudo mount /dev/sdc1 /mnt
```
and look in /mnt.  If there are multiple partitions, you'll need to create individual directories to which the partitions can be mounted.  E.g.,
```

cd /mnt
sudo mkdir part1 part2
sudo mount /dev/sdc1 /mnt/part1
sudo mount /dev/sdc2 /mnt/part2

```

---

### Post by sudodus on 2017-08-28
> **onlineaddy said:**
> Hi,
I wanted to make an .iso image of my USB drive (/dev/sdb) to another USB drive (/dev/sdc). The result I got: 

```
ubuntu@ubuntu ~ $ sudo dd if=/dev/sdb of=/dev/sdc bs=64K conv=noerror,sync62640+0 records in
62640+0 records out
4105175040 bytes (4.1 GB, 3.8 GiB) copied, 1493.43 s, 2.7 MB/s
ubuntu@ubuntu ~ $
```

You ***cloned*** the content from the drive **/dev/sdb** to the drive **/dev/sdc**

If you want to create an iso file, ***you must write to a file*** in a location (a directory in a mounted partition), where there is enough free drive space, in this case 4.1GB plus some extra workspace.

Let us assume that there is enough free space in your home directory (~). Then you can try with the following command line

```

sudo dd if=/dev/sdb of=~/filename.iso bs=4096

```

You can use a full path and write to any other location, where there is enough free space, for example to a mounted external drive.

```

sudo dd if=/dev/sdb of=/path-to-where-you-want-to-write-your-file/filename.iso bs=4096

```

But you must also consider the character of the content in the source drive **/dev/sdb**. If it corresponds a cloned image of an iso file, you will get an iso file that behaves as expected. Otherwise, it will be a general image file with properties, that can be 'anything'. For example it could be an image of a drive with a data partition, which cannot be booted, or it could be an image of a drive with an installed system, which is bootable and maybe even portable between computers. In this general case, you should use the extension **.img**, so

```

sudo dd if=/dev/sdb of=/path-to-where-you-want-to-write-your-file/filename.img bs=4096

```

It is safer and also faster to use Clonezilla to clone a drive or create an image of a drive (instead of dd). See this link

[http://clonezilla.org](http://clonezilla.org)

---

