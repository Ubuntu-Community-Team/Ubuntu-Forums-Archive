---
title: "completly delete tomcat9 from ubuntu"
date: 2022-02-05
forum: General Help
---

### Post by circle224 on 2022-02-05
[COLOR=#232629][FONT=-apple-system]I downloaded tomcat 9 from [https://linuxhint.com/install_apache_tomcat_server_ubuntu/](https://linuxhint.com/install_apache_tomcat_server_ubuntu/) this site. However, I was not able to import it in Inteliij Idea so i decided to remove it.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]i used following commands[/FONT][/COLOR]
    sudo apt remove --purge tomcat9 tomcat9-docs
    sudo apt autoremove
    sudo apt autoclean
[COLOR=#232629][FONT=-apple-system]When I use locate tomcat command it seems that there is still lots of tomcat files and folders.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Also in my Files, when i search *tomcat* following folders and files shows up[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][enter image description here]("https://i.stack.imgur.com/FDCrQ.png")[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I panicked and deleted some folder but there is still 34 folder containing total of 95 items and 198 item. total of 27,3MB.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]see image [enter image description here]("https://i.stack.imgur.com/7E054.png")[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]guys please help me to remove them entirely. also tell me if folders i deleted were important or not[/FONT][/COLOR]

---

### Post by TheFu on 2022-02-05
The locate DB is updated daily, not immediately.

Are you really worried about 28MB?

However the package is installed (I didn't follow the link), that's the way to remove it.  When using APT, the --purge option removes the libraries, programs and settings that are stored for the system.  It doesn't remove any extra configs you may have created (for inclusion) or data or personal settings. It just removes the files that were in the package manifest, then deletes any directories which are empty after.  This is why a common method to have localized settings is to use the file.local vs file.conf.  The file.conf is part of the package and will be removed by the apt remove --purge command, but the file.local will not. It isn't part of the package manifest.

---

