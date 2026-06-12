---
title: "How do I change the “Selected Items” color?"
date: 2014-06-22
forum: General Help
---

### Post by sameermw on 2014-06-22
I was trying to change the selected items color from the default orange to something else, however, the option isn't available on Ubuntu 14.04, as it used to be in the Appearance properties in previous versions of Ubuntu.

I tried this too, but it doesn't work at all,

> Path: org => gnome => desktop => interface
Find the line “gtk-color-scheme” and add this string:

bg_color:#f0f1f2;selected_bg_color:#023C88

Any idea? Thanks

---

### Post by Dennis N on 2014-06-22
Find the folder for the theme in use in /usr/share/themes
Example: /usr/share/themes/Ambiance
Open this theme folder. 
Editing will require root privileges.

In gtk-2.0 folder edit **gtkrc**:

In the line beginning **gtk-color-scheme =** find **selected_bg_color:#f07746** and change the color code after # to another color code. The existing code could be different than f07746. Use gcolor2 to find the code for a particular color.

In the gtk-3.0 folder edit **gtk.css**:

Find the line **@define-color selected_bg_color #f07746**; and change the color code after #.

In the gtk-3.0 folder edit **settings.ini**: 

In the line beginning **gtk-color-scheme =** find **selected_bg_color:#f07746** and change the color code after #.

Log out and back in.

(Based on Ubuntu 12.04)

---

### Post by sameermw on 2014-06-22
I use **GnomishGray** as my theme and there is no **@define-color selected_bg_color #******; **in **gtk.css (@gtk-3.0).** It contains only this line

> @import url("resource:///org/gnome/gnomishgray/gtk-main.css");

I changed everything as you said except above code. It's not working, by the way thanks for the comment.

---

### Post by Dennis N on 2014-06-23
> I changed everything as you said except above code. It's not working, by the way thanks for the comment. 

I think you might find the line **@define-color selected_bg_color #f07746** in gtk-main.css. From there, it is imported into gtk.css. That is the way it is done in some themes (but not all).

The directions were for 12.04 (as I noted in that post). They also work in my Lubuntu 14.04 except that my chosen theme there also uses gtk-main.css for color definitions.

---

### Post by grumblebum2 on 2014-06-23
I have installed the GnomishGray theme from the [**_[COLOR="#B22222"]noobslab theme ppa[/COLOR]_**]("http://www.noobslab.com/2014/01/gnomishgray-theme-for-ubuntulinux.html")
and by default the selection colour is grey.(Try logging out if colour doesn't change)
[ATTACH=CONFIG]254174[/ATTACH]

If I like, I can change the selection colour using **gtk-theme-config**.
[ATTACH=CONFIG]254173[/ATTACH]

After using **gtk-theme-config** I had to logout for colour to change.

To install gtk-theme-config...
```
sudo apt-get install gtk-theme-config
```

gtk-theme-config appears to create a **~/.config/gtk-3.0/gtk.css** file to override theme settings.

---

### Post by sameermw on 2014-06-23
wow, it worked for me.thank you so much. It is very easy and secure to use **gtk-theme-config**. thanks [grumblebum2]("http://ubuntuforums.org/member.php?u=1910493") again.

---

