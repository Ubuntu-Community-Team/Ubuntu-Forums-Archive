---
title: "Microsoft Media Center"
date: 2007-08-06
forum: General Help
---

### Post by sprinkles on 2007-08-06
I've been trying to get my Media Center remote and keyboard to work on Ubuntu.

Here's where I am so far:

I managed to get lirc installed, and running irw, then pressing remote keys shows output. The media keys on my keyboard also show up in irw, but the regular keys do not.

I then found out I'd have to use mod_mce. I compiled it and copied the .ko file to my modules folder.

I then stopped lirc, unloaded lirc_mceusb2, loaded lirc_mod_mce, and ran irw.

Again, the media keys work, but the regular keys do not!

Does anyone have any idea what to do next, as I'm stumped?

---

### Post by tgm4883 on 2007-08-06
Did you follow this 
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

---

### Post by sprinkles on 2007-08-06
> **tgm4883 said:**
> Did you follow this 
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

Yes, that just gets the remote and media keys working, though.

---

### Post by tgm4883 on 2007-08-06
Ok, what are you trying to use the remote to control

---

### Post by sprinkles on 2007-08-06
The keyboard is what I'm trying to get working.

I haven't set up the remote config to control anything yet, but I know it works from irw.

---

### Post by tgm4883 on 2007-08-06
> **sprinkles said:**
> The keyboard is what I'm trying to get working.

I haven't set up the remote config to control anything yet, but I know it works from irw.

Wait, What?  I'm confused.

So do all of your remote control keys work?

And where does your keyboard come into play with lirc?  Is it an IR keyboard?

---

### Post by sprinkles on 2007-08-06
Yes, It's a Microsoft Media Center keyboard.

[http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=038](http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=038)

---

### Post by tgm4883 on 2007-08-06
And the keys dont work in a text editor?  Or the mouse?

---

### Post by sprinkles on 2007-08-06
Nope, neither work.

---

### Post by sprinkles on 2007-08-06
Sorry to bump, but does anyone know?

---

### Post by tgm4883 on 2007-08-06
i've been thinking about it, not sure anymore as I dont have this keyboard so I'm just throwing darts here.

Did you try 

sudo rmmod lirc_mceusb2
sudo modprobe lirc_mod_mce

---

### Post by sprinkles on 2007-08-06
Just tried, still no dice :(

---

