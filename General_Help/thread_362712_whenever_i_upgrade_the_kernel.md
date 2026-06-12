---
title: "whenever i upgrade the kernel"
date: 2007-02-15
forum: General Help
---

### Post by Mateo on 2007-02-15
grub always incorrectly covers up information.  for example it incorrectly puts in hd(0,0) when mine is hd(0,2) and it also incorrectly uses hda1 when mine is sda3.  how do I tell it what the correct values is so that I don't have to manually do this whenever I upgrade.

I'd also rather it not complete erase my windows entry every time.

this is a big deal for non-techies.  imagine loading your computer and these values are wrong, but you have no idea what these values mean, let alone that they might be wrong.  This is ubuntu's fault, from where i stand.

---

### Post by jazzgossen on 2007-02-16
Have a look at GRUB's configuration file /boot/grub/menu.lst

It's not very clear, but it's all in there. What you want to do is set the groot value to (hd0,2), and remember not to uncomment that line, just change it. Also, to keep your Windows entry, move it past the "### END DEBIAN AUTOMAGIC KERNELS LIST" line.

---

### Post by andrill on 2007-02-16
Hi,
I had the same problem, in my case I edited the "###BEGIN AUTOMAGIC KERNELS LIST" section in the/boot/grub/menu.1st file. It seems to be used as a template for what parameters are used in new menu entries.
If I change the entry that says:
# groot=(hd0,0)
to for example
# groot=(hd0,2)
then next time a new menu item is created, hd0,2 will be used for root device.

cheers

---

### Post by Mateo on 2007-02-16
ok, i'll try altering the menu.1st and see what happens next time.

---

### Post by Mateo on 2007-02-23
> **andrill said:**
> Hi,
I had the same problem, in my case I edited the "###BEGIN AUTOMAGIC KERNELS LIST" section in the/boot/grub/menu.1st file. It seems to be used as a template for what parameters are used in new menu entries.
If I change the entry that says:
# groot=(hd0,0)
to for example
# groot=(hd0,2)
then next time a new menu item is created, hd0,2 will be used for root device.

cheers

Ok, that's 1 of the problems.  I also have the problem where it:

1) changes sda3 to hda1.  

2) Also, it deletes my windows entry.

---

### Post by konst88 on 2007-02-23
Add you windows entry after the:
#####END AUTOMATIC KERNEL LIST####

---

### Post by Mateo on 2007-02-23
> **konst88 said:**
> Add you windows entry after the:
#####END AUTOMATIC KERNEL LIST####

I want it to be at the top of the list so that it's the default.

---

### Post by Mateo on 2007-02-23
Bump still want to know:

1) how to make my windows entry at the top of the list, without grub overwriting it whenever a new kernel is upgraded.

2) How to make it so that it correctly puts my linux dev as sda3, instead of hda1.

---

### Post by konst88 on 2007-02-23
You may put it on the very top of the file, not sure if it will work..
Or you may change the default entry, which is much better solution.

---

### Post by Tomosaur on 2007-02-23
> **Mateo said:**
> Bump still want to know:

1) how to make my windows entry at the top of the list, without grub overwriting it whenever a new kernel is upgraded.

2) How to make it so that it correctly puts my linux dev as sda3, instead of hda1.

It's probably a better idea to keep it below the automagic line, and just grub to boot to it by default. To do this, edit the /boot/grub/menu.lst file, and set this line:
```

default 0

```
To whatever OS you want to boot into by default. The first item in the list is 0, second is 1, third is 2, etc etc. The 'Other Operating Systems' line **is** included in the count.

Alternatively, check the link in my sig to avoid editing the menu.lst file by hand.

---

### Post by Mateo on 2007-02-23
> **Tomosaur said:**
> It's probably a better idea to keep it below the automagic line, and just grub to boot to it by default. To do this, edit the /boot/grub/menu.lst file, and set this line:
```

default 0

```
To whatever OS you want to boot into by default. The first item in the list is 0, second is 1, third is 2, etc etc. The 'Other Operating Systems' line **is** included in the count.

Alternatively, check the link in my sig to avoid editing the menu.lst file by hand.


This won't work.  When I upgrade the kernel, the numbers change, so windows would no longer boot.  Here's an example of what I mean.  Let's say the list looks like this:

0 - Ubuntu 2.6.1.....

1 - Ubuntu 2.6.1.....SAFE

2 - Ubutnu memtest

