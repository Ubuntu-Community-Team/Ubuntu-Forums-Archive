---
title: "(GNOME) Application does not show up in search after install"
date: 2016-12-09
forum: General Help
---

### Post by SnuKies on 2016-12-09
I have installed CLion in my computer and it does not show up in my search bar. I've tried [http://askubuntu.com/questions/501880/applications-dont-appear-in-the-dash-14-04](http://askubuntu.com/questions/501880/applications-dont-appear-in-the-dash-14-04) desktop-file-validate does not return anything. I also tried [COLOR=#111111][FONT=Consolas]rm -rf ~/.local/share/zeitgeist  and still nothing. Any idea, please?
[/FONT][/COLOR]

---

### Post by Kirboosy on 2016-12-09
Hi SnuKies!

How exactly did you install CLion to your computer? I just downloaded CLion 2016.3 tar to my VM on Ubuntu 16.04 x64. I extracted the archive and ran ```
sh ~/Downloads/clion-2016.3/bin/clion.sh
``` It prompted me for a few things but when it prompted if I wanted it added to my search bar I accepted and clicked next. It is showing up in my search bar with no issues. 

I'm assuming you are running Ubuntu 14.04 since the Ask Ubuntu link is to a 14.04 issue. Perhaps this is only Ubuntu 14.04 issue?

Hope that helps!
~Caboose

---

### Post by Kirboosy on 2016-12-09
Also you can manually create the entry yourself. 

```
 nano ~/.gnome/apps/jetbrains-clion.desktop
```
Paste the following into the file and make sure to edit it to point it to the correct locations
```


[Desktop Entry]
Version=1.0
Type=Application
Name=CLion
Icon=/home/caboose885/Downloads/clion-2016.3/bin/clion.svg
Exec="/home/caboose885/Downloads/clion-2016.3/bin/clion.sh" %f
Comment=The Drive to Develop
Categories=Development;IDE;
Terminal=false
StartupWMClass=jetbrains-clion
OnlyShowIn=Old;
```

~Caboose

---

