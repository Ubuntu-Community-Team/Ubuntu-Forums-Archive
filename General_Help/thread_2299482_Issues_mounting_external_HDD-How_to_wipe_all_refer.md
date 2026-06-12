---
title: "Issues mounting external HDD-How to wipe all references to the drive?"
date: 2015-10-18
forum: General Help
---

### Post by eyeonyouproductions on 2015-10-18
Hello all,
I have been setitng up a media server with an external hard drive to store everything on. I finally got sharing and everything figured out, but suddenly, I have no permissions on the drive, can't mount it. When I went into the terminal to mount it, I got the following error:

Error mounting system-managed device /dev/sdb1: Command-line `mount "/mnt/usb-Maxtor_OneTouch_2HA1LA42-0:0-part1"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I put this drive onto my laptop with Ubuntu, and got no errors. I'm sure I hosed something up when trying to edit settings to make it share correctly across the network. Either way, I can copy the data onto my other external drive and go from there. What I need to know is how to wipe all evidence of the drive ever being connected so I can start fresh. I know that there are a couple of places where it stores the devices uniuque identifiers, I'd just like to kake those go bye-bye... :-) I really only have one drive in the computer, plus the extra partition it makes when it images the drive(Swap file, I'm guessing).

ANy help would be greatly appreciated! Thank you!

---

### Post by sandyd on 2015-10-18
On the media server, can you post the output of
```

cat /etc/fstab
```

Thanks.

---

### Post by eyeonyouproductions on 2015-10-18
Here it is. I left in the commented out parts.

                                                     ```
mikey@Media-Server:~$ cat /etc/fstab            
            # /etc/fstab: static file system information.            
            #            
            # Use 'blkid' to print the universally unique identifier for a            
            # device; this may be used with UUID= as a more robust way to name devices            
            # that works even if disks are added and removed. See fstab(5).            
            #            
            # <file system> <mount point>   <type>  <options>       <dump>  <pass>            
            # / was on /dev/sda1 during installation            
            UUID=c41d8937-c693-42fe-b1ec-d1710f3d209d /               ext4    errors=remount-ro 0       1            
            # swap was on /dev/sda5 during installation            
            UUID=b6af48ba-2c58-482f-9301-407e3fcbc848 none            swap    sw              0       0            
            #/dev/disk/by-id/usb-Maxtor_OneTouch_2HA1LA42-0:0-part1 /mnt/usb-Maxtor_OneTouch_2HA1LA42-0:0-part1 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=Archive 0 0            
            #UUID=F88D-1DE5 /media/archive ntfs-3g auto,users,permissions 0 0            
            /dev/disk/by-id/usb-Maxtor_OneTouch_2HA1LA42-0:0-part1 /mnt/usb-Maxtor_OneTouch_2HA1LA42-0:0-part1 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=archive 0 0            
            mikey@Media-Server:~$ 
```            


Next, I'm gonna figure out how to enable the clipboard for X2Go sessions. :-)

---

### Post by sandyd on 2015-10-18
Add a pound sign "#" in front of
```

/dev/disk/by-id/usb-Maxtor_OneTouch_2HA1LA42-0:0-part1 /mnt/usb-Maxtor_OneTouch_2HA1LA42-0:0-part1 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=archive 0 0

```

I like UUIDs more, but thats up to you :)

Anyways...

Try doing the mount now.
```

sudo mount /dev/disk/by-id/usb-Maxtor_OneTouch_2HA1LA42-0:0-part1 /mnt/usb-Maxtor_OneTouch_2HA1LA42-0:0-part1

```

If there are no errors, then it is your mount options in the fstab that are causing errors.

If you still have errors... then you have another problem. There are many things that could cause this. Output of ```
dmesg
```right after receiving the error would be useful.

---

### Post by eyeonyouproductions on 2015-10-18
Cool, thanks. I'll try that in a little bit, gotta get the kids to bed. I appreciate the help.

---

### Post by eyeonyouproductions on 2015-10-18
OK, that did it. The drive initially disappeared, and I had to go into Disk Manager and turn on/off the whole automatic mounting option to refresh it, but it is mounted now, that did the trick. What's the easiest way to make sure it auto-mounts, since I'm using it as a share, or is it now going to work? Also, you mentioned UUID, I commented out those upper lines trying to make this work in the first place, and those instructions used the UUID, and the UUID for that drive is in there, called UUID=F88D-1DE5. Can I un-comment that line, or will it frak everything up again? And I guess the last one is how much is commented out? Is it all contained on a single line, and I would just remove that one #? I would assume that I would also want to go into fstab and comment out this line I just added...

Once again, thanks for the help, this has me on the verge of being where I need to be. Nerd heaven awaits when I have all of the computers in the house using the same shared databases. :-)

---

