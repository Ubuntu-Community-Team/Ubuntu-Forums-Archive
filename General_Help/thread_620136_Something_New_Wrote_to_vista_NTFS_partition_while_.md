---
title: "Something New: Wrote to vista NTFS partition while it was in hibernate.. files lost."
date: 2007-11-22
forum: General Help
---

### Post by smileypaul on 2007-11-22
Here's something new (for me anyways),
  
 A friend has a dual boot laptop, Vista and Gutsy. Being new to Vista, he didnt realize that the "power" button on the login screen doesnt actually shut the computer down, but only puts it to hibernate mode (thanks for making things more complicated M$) .. 

So, his laptop goes into Hibernate, he then turns it back on, Grub pops up, and he boots into Ubuntu. 

He then mounts the Vista partition using the -o force option. 

He then copies 20gigs off of a NAS onto his Vista partition ..

Now, after rebooting, Vista wakes up.. files are not there. They do not show in either Vista or Ubuntu (TOC problem?).. but.. to top it off,  df --si shows that 20 gigs has been written, but the files cannot be seen, or retrieved.

So,

Does anyone have the slightest idea how we can remove this 20 gigs of "nothing"? saving the data is not important, as we still have a copy on the NAS, but removing it from his local hard drive is important!

Any help is appreciated..

Thanks.:confused:

---

### Post by rune0077 on 2007-11-22
Maybe just try a scandisk (from Vista), see if it doesn't consider this an "error". Else, try and defrag the drive. If its really 20 gigs of "nothing" I think defrag should free it up.

---

