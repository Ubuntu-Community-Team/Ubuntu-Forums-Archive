---
title: "How to restore GRUB to the MBR?"
date: 2007-12-14
forum: General Help
---

### Post by Scooter7 on 2007-12-14
Hi,

I reinstalled Windows XP, and, as I knew would happen, I lost grub due to a mbr overwrite.   I know it's possible to get it back, and I used these directions:

```
sudo su -
grub
find /boot/grub/stage1
root (hd0,2)
setup (hd0)
quit
```

But I get 'Error 15: File not found' when I run the find command.   I've checked various threads around the forum, including this one: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351), but these instructions return the same error:

> Mine was a slightly different story. I couldn't get grub to find the stage1 file or even recognizemy drive. So I borrowed some knowledge I picked up while using Gentoo:
You have to mount your root partition using the livecd:

```
sudo mkdir /mnt/root
```

```
sudo mount -t ext3 /dev/sda6 /mnt/root
```

Then you have to mount the proc subsystem and udev inside /mnt/root also:

```
sudo mount -t proc none /mnt/root/proc
```
```
sudo mount -o bind /dev /mnt/root/dev
```


I've seen this method:

> 1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

But I don't want to try that, since the command line option doesn't work, and I don't want to mess up and destroy my Ubuntu install.   My setup is like this: I have Windows and Grub installed to my internal hdd (hd0), and Ubuntu installed to my external hdd (hd1, I assume).  

 Any suggestions?

---

### Post by Craigus on 2007-12-14
Try supergrub :

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by froy02 on 2007-12-14
It seem that you went to the wrong root from the result of "find /boot/grub/stage1' 
your code: 'root (hd0,2)' could not be right because you said ubuntu is installed on a different hard drive "external hard".  it should have returned (hd1,x).

hd0,3 refers to the first hard drive, 3rd partition.
for the code: root (hdx,x) use what the code: 'find /boot/grub/stage1' returns. like i said it should not be (hd0,2) since ubuntu is installed in an external drive.as you said.

---

### Post by Scooter7 on 2007-12-14
froy02,

I couldn't get the output of 'find /boot/grub/stage1', so I couldn't know the proper value.   Craigus' solution worked, though.   I booted off of the SuperGrub disk, and restored grub.   I'm posting this from my Ubuntu installation now.

Thanks,

---

### Post by rockinlinux on 2007-12-14
the best way to do this is to boot from a super grub disk, it will take you 5 mintes to restore your grub to the MBR. In my opinion everyone should have this disk as it can be a life saver!! :)

---

