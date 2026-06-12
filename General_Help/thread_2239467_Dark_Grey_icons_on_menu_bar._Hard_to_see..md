---
title: "Dark Grey icons on menu bar. Hard to see."
date: 2014-08-14
forum: General Help
---

### Post by fried1ninja on 2014-08-14
Hey everyone, I have this problem where my icons in the menu bar are extremely dark. The menu bar is black, so it is hard to see the icons. Only my battery, wi-fi, mixer, and empathy is dark grey. The language utlility is still visible, as for my time and name.

My current icon theme is Nitrux. My GTK theme is Flattastic Minimal. 

I understand that the reason for the dark icons is because of the Icon theme. I like my entire setup except only the dark icons on the menu bar. 

Is there a way I can change JUST the icons on the menu bar? 

I went into the icon theme instalation directory in usr/share/icons/NITRUX 

I looked through all the icons, but none of them seem to be the ones on the menu bar. I was thinking about transfering over other icons, giving them the same name as the current ones.

When I tilt my laptop screen back, the grey icons are unvisible. 

Any help is appreciated. Thanks.

---

### Post by CantankRus on 2014-08-14
Do you mean the panel or in nautilus?
Pic would help.

---

### Post by fried1ninja on 2014-08-14
Thank you for the reply. I meant in the panel. sorry for the misunderstanding. 

Here is a picture. 

[IMG]http://i.imgur.com/aNM8EHP.png[/IMG]

(You may be able to see the icons well depending on what monitor you have. In my case, when my laptop is tilted at the preferred angle, it is unvisible. As you can see, when the battery is plugged in, its at least light-grey. That's what I would like all the icon colours to look like.)

---

### Post by CantankRus on 2014-08-14
Don't have a solution except change your panel colour.
In unity you can use gtk-theme-config to do this.
It will change the colour of the panel and the titlebar.
[ATTACH=CONFIG]255497[/ATTACH]

[COLOR="#FF0000"]**EDIT:**[/COLOR] Found this @ [http://gnome-look.org/content/show.php?content=154496](http://gnome-look.org/content/show.php?content=154496)

Run both of these commands to change the svg hex colors.

```
sudo sed -i 's|#1a1a1a|#ffffff|g;s|#151719|#ffffff|g;s|#100f0d|#ffffff|g;s|#010101|#ffffff|g' /usr/share/icons/NITRUX/actions/scalable/*

sudo sed -i 's|#1a1a1a|#ffffff|g' /usr/share/icons/NITRUX/status/scalable/*
```

---

### Post by fried1ninja on 2014-08-16
Thank you so much! I appreciate it! 

My panel icons are now my favourite colour!

---

