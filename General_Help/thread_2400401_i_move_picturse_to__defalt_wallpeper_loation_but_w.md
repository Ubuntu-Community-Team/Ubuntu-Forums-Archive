---
title: "i move picturse to  defalt wallpeper loation but when i go to setting not in setting"
date: 2018-09-05
forum: General Help
---

### Post by 8h567t20 on 2018-09-05
Hello can some body pleas help me. I movde some picturse over to /usr/share/backgrounds/ but when i go to settings and go to backgrounds the picturse i added are not  there.

---

### Post by deadflowr on 2018-09-05
Because just having the pictures in the /usr/share/backgrounds folder just means having the pictures in the /usr/share/backgrounds folder and nothing else.
To actually utilize the pictures within the wallpaper program they need to be added to the version-named-wallpapers.xml file located at /usr/share/gnome-background-properties.
The wallpaper xml file would be for which version of Ubuntu, such as bionic-wallpapers.xml or xenial-wallpapers.xml.
But you can also create your own xml file, by copying the existing one and replacing the names and filenames with the names and filename paths of yours.
It'll work as long as the syntax is complete and the file is located in the above directory.


It's painful (or tedious) to do which is why most will recommend just using the option to load Pictures from your home folder's Pictures folder instead.

---

### Post by 8h567t20 on 2018-09-06
Thank you ill try to add 1 or 2 to the xml file thank you for helping me

---

