---
title: "[SOLVED] Where would  go for help with a script?"
date: 2007-10-25
forum: General Help
---

### Post by Scruffynerf on 2007-10-25
Howdy all,

I've copied an existing script from the net which I would like to very slightly modify.

The script basically polls some settings in the GConf and displays the results in the terminal window. Mostly theme related.

One of the lines polls the background setting. In GConf, the setting displays the full path of the background picture and the filename

eg: "/home/scruffy/folder1/folder2/folder3/pictures/picture.jpg"

Is there a way that I can get the script to only see the filename? The directory structure will always be the same, however the name of the file and it's extension are the variables. So, if there was a way that I could get the script to ignore the first XX characters would be the ideal method, but I don't know how, as I cannot script to save my life.

The script in it's entirety is attached. The relevant bit is below:
```
 echo "GTK2:           		`gconftool-2 --get /desktop/gnome/interface/gtk_theme`"
  echo "Metacity:                       `gconftool-2 --get /apps/metacity/general/theme`"
  echo "Icons:          		`gconftool-2 --get /desktop/gnome/interface/icon_theme`"
  echo "Titlebar Font:      		`gconftool-2 --get /apps/metacity/general/titlebar_font`"
  echo "Application Font:  		`gconftool-2 --get /desktop/gnome/interface/font_name`"
  echo "Terminal Font:  		`gconftool-2 --get /apps/gnome-terminal/profiles/Default/font`"
  echo "Background:			`gconftool-2 --get /desktop/gnome/background/picture_filename`"
```

Any help would be appreciated.

cheers

Scruffy.

---

### Post by kidders on 2007-10-26
Hi there,

Is this what you want...?```
$ basename /boot/grub/menu.lst
menu.lst
```

---

### Post by Scruffynerf on 2007-10-26
> **kidders said:**
> Hi there,

Is this what you want...?```
$ basename /boot/grub/menu.lst
menu.lst
```

Hi,

Many thanks for replying!

That's the result I'm looking for.  Where would I put that command in the script file?

Very many thanks!

Rob

---

### Post by kidders on 2007-10-26
You could change [COLOR="Blue"]gconftool-2 --get /desktop/gnome/background/picture_filename[/COLOR] to [COLOR="blue"]gconftool-2 --get /desktop/gnome/background/picture_filename** | xargs basename**[/COLOR] or something similar.

---

### Post by Scruffynerf on 2007-10-26
Thanks for helping, however I can't get it to work. It will either display parsing errors or will include that command as text in the readout.

---

### Post by kidders on 2007-10-26
Are you sure everything is quoted and/or escaped correctly?

---

### Post by Scruffynerf on 2007-10-27
Erm, it should be. The info.sh that I attached to the original post is an exact copy/paste of what the script is running.

---

### Post by kidders on 2007-10-27
There are no errors in the script you posted in your o/p ... at least not in the portion you pasted into the body of the post itself. I assumed the trouble you were having had to do with modifications you've made since then.

Could you post the errors you're seeing, and the lines of the script the messages blame for the problem?

---

### Post by Scruffynerf on 2007-10-28
Sure. The problem is basically I've no idea where to put that command.

Eg1:
```
  echo "Background:		`gconftool-2 --get /desktop/gnome/background/picture_filename`"| xargs basename
```

Returns: "Background:                                                                                       " (ie: No returned info)

Eg2:
```
xargs basename | "Background:		`gconftool-2 --get /desktop/gnome/background/picture_filename`"
```

Returns: /home/rob/installs/scripts/themeinfo/info.sh: line 55: Background:             /home/rob/Desktop/documents/pictures/favourites/scarlet.jpg: No such file or directory

Eg3: 
```
  echo "Background:		`gconftool-2 --get /desktop/gnome/background/picture_filename`| xargs basename"
```

Returns: "  echo "Background:		`gconftool-2 --get /desktop/gnome/background/picture_filename`| xargs basename" (probably because it's in the quotes|

Eg4: ```
  echo "Background:"		xargs basename |"`gconftool-2 --get /desktop/gnome/background/picture_filename`"
```

Returns: "/home/rob/installs/scripts/themeinfo/info.sh: line 55: /home/rob/Desktop/documents/pictures/favourites/scarlet.jpg: cannot execute binary file"

Any ideas?

---

### Post by kidders on 2007-10-28
None of those commands makes any sense. Try...```
echo "Background:`gconftool-2 --get /desktop/gnome/background/picture_filename | xargs basename`"
```

---

### Post by Scruffynerf on 2007-10-29
Excellent! It worked wonderfully!

Many thanks for your help!

---

### Post by nikoPSK on 2007-11-21
mmm, love it! Great job!:KS

---

