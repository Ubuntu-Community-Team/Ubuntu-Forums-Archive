---
title: "Bluefish not running as root"
date: 2014-07-24
forum: General Help
---

### Post by AudioFlux on 2014-07-24
Same as [this]("http://askubuntu.com/questions/501899/bluefish-not-running-as-root") question on askubuntu.com.

I changed the name of the file that was open in Bluefish when Bluefish had been closed. But when I tried to open Bluefish again by entering simply ```
bluefish
``` in the terminal, it gave me this error.

```
error reading list 1 Error opening file: No such file or directory

** (bluefish:24717): WARNING **: no configfile rcfile-2.0, try to convert config files from older versions

config file migration error 1:Error opening file: No such file or directoryerror reading list 1 Error opening file: No such file or directory

(bluefish:24717): GLib-ERROR **: /build/buildd/glib2.0-2.40.0/./glib/gmem.c:103: failed to allocate 18446744073666193602 bytes
Trace/breakpoint trap (core dumped)
```

Bluefish still runs like nothing has changed without root. I uninstalled and purged the configurations. But when I installed it again and ran as root, again the same error.

---

### Post by grahammechanical on 2014-07-24
Text editors and wordprocessors usually offer us an option to open Recently Used documents. Some, like Bluefish, open with the last opened document in the editing window. But Bluefish cannot find the last opened document that it has in its records because you have renamed it. Un-installing and re-installing Bluefish did not remove/delete your Bluefish user configuration file. Bluefish is accessing the same user file as before.

Open the file manager and go to its View menu and tick show Hidden files. Now look in your home folder for a folder called .bluefish. The dot ( . ) makes the folder/file hidden unless we tick "show hidden files."

That is where Bluefish keeps your user configurations for Bluefish. You can delete that folder or examine the files in the folder and delete one of them. It will set Bluefish back to a default setting as when it was first installed. You may need to re-install Bluefish again. May be not.

Regards.

---

### Post by AudioFlux on 2014-07-24
> **grahammechanical said:**
> Text editors and wordprocessors usually offer us an option to open Recently Used documents. Some, like Bluefish, open with the last opened document in the editing window. But Bluefish cannot find the last opened document that it has in its records because you have renamed it. Un-installing and re-installing Bluefish did not remove/delete your Bluefish user configuration file. Bluefish is accessing the same user file as before.

Open the file manager and go to its View menu and tick show Hidden files. Now look in your home folder for a folder called .bluefish. The dot ( . ) makes the folder/file hidden unless we tick "show hidden files."

That is where Bluefish keeps your user configurations for Bluefish. You can delete that folder or examine the files in the folder and delete one of them. It will set Bluefish back to a default setting as when it was first installed. You may need to re-install Bluefish again. May be not.

Regards.
Worked perfectly! At first, I deleted the .bluefish folder from the Home folder but then I realized that since I had encountered the error as root it must be the .bluefish folder in the root directory that I had to delete. Thank you very much! :)

---

