---
title: "Can No Longer Boot From CD/DVD"
date: 2007-10-12
forum: General Help
---

### Post by zetasoul on 2007-10-12
Hi,

I have been trying desparately to find an answer to this problem for weeks now. This is my last resort. I am also a newbie to Ubuntu.

My installation of Ubuntu went smoothly. However, when I want inserted a Windows XP or Ubuntu LiveCD, it will not boot from the CD. Instead it goes straight to the desktop. I know that it might be different with Ubuntu, but in Windows all you have to do is go into the BIOS and set the CD/DVD-Rom as the top priority. I wanted to find something that is equivalent to that. I am not good with terminal/command lines, so any help with GUI would be great!

Ultimately, I want to boot Windows Recovery Console or at least get to the LiveCD menu in order to delete the hard drive. I tried GParted but it won't let me alter the drive because Ubuntu was using it. 

I have a Dell Inspiron 1100 laptop.

Thank you very much.

---

### Post by Pumalite on 2007-10-12
Go into the BIOS and set CD to first in boot order.

---

### Post by bodhi.zazen on 2007-10-12
Bios is the same if you use Linux or Windows.

In my experience if you can not boot a CD, it is either :

1. Improper BIOS settings.

2. Bad CD.

3. Hardware failure.

I have seen situations where the CD will work once the system is booted, but fail to boot from bios.

Sounds like you can not boot several known good CD's so I am betting hardware failure. Open your lappy and check for loose/broken wires, dust, etc ...

---

### Post by HelixAgent on 2007-10-12
It maybe be a BIOS problem, try selecting the "Best last configuration" option in your BIOS.

---

