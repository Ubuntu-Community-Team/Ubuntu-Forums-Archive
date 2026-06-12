---
title: "XScreen GLSlideshow Doesn'"
date: 2022-12-14
forum: General Help
---

### Post by webmanoffesto on 2022-12-14
XScreen GLSlideshow Doesn't See My Images 

I have an old computer. I want it to run a non-stop slideshow of the images in 
/home/user/Pictures/Screensaver_Pictures
That will be the main function of this computer.

I'm trying to do this using XScreenSaver and GLSlideshow. 
I read through an old post ([https://ubuntuforums.org/archive/index.php/t-1979116.html](https://ubuntuforums.org/archive/index.php/t-1979116.html)) in this forum on a similar topic. So I confirmed that libwww-perl is installed.

I'm also open to using other programs to do this.

What is the control that tells it to go on and choose the next image?

What setting tells Ubuntu to "sleep" and begin XScreenSaver? Is it Power / Blank Screen? Is it Suspend / Automatic Suspend?
How do I begin XScreenSaver now, without e.g. waiting for a 5 minute "idle". 
When I'm in Screensaver Preferences / Advanced / Choose Random Image
when I change the folder name it seems to revert back to the former folder name.
Being tricky, by changing my folder name back to what it was doesn't work.

---

### Post by Dennis N on 2022-12-14
As an alternative, you can just use gnome's image viewer, which has a slideshow option. It's installed by default in Ubuntu. Simple to use.

---

### Post by ajgreeny on 2022-12-14
Most image viewers have a slideshow option and allow you to set up the time delay before moving to the next in the preferences.

Assuming you are using xorg and not wayland graphics you can start xscreensaver with the command ***xscreensaver -no-splash*** in your *startup applications* list, but that is not the simplest method to have a continuous slideshow that never stops.

---

### Post by Holger_Gehrke on 2022-12-14
To make settings to xscreensaver and the various screen-hacks (that's what the programs showing the graphics are called ...) you can use 'xscreensaver-demo'. But as Dennis N and ajgreeny have already said, that's not the most effective way to set up a slideshow. Personally I'm a big fan of 'feh' because it can be completely controlled from the command line and therefore lends itself well to automation. Something like ```
feh --fullscreen --auto-zoom --hide-pointer --no-menus --preload --quiet --recursive --slideshow-delay 5.5 ~/Pictures/slideshow_pictures/*
``` should give you some idea of what's possible. It's in the repositories and can be installed with 'sudo apt install feh'

Holger

---

### Post by mIk3_08 on 2022-12-16
> **webmanoffesto said:**
> XScreen GLSlideshow Doesn't See My Images 

I have an old computer. I want it to run a non-stop slideshow of the images in 
/home/user/Pictures/Screensaver_Pictures
That will be the main function of this computer.

I'm trying to do this using XScreenSaver and GLSlideshow. 
I read through an old post ([https://ubuntuforums.org/archive/index.php/t-1979116.html](https://ubuntuforums.org/archive/index.php/t-1979116.html)) in this forum on a similar topic. So I confirmed that libwww-perl is installed.

I'm also open to using other programs to do this.

What is the control that tells it to go on and choose the next image?

What setting tells Ubuntu to "sleep" and begin XScreenSaver? Is it Power / Blank Screen? Is it Suspend / Automatic Suspend?
How do I begin XScreenSaver now, without e.g. waiting for a 5 minute "idle". 
When I'm in Screensaver Preferences / Advanced / Choose Random Image
when I change the folder name it seems to revert back to the former folder name.
Being tricky, by changing my folder name back to what it was doesn't work.

```
How do I begin XScreenSaver now, without e.g. waiting for a 5 minute "idle". 
``` Just click the preview button and never move your mouse after clicking the preview.
```
When I'm in Screensaver Preferences / Advanced / Choose Random Image 
```see image below.
Just point it to the folders full of image. I think, It will automatically change the image randomly. Regards and cheers.

---

### Post by Dennis N on 2022-12-16
> How do I begin XScreenSaver now, without e.g. waiting for a 5 minute "idle". 

On this point, you can activate the screensaver from the command line. No waiting.
```
xscreensaver-command --activate
``` 


FWIW, I have in the past tried to get the slideshow feature to work, but never succeeded.

---

