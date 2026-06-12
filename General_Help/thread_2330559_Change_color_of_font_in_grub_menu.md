---
title: "Change color of font in grub menu"
date: 2016-07-12
forum: General Help
---

### Post by 4kh3RAm on 2016-07-12
Going by what is here, I am trying to change the font color of my grub menu.
But there are no color changes. (I also did sudo grub-mkconfig -o /boot/grub/grub.cfg)

[http://www.thegeekstuff.com/2012/10/grub-splash-image/](http://www.thegeekstuff.com/2012/10/grub-splash-image/)

Here is a section of 05-debian_theme where I made changes.
    
     > set_default_theme(){
    case $GRUB_DISTRIBUTOR in
        Tanglu|Ubuntu|Kubuntu)
            # Set a monochromatic theme for Tanglu/Ubuntu.
            echo "${1}set menu_color_normal=white/blue"
            echo "${1}set menu_color_highlight=green/white"

            if [ -e /usr/share/plymouth/themes/default.grub ]; then
                sed "s/^/${1}/" /usr/share/plymouth/themes/default.grub
            fi
            # For plymouth backward compatiblity. Can be removed
            # after xenial.
            if [ -e /lib/plymouth/themes/default.grub ]; then
                sed "s/^/${1}/" /lib/plymouth/themes/default.grub
            fi
            ;;
        *)
            # Set the traditional Debian blue theme.
            echo "${1}set menu_color_normal=white/blue"
            echo "${1}set menu_color_highlight=green/white"
            ;;
    esac
}

---

### Post by deadflowr on 2016-07-12
Customizing those setting in Ubuntu keep changing release to release.
So an article from 2012 at this point is extremely outdated for anything other than 12.04.
(In fact I should point out that 12.04 uses an entirely different version of Grub than any of the other currently supported versions of Ubuntu)

Better resource and kept very up-to-date is Cavfans [MaintenanceFreeCustomGrub2Scree]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")n.

Here's the relevant section to what you are trying to accomplish:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Possible_Grub_font_colors]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Possible_Grub_font_colors")

Have fun.

---

### Post by CantankRus on 2016-07-12
If it's any help, heres the section in my  05-debian_theme.
```
# ... and write our configuration snippet to stdout. Use the colors
	# desktop-base specified. If we're using a user-defined background, use
	# the default colors since we've got no idea how the image looks like.
	# If loading the background image fails, use the default theme.
	echo "insmod ${reader}"
	echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
	
	[B][COLOR="#FF0000"]# my grub colours
	echo " set color_normal=cyan/black"
	echo " set color_highlight=yellow/black"[/COLOR]
[/B]
	if [ -n "${2}" ]; then
		echo "  set color_normal=${2}"
	fi
```
On 16.04 was added after line #122 which may differ for you.

---

### Post by 4kh3RAm on 2016-07-13
> **deadflowr said:**
> Customizing those setting in Ubuntu keep changing release to release.
So an article from 2012 at this point is extremely outdated for anything other than 12.04.
(In fact I should point out that 12.04 uses an entirely different version of Grub than any of the other currently supported versions of Ubuntu)

Better resource and kept very up-to-date is Cavfans [MaintenanceFreeCustomGrub2Scree]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")n.

Here's the relevant section to what you are trying to accomplish:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Possible_Grub_font_colors](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Possible_Grub_font_colors)

Have fun.

I read it over.

Four versions are listed, with each requiring different lines to edit.

Ubuntu-Mate is not mentioned.

> **CantankRus said:**
> If it's any help, heres the section in my  05-debian_theme.
```
# ... and write our configuration snippet to stdout. Use the colors
    # desktop-base specified. If we're using a user-defined background, use
    # the default colors since we've got no idea how the image looks like.
    # If loading the background image fails, use the default theme.
    echo "insmod ${reader}"
    echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
    
    [B][COLOR=#FF0000]# my grub colours
    echo " set color_normal=cyan/black"
    echo " set color_highlight=yellow/black"[/COLOR]
[/B]
    if [ -n "${2}" ]; then
        echo "  set color_normal=${2}"
    fi
```
On 16.04 was added after line #122 which may differ for you.

