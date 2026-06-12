---
title: "really need some help here..."
date: 2007-03-03
forum: General Help
---

### Post by mzilhao on 2007-03-03
ok, so i was using dapper and my system was working fine. 

i thought i'd try feisty out, so i installed it to a separate partition (my 'distro testing' partition). it seemed to work fine, so i decided to install it to my 'regular' partition.

after doing so, i'm now unable to boot to the newly installed feisty!
the booting process just freezes on
```
Attached scsi generic sg1 type 0
```
it just stays there forever...

but the weird thing is that i can boot just fine into Windows XP and to the feisty on my 'distro testing' partition!

i now have feisty on two separate partitions, but i only have access to one. it's really annoying...

so, what can i do? any ideas?

thanks,
Miguel

---

### Post by floke on 2007-03-03
I don't have any answer to this, but am just thinking that it might help if you gave details about what you actually did. Did you, for instance, install over Dapper? Did you delete the partition and then install into it? Or did you upgrade to Feisty from within Dapper itself?

---

### Post by mzilhao on 2007-03-03
thanks for your reply.

i deleted dapper and then installed feisty using the alternate CD. i installed grub to the mbr. 
i left my 'distro testing partition' untuched with the feisty i had already installed.

what's really strange is that about one month ago i decided to try debian etch. i installed it to my 'distro testing' partition, and it worked fine, along with dapper and win XP. 
after a week or so, i decided i was going to use etch as my main OS, so i deleted dapper and installed etch to my primary partition. 

after i did that, i could not boot into debian! i got the same error, the booting process would freeze on "Attached scsi generic sg1 type 0".

at the time i thought i had done something wrong and gave up on debian. installed dapper, and everything was working again.

but now i'm having the same issue with feisty! 
basically, feisty / etch only worked when they were installed to the 'testing' partition...

---

### Post by floke on 2007-03-04
The only thing I can think of (although my 'thinking of' list is fairly limited) is something perhaps to do with your grub file (/boot/grub/menu.lst) which is perhaps pointing to the wrong place?

---

### Post by mzilhao on 2007-03-04
i thought so as well, i changed a few settings but it didn't do any good...

in the end i managed to solve the problem by fiddling with the SATA drive settings on the BIOS. i put it on 'Native Mode' (whatever that means...) and it worked!

anyway, thanks a lot.

---

### Post by floke on 2007-03-04
Well, a fat lot of use I was, but glad you got it sorted.

---

### Post by floke on 2007-03-04
Well, a fat lot of use I was, but glad you got it sorted.

---

