---
title: "cant complete BU of win hd"
date: 2016-02-27
forum: General Help
---

### Post by zdvdla on 2016-02-27
Hi,
I am sorry if this is a newbe question but there are so many fragments of answers out there I can't put them all together to make one complete one.
I have a win laptop I want to sell so I want to back up everything, reformat like new, then sell.
The hd is in a HP pavillion that has a very strange hd connection. It connected directly to the MB with no cable, it just snaps in place. So taking it out to copy is not an option.
What is the best way to do this?
I have tried this before by booting linux cd and tried to copy, but got an error  'invalid or incomplete multibyte or wide character'  after 2 gigs...

any help would be great...thank you

---

### Post by oldos2er on 2016-02-27
Is this an NTFS partition? If so I'd run Windows' chkdsk on it to verify if it's healthy or otherwise.

---

### Post by zdvdla on 2016-02-27
thank os2er

yes it is ntfs...win 7 says it needs to be formatted...sees it as wd my passport and correct size in Disk Management...linux mounted it fine the first time I connected it, and still sees it...now I am looking at hooking up another drive to copy the laptop to but fear the same thing..
Since it was mounted on Linux, I used the GUI and dragged and dropped...then got the error..then I copied and pasted...same error...
should I try the command line, and if so, what precautions if any can I take?
Shouldn't drag and drop work? I read that Linux may put strange charcters in filenames so it might fail due to that. There is a switch that will correct that issue but is there a "best practices" for backing up ntfs from ntfs using linux running on a cd? 

Thank you guys...I know it seems like a trivial issue but it has had me confused for hours how something so simple can turn out to be such a time consuming ordeal...

---

### Post by sandyd on 2016-02-27
Use clonezilla -> [http://clonezilla.org/](http://clonezilla.org/)

Get another drive (external) and plug into the computer. Boot using Clonezilla, and you should be able to backup to the external drive.

---

