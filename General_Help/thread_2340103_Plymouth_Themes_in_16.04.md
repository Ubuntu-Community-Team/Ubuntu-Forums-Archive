---
title: "Plymouth Themes in 16.04"
date: 2016-10-15
forum: General Help
---

### Post by Kpenguin on 2016-10-15
Hello,
I've just recently installed 16.04 and I would like to customize the startup splash screen with a theme such as [this]("https://www.gnome-look.org/p/1009456/"). However, it seems the old way of doing this no longer works. How do I change this as of 16.04?

Thanks!
Kpenguin

---

### Post by Portaro on 2016-10-15
What is the old way that you use like a guide?

Based on that I know the process to change a Pymouth theme is:

Download the theme and put him on &#8594; /lib/plymouth/themes

Install theme &#8594;
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/mytheme/mytheme.plymouth 100

Then charge the theme to the system -
&#8594; sudo update-alternatives --config default.plymouth

Choose your new theme

And finally make the theme active to initramfs -
&#8594; sudo update-initramfs -u

See more questions like your here for example &#8594;  [http://askubuntu.com/questions/2007/how-do-i-change-the-plymouth-bootscreen](http://askubuntu.com/questions/2007/how-do-i-change-the-plymouth-bootscreen)

---

### Post by Kpenguin on 2016-10-16
/lib/plymouth/ no longer exists in 16.04. The method you posted is what I've used in the past, but that directory doesn't exist anymore.

---

### Post by deadflowr on 2016-10-16
It's in /usr/share/plymouth now

---

### Post by Kpenguin on 2016-10-16
I did some looking around and found the new directory for Plymouth Themes is /usr/share/plymouth/themes/. If anyone else is trying to do this, just switch the directories in Potaro's post with that directory.

---

### Post by Kpenguin on 2016-10-16
Thanks deadflower!

---

### Post by deadflowr on 2016-10-16
> **kpenguin said:**
> i did some looking around and found the new directory for plymouth themes is /usr/share/plymouth/themes/. If anyone else is trying to do this, just switch the directories in potaro's post with that directory.

> **kpenguin said:**
> thanks deadflower!

:p
comical how timing works sometimes.

---

### Post by Portaro on 2016-10-16
If the path change all you need is replace the path by the correct way for example &#8594; (obviously You you need to put the theme extracted on /usr/share/plymouth ...)
[COLOR=#000000]sudo update-alternatives --install [/COLOR][COLOR=#000000]/usr/share/plymouth[/COLOR][COLOR=#000000]/themes/default.plymouth default.plymouth [/COLOR][COLOR=#000000]/usr/share/plymouth[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]themes/mytheme/mytheme.plymouth 100

[/COLOR]:popcorn:[COLOR=#000000]
[/COLOR]

---

### Post by Kpenguin on 2016-10-16
The funny thing is I haven't actually been able to see my new plymouth theme in action because Ubuntu boots so fast with my SSD. :D

---

### Post by deadflowr on 2016-10-16
> **Kpenguin said:**
> The funny thing is I haven't actually been able to see my new plymouth theme in action because Ubuntu boots so fast with my SSD. :D

Install or enable a bunch of useless services, like powerd. :biggrin::twisted:

---

