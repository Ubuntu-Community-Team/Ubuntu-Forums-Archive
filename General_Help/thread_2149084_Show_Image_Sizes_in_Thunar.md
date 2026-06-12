---
title: "Show Image Sizes in Thunar"
date: 2013-05-27
forum: General Help
---

### Post by SillySod on 2013-05-27
Is there any way to get an image dimensions column in Thunar?  I've read around, and there appears to be an add-on for Nautilus which will do this, called "nautilus-columns", but I couldn't find it in the Synaptic list, and anyhow I tend not to use Nautilus.

I also use Gthumb, if there is a facility for it to produce an image file list with a dimensions column, that would do nicely.

---

### Post by Merrattic on 2013-05-27
Don't think so, but the image dimensions do show, for the selected image, in the status bar at the bottom.

Otherwise it is right click > properties > image

or

Write a custom action

---

### Post by VViL on 2013-10-04
In order to create a [COLOR=#000000]custom action (option in the right-click menu), here its what I have done.
1-Create a bash file named "image_size" with this content
[/COLOR]```
zenity --title "Size" --info --text="`identify -format "%G" $1`"
exit 0

```
2-Put in /usr/bin
```
#sudo su
#mv image_size /usr/bin/
#cd /usr/bin/
#chown root:root image_size
#chmod 755 image_size
```
3-In thunar add new custom action ([http://docs.xfce.org/xfce/thunar/custom-actions](http://docs.xfce.org/xfce/thunar/custom-actions))
with this command:
```
image_size %f
```
and in Appearance Conditions check only images files

:!: The bash file uses identify, part of imagemagick ([http://www.imagemagick.org/script/command-line-options.php#format_identify_](http://www.imagemagick.org/script/command-line-options.php#format_identify_)) and zenity to work

---

