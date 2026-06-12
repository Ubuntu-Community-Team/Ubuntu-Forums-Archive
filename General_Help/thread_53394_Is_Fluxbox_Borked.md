---
title: "Is Fluxbox Borked"
date: 2005-07-31
forum: General Help
---

### Post by Omnios on 2005-07-31
Hi im playing aroudn with Fluxbox as aperently it can do some amazing things with the desktop. The problem im having is configuring it. I googled and could not find anything addressing my problem. I tryed fluxmenu and cluxconfig to no avail. What im trying to do is get a menu populated like my gnome menu as I heard this is possible but even help files just seem to say this is Fluxbox. 

 I want to get the menu working as this will allow me to work from inside Fluxbox.

 Lastly is the latest version borked in Ubuntu because what im reading seems to differ from what im experienceing.

---

### Post by Xian on 2005-07-31
[QUOTE=Omnios]What im trying to do is get a menu populated like my gnome menu as I heard this is possible but even help files just seem to say this is Fluxbox.[/QUOTE]
IMO if you want this done right then just do it yourself.
There are tools to autopopulate the menu but I don't prefer them.

Just open the /home/username/.fluxbox/menu file in a text editor.

The format is very intuitive. Edit the menu items as you desire.
Follow the same format to add new items.

The changes are presented instantly.

For example, let's say that want to add the Gnome Terminal
You'd just place this entry under a given submenu:
```
[exec] (Gnome Terminal) {/usr/bin/gnome-terminal}
```

---

### Post by Omnios on 2005-07-31
Thanks Xian, could recomend a website with a good read on setting up Fluxbox?

---

### Post by Omnios on 2005-07-31
[QUOTE=Xian]IMO if you want this done right then just do it yourself.
There are tools to autopopulate the menu but I don't prefer them.

Just open the /home/username/.fluxbox/menu file in a text editor.

The format is very intuitive. Edit the menu items as you desire.
Follow the same format to add new items.

The changes are presented instantly.

For example, let's say that want to add the Gnome Terminal
You'd just place this entry under a given submenu:
```
[exec] (Gnome Terminal) {/usr/bin/gnome-terminal}
```[/QUOTE]

 Um one quick question what do you mean by sub menu my menu file seems to be totaly blank. Also its shows as an unkown file so I opened with notepad. Im just a bit confused but I think that is why I enjoy Linux so much. I enjoy a bit of a challenge but spinning my weels in a void gets a bid nippy but this forum helps a bundle.

---

### Post by Xian on 2005-07-31
[QUOTE=Omnios]Thanks Xian, could recomend a website with a good read on setting up Fluxbox?[/QUOTE]
The [Fluxbox Documentation](http://fluxbox.sourceforge.net/docbook/en/html/) page is a great resource.
Gentoo has a nice [WIKI](http://gentoo-wiki.com/HOWTO_Fluxbox) entry.

---

### Post by Xian on 2005-07-31
[QUOTE=Omnios]Um one quick question what do you mean by sub menu my menu file seems to be totaly blank. [/QUOTE]
I thought there was a script in debian to initially populate that.
Open a teminal and enter this command:
```
$ fluxbox-generate_menu
```

---

### Post by Omnios on 2005-07-31
Thanks worked great, now I have to read up on how to change the screen res. Right now its like 1600 on a 17" monitor lol squints

---

### Post by Omnios on 2005-07-31
Umm googles stumped, anyone have any idea?

---

