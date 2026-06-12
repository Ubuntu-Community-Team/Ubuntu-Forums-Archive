---
title: "Dead Xenix machine"
date: 2008-03-10
forum: General Help
---

### Post by matthamer on 2008-03-10
Hello!

I read with great interest [the following post on]("http://ubuntuforums.org/showthread.php?t=593180") this forum. I have a similar situation actually, so wondered if you knowledgeable folks could assist further.

An old engineering database system is on a 234MB hard drive, which suffered mechanical fault. I had the drive sent away to a lab for reconstruction and the data was returned on a giant 80GB. The file system indeed shows up as Xenix Root. However, booting the machine shows a "NO OS" error. 

I thought [this would do the trick]("http://docsrv.sco.com:507/en/HANDBOOK/sstT.no_os.html"), but I just don't have a boot image. Nor can I find one. There are no floppy disks for the machine anywhere to be found.

I was advised to try using [ftp://ftp.caldera.com/pub/SLS/xnx264.n1.Z](ftp://ftp.caldera.com/pub/SLS/xnx264.n1.Z) but it looks like this is some kind of patch or update. Booting from the disk just results in a stream of Es appearing on screen. (????)

I'm trying to just view the contents of this disk to see if anything is salvagable. Apparently in the other forum post, someone has said that if the machine runs Oracle, then it's possible to grab the DB and import it. 

I really don't have much background about the machine, other than it has been around the building for many many years and has lots of important info. (Same old story, I guess!) I just am trying to salvage what is possible.

Can anyone provide a link to a boot image? Would this even work with different hard disk geometry? Can I generate an image of the drive and mount it in linux?

THANK YOU!

---

### Post by nlong on 2008-03-10
It looks like the info in the following post could be useful.  I don't expect you would be able to boot from the recovered hard drive, and given the importance of the data, creating a direct copy of the drive (or 2) might not be a bad idea before beginning.  Your best bet is to try and mount the disk from inside a running linux installation on an already running machine, possibly even a live cd.   Much of the info from [http://ubuntuforums.org/showthread.php?t=593180](http://ubuntuforums.org/showthread.php?t=593180) would be helpful for doing just that.

---

### Post by matthamer on 2008-03-10
> **nlong said:**
>  Your best bet is to try and mount the disk from inside a running linux installation on an already running machine, possibly even a live cd. 


Alrighty - I am on a Windows box (urgh) attempting this with the Ultimate Boot CD and running a linux boot disk on M$ Virtual PC. I imaged the drive and now I have the virtual drive installed in the machine. so far so good. I can see the disk with the 234~ MB partition.

hda4 is listed in the dmesg as the partition in question, but when i try and mount it 

```
mkdir /mnt/xenix
mount -t xenix /dev/hda4 /mnt/xenix
```

it fails! with "no device found". d'oh. can you tell i'm a newbie?????

Where am I going wrong?

THANKS:)

ADDITIONAL:

With another boot disk, it said "xenix not supported by kernel" - ****! what boot disk would support xenix?????

---

