---
title: "Issues with Kubuntu"
date: 2015-04-21
forum: General Help
---

### Post by Kpenguin on 2015-04-21
Hi everyone,
Recently, I've been having an issue with Kubuntu. At times, none of the system applications work and I have to force shutdown of my computer to fix it. For example, system settings won't open, shutdown/logout commands don't work, etc. Also, sometimes the authentication window doesn't open when I need to install a program or change user settings and I get a error window that says "Action failed since proper authentication was not recieved". As I said, the only way to fix this is to force shutdown of my computer using the power button. Anyone know what's going on here?
I also have Unity, XFCE, and GNOME installed as desktop environments if that helps any. I haven't had any issues with them.

---

### Post by mastablasta on 2015-04-22
> **Kpenguin said:**
> 
I also have Unity, XFCE, and GNOME installed as desktop environments if that helps any.

it actually doesn't help. especially since we do not know how you installed them. you might have some conflict between desktops  or some applications. hard to say. your description of the problem doesn't provide any clues to the errror. i suggest you use only one desktop since you can't use all of them at once anyway. choose which one you like best and use that one.

i mean for example by default Gnome uses GDM to login while kubuntu is using lightdm. form your post i can't tell which one is having the issue. etc. 

if applicaitons do not work you can try running them form terminal (konsole) which should provide any error ouput.

---

### Post by timgood on 2015-04-24
Try this: press CTRL ALT F2 to open a terminal. Then type rm -rf .Xauthority 
After a reboot, you may find things work again.

---

