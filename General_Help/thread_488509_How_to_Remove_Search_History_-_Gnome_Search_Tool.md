---
title: "How to Remove Search History - Gnome Search Tool"
date: 2007-06-30
forum: General Help
---

### Post by Qualmcon on 2007-06-30
Under the Gnome Desktop Environment, how do you clear/remove the search history for the default search tool (Place ----> Search for Files..).  I believe the search tool is called Gnome Search Tool (gnome-search-tool on the command line).  I am using Ubuntu 7.04.


Thanks

---

### Post by eggdeng on 2007-06-30
There really ought to be an easier way but you can always edit /home/your_username/.gconf/apps/gnome-settings/gnome-search-tool/%gconf.xml, which is the file where gnome stores these values. 
Open it by running ```
gedit /home/your_username/.gconf/apps/gnome-settings/gnome-search-tool/%gconf.xml
``` in a terminal. To eliminate an individual item, delete everything between the opening <li tag and the closing </li> of that block. Save the file and restart gnome.

---

### Post by Qualmcon on 2007-06-30
That solution seems to have done it.


Thanks

---

### Post by mpeters on 2007-06-30
A slightly easier way I believe is to run:

gconftool --unset /apps/gnome-settings/gnome-search-tool/history-gsearchtool-file-entry

but make sure the search tool isn't running when you run this or the value will just get reset when you next close it down.

---

