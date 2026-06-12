---
title: "Possible to change size of full screen, minimise, close etc icons?"
date: 2015-03-09
forum: General Help
---

### Post by ragdoll2 on 2015-03-09
I would like to change the size of the icons used for full screen, close and minimise etc (photo attached of the up arrow, yellow, blue and orange circle I mean), is it possible to make them larger. Using voyager linix 14.04 64 bit (xubuntu based).

[ATTACH=CONFIG]260544[/ATTACH]

---

### Post by Toz on 2015-03-09
Hello and welcome to the forums.

Yes. Those icons are actually image files. You'll find them in your theme's xfwm4 folder. You can change them (or create an xfwm4 theme of your based on an existing one) as you wish. There is more information about creating xfwm4 themes at [https://wiki.xfce.org/howto/xfwm4_theme]("https://wiki.xfce.org/howto/xfwm4_theme").

---

### Post by ragdoll2 on 2015-03-09
> **Toz said:**
> Hello and welcome to the forums.

Yes. Those icons are actually image files. You'll find them in your theme's xfwm4 folder. You can change them (or create an xfwm4 theme of your based on an existing one) as you wish. There is more information about creating xfwm4 themes at [https://wiki.xfce.org/howto/xfwm4_theme](https://wiki.xfce.org/howto/xfwm4_theme).

Thanks Toz, I am just in that folder now (xfwm4) and the images are all .svg but when I try to save (eg- closed-pressed) in gimp after changing its size, that .svg extension does not appear to be useable and when trying to save all images are .png in the xfwm4 folder and the and the closed-pressed image does not exist there.
I am obviously nearer but still no less lost ;-)

Edit - I have just read that the .svg image files can be edited via a text editor, I will try that.

---

### Post by ragdoll2 on 2015-03-09
Well, I tried to change the image size in mousepad but even after chmod 775 on the xfwm4 folder,"permission denied". Any ideas on gaining access to make changes save?

---

### Post by Toz on 2015-03-09
It's probably best to create a copy of the theme first in your home directory, then edit the copy. To do this, first create the .themes directory in your home directory:
```
mkdir ~/.themes
```

Then copy over the theme that you want to edit (let's assume that you want to edit the Greybird theme):
```
cp -rv /usr/share/themes/Greybird ~/.themes/Greybird.2
```
...note that I changed the name of the theme to "Greybird.2" - you can select any theme name that you want. The name that you select is the name that will be displayed in the Appearance and Window Manager dialogs where you can change the theme.

Then finally, edit the files in your ~/.themes/Greybird/xfwm4 directory. You will have the necessary permissions to do so.

The benefit of this process is that you still have the original theme available if you want to check things or even start from scratch.

---

### Post by ragdoll2 on 2015-03-10
Thanks again Toz. I have done as directed and made changes to the images within the xfwm4 folder and it makes no difference when the new theme is chosen, logged out and back in again just in case. 
Are there other folders that also require changes within the themes folder ie - gtk.2, gtk.3, metacity-1, index.theme or index.theme~

---

### Post by Toz on 2015-03-10
Are you changing the Window Manager theme from Settings Manager >> Window Manager >> Style tab?

---

### Post by ragdoll2 on 2015-03-10
No, I was not using the window manager, when I do use it, it changes the coloured items I wish OK but they do not look any larger, simply out of line off the top of the window almost. Maybe I am changing the wrong images or another item requires changing within the theme.
I want to change the sizes purely for use on my tablet, everything else works great except the navigation which is too small.

---

### Post by Toz on 2015-03-10
A screenshot might be helpful.

There is also a themerc file with settings that can be adjusted.

Xfce 4.12 (the newer version) now comes with an hdpi and xhdpi xfwm4 theme specifically for this purpose. Maybe you can try them out and see if they work and/or are helpful. Simply download the [xfwm4 source]("http://git.xfce.org/xfce/xfwm4/snapshot/xfwm4-4.12.0.tar.bz2"), and extract out the 2 themes to your ~/.themes directory. Then try them out. (No need to build/compile the source, just grab the theme files).

You can see a picture of the [xhdpi theme]("http://www.webupd8.org/2015/03/a-look-at-whats-new-in-xfce-412-video.html") on this page.

---

