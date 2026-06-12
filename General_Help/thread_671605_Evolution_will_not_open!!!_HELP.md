---
title: "Evolution will not open!!! HELP"
date: 2008-01-18
forum: General Help
---

### Post by kystorms on 2008-01-18
HELP please

Suddenly out of no where my Evolution quit opening, I rebooted, nothing changed!
Here is teh code from putting in evolution in terminal:

lisac@lisac-desktop:~$ evolution
/home/lisac/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/lisac/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/lisac/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
RSS Plugin enabled
Segmentation fault (core dumped)
lisac@lisac-desktop:~$ 

Will I lose all my saved emails? How could I retrieve them if I have to reinstall Evolution?

:confused:

added info -
found on a Mandriva help site about evolution help

did that, saw an option to disable plugins, which I did
and this is the code I got 
lisac@lisac-desktop:~$ evolution --disable-eplugin
/home/lisac/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/lisac/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/lisac/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
evolution-shell-Message: Killing old version of evolution-data-server...

(evolution:7055): camel-CRITICAL **: camel_store_get_folder: assertion `folder_name != NULL' failed

(evolution:7055): camel-CRITICAL **: camel_object_is: assertion `o != NULL' failed

(evolution:7055): evolution-mail-CRITICAL **: mail_tools_folder_to_url: assertion `CAMEL_IS_FOLDER (folder)' failed

(evolution:7055): camel-CRITICAL **: camel_store_get_folder: assertion `folder_name != NULL' failed

(evolution:7055): camel-CRITICAL **: camel_object_is: assertion `o != NULL' failed

(evolution:7055): evolution-mail-CRITICAL **: mail_tools_folder_to_url: assertion `CAMEL_IS_FOLDER (folder)' failed

lisac@lisac-desktop:~$ 

But as soon as I did this, my evolution did open and then quickly shut down , so do I have to reinstall the plugins?

thanks

---

### Post by dcstar on 2008-01-18
> **kystorms said:**
> HELP please

Suddenly out of no where my Evolution quit opening, I rebooted, nothing changed!
.........

Rename your (hidden) .evolution directory and then start Evolution. If it now starts, you had a corrupted environment.

If this is the case, you can copy e-mails etc. from your renamed directory to the new one to recover your data, but you may have to reconfigure your e-mail account settings.

---

### Post by kystorms on 2008-01-20
Many thanks for your help! I was feeling this would be the case.

:KS

---

