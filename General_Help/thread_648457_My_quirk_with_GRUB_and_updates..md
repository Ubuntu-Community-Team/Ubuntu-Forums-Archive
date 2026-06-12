---
title: "My quirk with GRUB and updates."
date: 2007-12-23
forum: General Help
---

### Post by Tristra on 2007-12-23
Hi, I have been using UBUNTU with a dual boot along side Win XP pro for about a year.
A few months ago I installed 7.10 to try it out. After some grub tweeks to got the dual boot to work it runs fine but every now and then when I update my grub to tries to load ubuntu from a drive I don't have.
it should be : ubuntu loading from (hd0,1)
                   win loading from (hd0,0)
but it re wrights ubuntu to load from (hd2,1)

as you have probably guessed there running on the same drive.
It doesn't seem to affect loading windows but ubuntu has been reset three times in two months.
I can use the grub edit commands to fix it within 30 sec (it is just a  hassle). 

I just was wondering if any one else has had this problem and if so has any one found a long term solution.

---

### Post by oscarsfriend on 2007-12-23
Take a look here: [http://ubuntuforums.org/showthread.php?t=648377](http://ubuntuforums.org/showthread.php?t=648377)

---

### Post by meierfra on 2007-12-23
This should fix your problems once and for all.

Open a terminal (Applications->Accessories->Terminal)
 Open the file "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Look for the line

#groot (hd2,1)

(it is somewhere in the middle of the file)
Change it do

#groot(hd0,1)

Save and close  the file. In the terminal type

```
sudo update-grub
```

That's it.

---

