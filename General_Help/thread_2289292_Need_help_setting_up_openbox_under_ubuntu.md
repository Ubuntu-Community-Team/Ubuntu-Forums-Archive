---
title: "Need help setting up openbox under ubuntu"
date: 2015-08-02
forum: General Help
---

### Post by andreadixon825 on 2015-08-02
Hi, I just installed openbox and I'm trying to find  /etc/xdg/openbox/menu.xml ~/.config/openbox/menu.xml
and in terminal it says No such file or directory. But when I go to terminal and go to  /etc/xdg/openbox/
the file is there, I'm I doing something wrong here? I'm following [https://urukrama.wordpress.com/openbox-guide/](https://urukrama.wordpress.com/openbox-guide/)
and it says to do this command  cp /etc/xdg/openbox/menu.xml ~/.config/openbox/menu.xml
but every time I do it comes back saying No such file or directory, but I know its there. Please help or
if you know a better guide can you please tell me where? Thank you for your time :)

---

### Post by malspa on 2015-08-02
Maybe paste the exact "No such file or directory" message into a post here.

---

### Post by vasa1 on 2015-08-03
If you're sure you want to use Openbox as your window manager why not do a clean install of Lubuntu which uses Openbox as its default window manager and then use the Openbox session?

I'm sure you can get Openbox to work with Ubuntu but I've never tried it.

I've posted a bit about the Openbox session using Lubuntu here: [http://ubuntuforums.org/showthread.php?t=2173126](http://ubuntuforums.org/showthread.php?t=2173126)

I'm generally happy with it because I don't need a desktop environment.

---

### Post by CantankRus on 2015-08-03
> **andreadixon825 said:**
> Hi, I just installed openbox and I'm trying to find  /etc/xdg/openbox/menu.xml ~/.config/openbox/menu.xml
and in terminal it says No such file or directory. But when I go to terminal and go to  /etc/xdg/openbox/
the file is there, I'm I doing something wrong here? I'm following [https://urukrama.wordpress.com/openbox-guide/](https://urukrama.wordpress.com/openbox-guide/)
and it says to do this command  cp /etc/xdg/openbox/menu.xml ~/.config/openbox/menu.xml
but every time I do it comes back saying No such file or directory, but I know its there. Please help or
if you know a better guide can you please tell me where? Thank you for your time :)
Just use your file browser to copy and paste.
Will be easier to see if a directory or file is missing.
Maybe you don't have the **~/.config/openbox** destination directory, in which case create it.

---