3 - Windows


If you set it to 3 it works... until a kernel upgrade.  Then this is what happens:

0 - Ubuntu 2.6.2.....

1 - Ubuntu 2.6.2.....SAFE

2 - Ubuntu 2.6.1.....

3 - Ubuntu 2.6.1.....SAFE

4 - Ubutnu memtest

5 - Windows

So windows is no longer #3 on the list, so it wouldn't boot there by default.  That's why it needs to be at the top of the list.

---

### Post by Tomosaur on 2007-02-23
> **Mateo said:**
> This won't work.  When I upgrade the kernel, the numbers change, so windows would no longer boot.  Here's an example of what I mean.  Let's say the list looks like this:

0 - Ubuntu 2.6.1.....

1 - Ubuntu 2.6.1.....SAFE

2 - Ubutnu memtest

3 - Windows


If you set it to 3 it works... until a kernel upgrade.  Then this is what happens:

0 - Ubuntu 2.6.2.....

1 - Ubuntu 2.6.2.....SAFE

2 - Ubuntu 2.6.1.....

3 - Ubuntu 2.6.1.....SAFE

4 - Ubutnu memtest

5 - Windows

So windows is no longer #3 on the list, so it wouldn't boot there by default.  That's why it needs to be at the top of the list.

You can stop this behaviour and force grub to only show the most recent kernel, or however many you want. I recommend 2 different kernels as a minimum. Again, in menu.lst - find the line which says:
```

howmany=all

```
and change it to
```

howmany=2

```

or whatever number you want. Again, the link in my sig will allow you to do this. This will stop the length of the boot menu from changing,

---

### Post by Mateo on 2007-02-23
ok, I will give that a try then.  I only keep 1 kernel installed at a time though.  It's only in the gap between installing a new kernel and making sure everything works fine before uninstalling the previous kernel that this problem occurs.  I'd rather never have to edit menu.lst again.

That leaves the 1 problem of grub replacing the correct sda3 with the incorrect hda1.

---

### Post by Rui Pais on 2007-02-23
> **Mateo said:**
> ok, I will give that a try then.  I only keep 1 kernel installed at a time though.  It's only in the gap between installing a new kernel and making sure everything works fine before uninstalling the previous kernel that this problem occurs.  I'd rather never have to edit menu.lst again.

That leaves the 1 problem of grub replacing the correct sda3 with the incorrect hda1.

hi, check for entrys like
> # kopt_2_6=root=/dev/hda1 ro
# kopt_2_6_16=root=/dev/hda1 ro
# kopt_2_6_17_10=root=/dev/hda1 ro
and replace the hda1 with sda3. Do not remove the # from beginning of line. 
The notation is self explanatory, i think...


Edit:
btw, another way for your to keep Windows as entry zero and keep as kernel as you wish is to set the updatedefaultentry as:
> # updatedefaultentry=true
and set the default for Windows.

I didn't try but that should keep Windows entry and point to it is as default.

---

### Post by Mateo on 2007-02-23
> **Rui Pais said:**
> hi, check for entrys like

and replace the hda1 with sda3. Do not remove the # from beginning of line. 
The notation is self explanatory, i think...

Thanks, I will try that.  BTW, what do those entries mean?  I'm afraid that a future kernel upgrade will create new ones, will it?  I'd rather not have to ever edit menu.lst if possible.  thanks.

> Edit:
btw, another way for your to keep Windows as entry zero and keep as kernel as you wish is to set the updatedefaultentry as:

and set the default for Windows.

I didn't try but that should keep Windows entry and point to it is as default.

i'll try that too, thanks.

---

### Post by Mateo on 2007-02-23
Wait a second, I don't uncomment the sda3 part?  What about the part to change it to hd(0,2), do I uncomment that or not?

---

### Post by Rui Pais on 2007-02-23
> **Mateo said:**
> Wait a second, I don't uncomment the sda3 part?  What about the part to change it to hd(0,2), do I uncomment that or not?

No.

do not uncomment nothing between the lines:
> ## DO NOT UNCOMMENT THEM, Just edit them to your needs
and
> ## ## End Default Options ##

Comments on that section are double ##.

Ubuntu grub updater (some part of dpkg i think...) reads the commented lines (#) and act according to it, while grub still reads the file normally. 
A weird choice, indeed, a separate conf file would be simpler and create less confusion :(

---

### Post by orb9220 on 2007-02-23
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

