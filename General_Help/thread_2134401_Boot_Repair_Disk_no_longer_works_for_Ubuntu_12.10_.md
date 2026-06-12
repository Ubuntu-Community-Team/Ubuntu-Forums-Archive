---
title: "Boot Repair Disk no longer works for Ubuntu 12.10 x86_AMD64 bit"
date: 2013-04-11
forum: General Help
---

### Post by patagriff on 2013-04-11
Boot Repair won't work for me any more since I went to 64 bit 12.10 version of Ubuntu. Tells me LVM detected and tells me to use Secure Boot Distribution. I'm not installing a new version of my OS just to enable boot repair. Source forge just says the GRUB/LVM are old on the disk version, but when I run the disk, it goes online and updates before running. I don't see what the issue is.

My question is, are their alternatives to Boot Repair, or is their similar software/ solutions for boot difficulties I used to encounter frequently with Ubuntu. I would like to be prepared/ have a disk burnt or tools on a USB stick in the event of difficulties.

Any suggestions?

---

### Post by nerdtron on 2013-04-11
I haven't personally used Boot Repair. Almost all my problems about boot are solved by the forums and a google search. What are your problems specifically? Maybe someone in the forums can help you.

---

### Post by patagriff on 2013-04-11
I am not currently experiencing a boot problem. I was just made aware that my Boot Repair Disk has no LVM and will no longer work for my laptop since I've installed Ubuntu 12.10 x86_AMD64. I'm looking for suggestions of tools I can prepare in case I should experience problems in the future. If I am in the field and my laptop will not boot because of, for example, a grub related issue, thereby preventing me from reaching a forum or the Ubuntu community, I want a disk or USB stick with the tools I need to solve the problem, as I have in the past using Boot Repair Disk.

I guess I'll just download the Secure Remix ISO and burn a live CD with which I can always boot my computer, since this distro already has the latest Boot Repair installed the has the grub/LVM I would need to solve most problems.

I was asking for suggestions of other strategies/tools I might prepare.

---

### Post by oldfred on 2013-04-12
Did you implement full disk encryption? As that does use LVM and adds the extra levels of complication of LVM and encryption.

Boot-Repair has worked for LVM, but has issues knowing if /mapper is RAID or LVM as /mapper may be either. I think it installs the LVM drivers, but is not sure which RAID drivers it needs so may give warning messages. 
And with the encryption you may need to mount it first or else it cannot see into anything that is encrypted.

---

