---
title: "Dualbooting Ubuntu 18.04  and Windows 10: manual fsck repeatedly required"
date: 2019-04-07
forum: General Help
---

### Post by tomstewart on 2019-04-07
Hi all,

I dual-boot Windows 10 and Ubuntu 18.04 (on a HP Pavillion Touchsmart 15 Notebook PC 15-n090sa, bought in 2014, with a 1 TB HDD). Ubuntu is located on the /dev/sda6 partition. I boot into Ubuntu every day. About once every week, I see the following message:

[I]/dev/sda6 contains a file system with errors, check forced.
Inodes that were part of a corrupted orphan linked list found.

/dev/sda6: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
fsck exited with status code 4
The root filesystem on /dev/sda6 requires a manual fsck

Busybox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3.1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _[/I]

I enter "fsck /dev/sda6". It then lists a bunch of errors I don't understand. It asks if I want them fixed. I enter "y" for all of them, and things seem to be fixed. I am able to boot up Ubuntu. The only problem is that this happens again and again.

1. Does anyone know what the problem is? Do you think it is a hardware or software problem?
2. Does anyone know what I can do to fix it?

---

### Post by yancek on 2019-04-07
Posting some of the errors might help someone help you.  Also, take a look at the link below which discusses the various parameters to the basic fsck command which might be useful.

[https://www.linode.com/docs/quick-answers/linux/how-to-use-fsck-to-fix-disk-problems/](https://www.linode.com/docs/quick-answers/linux/how-to-use-fsck-to-fix-disk-problems/)

If you have message such as bad sectors, you can't repair that with software.  fsck or similar software will simply mark those sectors as bad so the system does not try to use them.

---

### Post by tomstewart on 2019-04-08
Thanks Yancek. None of the errors have ever mentioned a bad sector (to my knowledge), so hopefully I'm not dealing with that.

The next time I see the errors, I will take note of them and post them here.

---

### Post by yancek on 2019-04-08
Have you run fsck with the a and/or p options shown in the error message your posted?

---

### Post by tomstewart on 2019-04-08
I have never used the a or p options when running fsck. I always just enter "[COLOR=#000000]fsck /dev/sda6"[/COLOR] and and then fix each error one by one by entering "y".

---

### Post by oldfred on 2019-04-09
This is a full fsck set of commands. Second one includes the -y for yes.

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 
    

Are you using a Windows driver to try to read the Linux partitions? They often cause issues.

---

### Post by tomstewart on 2019-05-04
@OldFred: I was not using a Windows driver to read the Linux partitions (that I know of). I wasn't (intentionally) performing any actions across the OS's at all.

Thank you all for your help. But the issue was resolved here:

[https://askubuntu.com/questions/1131942/dualbooting-ubuntu-18-04-and-windows-10-manual-fsck-repeatedly-required-on-ubun](https://askubuntu.com/questions/1131942/dualbooting-ubuntu-18-04-and-windows-10-manual-fsck-repeatedly-required-on-ubun)

I have two 4Gb memory modules in my computer. It turns out that one of them was failing badly, which was causing all the issues.

---

