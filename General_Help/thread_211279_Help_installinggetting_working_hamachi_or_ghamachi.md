---
title: "Help installing/getting working hamachi or ghamachi"
date: 2006-07-08
forum: General Help
---

### Post by nameiwantistaken on 2006-07-08
I've tried following the few tutorials around that show you how to install hamachi.  I can do the hamachi init, but when I start it, it gives, 

"07 23:38:31.080 [   0] [ 6142] tap: connect() failed 2 (No such file or directory)"

The install went fine, but I was getting access errors when trying to access the tuncfg file.  It would be really just swell if people could pack up hamache and ghamache into a single file that would spawn a modern isntaller when you click it.  It literally took me 2 minutes to get this up and running under windows including download time and I only had to click 3 mouseclicks.

---

### Post by Appolusionist on 2006-07-08
> **nameiwantistaken said:**
> I've tried following the few tutorials around that show you how
 to install hamachi.  I can do the hamachi init, but when I start it, it gives, 

"07 23:38:31.080 [   0] [ 6142] tap: connect() failed 2 (No such file or directory)"

The install went fine, but I was getting access errors when trying to access the tuncfg file.  It would be really just swell if people could pack up hamache and ghamache into a single file that would spawn a modern isntaller when you click it.  It literally took me 2 minutes to get this up and running under windows including download time and I only had to click 3 mouseclicks.

You didn't mention which guides you tried, but I found this one for Ubuntu. Take a look at the first half:
[http://doc.gwos.org/index.php/VNC_and_Hamachi]("http://doc.gwos.org/index.php/VNC_and_Hamachi")

---

### Post by nameiwantistaken on 2006-07-08
When I get to the sudo tuncfg it says command not found.  If I try to reinstall it, it says copying hamachi into /usr/bin..
creating hamachi-init symlink ..
copying tuncfg into /sbin ..
install: cannot run strip: No such file or directory
install: strip failed
make: *** [install] Error 1

---

### Post by nameiwantistaken on 2006-07-10
It seems that the issue is build-essentials is not installed in Ubuntu for some reason by default.  Hamachi looks for this, but errors during the install.  A graphical installer that would run when I click the hamachi install file that could look for this would be peachy, but probably too convenient for the linux realm.  Long story short, if you're reading this and are having a problem then you need to either find build-essentials in Synaptic or do an apt-get at a command line with something like apt-get install build-essentials.

---

