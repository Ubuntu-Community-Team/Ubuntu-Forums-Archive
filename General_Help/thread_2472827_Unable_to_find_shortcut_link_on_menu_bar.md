---
title: "Unable to find shortcut link on menu bar ?"
date: 2022-03-14
forum: General Help
---

### Post by satimis on 2022-03-14
Unable to find shortcut link on menu bar ?

```
$ ls -al /home/satimis/Videos/shotcut-linux-x86_64-220130.AppImage
-rwxrwxr-x 1 satimis satimis 104834240 Mar 14 16:15 /home/satimis/Videos/shotcut-linux-x86_64-220130.AppImage

```

```
$ ls -al /home/satimis/.local/share/applications/shotcut.desktop
-rw-r--r-- 1 root root 148 Mar 14 18:50 /home/satimis/.local/share/applications/shotcut.desktop

```

```
$ cat /home/satimis/.local/share/applications/shotcut.desktop 
Desktop Entry]]Name=shotcu
Type=Application
Exec=/home/satimis/Videos/shotcut-linux-x86_64-220130.AppImage
Icon=/home/satimis/Pictures/shotcut.png

```

Pls help.  Thanks

Regards

---

### Post by ajgreeny on 2022-03-14
You have to create your own launcher (shortcut) to appimages, which you have done but unfortunately with one important and two other minor errors.

You missed the first square bracket in the text.
Your file contains ***Desktop Entry]]Name=shotcut***, but it should be ***[Desktop Entry]]Name=shotcut***, note the extra [ at the start.
I don't  think the misspelling of shotcut to shotcu matters but put that right as well.

You may also find it makes things easier if you add the line ***Categories=Graphics;Viewer;*** into the text.

---

### Post by satimis on 2022-03-14
> **ajgreeny said:**
> You have to create your own launcher (shortcut) to appimages, which you have done but unfortunately with one important and two other minor errors.

You missed the first square bracket in the text.
Your file contains ***Desktop Entry]]Name=shotcut***, but it should be ***[Desktop Entry]]Name=shotcut***, note the extra [ at the start.
I don't  think the misspelling of shotcut to shotcu matters but put that right as well.

You may also find it makes things easier if you add the line ***Categories=Graphics;Viewer;*** into the text.
Thanks for your advice.

I got the problem fixed.

```
$ cat /home/satimis/.local/share/applications/shotcut.desktop 
[Desktop Entry]
Name=shotcut
Type=Application
Exec=/home/satimis/Videos/shotcut-linux-x86_64-220130.AppImage
Icon=/home/satimis/Pictures/shotcut.png
Categories=Graphics;Viewer;

```

Regards

---

