---
title: "Gparted messed up, my harddrive wont grow!!"
date: 2008-03-10
forum: General Help
---

### Post by rainbowmagik on 2008-03-10
hello

I used the [COLOR="Red"]Gparted live CD[/COLOR] to grow an [COLOR="Red"]NTFS partition[/COLOR]. The operation [COLOR="Red"]failed[/COLOR].

The [COLOR="Red"]size[/COLOR] of the partition on disk [COLOR="Red"] increased[/COLOR], but the available [COLOR="Red"]storage did not[/COLOR].

[COLOR="RoyalBlue"]Is there someway of fixing my drive?[/COLOR] I've used [COLOR="Red"]scan disk and defrag[/COLOR], but they don't seem to help.

[COLOR="SeaGreen"]Reformatting the whole drive is not an option right now. Thanks for any help!![/COLOR]

---

### Post by scragar on 2008-03-10
you could try shrinking it back down to it's origional size and trying again, although I'm guessing that you'll just encounter the same error message again...

---

### Post by Shazaam on 2008-03-10
What scragar said.
Short of getting into changing cluster size and other disk related settings (which WILL destroy all of your data) you won't be able to change much. You can run tools that help get rid of slack space and such but you run the risk of losing your files.
IMHO the only safe way to get more "Free Space" in Windows is to uninstall programs and defrag the heck out of it. Or save all of your stuff, blank the Windows partition and reinstall Windows.

---

