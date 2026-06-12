---
title: "Making a script to automatically copy attached disks"
date: 2007-01-19
forum: General Help
---

### Post by Ted_Smith on 2007-01-19
Hi

An unusual request this one....

I want to write a script that will run off a CD and enable a user to do the following in the numbered order : 

1. Boot a PC 
2. Run a terminal based flavour Ubuntu (or Linux generally)
3. Put Linux into overall read-only mode 
3. Scan the PC for all attached disk drives including SCSI and USB
4. Render the results as a selectable menu such as 'Press 1 for disk A' etc
5. Enable that selection to be the 'target' device in **read-only mode**
6. Enable another selection to be the 'destination' device in **write enabled mode**
8. Run MDS5sum on the target device and store the MD5 hash value in a log file on the target device
7. Run DD using fixed options that basically tell DD to image the target device to the destination device and then pipe the output via gzip (dd....| gzip > image.img) to compress the image.
8. Run MDS5sum again but this time on the image stored on the destination device and store the MD5 hash value in a log file on the destination device
9. Compare the two hashes spitting out an error if they mismatch. 

So I have what I want to do, but I'm not sure what commands I'll need to do it. Can anyone help? 

(BTW - I know there is a GUI that does something similar called AIR (Automated Image & Restore) but I want my script to run off the CD and within a terminal rather than using a GUI.)

Thanks

Ted

---

### Post by kidders on 2007-01-19
Hi there,

Interesting script!

> **Ted_Smith said:**
> 3. Put Linux into read-only modeNot quite sure what you mean by that. If Linux can't write to anything, it can't do much!

> **Ted_Smith said:**
> 3. Scan the PC for all attached disk drives including SCSI and USBThere are lots of ways of doing that, most of which involve using sysfs (directly or indirectly). Perhaps one simpler option would be to probe devices attached to /dev/sd? and /dev/hd? for readable filesystems.

> **Ted_Smith said:**
> 4. Render the results as a selectable menu such as 'Press 1 for disk A' etc
5. Enable that selection to be the 'target' device in write-mode
6. Enable another selection to be the 'destination' device
That's a pair of "mount" commands, I suppose.

> **Ted_Smith said:**
> 8. Run MDS5sum on the target device and store the MD5 hash value in a log file on the target device
7. Run DD using fixed options that basically tell DD to image the target device to the destination device and then pipe the output via gzip (dd....| gzip > image.img) to compress the image.
8. Run MDS5sum again but this time on the image stored on the destination device and store the MD5 hash value in a log file on the destination device
9. Compare the two hashes spitting out an error if they mismatch.As your plan stands, the MD5 sums will always mismatch, since one image will be gzipped and the other won't. In any case, a good place to store MD5 sums temporarily would be a RAMdisk, rather than on one of the physical devices your script will be playing with.

Here's a quick (messy) suggestion to get you started. It creates a large number of variables based on the output of **vol_id**, so you have some information at hand to give to users of your script. Successfully probed devices are numbered, so If you wanted to get, say, the UUID of device #2, you'd find it in **$dev2UUID**. Similarly, the filesystem type of, say, device #3 is at **$dev3TYPE**. I've used the variables created to throw together a sort of a menu. You could ask your users to pick a number and use the selected partition's UUID to mount it someplace.

```
DEVICES=0
for f in /dev/sd[a-z]?*; do
        INFO=`vol_id $f`
        if [ $? -eq 0 ]; then
                let DEVICES=DEVICES+1
                `vol_id $f | sed "s/ID_FS_\(\w*\)\=\(.*\)/export dev$DEVICES\1=\2/"`
        else
                echo "Couldn't read $f"
        fi
done

for i in `seq 1 $DEVICES`; do
        printf %3d $i
        eval printf %20s "\$dev"$i"USAGE"
        eval printf %20s "\$dev"$i"TYPE"
        eval printf %20s "\$dev"$i"LABEL"
        echo -en "\n"
done
```

On my box, the script fragment does this:
```
Couldn't read /dev/sdb3
  1                raid   linux_raid_member        AoE    
  2          filesystem                ext2              cctv
  3          filesystem                ext3              Ubuntu
  4               other                swap                    
  5          filesystem                ext3              Gentoo
  6               other                swap                    
  7          filesystem            reiserfs
```

Once you ask for two numbers, perform your md5sum and mount **$dev**X**UUID** and **$dev**Y**UUID**, you're half way there. :-)

---

### Post by Ted_Smith on 2007-01-24
Thanks very much for that response. It is very comprehensive and gives me a few places to start.

Regarding the MD5 issue - I mis-wrote that. What I meant to say was two things. First I need an MD5 of the finished DD image set for integrity purposes so that no one could claim the image had been tampered with between it being created and subsequently access some days or weeks later. Yes - I realise it would be different from the MD5 hash of the actual source device itself. But I also need an MD5 hash of the source to be taken before the DD image begins. 

Does anyone know though, of a guide where I could learn about setting up my own customised Linux boot CD? I know you can set various aspects of it and p'package it'? For example, Dam Small Linux, and various others, are all the Linux kernel with bits added and removed and customised?

---

### Post by kidders on 2007-01-24
> **Ted_Smith said:**
> Thanks very much for that response. It is very comprehensive and gives me a few places to start.No problem. :-)

> **Ted_Smith said:**
> Regarding the MD5 issue - I mis-wrote that.Yeah, I figured you understood what needs to happen there, so I didn't go into it in my last post. I can't help wondering if there's a way of avoiding the *dramatic* slowdown md5sum-ing and then dd-ing a large partition would create. One of us is bound to come up with something clever! Hehe.

> **Ted_Smith said:**
> Does anyone know though, of a guide where I could learn about setting up my own customised Linux boot CD? I know you can set various aspects of it and p'package it'? For example, Dam Small Linux, and various others, are all the Linux kernel with bits added and removed and customised?I can't help you there, I'm afraid. :-( The distro I'm most familiar with is Gentoo, which I find *incredibly* flexible, when it comes to doing odd things with it. That's not to say it would be your best option though ... I'm just resorting to what I know hehe.

This may be blatantly obvious to you already, but I would suggest compiling your own kernel, with a wide range of I/O-related bits built as modules, and running the whole thing from a RAMdisk. There is one thing that concerns me...

I wonder what would happen if you ran your script on a box with limited RAM and very large hard disks. Do you suppose you would run into trouble md5summing, dd-ing, etc? What I'm driving at is whether it would be worth your while investigating ways of distinguishing whether it is safe to hijack swap partitions. (I'm assuming there's an easy way to detect whether swap space contains a hibernate image, for instance.)

Hell... maybe that's over-thinking things!

---

### Post by Ted_Smith on 2007-03-14
As excited as I was about this, it seems that something that acheives the same aim but to a much higher standard than I could have achieved myself has already been done : The Advanced Forensic Format (AFF) - [http://afflib.org](http://afflib.org). There's even packages in the Ubuntu Packages for use with Edgy (but not Dapper). It's basically for forensic practioners (which I am, and this is why I wanted to create something as described) but it can be used as a thorough backup procedure. 

2007-Jan-23: AFFLIB Version afflib-2.2.0 was released

Ted

---

