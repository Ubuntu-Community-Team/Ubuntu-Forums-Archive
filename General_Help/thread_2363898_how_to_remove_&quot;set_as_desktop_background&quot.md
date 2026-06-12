---
title: "how to remove &quot;set as desktop background&quot; in dropdown menu in ubuntu 16.04"
date: 2017-06-16
forum: General Help
---

### Post by Hendrik_Van_Marcke on 2017-06-16
Hi there,

My native language is Dutch, but i'm trying to write in English, so sorry for faults in my writings.

A friend of mine is a school teacher and has 30 computers with Ubuntu 16.04
One big problem!
The students keeps changing the wallpaper lol.

Is there a way to prevent that.
Can in the dropdown menu (if rightclicking) de "set as background" menu been removed?

---

### Post by SeijiSensei on 2017-06-16
If the students don't have individual log in accounts, but just use a common shared account, then your friend should make the configuration files for that account read-only.  Changing the background is only one of the possible ways students could futz with the desktop settings and many other things.

The real solution for this is to give each student a separate account with authentication handled by a server using a solution like NIS, LDAP, or RADIUS.

Your English is fine!

---

### Post by Hendrik_Van_Marcke on 2017-06-16
Hi SeijiSensei,

I believe the desktops are not connected to a server because of the lack on financial recources.
So each student has it's own log in account.

---

### Post by SeijiSensei on 2017-06-18
Any one of the machines could be a "server" as well as functioning as a desktop.  They would need to be wired together with Ethernet, of course.

I just fired up my Ubuntu 16.04 virtual machine and changed my desktop background.  The change was recorded in the file /home/myusername/.config/dconf/user.  That's a binary file, as it turns out, so it's not directly editable.

However the administrator can freeze the settings as follows:

1)  Set the appropriate background from the desktop..
2)  Now the administrator can open a terminal and enter the following:
```

cd /home
sudo chattr +i */.config/dconf/user

```
That chattr command turns on the "(i)mmutable" bit.  Immutable files cannot be changed, even by their owners.  Even root has to first turn off the bit with "chattr -i" in order to change or delete the file.

The command I wrote would be applied to every user's directory under /home. 

This is a tedious process if the machines are not connected to a network, but it will prevent the students from changing the backgrounds.

---

### Post by mc4man on 2017-06-18
You could look here, whether this ever worked correctly in Ubuntu is debatable.
[https://help.gnome.org/admin/system-admin-guide/stable/dconf-lockdown.html.en](https://help.gnome.org/admin/system-admin-guide/stable/dconf-lockdown.html.en)

Making a user's .config/dconf/user file unwritable may cause issues, never tried but many apps write to it..

---

### Post by Hendrik_Van_Marcke on 2017-06-18
Hi dear SeijiSensei,

You are a wonderfull person.
The command did the trick.
Users can't change their background enymore.

Now my question is:

If the school want a new background on their computers, how can i undo this woderfull trick?

---

### Post by SeijiSensei on 2017-06-19
The administrator needs to run
```
sudo chattr -i /home/username/.config/gconf/user
```
before making any changes, then freeze them with "chattr +i".

I don't know if making this file immutable will cause "collateral damage" as mc4man is concerned about.  You'll probably discover any problems pretty quickly.

---

### Post by Hendrik_Van_Marcke on 2017-06-19
Hi dear SeijiSensei,

I believe the last command you wrote is faulty, because i have it changed to dconf instead of gconf
gconf file is not in the .conf

but it works splendid so far...
thanks for that.

---

### Post by Hendrik_Van_Marcke on 2017-06-19
> **SeijiSensei said:**
> You'll probably discover any problems pretty quickly.

Well eh... yes, i can't set the hidden files back to hidden after the first command: 

```
sudo chattr +i */.config/dconf/user
```

---

### Post by deadflowr on 2017-06-19
> **Hendrik_Van_Marcke said:**
> Hi dear SeijiSensei,

I believe the last command you wrote is faulty, because i have it changed to dconf instead of gconf
gconf file is not in the .conf

but it works splendid so far...
thanks for that.

gconf was the old configuration setup...
easy to confuse the two.

---

### Post by SeijiSensei on 2017-06-21
> **Hendrik_Van_Marcke said:**
> Well eh... yes, i can't set the hidden files back to hidden after the first command: 

```
sudo chattr +i */.config/dconf/user
```

The "user" file itself isn't hidden, but ~/.config should still be.  You need to make all the changes you want before setting the immutable bit.  Once it's set, the file is frozen.

> **deadflowr said:**
> gconf was the old configuration setup...
easy to confuse the two.
Especially if you're a KDE user like me with only a passing acquaintance with GNOME and its offspring.

---

