---
title: "AutoHotKey OSS alternative"
date: 2007-05-31
forum: General Help
---

### Post by FFighter on 2007-05-31
When on Windows, I used to use a handy app called AutoHotKey ([http://www.autohotkey.com/](http://www.autohotkey.com/)) which allowed me to associate any combination of keyboard keys to custom actions. I had it set up to launch many often-used folders and applications as well as web pages and custom scripts. Is there something like that for Linux ?

Thanks,

Marcelo.

---

### Post by JSThePatriot on 2007-05-31
I would actually like to recommend AutoIt for Windows. I know you are looking for a Linux alternative. There are some guys on the AutoIt forums testing the different functionality of AutoIt in a Linux environment with Wine. Give it a look see. AutoHotKey actually originally came from the sources of AutoIt v2.

I hope this is somewhat helpful,
JS

---

### Post by happy-and-lost on 2007-05-31
If you navigate to /apps/metacity/global_keybindings in gconf-editor, you'll see a whole load of empty strings which say "run_command_2" and so forth. From here you can set which keys you want bound (eg. <Ctrl><Alt><Del>) which will correspond with key strings in /apps/metacity/keybinding_commands, where you can set the corresponding action on, say "command_2" (eg. gnome-system-monitor).

At least, that's my understanding of the Metacity keybindings. These will NOT work when you have Compiz enabled.

(Please correct me if I'm wrong, anyone!)

---

### Post by peabody on 2008-02-18
My program does stuff like autohotkey.  It doesn't do everything I'd like it to, but it does the hotstring functionality and can run shell programs.  With this fact you can glue stuff together and hopefully get some semblance of your former functionality.  The link is in my sig, autokey.

---

