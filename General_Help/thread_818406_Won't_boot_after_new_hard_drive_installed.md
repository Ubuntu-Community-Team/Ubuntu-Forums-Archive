---
title: "Won't boot after new hard drive installed"
date: 2008-06-04
forum: General Help
---

### Post by evencoil on 2008-06-04
I had two IDE hard drives, the master was a Win2K partition and the slave is a Xubuntu partition.

I wanted to simultaneously get rid of Win2K and upgrade the hard drive it was on, so I figured hey I'll just remove it and pop in the new hard drive.

When I first tried to boot I got some sort of boot disk failure. I tried changing the BIOS to boot off of the slave and I got the same error.

Then I tried booting off the Ubuntu live CD and using Gparted to create an ext3 partition on the new drive.

Now when I try to boot either from the master or the slave I just get nothing.

I assume this has something to do with GRUB or MBR or one of those acronyms, but I haven't had to deal with those yet and have no idea what they are or how they apply to this problem! Any help (or links to guides) would be appreciated. Thanks

---

### Post by Pjotr123 on 2008-06-04
What you need to do is to restore Grub. Apply this how-to:
[http://ubuntutip.googlepages.com/grub](http://ubuntutip.googlepages.com/grub)

Grub was in the MBR of the removed hard disk, that's why...  :-)

Greeting, Pjotr.

---

### Post by evencoil on 2008-06-04
that was exactly what I needed, thanks! :)

---

