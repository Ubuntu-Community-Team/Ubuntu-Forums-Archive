---
title: "Test tools to detect bad sectors on hard disk?"
date: 2018-12-20
forum: General Help
---

### Post by dimmetrix on 2018-12-20
I recently bought a new 1TB hard drive and I would like to do a  couple of tests before I start using it (I prefer to know if there are  problems or there may be problems now before it is too late).
  
The question is: How useful or how to scan it?


  In Windows when a unit is formatted with zeros, if there is a  defective sector, the unit automatically reassigns it for a new one  (tests performed in this scenario). In Linux I'm not sure if this  happens and I do not have to do these tests anymore. So, I can think of  some options and at the same time some doubts:
  
1. Format the unit with zero fill If there are bad sectors, will they be replaced by new sectors automatically as in Windows?

2. Execute the badblocks tool. This tool although I  consider it very good, for a new disc I do not know if it is too  exaggerated since it tests with 3 different patterns; demanding more  time and wear, perhaps, unnecessary. Can only 1 pattern be programmed?  Would it be advisable for this case?

3. Run tool F3 - Fight Flash Fraud. This tool writes a file  occupying the entire space of the unit and then checks it, so that the  following tests (write / read / test) would be executed. It is used to  detect fraudulent pendrives and because after writing the file it proves  it, I suppose that this would detect any error in sectors of the  surface. For what I think is a good alternative for testing.

These are the options that occur to me and I would like to be told,  which of these options would be best applied in cases of new discs and  also in cases of used discs and why.

---

### Post by QIII on 2018-12-20
Moved to ***General Help***

---

### Post by dimmetrix on 2018-12-20
> **QIII said:**
> Moved to ***General Help***

Thanks!

---

### Post by HermanAB on 2018-12-20
There are utilities called badblocks and smartctl, which you can use in conjunction with fsck.

Whether those utilities actually work, or will chew up and destroy a perfectly good disk and cause your hair to fall out in the process, I don't know...

---

### Post by CatKiller on 2018-12-20
> **dimmetrix said:**
> In Windows when a unit is formatted with zeros, if there is a  defective sector, the unit automatically reassigns it for a new one  (tests performed in this scenario). In Linux I'm not sure if this  happens and I do not have to do these tests anymore. 

That's nothing to do with Windows. The drives do that themselves. All drives from the last two decades can do that.

Smartctl, part of smartmontools, will display the results of the drive's self-tests.

Fsck gets run at boot time every *n* boots to check the integrity of the filesystem.

Keep regular backups.

---

