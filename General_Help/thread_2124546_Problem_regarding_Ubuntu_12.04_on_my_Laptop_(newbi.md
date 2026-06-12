---
title: "Problem regarding Ubuntu 12.04 on my Laptop (newbie here)"
date: 2013-03-11
forum: General Help
---

### Post by techbuntu27 on 2013-03-11
First stop. So I am somewhat new to Linux, been using it for a month or so but I am not that expert specially with deeper things about it, I hope you can assist me regarding this problem of mine.

Okay, First, I'm using a Laptop which is ([http://www.asus.com/Notebooks_Ultrabooks/K43SJ/](http://www.asus.com/Notebooks_Ultrabooks/K43SJ/)) and my problem is that everytime I boot my laptop the* "Screen Brightness" *is bump up to its full settings, it's so very bright and I keep on adjusting it everytime I turn on this laptop and its annoys and bothers me a lot.

Second is that, the *Grub menu *seems to be so enlarge? and the *Ubuntu logo *during start-up is also too big or so enlarge this making it look odd because its blurry. I've done dual booting before on my desktop and samsung netbook. But it's my first time to have this type problem especially the *Brightness *and the *too enlarge thing. *Although I had already installed the *recommended graphics drivers *for this laptop, still the problem persist. I hope you guys can help a newbie like me and assist me to solve this problem that I'm having right now. Thanks

Here's some shots: 

[IMG]http://i.imgur.com/V0WkvW8.jpg[/IMG]

[IMG]http://i.imgur.com/DMix7zb.jpg[/IMG]

---

### Post by zero2xiii on 2013-03-11
Hay,

Grub and boot screen animations and such is not much affected by the "graphical drivers" since they are loaded somewhat later.
Screen brightness is also a relative common issue under laptop users.

Fixing the issues:
[http://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution](http://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution)

It seems like from what I read (via google) that this will fix the boot screen aswell..

Good luck :)

---

### Post by techbuntu27 on 2013-03-12
I did the steps but none of them works. I don't know, maybe I've done something wrong.

It states that > [COLOR=#333333][FONT=Ubuntu Beta]Reboot and press and hold [/FONT][/COLOR]shift[COLOR=#333333][FONT=Ubuntu Beta] to display your grub. Press [/FONT][/COLOR]C[COLOR=#333333][FONT=Ubuntu Beta] to enter console mode.
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]Type [/FONT][/COLOR]vbeinfo , [FONT=Ubuntu Beta][COLOR=#333333]this will display various stuff how grub recognizes your display. At the bottom is "preferred mode" - in your case it should say 1200x800. Note down the value.[/COLOR][/FONT]. 

But when I typed vbeinfo, this is the result [IMG]http://i.imgur.com/vzIg7vq.jpg[/IMG]

I also search for other solutions: [http://askubuntu.com/questions/127851/change-boot-screen-resolution](http://askubuntu.com/questions/127851/change-boot-screen-resolution) and also tried the "[Grub Customizer]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183")[FONT=Ubuntu Beta][COLOR=#333333]" still none of them works [/COLOR][/FONT]:(:(:(:confused::confused::confused:

---

### Post by techbuntu27 on 2013-03-14
*bump

---

