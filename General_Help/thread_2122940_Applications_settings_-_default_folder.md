---
title: "Applications settings - default folder"
date: 2013-03-06
forum: General Help
---

### Post by tomerc on 2013-03-06
Hi,

By default all applications are storing their settings to my home dir (each has its dedicated hidden folder under the home dir), is there any global configuration that changes this default location?
i would basically like to move it to a dedicated folder under my home dir that will hold all the hidden folders..

---

### Post by The Cog on 2013-03-06
I don't think so - I think it is application specific. Note that it is becoming common to place configuration files in /home/username/.config/programname instead of filling the home folder with hidden files/folders. I think using .config/programname makes a great deal of sense.

You could of course symlink to folders in .config, but your home directory will still be full of hidden symlinks.

---

### Post by tomerc on 2013-03-06
Thanks for your reply.

I suspected that was the case, abit annoying.. hate it that my home dir is filled with alot of hidden folders.

I am with you about the .config dir, too bad alot of programs are using $HOME instead.

---

### Post by Impavidus on 2013-03-06
Some applications may have a command line option for where to look for their configuration file. It would mean changing the launchers of those programs or setting up bash aliases to automatically include that option, depending on how you start them. Also, some programs may look for an environment variable that tells them where to find their configuration file. You'd have to add those environment variables to your .profile. It won't work for all programs though.

---

