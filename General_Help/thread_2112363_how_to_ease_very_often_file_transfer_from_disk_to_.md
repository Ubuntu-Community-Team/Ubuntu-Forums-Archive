---
title: "how to ease very often file transfer from disk to disk"
date: 2013-02-04
forum: General Help
---

### Post by alain.roger on 2013-02-04
Hi,


I need to transfer very often files or folder from 1 disk to another and i'm not satisfied with nautilus from gnome shell.

Could you tell me if something like total commander (windows world) exist under Linux ?

you can see what is total commander at the following address: [http://www.ghisler.com/screenshots/en/01.html](http://www.ghisler.com/screenshots/en/01.html)

maybe filezilla but without ftp connection...from disk to disk could be ok...
thx

---

### Post by sudodus on 2013-02-04
You can run Total Commander with Wine, but I like to suggest a native linux tool. There is Midnight Commander **mc**, that looks a lot like the original Norton Commander.

```
sudo apt-get install mc
```

but honestly, I prefer to run Nautilus with two panes (click F3 to toggle one-pane <--> two-panes)

If you want to use the command line, you can use rsync. The manual is good ```
man rsync
```

---

### Post by kanikilu on 2013-02-04
[http://168hours.wordpress.com/2008/08/18/10-total-commander-alternatives-for-linux/](http://168hours.wordpress.com/2008/08/18/10-total-commander-alternatives-for-linux/)

---

### Post by Zill on 2013-02-04
alain.roger:  [emelFM2]("http://emelfm2.net/") is a file manager that implements the popular two-pane design. It features a simple GTK+2 interface, a flexible file typing scheme, and a built-in command line for executing commands without opening an xterm.

It's in the Ubuntu repos.

---

