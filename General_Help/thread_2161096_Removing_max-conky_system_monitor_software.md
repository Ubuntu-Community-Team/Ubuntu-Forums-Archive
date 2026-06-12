---
title: "Removing max-conky system monitor software"
date: 2013-07-09
forum: General Help
---

### Post by jackson21 on 2013-07-09
Dear Readers, 
Ubuntu 13.04 here. Installed max-conky system monitor software.
Ok. Then removing the max-conky with  : sudo apt-get remove
didn't work. 
software center responded to removing the software ok.
But conky still came up
Then I resided to "locate" in terminal, which listed all the conky files
and I removed them  each separately as super user
Now conky doesn't  start any more .
Nevertheless all the conky files I have deleted  still come up when I run
"locate" but they are not on the system any more ????

Thank you

---

### Post by Hylas de Niall on 2013-07-09
Max-conky looks nice, though it seems to me that adding a ppa to do what can be done in stock conky anyway is a bit overkill.
Why did you choose to remove it?

Did you ```
sudo apt-get remove max-conky
``` letter for letter as noobslab says?
[http://www.noobslab.com/2013/06/max-conky-for-ubuntulinux.html](http://www.noobslab.com/2013/06/max-conky-for-ubuntulinux.html)

Also, did you disable its ppa in your software sources? Maybe it's getting updated and reinstalled?

Not sure, just a few ideas but i hope it helps.

---

### Post by stinkeye on 2013-07-09
Conky is an application that uses a config file to display stuff on your desktop.

What noobslab did was create a deb file to install a config file and add conky-all to startup applications.
It also installs **conky-all** as a dependency.
conky-all is conky with most compile options enabled.(conky with the bells and whistles)

Removing the **max-conky** package does not remove the conky-all application.

It's not necessary to remove **conky-all** as by removing max-conky it should no longer autostart.
You are able to try different conky setups by replacing the hidden file **.conkyrc** in your home folder with another config.
This thread is a place to find other configs. [**_[COLOR="#B22222"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=2214")

But if you wish to remove, search and remove **conky-all** in the software center.

Also when you delete a file it will continue to show with the locate command until
the database is updated.
I think this is scheduled to run once a day, or you can run...
```
sudo updatedb
```

---

### Post by jackson21 on 2013-07-10
Thanks for help

---

