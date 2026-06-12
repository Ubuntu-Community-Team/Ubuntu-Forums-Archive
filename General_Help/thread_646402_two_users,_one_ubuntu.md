---
title: "two users, one ubuntu"
date: 2007-12-21
forum: General Help
---

### Post by tubunu on 2007-12-21
I would like to ask if it's possible to setup a login screen avatars for each of the users at the login prompt. I think Windows has this option where you click on your avatar and you provide a password to enter your setup. 

Can this be done in Ubuntu? (I KNOW it's possible, but how?) :P

---

### Post by Sergio Moura on 2007-12-21
You need a GDM theme that can do it.
Download it, install and change it on the Login Manager (under Administration)
An GDM example theme: [http://www.gnome-look.org/content/show.php/Avio-GDM?content=37395](http://www.gnome-look.org/content/show.php/Avio-GDM?content=37395)

Good luck,
- Sergio

---

### Post by tubunu on 2007-12-21
Thanks, it looks good! What a pity though Ubuntu doesn't have it by default. :(

---

### Post by floke on 2007-12-21
You can change your avatar - in gnome - via system/preferences/about me - and click on the avatar to change it.

---

### Post by CatKiller on 2007-12-21
> **tubunu said:**
> What a pity though Ubuntu doesn't have it by default. :(

Strictly speaking, it's a security risk, since it means that some hypothetical unauthorised user doesn't need to guess any user names. Also, I believe that Ubuntu does come with some GDM themes that include a face browser, so it's easy enough to change to one if you want.

---

### Post by adam.tropics on 2007-12-21
Go to the login window preferences. Then from the 'local' tab, just select 'plain with face browser', or 'themed with face browser' in the style section.

---

### Post by tubunu on 2007-12-26
Thanks.

---

### Post by tubunu on 2007-12-26
I got it working. Now, I'd like to change the user icon for each of the users. In Login Window, Users tab I have an option to choose an icon of my choice, but it says the image needs to be stored in **gdk-pixbuf supported format**. Could someone please explain what it is?

---

### Post by adam.tropics on 2007-12-26
Sort of! This link may not mean much...but have [a read]("http://developer.gnome.org/arch/imaging/gdkpixbuf.html"). Basically, you want a photo in GIF,         JPG, PNG, TIFF,or XPM format.

---

### Post by tubunu on 2007-12-26
Right, thanks! 

Now, the other question is, having a png picture (32 by 32 pixels) where do I place it in the file system so that it can be accessed by the GDM login prompt? I already tried copying the pictures to /home/user  and  /usr/share/icons  directories. And in both cases all I get at the login is the default login icon (which can be found in /usr/share/icons/gnome/32x32/stock/generic/stock_person.png, *see attachment*)

I'm not sure how to replace it. 
Btw, I'm using Ubuntu default welcome theme with face browser. (Human List)

---

### Post by adam.tropics on 2007-12-26
If I'm not mistaken, it ia a hidden file in the user's home directory, saved as .face

It can be set if the user uses system-->preferences-->about me, or saved there manually.

---

### Post by tubunu on 2007-12-27
Thank you, it worked perfectly! :)

---

