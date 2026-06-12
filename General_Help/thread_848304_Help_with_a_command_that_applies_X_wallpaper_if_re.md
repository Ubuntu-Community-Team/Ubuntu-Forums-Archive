---
title: "Help with a command that applies X wallpaper if resolution is X."
date: 2008-07-03
forum: General Help
---

### Post by perfectska04@hotmail.com on 2008-07-03
Hi, I'm writing a script that changes the current theme/icons/wallpapers, etc. I would like to know if there is a way to set a different wallpaper for different resolutions... 

For example, if resolution is 1024x768, then it would run gconftool-2 and apply X wallpaper.

But if resolution was a different aspect ratio, like, 1280x800, it would apply Y wallpaper.

Is there any way to do this? thanks, in advance.

---

### Post by perfectska04@hotmail.com on 2008-07-03
Also, a bit unrelated. Is there a command to change GDM themes?, I would like to add it to the script I mentioned previously as well.

---

### Post by koenn on 2008-07-03
```

#/bin/bash
# set wallpaper depending on screen resolution
#

RES=$(xvidtune -show |cut -d' ' -f1)

case $RES in 
	"\"1440x900"\" ) 
			#do something with gconf
			echo "test 1"
	;;
	"\"1024x768"\" ) 
			#do something with gconf
			echo "test 2"
	;;
	*) 
			# fall back to a sensible default here
			echo "default, no matching case"
	;;
esac

```

Here's a start. You need to list all screen resolutions you want the script to handle (mind the quotes) and add a suitable gconf statement

---

### Post by perfectska04@hotmail.com on 2008-07-03
Thanks a lot! this is just what I was looking for. I will try it now.

---