I used your colors.

Will post the results later. :-)

---

### Post by deadflowr on 2016-07-13
> **4kh3RAm said:**
> I read it over.

Four versions are listed, with each requiring different lines to edit.

Ubuntu-Mate is not mentioned.

Grub is Grub and nothing to do with the OS at hand.
Ubuntu Kubuntu Xubuntu Ubuntu-Mate all use the same version of Grub.

---

### Post by 4kh3RAm on 2016-07-13
I have followed the directions and still cannot change the font colors in grub. :-(

---

### Post by grahammechanical on 2016-07-13
When we make changes to those Grub files that we are allowed to edit we should afterward run this command for the changes to go into grub.cfg (which we do not edit)

```
sudo update-grub
```

Regards

---

### Post by 4kh3RAm on 2016-07-13
Have already been doing that.

???

I suspect no one here has ever changed font color in grub for Ubuntu-Mate.

I also think that 05-debian_theme is not even used by grub.

Here is an example of programming that make it easier to users to customize. :-)

> # menu.lst produced by grub4dosconfig-v1.9.2
color white/blue black/cyan white/black cyan/black
#splashimage=/splash.xpm
timeout 10
default 1

---

### Post by Dennis N on 2016-07-13
Ubuntu MATE uses it's own custom grub theme. So I would think you have to edit that. See:

[B]/boot/grub/themes/ubuntu-mate/
[/B]
In particular, look at the file **theme.txt** in this folder. It contains color definitions.

---

### Post by 4kh3RAm on 2016-07-13
Editing theme.txt did not change font colors.

File is confusing as it uses both word values and numerical values for colors ??

---

### Post by Dennis N on 2016-07-13
Here you go: I have a grub menu (no theme) with yellow color text for selected line. It's controlled by 2 lines in /etc/default/grub:

```
# Uncomment and set to the desired menu colors.  Used by normal and wallpaper
# modes only.  Entries specified as foreground/background.
GRUB_COLOR_NORMAL="light-gray/black"
GRUB_COLOR_HIGHLIGHT="yellow/black"

```
I know it works, because I changed one and that text color changed in the grub menu. Run sudo update-grub if you do change it.

Possible values are here:

[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

under "Grub 2 Colors"

Have fun with color!

---

### Post by 4kh3RAm on 2016-07-13
Here is my file.

Do I put your statements anywhere ?

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_FONT="/boot/grub/fonts/MyGrub2CustomFont.pcf"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub star

---

### Post by deadflowr on 2016-07-14
I hate 3rd party themes sometimes.
Anyway, you can add those lines posted by Dennis N at the bottom of the /etc/default/grub file.
I'd copy them exactly and then simply change the colors, just make sure the second color: black is the still black.

Also, with regards to the mate theme, you can change the color by changing the color for the to lines in the boot menu section:
item_color = "black"
selected_item_color = "black"

changing the color is /etc/default/grub requires you to run the update-grub command.
changing the color in the theme.txt does not require an update-grub.
for what it's worth.

---

### Post by 4kh3RAm on 2016-07-14
Did you mean ?

sudo grub-mkconfig -o /boot/grub/grub.cfg

---

### Post by deadflowr on 2016-07-14
> **4kh3RAm said:**
> Did you mean ?

sudo grub-mkconfig -o /boot/grub/grub.cfg

Yes and no
sudo update-grub does the same thing.
It's a simple script that runs that grub-mkconfig command, making it easier on users to update grub.
I mean, who wants to type that much every time they run a quick update?

---

### Post by 4kh3RAm on 2016-07-14
sudo update-grub did NOT work.

---

### Post by deadflowr on 2016-07-14
> **4kh3RAm said:**
> sudo update-grub did NOT work.

In which way?

---

### Post by 4kh3RAm on 2016-07-14
I made a mistake.

The command worked.

---

