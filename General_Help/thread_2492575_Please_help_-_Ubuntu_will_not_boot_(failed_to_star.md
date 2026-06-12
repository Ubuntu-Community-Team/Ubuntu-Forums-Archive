---
title: "Please help - Ubuntu will not boot (failed to start default.target)"
date: 2023-11-15
forum: General Help
---

### Post by doug81873 on 2023-11-15
Hello All,

I am having a very bad problem with Ubuntu - it will  not boot and I am wondering if I can fix this and recover my files or if  all is lost.

Basically what happened is this, I completely ran  out of drive space and now when I attempt to boot I get a "failed to  start default.target" error. I have already tried system recovery, which  freezes up and does not allow me to select any options on the list such  as free disk space. I have also already tried a live USB boot repair,  which did not work either.

Just to note - when I installed I chose ZFS file encryption (if I remember correctly).

If  anyone can help I would greatly appreciate it because there were  important files that I need to recover on the drive. I am relatively new  to Linux so if you can be detailed and provide command lines I would be  forever grateful. Thanks in advance!

---

### Post by Rubi1200 on 2023-11-16
Hi and welcome to the forums -:)

We need to try and see what is going on.

In my signature there is a link to the boot info script.

You need to boot using the liveUSB and then follow the instructions to create a summary report. Post the link to the pastebin back here so we can analyze the situation.

Thanks.

---

### Post by MAFoElffen on 2023-11-16
Do instead, the 'system-info' script in both our signature lines... I contribute to the 'boot-info' script and am the author of the 'system-info' script. I submitted how I chroot into encrypted ZFS systems to Yannubuntu, but that logic isn't included in the 'boot-info' script yet... The right tool to get the info we need right now to help you will be from the 'system-info' script. When you start the script, instead of using "./system-info", do "./system-info --details" so it will show more info on ZFS. 

Once you post the URL of that report, either i will give you instructio for chrooting into encryted ZFS-On-Root installed system from the information there...

If you installed manually, for ZFS-On-Root, then wait for instructions. If you installed, from the Installer, and checked it's box, then it does it like below... They did that a bit "Special".

Or if you do not want to wait on me, search my username and "zfs encrypted chroot"...  Look in the 'boot-info' dev thread, and I posted what I do for the regular LUKS encrypted ZFS-On-Root, which is included somehwhat in 'boot-info'.

I found one of the posts I did for Encrypted ZFS-On-Root if installed from the Ubuntu Deesktop ZFS installer scripts: [https://ubuntuforums.org/showthread.php?t=2491426&p=14160347#post14160347](https://ubuntuforums.org/showthread.php?t=2491426&p=14160347#post14160347)

That is from any recent Ubuntu Installer LiveUSB... After chrooting into it, then check to what is full from doing 
```

sudo zfs list

```
And posting the output of that in a post, withing CODE Tags (refer to the CODE Tags link in my signature line).

Important, when you are chrooted in, do not turn off the machine without exiting gracefully... Those instructions are later in that thread... Or
```

exit
mount | grep -v zfs | tac | awk '/\/mnt/ {print $3}' | \
    xargs -i{} umount -lf {}
zpool export -a

```
That will unmount the mounts, and shutdown the filesystems in the pools gracefully.

---

