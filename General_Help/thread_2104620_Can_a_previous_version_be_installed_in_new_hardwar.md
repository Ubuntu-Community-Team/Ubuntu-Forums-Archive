---
title: "Can a previous version be installed in new hardware?"
date: 2013-01-13
forum: General Help
---

### Post by DVD-R on 2013-01-13
Hi,
Please excuse me if I should be posting this in the beginners section.
I wasn't sure.
I've been a ubuntu user since 2008
My favorite version was ubuntu 10xx

I am replacing my main PC which has Ubuntu 10.04 on it with my favorite applications.

Is it feasable for me move over this version along with the apps I installed onto a new machine?

Perhaps use the 10.04 live-cd to install the OS, and then install the packages from a personal store instead of the online repositories.

Is this possible?
And if so, where do I find instructions for doing this.
*** HUGE THANKS!!! ***

---

### Post by oldos2er on 2013-01-13
10.04 desktop support ends in a few months, so you should weigh whether it's worth it to install it now and need to upgrade soon, or install 12.04 which will be supported until April 2017.

---

### Post by DVD-R on 2013-01-14
Hi Ann,
Thanks for your response.

Can you advise on how one would go about migrating a current ubuntu setup to a new machine?

If the process is not too extensive, it would save hours of desktop customizations and application installs.

Any info would be greatly appreciated!!

---

### Post by oldos2er on 2013-01-14
If possible I would install the hard drive from the old machine into the new one, or get a USB enclosure for it and copy the data that way.

---

### Post by ibjsb4 on 2013-01-14
Like Ann said, HDD to HDD and you could use clonezilla to do that.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by DVD-R on 2013-01-15
Sweet!!
I think Clonzilla might work....but I've never tried it.
Is there a possibility that standard file permissions will interfere?

I believe I tried to copy the contents of the HD out to a thumb drive by booting up in an install CD and using the file manager.
However if I remember, I got stopped with a file permissions issue.

Perhaps I will have to boot up the old system as ROOT and reset the permissions to the files first?

Or does Clonzilla somehow provide a work around the permissions issue?  Perhaps its not something I should worry about and just try it.

Thanks both of you for your help!!!
I'll let you know how it goes :)

---

### Post by ibjsb4 on 2013-01-15
You do not boot into your system at all.  Clonezilla comes on a live CD and will boot its self up, just like the ubuntu live CD will boot its self up.

Use the beginner (not advance) option, copy hdd to hdd and you do not want a snapshot.

---

### Post by asmoore82 on 2013-01-15
Big +1 for Clonezilla - it operates below the filesystem layer and outside of the normal OS, no worries :D.

---

