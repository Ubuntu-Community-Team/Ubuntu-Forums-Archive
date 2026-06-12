---
title: "How i can change the System Name in Systemsettings -&gt; Details ?"
date: 2014-09-27
forum: General Help
---

### Post by zottel703 on 2014-09-27
Hello.

Anybody know how i can change the System Name in Systemsettings -> Details ? For Example: Zottel OS

I have modded my Ubuntu and want to "rename" it for a nice Joke :)

---

### Post by Frogs Hair on 2014-09-27
Re-branding: [http://askubuntu.com/questions/194062/how-can-i-replace-ubuntu-branding-with-my-own](http://askubuntu.com/questions/194062/how-can-i-replace-ubuntu-branding-with-my-own)

---

### Post by mc4man on 2014-09-27
na

---

### Post by cariboo on 2014-09-27
What has this got to do with Utopic?

---

### Post by mc4man on 2014-09-27
> **cariboo907 said:**
> What has this got to do with Utopic?
nothing

---

### Post by cariboo on 2014-09-27
> **mc4man said:**
> nothing

Moved to General Help.

---

### Post by deadflowr on 2014-09-28
> **zottel703 said:**
> Hello.

Anybody know how i can change the System Name in Systemsettings -> Details ? For Example: Zottel OS

I have modded my Ubuntu and want to "rename" it for a nice Joke :)

You mean the name across the top of the details that says "Ubuntu 12.04 LTS" or whatever your version is?

If so, you can change it by replacing the image in /usr/share/gnome-control-center/ui(for 12.04) or /usr/share/unity-control-center/ui.(14.04)
It is the image UbuntuLogo.png.
Commonly, it should be noted that, if for whatever reason an update for that package comes up, it'll probably reset the package, including that image to its default. Overriding the one you placed there.

---

