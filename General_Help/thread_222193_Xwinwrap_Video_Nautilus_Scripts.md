---
title: "Xwinwrap Video Nautilus Scripts"
date: 2006-07-24
forum: General Help
---

### Post by orgy on 2006-07-24
hi, i've made 2 nautilus scripts so you can run video as background when running XGL/Compiz, 1 to start the video, and 1 to stop it.

What you need:

[LIST]
[*]Install xwinwrap through Synaptic Package Manager.
[*]Install mplayer. You can find the .deb right [HERE]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mplayer&searchon=names&subword=1&version=dapper&release=all") along with its perequisites.
[/LIST]

Open a terminal and do:

```
 gedit ~/.gnome2/nautilus-scripts/xwinwrap 
```

and copy and paste this into the file:
[PHP]
#!/bin/bash
xwinwrap -ni -o 0.6 -fs -s -sp -st -b -nf -- mplayer -wid WID "`echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`"
[/PHP]

Save and close the file. Then:
```
 chmod 700 ~/.gnome2/nautilus-scripts/xwinwrap 
```

Thats all for the first file. Now the script to stop the movie:

```
 gedit ~/.gnome2/nautilus-scripts/stop-xwinwrap 
```


and copy and paste this into the file:
[PHP]
#!/bin/bash
FILE="`echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`"
kill "`pgrep -fn $FILE`"
[/PHP]

Save and close the file. Then:
```
 chmod 700 ~/.gnome2/nautilus-scripts/stop-xwinwrap 
```

Now just rightclick any video file then select "Scripts" and then "xwinwrap" or "stop-xwinwrap"

[COLOR="Red"]NOTE: THESE SCRIPTS DONT INCLUDE FILE TYPE VALIDATION, SO JUST BE SURE TO USE THEM ON THE RIGHT VIDEO FILES[/COLOR] ;)

---

### Post by cechico on 2006-07-31
i get an error trying to install mplayer, can this work with kmplayer???

---

### Post by markp1989 on 2007-08-21
i been looking for somthing like this for a while, thankyou#

the start script works fine, but i cannot get the stop script to work, the only way i can get rid of the video is to kill X (crtl+alt+backspace), any ideas y i cannot stop the videos?

---

### Post by Posterus on 2007-09-12
thanks for this little tutorial.  i've been wanting to do something like this ever since i tried vista(which i didnt like and ended up getting rid of windows all together :-D).  works great :)



--Future

---

### Post by nickelby on 2007-09-19
Actually you don't need to kill X. All you need to do is kill the xwinwrap process e.g. 'killall xwinwrap' in a console window. That will return you back to your original desktop.


> **markp1989 said:**
> i been looking for somthing like this for a while, thankyou#

the start script works fine, but i cannot get the stop script to work, the only way i can get rid of the video is to kill X (crtl+alt+backspace), any ideas y i cannot stop the videos?

---

### Post by LinuxIsInnovation on 2007-12-18
I dont get the scripts option when I right click on vids..

---

### Post by LinuxIsInnovation on 2007-12-23
I get a blue desktop, nothing else..

---

