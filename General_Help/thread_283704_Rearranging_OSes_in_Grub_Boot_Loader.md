---
title: "Rearranging OSes in Grub Boot Loader"
date: 2006-10-24
forum: General Help
---

### Post by sbjaved on 2006-10-24
I want to bring Windows XP at the top instead of Ubuntu at startup...How do i do that? So that if i don't touch a key the PC *automatically* boots Windows.

---

### Post by ahaslam on 2006-10-24
gksudo gedit /boot/grub/menu.lst

arrange the boot options as desired ;)

Tony.

---

### Post by glotz on 2006-10-24
[http://www.gnu.org/software/grub/manual/grub.html#default](http://www.gnu.org/software/grub/manual/grub.html#default)

---

### Post by mssever on 2006-10-24
Here's a GUI Grub editor: [http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

---

### Post by kerry_s on 2006-10-24
You can also have it boot the last OS used by changing this line->

default		0
To->
default		saved
 
And it will boot what ever you used last.

---

### Post by user1397 on 2006-10-24
the best thing to do is to change the part that says "default 0" to whatever place the OS is in.  for example, if you got the two kernel entries, the memtest, the "Non Debian OS's one, and then windows, the you would put "default 4" because the first entry is o, not 1, so it goes 0, 1, 2, 3, 4.

rearraging the actual OS's is not encouraged, as grub has a smart and safe way of arranging the os's accordingly

---

### Post by mssever on 2006-10-24
> **erik1397 said:**
> the best thing to do is to change the part that says "default 0" to whatever place the OS is in.  for example, if you got the two kernel entries, the memtest, the "Non Debian OS's one, and then windows, the you would put "default 4" because the first entry is o, not 1, so it goes 0, 1, 2, 3, 4.

rearraging the actual OS's is not encouraged, as grub has a smart and safe way of arranging the os's accordingly

I haven't actually tried this, but I don't think it will work. When a new upgrade comes out, the old kernel is not removed from the list. So if Windows is number 4, after the upgrade it will become number 6, unless you manually remove the old kernel.

---

### Post by user1397 on 2006-10-24
> **mssever said:**
> I haven't actually tried this, but I don't think it will work. When a new upgrade comes out, the old kernel is not removed from the list. So if Windows is number 4, after the upgrade it will become number 6, unless you manually remove the old kernel.yes that happens, so then you should either test out the new kernel, and if it works fine, remove the old one, or you can go back to the /boot/grub/menu.lst file, and change the "default 4" to "default 6"

---

### Post by sbjaved on 2006-10-25
Thankyou. That solved it.

---

