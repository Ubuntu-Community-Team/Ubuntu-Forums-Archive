---
title: "Done with MS; How to remove GRUB"
date: 2008-06-16
forum: General Help
---

### Post by momo07 on 2008-06-16
I would know how how to remove the GRUB, so I can boot straight up the box with the one and only> HARDY

---

### Post by prshah on 2008-06-16
> **momo07 said:**
> I would know how how to remove the GRUB, so I can boot straight up the box with the one and only> HARDY

You shouldnt remove GRUB since it carries other options (such as recovery mode and memtest) that will be useful in the future. If you want to remove entries related to your windows installation, post the contents of your "/boot/grub/menu.lst" here for specific instructions.

---

### Post by Titan8990 on 2008-06-16
Ubuntu uses grub no matter how many operating systems you have. If you remove GRUB you will not be able to boot into **any** OS. You can remove Windows from the GRUB boot list via your menu.lst file located in /boot/grub/.

$gksudo gedit /boot/grub/menu.lst

---

### Post by MacAnthony on 2008-06-16
If you want to change the timeout or other settings in grub so that it boots quicker into your OS and which it chooses as the default, you could edit the /boot/grub/grub.conf file too.

---

### Post by Happy_Man on 2008-06-16
As an extension on what Titan8990 said, you can set up GRUB so that it doesn't show the menu every time you boot up. Run the command he's posted, and then find the line that says ```
#hiddenmenu
``` and delete the #. Now the menu will be, well, hidden, unless you press escape.

---

### Post by Happy_Man on 2008-06-16
> **MacAnthony said:**
> If you want to change the timeout or other settings in grub so that it boots quicker into your OS and which it chooses as the default, you could edit the /boot/grub/grub.conf file too.
I believe in Ubuntu, the file is /boot/grub/menu.lst, as there is no grub.conf in that folder. :p

---

### Post by waspbr on 2008-06-16
you can also download startup manager from synaptic, which basically is a GUI for grub editing. There you can select to boot automatically to whatever OS you want.

---

### Post by MacAnthony on 2008-06-16
> **Happy_Man said:**
> I believe in Ubuntu, the file is /boot/grub/menu.lst, as there is no grub.conf in that folder. :p

My mistake. It's been a while since I've modified grub and at the moment, I only have access to a CentOS box, which does still have a grub.conf. Sorry if I caused any confusion.

---

