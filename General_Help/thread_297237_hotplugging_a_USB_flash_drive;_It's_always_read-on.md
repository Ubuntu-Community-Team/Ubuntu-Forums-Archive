---
title: "hotplugging a USB flash drive; It's always read-only! How do I get it to mount rw?"
date: 2006-11-10
forum: General Help
---

### Post by joseph221b on 2006-11-10
Hi, Everybody!

I am using Ubuntu 6.10. It's great!

I have a USB flash drive that is formatted FAT (for compatibility with Windows). Whenever I plug it in, Ubuntu detects it, creates a directory in /media for it, and then mounts it. When I unplug it, it unmounts and removes the directory. So far so good.

The problem is that it mounts it read-only every single time. I would like it to be mounted rw automatically.



I have searched online for this for a while, and mostly people say to edit the /etc/fstab file. This is no good, however, because the mounting of removable drives is not handled in fstab the way it is for fixed drives. 

So, how do I get it to mount USB flash drives rw as default? Is there a "hotplug" configuration file that I need to edit?


Thank you.

Joe

---

### Post by kidders on 2006-11-11
Hi there,

Do your system logs indicate a problem with your USB device by any change? Occasionally, corruption/etc. can cause Linux to force a read-only mount, to avoid doing further damage.

Another (perhaps stupid) question ... does your USB disk have a write protect switch on it?

---

### Post by joseph221b on 2006-11-12
Hi, Kidders. Thanks for replying.

To answer your questions:

The USB drive does not have a write protect switch on it. 

I did dmesg, and I get many entries about plugging in the drive. There are no errors, but there is a FAT warning that says:

 FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!


There are also explicit entries that say:

 sda: Write Protect is off


So, it seems that the drive is not write protected. I'm thinking that it is some behavior of whatever mechanism Ubuntu uses for automatically mounting removable media. 

Do you have any idea what this is and what it's called? "udev"? "hotplug"?

If I could find this, then I might be able to configure it.

Thanks.

Joe.

---

### Post by kidders on 2006-11-12
Are you certain the filesystem is write protected? Does the "ro" option appear in the appropriate line of **mount**?

---

### Post by joseph221b on 2006-11-12
Sorry, I must have used the wrong terminology... 
It is indeed mounted "rw", but the problem is that the permissions on the mountpoint are rwx------. Mount options show "umask=077". It all makes sense, other than I could not edit anything on there.

Previously, only root could write to it; it was mounting as root, I guess.

Now for some reason, it is mounting as my current user!!! So, I'm a bit... perplexed? I'm not sure what I'm doing differently now, actually. 


I'm gonna reboot, and see what happens again...


Be back in a bit.

---

### Post by joseph221b on 2006-11-12
ok, well, it seems to be working exactly the way I expect now. 

I am not sure what the problem was previously.

So, now, when I plug in the USB drive, it mounts umask=077, but with current user. So it does everything I need.

Thanks for your help kidders.


I would still like to know where the mount options are coming from. There are a lot of them, such as the uid, gid, umask, iocharset. Is there a config file in /etc that contains these options? Just for example, if I wanted to make something rwxrwx--- someday when it's plugged in, like if I have multiple users switching, or something like that.

If you have any ideas, please tell me.

Otherwise, still, thanks for your time and your help.

Thanks.

Joe

---

### Post by kidders on 2006-11-12
Hehe... Ubuntu isn't made my microsoft, so there's no need to constantly reboot it!

If you use a umask of 077, only the user that mounts the device will be able to access it. You see, since FAT filesystems don't support ownership & access control, you have to specify an artifical user/group/permissions combination to impose on the filesystem. If you don't, Linux will choose defaults that are specifically designed to keep the risk of unauthorised access to your data as low as possible.

Take a look at the vfat section of the man page for mount ... specifically, the uid, gid and umask options. You might find, for instance that mount options like **noauto,noexec,umask=026,users** might be acceptable. If you added them to your /etc/fstab entry for the device:

