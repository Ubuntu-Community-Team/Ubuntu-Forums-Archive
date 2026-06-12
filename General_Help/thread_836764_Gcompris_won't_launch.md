---
title: "Gcompris won't launch"
date: 2008-06-21
forum: General Help
---

### Post by Brian96 on 2008-06-21
I have installed Edubuntu Hardy (32 bit) for my kids, but gcompris won't launch. (Neither will the "Gcompris Administration" app.)

When I launch it in a terminal I get this output:

```


 gcompris
exec_prefix NULL
XF86VidMode: Compiled with XF86VidMode.
If you have problems starting GCompris in fullscreen, try the -x option to disable XF86VidMode.

** (process:6059): WARNING **: Binary relocation disabled
package_data_dir         = /usr/share/gcompris/boards
package_locale_dir       = /usr/share/locale
package_plugin_dir       = /usr/lib/gcompris
package_python_plugin_dir= /usr/share/gcompris/python
Infos:
   Config dir '/home/kids/.config/gcompris'
   Users dir '/home/kids/My GCompris'
   Database '/home/kids/.config/gcompris/gcompris_sqlite.db'

```

Any ideas?

---

### Post by avtolle on 2008-06-21
Long shot; presuming you created the Users directory, the name of which is shown in the output, there is a space in the My GCompris name. This may be the problem. Possible solution: change the name from 'My GCompris' to 'My_GCompris' or 'MyGCompris' (w/out the apostrophes, of course). As I'm not familiar with this, I don't know if there is an option to edit the name, or if you will need to make a new directory with a name that doesn't cause trouble after deleting the current directory.

---

### Post by Brian96 on 2008-06-22
> **avtolle said:**
> Long shot; presuming you created the Users directory, the name of which is shown in the output, there is a space in the My GCompris name. This may be the problem. Possible solution: change the name from 'My GCompris' to 'My_GCompris' or 'MyGCompris' (w/out the apostrophes, of course). As I'm not familiar with this, I don't know if there is an option to edit the name, or if you will need to make a new directory with a name that doesn't cause trouble after deleting the current directory.

Thanks for the input. That folder is auto-created by the application, and the filename is identical on the two other machines in which the program is working properly.

Thanks again, though.

---

### Post by Brian96 on 2008-06-22
> **Brian96 said:**
> I have installed Edubuntu Hardy (32 bit) for my kids, but gcompris won't launch. (Neither will the "Gcompris Administration" app.)

When I launch it in a terminal I get this output:

```


 gcompris
exec_prefix NULL
XF86VidMode: Compiled with XF86VidMode.
If you have problems starting GCompris in fullscreen, try the -x option to disable XF86VidMode.

** (process:6059): WARNING **: Binary relocation disabled
package_data_dir         = /usr/share/gcompris/boards
package_locale_dir       = /usr/share/locale
package_plugin_dir       = /usr/lib/gcompris
package_python_plugin_dir= /usr/share/gcompris/python
Infos:
   Config dir '/home/kids/.config/gcompris'
   Users dir '/home/kids/My GCompris'
   Database '/home/kids/.config/gcompris/gcompris_sqlite.db'

```

Any ideas?

I just tried launching it in a terminal on another machine, and although the application launched perfectly, I got the exact same output as noted above. So I guess posting the terminal output won't really shed any light on this matter.

In the same Edubuntu install I'm also having other quirky problems, like right-clicking on the main menu and selecting "edit menus" does nothing. I have to run alacarte with a sudo command to change anything.

---

### Post by Brian96 on 2008-06-26
Anybody else having a problem with this? I'd really like a solution. I did a regular install instead of a "custom" install built up from a CLI install to AVOID this kind of problem.

Any suggestions?

---

### Post by avtolle on 2008-06-26
I'm at the "cure all solution" stage; do a clean install. I really don't know that this is necessary, but it seems it might be quicker to do a clean install, totally update the system, install the Edubuntu at that point, and update it, than trying to keep fighting the battles when no one here has any ideas (me included).

---

### Post by Brian96 on 2008-06-26
> **avtolle said:**
> I'm at the "cure all solution" stage; do a clean install. I really don't know that this is necessary, but it seems it might be quicker to do a clean install, totally update the system, install the Edubuntu at that point, and update it, than trying to keep fighting the battles when no one here has any ideas (me included).

I'm creeping up on that point. But if I have to reinstall, I am NOT going to use edubuntu. I've run gcompris on this machine with Feisty and Gutsy, so I know it's not hardware. The only difference is the edubuntu (though I don't know why that would matter).

The only other thing I've noticed is that where my machines with working gcompris have config files (in the .config folder in the home directory) the edubuntu install has nothing.

---

### Post by Brian96 on 2008-06-26
Well, I got it to work by copying the config files from a working install into the /home/[uname]/.config/gcompris folder and then changing the permissions to the appropriate username.

It's a workaround, and I still don't understand why I had this problem, but at least it is working now.

Thanks for your help, avtolle.

---

