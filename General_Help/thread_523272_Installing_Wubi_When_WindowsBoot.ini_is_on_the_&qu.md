---
title: "Installing Wubi When Windows/Boot.ini is on the &quot;D&quot; Drive"
date: 2007-08-11
forum: General Help
---

### Post by marioluigi123 on 2007-08-11
I recently tried to install Wubi (a different version from the current) and was able to install just fine until I rebooted to boot into Ubuntu. I selected Ubuntu on the boot loader screen, and I can't quite remember the exact error messages, I was able to surmise that the problem was due to my Windows installation (along with boot.ini) being on the D:\ drive, while Wubi was trying to install it's images on the C:\ drive. I remember reading the Ubuntu wiki page about "install.exe" and seeing the FAQ with a very similar question to mine. It said that there was no solution at the time.

Flash forward to just a week ago. I tried the newest version of Wubi (and was impressed at the new look and feel) but now the program won't even set up the virtual drive correctly.

I realize that this is probably a somewhat unusual case, but I'm hoping someone can solve this problem. In case you're wondering why the Windows install is on the D:\ drive, I think (this is a secondary computer so I'm not sure of the specifics) it's because a second hard drive was installed and this drive was cloned. They are actually two separate hard drives, not just one drive with two partitions.

So, to sum this up nicely, is there a way to use Wubi if your main drive is not the "C" drive?



By the way, this: :popcorn: is just completely random.

---

### Post by ago on 2007-08-13
Should be possible, uninstall everything and then install the latest version. Make sure there is an ubuntu entry in boot.ini

---

### Post by marioluigi123 on 2007-08-13
So back in the day with earlier versions, this was a valid concern, but now it's not?

I suppose I will try it again though, seeing as how it failed at a completely different point the most recent time around.


EDIT: I tried again, and I (thankfully) managed to get further than ever before. I installed Wubi on D:\ using the form field on the installer, rebooted the system as per normal operation, and waited while it booted and loaded all sorts of things. Well, all seemed fine until it got to the 'installing base system' portion. A dialog with an error saying that the 'base system' could not be installed showed up, and it suggested skipping the step by selecting a new step from a menu that popped up. Of course, all the later steps didn't work either - presumably because they need something from the 'base system' step. So, is there any way of fixing this problem?

EDIT Part 2: Well, I tried installing one more time just to be sure, and it installed. I didn't change a thing so I guess something unlucky was happening before. Unfortunately, I'm still in trouble. After the Ubuntu splash screen loads to about 65%, I got a huge wall of text talking about tty(numbers 1-6) being terminated and respawning too quickly. I have no idea what to do with that. Is that an Ubuntu problem, or a Wubi one?

---