[LIST]
[*]The device would not be mounted by the root user at startup.
[*]Any user could mount the device with access limited largely (but not *entirely*) to himself.
[*]Another user could then dismount it, and remount it himself to gain full access in his own right, something which is not usually permissable.
[/LIST]

Alternatively, of course, you can play with other systems, like pmount, that can do all this for you, avoiding the need to go fiddling with /etc/fstab altogether.

---

### Post by joseph221b on 2006-11-12
Hi, Kidders. 

Good just about MS! Well, I rebooted in case of something with the init scripts. I was trying a few different things in /etc/udev, and I was not sure if it was read at boot time or every time I plug something in.

I'm familiar with umask, etc., but really unfamiliar with hotplugging and auto detection/mounting. There are a few things happening with hotplug USB beyond that which would happen say, mounting a HD partition. When I plug something in, a directory in /media is created for it, and then it's mounted with a bunch of mount options.

Normally when I deal with HD partitions, I would set up the options in fstab, but now there seem to be a bunch of default options happening.

Is there a way to setup the default options for usb drives?


Take a look at the vfat section of the man page for mount ... specifically, the uid, gid and umask options. You might find, for instance that mount options like **noauto,noexec,umask=026,users** might be acceptable. If you added them to your /etc/fstab entry for the device:

[LIST]
[*]The device would not be mounted by the root user at startup.
[*]Any user could mount the device with access limited largely (but not *entirely*) to himself.
[*]Another user could then dismount it, and remount it himself to gain full access in his own right, something which is not usually permissable.
[/LIST]

Alternatively, of course, you can play with other systems, like pmount, that can do all this for you, avoiding the need to go fiddling with /etc/fstab altogether.



Cool! Is pmount something I call explicetly, or does it run in the background like udev?


Thanks, kidders, for your clear and well thought out explanations. You have a skill in explaining things well without lapsing into too much step-by-step beginner type prose.
 I appreciate it.

Joe

---

### Post by kidders on 2006-11-12
Hey again,

> **joseph221b said:**
> I was trying a few different things in /etc/udev, and I was not sure if it was read at boot time or every time I plug something in.If you're playing with udev rules, you can force your system to refresh them with **udevcontrol reload_rules**. Depending on what you've done, you may then have to unplug & re-attach a device, to see your new rules applied to it.

> **joseph221b said:**
> I'm familiar with umask, etc., but really unfamiliar with hotplugging and auto detection/mounting.Yeah... it's a quagmire of all kinds of little bits and pieces, isn't it?!

> **joseph221b said:**
> Normally when I deal with HD partitions, I would set up the options in fstab, but now there seem to be a bunch of default options happening.That's certainly the *easy* way to make things happen, but it's not always convenient. For instance, you will probably still want your system to be able to handle USB devices it's never seen before (and may never see again!) gracefully ... without having to tweak /etc/fstab.

> **joseph221b said:**
> Is there a way to setup the default options for usb drives?I don't really use tools like pmount/etc. that often myself, but yes, my understanding is that you get quite a good deal of control with these kinds of tools. People use them to handle mounts for devices that are not referenced in /etc/fstab. They run daemonised in the background ... you typically start them with a **sudo /etc/init.d/whatever start** type of command.

> **joseph221b said:**
> You have a skill in explaining things well without lapsing into too much step-by-step beginner type prose. Lol you're more than welcome!

---

### Post by Foopdog on 2006-11-14
Here is my problem. I have an external usb drive that had ntfs which I could read and not write. So, I formatted it with gparted and the whole 320 gig is ext3 now which I was told that this was the way to go since its a native linux fs. Well it mounts when Plug it in and unmounts when I eject  it, but I cannot write to it. It says in the permissions that it is owned by root. I try  to change the permissions, but get "cannot change messages". I am using Edgy which I so far think is awesome and will be Microsoft free after I work out a couple of issues. Help!

---

