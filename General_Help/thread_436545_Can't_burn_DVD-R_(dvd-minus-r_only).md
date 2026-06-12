---
title: "Can't burn DVD-R (dvd-minus-r only)"
date: 2007-05-07
forum: General Help
---

### Post by slumcat05 on 2007-05-07
**UPDATE: I've (reluctantly) installed an old copy of Windows to run the drive's firmware update, and am now able to burn DVD-R. Unfortunately I can no longer burn CD-R or CD-RW, the drive is reported as having no media present, as if the disc is invisible. I was having some problems with CD-RW media before the firmware update as well, but I just assumed I had bad discs. Now after the update and with new discs, still no dice. If anyone has any further advice on what to do next, it'd be much appreciated.**


I'm trying to burn an ISO image to a DVD. I can successfully burn the image to a DVD+RW and a DVD+R, but this type of disc doesn't seem to be supported by the DVD player I'm trying to play it on (yes, it's old). According to HAL Device Manager I have a SONY DVD RW DRU-710A. It shows the following values (among many) for the drive:

```
storage.cdrom.dvd = true
storage.cdrom.dvdplusr = true
storage.cdrom.dvdplusrdl = true
storage.cdrom.dvdplusrw = true
storage.cdrom.dvdplusrwdl = false
storage.cdrom.dvdr = true
storage.cdrom.dvdram = false
storage.cdrom.dvdrw = true
```

When I insert a blank DVD-R (minus), a new node called "Unknown Device" appears on the devide tree under the SONY DVD RW DRU-710A (I'm guessing "Unknown Device" is the volume, whereas SONY is the drive). It has these notable values:

```
volume.block_size = 0 (0x0)
volume.disc.capacity = 4706074624 (0x118810000)
volume.disc.has_audio = false
volume.disc.has_data = false
volume.disc.is_appendable = false
volume.disc.is_blank = true
volume.disc.is_rewriteable = false
volume.disc.type = dvd_r
```

When I try to burn in K3b, it doesn't even let me start the burn, and where the device is listed it says "Please insert an empty DVD+/-R(W) medium..." GnomeBaker  attempts to start the burn, but crashes after a few seconds with this error message:

```
Executing 'builtin_dd if=/media/My Book/Cruise_vid.iso of=/dev/hdc obs=32k seek=0'
/dev/hdc: "Current Write Speed" is 1.0x1352KBps.
:-[ WRITE@LBA=0h failed with SK=2h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type
```

The "right-click --> write to disc" feature crashes almost instantly and gives the error message "Unhandled error, aborting."

My guess is that maybe the volume is reorting its type as "dvd_r", but the drive thinks it should be able to handle "dvdr", so maybe there is a difference with the naming conventions for disc type? I have not tried another brand of DVD-Rs (I'm using Memorex), because I don't want to waste money on useless media if I can't get this fixed. Is there any way to change the "dvd_r" or "dvdr" values (I tried changing them in the HAL Device Manager, but they just automatically switch back after typing in the box, even when running it with sudo privileges...) or is there a way to add a disc type to the drive so that it will recognize the media? Any help or advice would be greatly appreciated, sorry for the unusually long post. Thanks in advance.

---

### Post by slumcat05 on 2007-05-07
Forgot to mention:

When I insert the media, it automounts and asks if I want to "Make DVD" or "Ignore" (like it should) and the icon on the desktop says "Blank DVD-R Disc." Also, inside K3b, in Settings -> Devices, under the Sony drive there is a line that reads "Writes DVD-R(W):        yes." So why do K3b and GnomeBaker not realize the disc is DVD-R, when clearly Ubuntu does (as evidenced by the desktop icon?). I am running the latest versions of K3b and GnomeBaker from the distros on Feisty.

---

### Post by strixy on 2007-05-07
There is a firmware upgrade for your burner.

[http://sony.storagesupport.com/dvdrw/firmware.htm#710](http://sony.storagesupport.com/dvdrw/firmware.htm#710)

But then again, you bought a Sony... I'm a little, uhhhh...  politically apathetic? where Sony is concerned.

---

### Post by slumcat05 on 2007-05-07
Thanks, I'll give it a shot. I have also developed a distaste for Sony and its products lately, but this drive was purchased quite a while ago, before I was so world-wise. Unfortunately, I'm too poor to get a better drive. Thanks for the tip.

---

### Post by strixy on 2007-05-07
Also check out 

[https://help.ubuntu.com/community/CdDvdBurning](https://help.ubuntu.com/community/CdDvdBurning)
> 
      Install the dvd+rw-tools package. See [InstallingSoftware].

      Use the packages growisofs application to burn a DVD or Blu-Ray disc.
```

growisofs -Z /dev/scd0 -R -J /some/files

growisofs -speed=2 -dvd-compat -Z /dev/dvdwriter=dvd_image.iso
```

---

### Post by slumcat05 on 2007-05-08
Yup, tried growisofs earlier, it gives the exact same error as GnomeBaker, so I'm guessing that is the command GnomeBaker uses. As far as the firmware, thanks again for the tip. Unfortunately Sony only released a patch for Windows machines, and I can't get Wine configured to recognize the DVD drive, so I guess I'm screwed on this until I can get a new drive (I'd rather do that than pay for a copy of Windows anyways). Thanks for your help.

---

### Post by orb9220 on 2007-05-08
If they have the firmware in a bin file with a flash program in  exe format you can copy to floppy then you can flash the firmware with a bootable floppy.

Alot of drives hav a dos version floppy and a windows gui installer for firmware, You just have to look closer and see if they offer both versions.

---

