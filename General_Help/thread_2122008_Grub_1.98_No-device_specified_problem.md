---
title: "Grub 1.98 No-device specified problem"
date: 2013-03-03
forum: General Help
---

### Post by RedBall42 on 2013-03-03
I recently installed Backtrack 5r3 (which is based off of Ubuntu 10.04) alongside my installation of Ubuntu 12.04 Desktop. I have been trying to change the 05_debian_theme script in /etc/grub.d in the Backtrack OS to include an image on the grub menu since it seems as if Backtrack's version of grub (Grub 1.98) has replaced the one in Ubuntu 12.04. I put a .jpg image in my /boot/grub folder and change the use_bg value to true. However, when I do change the value to true and run update-grub I get an error message saying "no path or device specified." I have found that the 05_debian_theme script is correctly written and I do have the jpeg.mod file in /boot/grub. So I am trying now to do one of the following:
1)Change my default grub to the one that my installation of Ubuntu_12.04 is running(Grub 1.99)
2)Change my grub version to Grub1.99 via the command line
3)Find out why my script won't process the image

I am running both these OS's on an HP mini 210. Below is the code for the Backtrack 05_debian_theme script.

Please note that I am not very versed in posting in Forums, so if I need to provide any more information, just tell me what else I need to provide.
```

#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
EOF
}

# check for usable backgrounds
# for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do


use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found background image: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

# set the background if possible
if ${use_bg} ; then
 prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=${COLOR_NORMAL}
  set color_highlight=${COLOR_HIGHLIGHT}
else
EOF
fi

# otherwise, set a monochromatic theme for Ubuntu
if ${use_bg} ; then
  set_mono_theme | sed -e "s/^/  /g"
  echo "fi"
else
  set_mono_theme
fi

```

---

### Post by dcstar on 2013-03-04
> **RedBall42 said:**
> I recently installed Backtrack 5r3 (which is based off of Ubuntu 10.04) alongside my installation of Ubuntu 12.04 Desktop. I have been trying to change the 05_debian_theme script in /etc/grub.d in the Backtrack OS to include an image on the grub menu since it seems as if Backtrack's version of grub (Grub 1.98) has replaced the one in Ubuntu 12.04. I put a .jpg image in my /boot/grub folder and change the use_bg value to true. However, when I do change the value to true and run update-grub I get an error message saying "no path or device specified." I have found that the 05_debian_theme script is correctly written and I do have the jpeg.mod file in /boot/grub. So I am trying now to do one of the following:

**1)Change my default grub to the one that my installation of Ubuntu_12.04 is running(Grub 1.99)**
.........

Boot Ubuntu 12.04, then:

```
sudo dpkg-reconfigure grub-pc
```

And select the drive to install the bootloader.

---

