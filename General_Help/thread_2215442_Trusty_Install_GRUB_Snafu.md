---
title: "Trusty Install GRUB Snafu"
date: 2014-04-06
forum: General Help
---

### Post by moore.bryan on 2014-04-06
So, after upgrading to Trusty to test it out, attempting to install ElementaryOS later, and going back to Trusty, I now only have a GRUB prompt... no matter what, Ubuntu won't launch. I'm at wits-end... I've tried reinstalling GRUB by reinstalling the entire system AND chroot method, as well with no luck.

I've also tried the boot-repair program and that was only helpful in getting me back into Windows.

Any ideas where I can start debug this? Thanks, in-advance...

---

### Post by oldfred on 2014-04-06
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

    

Best to see where you are at.
Second install or Elementary probably has its grub in MBR, but Boot-Repair should have installed Ubuntu's grub to MBR?

---

### Post by moore.bryan on 2014-04-07
Yeah, I was an idiot and never copied the pastbin... 

I can confirm boot-repair *did not* install grub to mbr.

---

### Post by grahammechanical on 2014-04-07
If you are getting a grub rescue prompt then Grub installed somewhere and is loading. But it may not be finding its grub.cfg file or a Linux kernel where it is expecting to find one.

Regards.

---

### Post by moore.bryan on 2014-04-28
Sorry for the long delay in responding; life took over for a while...

Sadly, I'm not very familiar with the GRUB rescue prompt... precisely what commands can I use the actually get Ubuntu going, then?

---

### Post by oldfred on 2014-04-28
You can rerun BootInfo report and post new link.

---

### Post by moore.bryan on 2014-04-29
I'm leery to screw around with the boot any longer because I don't have the time to troubleshoot and/or not have a working computer; last time, it took me three days to get back into the Windows boot.

Is that really the only/best option?

EDIT
Well, I'm clearly impatient because I went ahead and did what you suggested anyway oldfred after reading through the thread in your signature. I followed the second post by spryte in that thread--deleting my bios_grub partition and then using boot-repair--and that seemed to do it; however, even though I followed boot-repair's commands to a "T," I received any number of errors along the way... I've pasted them here, as well as my bootinfo:
[http://paste.ubuntu.com/7359264](http://paste.ubuntu.com/7359264)
[http://paste.ubuntu.com/7359326](http://paste.ubuntu.com/7359326)
[http://paste.ubuntu.com/7359351](http://paste.ubuntu.com/7359351)
[http://paste.ubuntu.com/7359354](http://paste.ubuntu.com/7359354)

Now, I have one last question--at least for the moment: my laptop still boots into Windows boot manager by default, requiring me to continuously hit the ESC key to get a boot selection, to choose Ubuntu, and then I see GRUB with Windows listed. How, exactly, can I have it boot straight to GRUB or is that a bios thing?

---

### Post by oldfred on 2014-04-29
Boot-Repair usually includes this:
       sudo efibootmgr -v

That should show the UEFI entries and one should be ubuntu. And then in your UEFI/BIOS you should be able to change boot order to make ubuntu first. Some have one list, others have two lists where one is hardware and the other just the efi folders or Windows & ubuntu entries. 
Many have reported that any Windows maintenance or updates reset Windows to first in boot order, but Ubuntu does not seem to do that.

Some UEFI have been modified by the vendor to only boot Windows and there are work arounds for that.

You still have a grub in the protective MBR that now will not work. But if you do try to boot in BIOS mode you will just get a grub error.

It also looks like you are missing a Windows partition. Just like grub has to have a bios_grub to boot in BIOS mode because in gpt partitioning there is no space after MBR and grub put core.img into that space. But Windows also puts serial numbers, encryption info or DRM type data in that space in BIOS systems. So it now also has a small system reserved partition for that and it needs to be just in front of the first NTFS partition. You now have Ubuntu in front. 
I would shrink the sda3 by 128KB and create a system reserved partition.

      
 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

---

### Post by moore.bryan on 2014-04-29
Thanks for the quick reply, oldfred, but you lost me in a lot of the technical stuff... I can boot into both Ubuntu and Windows now, no problem; however, I cannot set Windows to be the default OS loaded by GRUB, even though I have it set that way in /etc/default/grub. Any ideas there?

---

### Post by oldfred on 2014-04-29
What setting did you use in /etc/default/grub?
I prefer to use descriptions, not a number.

Does this entry work to boot Windows?

```
menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 2407-37A0
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}
```

You must keep Windows fast boot or always on hibernation off, or you will have issues. 

 find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default  here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by moore.bryan on 2014-04-29
I've successfully figured it out; I considered all other possibilities and realized I was likely being a moron and never ran "update-grub." Yup. Me=dufus.

Thanks for all the help, I figured it all out!

---

### Post by oldfred on 2014-04-29
I also always forget the update-grub, too. :)

Glad you got it working.

---

