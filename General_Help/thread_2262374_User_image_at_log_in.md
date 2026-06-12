---
title: "User image at log in"
date: 2015-01-24
forum: General Help
---

### Post by stoneage on 2015-01-24
So, I want to customise this guy on the login screen, preferably one for each user. Can anyone tell me where it is or what it is called, and can I have a unique one for each user?

[ATTACH=CONFIG]259461[/ATTACH]

[http://www.pasteall.org/pic/82773](http://www.pasteall.org/pic/82773)

Ubuntu Gnome with the Mate desktop environment. 

:)

---

### Post by deadflowr on 2015-01-24
I think you just need to look for User Accounts(maybe users and groups) and then click on the image next to the username and then select whatever image you want.

---

### Post by stoneage on 2015-01-24
'Contacts' and 'About Me' don't show the image, just a space to put one. I want to first amend the original existing image, but can't find it in the file system.

---

### Post by deadflowr on 2015-01-24
Having no idea which display manager ubuntu-gnome uses, running Ubuntu-mate i found it uses the lightdm-gtk-greeter.
So looking through that I found it sets the default image from LoginIcons, in the icons directory.
LoginIcons has an index.theme file which lists where the icons are actually stored. Humanity, hicolor, and gnome.
So looking through each of those I found what is MY default avatar in Humanity >> stock >> pick a size.
(Basically i found the one used in mate in /usr/share/icons/Humanity/stock/32/stock_person.svg)

Of course as i stated, I really have no idea what display manager you are using, gdm or lightdm.
And as such if using gdm, I don't know how it is configured.

But I would think that those icons folders would be a place to start...

---

### Post by stoneage on 2015-01-24
These come up for the Gnome log in screen, but you were right. 

I found the .svg in  /usr/share/icons/gnome/scalable/status/ Dunno if it is loaded from there but I'll do some experimenting.

Thanks :)

---

### Post by deadflowr on 2015-01-24
Yeah, I decided for fun to install gdm to see, and unfortunately for me, I need to learn more about how it works, in terms of it's configurations.
Lightdm has very easy to understand config files, so digging around to find where things are is easy. Mostly because I'm used to doing that.

But I had not changed anything and the avatar image looked like the one you posted in the image.

Like I posted I would think it's a starting point.

As well, I enjoy these learning experiences, so...

---

