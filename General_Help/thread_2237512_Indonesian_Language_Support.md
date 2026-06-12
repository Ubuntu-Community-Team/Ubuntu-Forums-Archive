---
title: "Indonesian Language Support"
date: 2014-08-02
forum: General Help
---

### Post by West Swan on 2014-08-02
Hello,

I have an Indonesian friend coming to visit me and I am going to lend them a laptop with Lubuntu 14.04 installed.

I'd like to have language support for her but there is no "language support" option under the preferences menu.

Is there another way of doing this?

Regards,

Paul

---

### Post by Rex Bouwense on 2014-08-02
There sure is.  Whatever language you have installed there should be a little flag or county code on the right side of your LXPanel.  Right click that and choose keyboard layout handler settings.  Uncheck "keep system layouts" and then choose "add".  Select which language you want to add and arrange the languages in the order you want.  Recheck "keep system layouts".  I believe that you have to log out and then log in again for it to take effect.
Also see 
[http://lxlinux.com/#19](http://lxlinux.com/#19)
for more information.

---

### Post by West Swan on 2014-08-02
> **Rex Bouwense said:**
> There sure is.  Whatever language you have installed there should be a little flag or county code on the right side of your LXPanel.  Right click that and choose keyboard layout handler settings.  Uncheck "keep system layouts" and then choose "add".  Select which language you want to add and arrange the languages in the order you want.  Recheck "keep system layouts".  I believe that you have to log out and then log in again for it to take effect.
Also see 
[http://lxlinux.com/#19](http://lxlinux.com/#19)
for more information.

Hi Rex,

Thank you for that.

I wasn't clear enough in my question.

What I was hoping to do is temporarily change the language of the Lubuntu menus etc to Indonesian so that for example instead of 'preferences' it would read 'Preferensi' or something like that.

Regards,

Paul

---

### Post by Rex Bouwense on 2014-08-02
To find out which language packs are installed enter:
```
locale -a
```
If you do not have Indonesian installed (and I suspect that that you do not) you must install it.
Menu->Preferences->Language Support.  Navigate to Install/Remove Languages.  Check Indonesian and apply changes. 
Is that what you are looking for?

---

### Post by West Swan on 2014-08-02
Hi Rex :-)

That is exactly what I am looking for however when I got to Menu -> Preferences there is no Language Support menu at all.

Regards,

Paul

---

### Post by West Swan on 2014-08-03
Hi Again,

Problem solved.  I did a clean install of Lubuntu and installed Indonesian and it is working great.

I must have deleted the language support somehow previously.

Regards,

Paul

---

### Post by Rex Bouwense on 2014-08-03
Great.  Please mark your thread as solved using the thread tools by your initial post.

---

