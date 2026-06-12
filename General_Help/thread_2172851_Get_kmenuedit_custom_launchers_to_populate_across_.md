---
title: "Get kmenuedit custom launchers to populate across multiple users"
date: 2013-09-06
forum: General Help
---

### Post by isaac-i2 on 2013-09-06
I recently created a few scripts that download and install some packages. I opened kmenuedit and I added entries for them in the menu under the default subgroups. 

When I go into my applications menu they appear however when I go into another users menu they don't.

i have tried copying the applications-kmenuedit.menu file to /etc/skel/.config/menus as well as /home/otheruser/.config/menus.

How do I get it to show up across all users? Is their something that I overlooked?

---

### Post by SeijiSensei on 2013-09-07
I'm pretty sure customizations like that you described are user-specific.  It sounds like you've made the appropriate fix to /etc/skel for new users.  For existing users, I think you'll have to copy your revised menu into their home directories, but you might be able to find something in /usr/share/kde4 that you can use to make the changes global.

---

### Post by isaac-i2 on 2013-09-07
I managed to do it. I copied the menu file to /etc/skel then I looked for the .desktop files linking to the script. Kmenuedit put them in ~/.local/share/applications I think. I copied the .desktop files to /usr/share/applications and when I created a new user it added the entries to the menu. 

As for existing users I think that I just have to copy the kmenuedit file to their home directory.

---

