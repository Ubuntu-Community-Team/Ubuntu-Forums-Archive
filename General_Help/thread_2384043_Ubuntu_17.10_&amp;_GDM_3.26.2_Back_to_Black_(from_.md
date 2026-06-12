---
title: "Ubuntu 17.10 &amp; GDM 3.26.2: Back to Black (from Purple)"
date: 2018-02-01
forum: General Help
---

### Post by TJSL on 2018-02-01
I prefer a dark minimalist Ubuntu desktop for its aesthetic and reduce eyestrain. After three days of effort, I succeeded in changing all purple Ubuntu screen (boot, login, desktop) to black and installed a dark theme. Since I came across a number of posts that had the same objective, but which were incomplete or outdated, I am providing my working setup (on a clean 17.10 install). The  boot, startup/shutdown, wallpaper, lock screen, and dark theme are fairly straight forward. However, changing the background on of the gdm login screen proved challenging (but should be relatively easy with the guidance below). I found it necessary to rebuild the gdm .gresource file to eliminate the brief purple flash between login and initial display of the desktop (others suggested installing alternatives like gnome-session, but this only replaces the purple for a gray flash).

1.) Dark Theme (i.e., Ark-Dark)
2.) Wallpaper & Lockscreen
3.) Ubuntu Start/Shutdown screen (w/ ubuntu logo)
4.) Grub
5.) GDM Login Screen


###########################  Dark Theme (Arc-Dark) ###########################

### install arc-theme
sudo apt install arc-theme

### set theme
gsettings set org.gnome.desktop.interface gtk-theme 'Arc-Dark'

###############################################################################


########################### Wallpaper & Lockscreen ############################

DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"

sudo cp <wallpaper_1920x1080.png> /usr/share/backgrounds

# desktop wallpaper
gsettings set org.gnome.desktop.background picture-uri 'file:///usr/share/backgrounds/<wallpaper_1920x1080.png>'

# lock screen
gsettings set org.gnome.desktop.screensaver picture-uri 'file:///usr/share/backgrounds/<wallpaper_1920x1080.png>'


###############################################################################


################ Ubuntu Start/Shutdown Screen (w/ ubuntu logo) ################

xhost +local: && sudo nano /usr/share/plymouth/themes/ubuntu-logo/ubuntu-logo.script

### Change from:
# Window.SetBackgroundTopColor (0.16, 0.00, 0.12);     # Nice colour on top of the screen fading to
# Window.SetBackgroundBottomColor (0.16, 0.00, 0.12);  # an equally nice colour on the bottom
#######################################

### Change to:
 Window.SetBackgroundTopColor (0.0, 0.00, 0.0); # Nice colour on top of the screen fading to
 Window.SetBackgroundBottomColor (0.0, 0.00, 0.0); # an equally nice colour on the bottom

 sudo update-initramfs -u

###############################################################################


##########################  Grub Splash Screen Image ##########################

# copy image file to /boot/grub directory
sudo cp <wallpaper_1920x1080.png> /boot/grub

# comment out problematic line
sudo sed -i "/GRUB_HIDDEN_TIMEOUT=0/ s/^/# /" /etc/default/grub

# update /boot/grub/grub.cfg
sudo update-grub


################ NOTES ################
# sudo nano /etc/default/grub

# /etc/default/grub provides GRUB_HIDDEN_TIMEOUT and GRUB_HIDDEN_TIMEOUT_QUIET.
# Running sudo update-grub gives following warning: 
# Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
# To see custom grub wallpaper, instead of black screen, cannot have both 
# GRUB_HIDDEN_TIMEOUT and GRUB_HIDDEN_TIMEOUT_QUIET. Commenting out one or the
# other will permit #the custom wallpape to be displayed.

# Fix black splash screen in 17.10 by commenting out one of the following two lines:
#GRUB_HIDDEN_TIMEOUT=0 # comment out this line (to show both splash screen and grub menu)
#GRUB_HIDDEN_TIMEOUT_QUIET=true

# verify update-grub correctly updated splash screen image (search for image filename)
# cat /boot/grub/grub.cfg

###############################################################################


########################### GDM Login Screen ###########################

# extract gresource, replace noise-texture.png, rebuild gresource, copy .gresource into /usr/share/gnome-shell/

# gresource extractor
# [https://www.devpy.me/the-best-linux-lockscreen/](https://www.devpy.me/the-best-linux-lockscreen/)
# [https://github.com/devpytech/scripts/tree/master/gresource-extract](https://github.com/devpytech/scripts/tree/master/gresource-extract)

### Instructions to update GDM Login Screen
1.) download the scripts on the DevPy GitHub: devpytech/scripts/gresource-extract
2.) run ./extract.sh to extract your current theme to the "theme" folder in the same folder as the extract script
3.) edit ./theme/gnome-shell.css (change #lockDialogGroup)
          # background: #000000 url(resource:///org/gnome/shell/theme/noise-texture.png);
4.) copy background image to ./theme/noise-texture.png (i.e., use same name) 
5.) run ./build.sh from DevPy's GitHub to create .gresource file in the theme folder
6.) sudo mv ./theme/gnome-shell-theme.gresource /usr/share/gnome-shell/gnome-shell-theme.gresource


################ NOTES ################
### Change from:
# lockDialogGroup {
#  background: #2c001e url(resource:///org/gnome/shell/theme/noise-texture.png);
#  background-repeat: repeat; }

# purple (#2c001e) -> black (#000000)
#######################################

### Change to:
# lockDialogGroup {
background: #000000 url(resource:///org/gnome/shell/theme/noise-texture.png);
#  background-repeat: repeat; }
#######################################

---

### Post by denn1s-r on 2018-12-28
Thanks! I hate the purple everywhere!

---

### Post by araghuramindia on 2019-11-13
The default Orange Shield Screen still appears on resumption after the login screen at start up is allowed to fade out.  This happens only at start up.  Is there a way to have a custom background for this Screen Sheild also ?

---

### Post by deadflowr on 2019-11-13
Bed time
Back to sleep
Thread closed

---

