---
title: "What to do ???"
date: 2007-11-23
forum: General Help
---

### Post by ashzoomerintrack on 2007-11-23
I am a pretty newbie. Tell me guys why i am not able to make any folders or paste anything in filesystem or /home/ etc. it says permission denied or the the Paste option  in the right click menu gets faded <not active> plz help me really a newbie...............

---

### Post by LaRoza on 2007-11-23
You can make directories in your home folder:

/home/$USER

/home/ itself contains the individual home folders. Don't store anything outside of home or other drives, if  you don't have write access, there is usually a reason for it.

---

### Post by Cannaregio on 2007-11-23
You can create any folder anywhere [COLOR="Blue"]therefore also inside home[/COLOR] if you act as root using sudo
First go where you want to create a subfolder

```
cd /home
```

then create it
```
sudo mkdir mynewfolder
```

check how it looks like with permissions
```
ls -lart
```

and then, eventually, change ownership or file access permission of such folder to whomever you like using [COLOR="Blue"]chown[/COLOR] and [COLOR="#0000ff"]chmod[/COLOR], or else keep the new folder owned by  root, depending what you'r doing and why you'r doing it...

---

### Post by LaRoza on 2007-11-23
> **Cannaregio said:**
> You can create any folder anywhere [COLOR="Blue"]therefore also inside home[/COLOR] if you act as root using sudo


Yes, but don't do that except in very few circumstances.

---

### Post by ashzoomerintrack on 2007-11-24
Thank you so much for your kind help but some times it is necessary to paste skins or plugins to certain root folders for softwares, so during that time how should i paste those files????....:confused:

Also is anybody having an e-book about operating or working in Ubuntu?????

---

### Post by Cannaregio on 2007-11-24
Start here:
[http://www.linux-books.us/ubuntu.php]("http://www.linux-books.us/ubuntu.php")

continue here:
[http://vntutor.blogspot.com/2007/06/free-online-ubuntu-linux-books.html]("http://vntutor.blogspot.com/2007/06/free-online-ubuntu-linux-books.html")

Enjoy.

---

### Post by jken146 on 2007-11-24
> **ashzoomerintrack said:**
> Thank you so much for your kind help but some times it is necessary to paste skins or plugins to certain root folders for softwares, so during that time how should i paste those files????....:confused:?

If you want to copy and paste graphically with root permissions,
Press Alt+F2
Enter ```
gksu nautilus
```
and be careful!

---

### Post by ashzoomerintrack on 2007-11-27
Thanks guys my problem is solved also the book references were great but got stuck in another problem. I was trying to get multimedia codecs but not able to get them the terminal shows the following error:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Help me!!!!

---

### Post by -grubby on 2007-11-27
do as it says...open a terminal and type
dpkg --configure -a

---

### Post by FuturePilot on 2007-11-27
> **nathangrubb said:**
> do as it says...open a terminal and type
dpkg --configure -a

That won't do anything. You need to use sudo
```
sudo dpkg --configure -a
```

---

### Post by ashzoomerintrack on 2007-11-28
On running the above given command the terminal returns a reply:
dpkg: status database area is locked by another process

Dont know what to do?????

Also a small tutorial on installing applications from .tar.gz downloaded to pc (Not the wiki.ubuntu one)... Help

---

### Post by ashzoomerintrack on 2007-11-29
> **ashzoomerintrack said:**
> On running the above given command the terminal returns a reply:
dpkg: status database area is locked by another process

Dont know what to do?????

Also a small tutorial on installing applications from .tar.gz downloaded to pc (Not the wiki.ubuntu one)... Help

Help Me?????

---

### Post by PmDematagoda on 2007-11-29
If you are running Synaptic or any other package managers, make sure that they are closed, then try again.

---

### Post by ashzoomerintrack on 2007-11-29
> **PmDematagoda said:**
> If you are running Synaptic or any other package managers, make sure that they are closed, then try again.

Terminal replies that files needed for ttd & a blue box appears.....

---

### Post by PmDematagoda on 2007-11-29
Could you please post a screenshot of your problem? It would be better.

---

