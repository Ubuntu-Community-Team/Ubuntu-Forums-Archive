---
title: "Rescue partition table"
date: 2007-01-15
forum: General Help
---

### Post by that guy on 2007-01-15
Hmm...where to begin??

I have 160G hard drive (hdold) with 130G of music on it.  Several hours ago it was in my windows machine and formatted NTFS.  My plan was to move it into my Linux box, but first I thought it best to reformat it to ext3 so that it would play nice and we'd all live happily ever after.  

So I acquired another 160G hard drive (hdnew) and put hdold and hdnew both in the linux box and fired up the LiveCD.  I formatted hdnew "sudo mkfs -t ext3 /dev/hdb".  (Apparently I should have done something different here.)  Then I mounted both the drives and proceeded to copy everything from hdold to hdnew.  

Once that was finished, I made sure the files were all there.  Then I proceeded to format hdold in the same way.  Then I copied all of the files back from hdnew to hdold and again checked that they were all there.  Finally, I moved hdnew into the hda position and installed a fresh copy of Edgy.  I did not add hdold until later, because I wanted to mount it myself. (probably a mistake)

Now when I type "sudo fdisk -l" I get

[INDENT]Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19175   154023156   83  Linux
/dev/hda2           19176       19457     2265165    5  Extended
/dev/hda5           19176       19457     2265133+  82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdb doesn't contain a valid partition table[/INDENT]

Can I save this?  Am I screwed?  Please tell me no.  The data has to still be there.  Is there a way to make a new partition table without losing all the data.

Thanks in advance for any help that anyone might have.

PS My linux skills are not the best, so please use noob talk.

---

### Post by logos34 on 2007-01-16
Try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").  Worked like a charm for another poster just the other day.

---

