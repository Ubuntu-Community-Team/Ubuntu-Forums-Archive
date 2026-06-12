---
title: "Some Help Needed"
date: 2007-02-26
forum: General Help
---

### Post by Loner_Tech on 2007-02-26
Hello guys am a linux noob just installed ubuntu its a dual boot with xp being a noob i cant solve two of my problems the first problem is when i installed ubuntu i saw 3 options in grub menu ubuntu normal, mode ubuntu recovery mode and other o/s: win xp pro last night i updated ubuntu and since then am seeing 4 ubuntus they all are same 2 are normal boot options and two are recovery mode options both have exactly same names and it looks pretty annoyin to me can anyone help me over this please? and my other problem is i installed fluxbox but now my whole desktop is totally blank i dont even get the file manager running in fluxbox can anyone tell me how do i get those gnome mode icons and thoe start menus like applications and firefox shorcut i mean can i have a gnome type desktop in fluxbox? i wud be really thankful to u guys if u help me.

---

### Post by Tesiph on 2007-02-26
It might help if you use punctuation.

1. The other 2 options will stay there, and are not a problem. They just start the previous kernel in case the new one doesn't work.

2. Fluxbox doesn't have desktop icons

---

### Post by smartbei on 2007-02-26
Ummm....why did you install fluxbox?

Anyway, when logging in there is a button on the bottom left corner of the screen named options (I think) and through it in one of the options you can pick which Desktop Environment you want to boot into.

---

### Post by RedSquirrel on 2007-02-26
> **Loner_Tech said:**
>  and my other problem is i installed fluxbox but now my whole desktop is totally blank i dont even get the file manager running in fluxbox can anyone tell me how do i get those gnome mode icons and thoe start menus like applications and firefox shorcut i mean can i have a gnome type desktop in fluxbox? i wud be really thankful to u guys if u help me.


Fluxbox can be made to have a GNOME-like appearance, but it will take a fair bit of configuration to get that. Fluxbox has a very basic appearance when you first install it, but it can be made very pretty with some effort. See the links in my sig for info on configuring Fluxbox.

In terms of a menu, you get to the Fluxbox menu by right-clicking on the desktop. If there's nothing in your menu when you start Fluxbox, you need to create the menu:

1. Press Ctrl-Alt-F2 to go to a virtual console.

2. login with your username and password.

3. at the prompt ($), type

```
sudo update-menus
```and press ENTER (this will ask for your password; enter it).

4. type 

```
exit
```and press ENTER

5. press Ctrl-Alt-F7 to go back to the gdm login window.


When you login to Fluxbox, you should now have a menu when you right-click on the desktop.


EDIT:

I added numbers to the steps above and a few more words to make things clearer (I hope!).

By the way, Fluxbox is very configurable, but by itself it doesn't offer all of the panels and other stuff that GNOME and KDE have. Those are available separately, though, if you want them. With those "add-ons", you can have desktop icons, panels, and all sorts of eye candy if you like.

If you want a desktop that is suitable for an older system, you might want to give Xubuntu a try, since it has panels and desktop icons and stuff like GNOME has, but it uses Xfce, which has lower system requirements than GNOME.

Anyway, I am also curious about your reasons for installing Fluxbox. Don't get me wrong. I think Fluxbox is great and I use it all the time; you just need to be aware that it takes some work to get it to look and behave exactly as you want.

---

