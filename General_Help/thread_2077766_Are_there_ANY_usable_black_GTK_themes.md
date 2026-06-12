---
title: "Are there ANY usable black GTK themes"
date: 2012-10-29
forum: General Help
---

### Post by Champlin93 on 2012-10-29
I can't seem to find any black GTK themes that actually work right. The problem is somewhere there is always a white background with white text. i.e. with Banshee the column titles are just white on white: [IMG]https://lh6.googleusercontent.com/-dZmnKxAjsBU/UI6MTYDlvTI/AAAAAAAAAII/jFVMiurHabQ/s971/Screenshot+-+10292012+-+09%3A51%3A10+AM.png[/IMG]
Is there ways to work around something like that? I use XFCE4 but this problem happens in other DEs as well.

---

### Post by dino99 on 2012-10-29
i get what i want using gnome-tweak-tool

---

### Post by Frogs Hair on 2012-10-29
What version of Ubuntu ? 12.10 uses 3.6, 12.04 uses 3.4, and 11.10 uses 3.2. I have found that 3.4 themes don't display in certain applications and menus  properly on 12.10 though they work to a point.

---

### Post by Champlin93 on 2012-10-29
> **Frogs Hair said:**
> What version of Ubuntu ? 12.10 uses 3.6, 12.04 uses 3.4, and 11.10 uses 3.2. I have found that 3.4 themes don't display in certain applications and menus  properly on 12.10 though they work to a point.
I have Ubuntu 12.10. Xfce, however uses only GTK2 I believe ([https://wiki.xfce.org/howto/install_new_themes]("https://wiki.xfce.org/howto/install_new_themes")). Themes I've tried are: Cobra(GTK2), Delorean-Dark(GTK-2.0/3.0), Ice Cream GTK(GTK-2.0/3.0), Khali(GTK-2.0), and Xfce-Dusk(Not sure). I just looked in each themes folder to get the GTK versions. Could I maybe just change the text color of that theme somehow?

---

### Post by Frogs Hair on 2012-10-29
I am using the XFCE 4.10 session on 12.10  and have been installing Gnome 3.6 Themes , but some of those themes include GTK 2 and XFWM4 themes also. I am not sure if Gnome 2 themes work on the Gnome 3 applications or not. All 12.10 Ubuntu flavors have Gnome 3.6 under the hood as far as I know.

I have used the Delorean 3.6 theme but didn't notice any problem except for the software center. I don't use Banshee either.

---

### Post by Champlin93 on 2012-10-29
> **Frogs Hair said:**
> What version of Ubuntu ? 12.10 uses 3.6, 12.04 uses 3.4, and 11.10 uses 3.2. I have found that 3.4 themes don't display in certain applications and menus  properly on 12.10 though they work to a point.
I edited I file called gkrc in the Delorean theme and changed the default text to blue(#0099CC). [IMG]https://lh6.googleusercontent.com/-Jt67OYUZyLI/UI65i-1GoPI/AAAAAAAAAIw/ErcXgCe-xqA/s888/Screenshot+from+2012-10-29+13%3A12%3A29.png[/IMG]

---

### Post by Champlin93 on 2012-10-29
> **Frogs Hair said:**
> I am using the XFCE 4.10 session on 12.10  and have been installing Gnome 3.6 Themes , but some of those themes include GTK 2 and XFWM4 themes also. I am not sure if Gnome 2 themes work on the Gnome 3 applications or not. All 12.10 Ubuntu flavors have Gnome 3.6 under the hood as far as I know.

I have used the Delorean 3.6 theme but didn't notice any problem except for the software center. I don't use Banshee either.
Yeah of all the GTK 3.x themes I have they all seem to have GTK2 folders as well. Seems most are made backwards compatible.

---

### Post by vasa1 on 2012-10-29
> **Champlin93 said:**
> I edited I file called gkrc in the Delorean theme and changed the default text to blue(#0099CC). [IMG]https://lh6.googleusercontent.com/-Jt67OYUZyLI/UI65i-1GoPI/AAAAAAAAAIw/ErcXgCe-xqA/s888/Screenshot+from+2012-10-29+13%3A12%3A29.png[/IMG]

gtkrc, not gkrc.

---

