---
title: "How can I get finer adjustment of cursor size? (22.04.3 LTS)"
date: 2023-10-29
forum: General Help
---

### Post by fred79 on 2023-10-29
When I go to (mouse and touchpad) and try and change cursor size there's only 3-4 sizes (depending on theme) even though you can set it between 16 and 72.
 
It's either too big or too small for my preferences.
Is there some way to make it so I have more control of the cursor size?

thanks.

---

### Post by MAFoElffen on 2023-10-30
This:
```

gsettings get org.gnome.desktop.interface cursor-size

```
Will retrieve what the current setting is. Default is 24.

This will set it to 36
```

gsettings set org.gnome.desktop.interface cursor-size 36

```
The docs say most usually settings for cursor-themes are set to 24, 32, 48, 64. I have mine set to 36.

---

### Post by fred79 on 2023-10-30
Thanks for the suggestion, I tried it and it doesn't change anything (besides the cursor size number in terminal) being xubuntu wouldn't it be something to do with xfce and not gnome?

---

### Post by bobunderwood99 on 2023-10-30
Settings Editor>xsettings>CursorThemeSize

---

### Post by fred79 on 2023-10-30
thanks for the suggestion. 
I just tried that, it doesn't give me any more control over size than when adjusting it in "mouse and touchpad", for instance there's no size difference between 30 and 40.

---

### Post by bobunderwood99 on 2023-10-31
The integers entered in "Settings Manager" or "Mouse and Touchpad" do not scale the cursor size. The cursors are bitmaps - a range of integers will display the same size cursor.

You could try installing new cursor themes that are sized more to your liking or

find the cursor files in an existing theme and resize one of them (e.g. with GIMP). I've never tried this.

---

### Post by Holger_Gehrke on 2023-10-31
On X11 - and since you tagged your post 'xubuntu' I assume you're on X11 - cursors are stored in files with no extension in /usr/share/icons/THEME_NAME/cursors/,/usr/local/share/icons/THEME_NAME/cursors/, or possibly ~/.local/share/icons/THEME_NAME/cursors/. If you run 'file' on one of these files you will be told it's an 'X11 cursor'. These files hold multiple bitmap images, either for different sizes or for different frames of an animated cursor. You can generate a cursor file with 'xcursorgen' from a small text file describing the images (size, position of the hotspot, ...) and one or more PNG images. Gimp can open cursor files.

Most cursors only have very few sizes. For example the cursors in the Adwaita theme (/usr/share/icons/Adwaita/cursors/) only comes in five sizes (24,32,48,64,96). If you really need more, you can roll your own. Find a (cursor-) theme you like, open the cursors in GIMP, save the layers as PNG images and create your own additional sizes. Then generate a new cursor file with xcursorgen. Do this for all the 50 or so cursors in the theme.

Holger

---

### Post by fred79 on 2023-10-31
Thank you Holger_Gehrke and bobunderwood99 
I thought maybe that's how it was set up.
If I can't find a set of cursors with sizes I like, I'll try making some.
 I'll give it a shot and report back.

---

### Post by jabowery2 on 2024-04-05
> **bobunderwood99 said:**
> Settings Editor>xsettings>CursorThemeSize

There is no "Settings Editor"


 Ubuntu 22.04.4 LTS

  NVIDIA Corporation GA104 [GeForce RTX 3070 Ti]

GNOME Version 42.9

---

### Post by dragonfly41 on 2024-04-06
I am not on Xubuntu although I can select different desktop sessions at bootup time. In my case (Ubuntu) I click on top bar, right, the button used to Power Off / Log Off
In that Menu we see Settings > Accessibility > Cursor size
Mine is set to Larger.

---

### Post by him610 on 2024-04-06
@fred79, can you follow these (Xubuntu) directions?

> Settings > Mouse & Touchpad, select Theme tab, Size, Cursor size:[ - | + ] 

Yes, the actual cursor size does increase or decrease. I increased mine from 24 to 36 followed by decrease back down to 24.

---

