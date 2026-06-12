---
title: "Removing Applications"
date: 2008-04-11
forum: General Help
---

### Post by smoove on 2008-04-11
I ran:

sudo aptitude remove DeVeDe 
sudo apt-get --purge autoremove DeVeDe

(Tried both to make sure, whats the difference?) 

To remove that program, but it's still appearing in my applications folder and still appears to execute when I launch it, why isnt this being removed?

---

### Post by Ziggy72 on 2008-04-11
I'm not a command line guru so I can't answer your question. However, why don't you just use Synaptic to remove the program? I suspect that will do the job nicely.
Edit...
Synaptic shows the program as devede so maybe that's the problem with your command line - i.e. not DeVeDe but possibly devede instead?

---

### Post by smoove on 2008-04-12
Synaptic doesnt have it listed as installed? But its in the apps menu?

---

### Post by smoove on 2008-04-12
bump

---

### Post by jakupl on 2008-04-12
Have you tried

```
sudo apt-get remove devede
```

---

### Post by smoove on 2008-04-12
Package devede is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

so yes... but its still in the apps menu and still executeable?

---

### Post by jakupl on 2008-04-12
> **smoove said:**
> Package devede is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

so yes... but its still in the apps menu and still executeable?


You mean it starts when you press it?? the actual program? if not, then right click the menus, press "edit menus" and you can remove it there.

---

### Post by smoove on 2008-04-12
Yep it still starts! 

I've also removed realplayer the same way and it still loads when the icon is clicked?

---

### Post by jakupl on 2008-04-12
right click on the launcher, press "add this launcher to desktop"
right click on the launcher located at the desktop, press "launcher".

what is written in the "command" box?

---

### Post by unutbu on 2008-04-12
Do you recall how you installed DeVeDe?

If it was not installed by apt-get or aptitude, then I don't think they are capable of removing the program.

If you installed devede-3.6.tar.bz2 from the download section of 
[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html),
then inside the tarball is a script called 'uninstall.sh' 
So you'd run

```
./uninstall.sh
```

(of course) to remove it.

---

### Post by smoove on 2008-04-14
Which is the install directory then? believe it downloaded it from the site and launched it using archive manager? Dont remember what else I did then!

---

### Post by unutbu on 2008-04-14
Just to make sure devede was not installed by dpkg, please run the following command:

```
dpkg --list | grep devede
```

You should get no output as a response. If you get something else, then please post the output.

If you get back nothing (meaning dpkg did not install devede), then you could try the following
```

locate uninstall.sh
```

This should tell you about all the files called uninstall.sh on your system. Beware that they may be unistall scripts for other programs. Great sadness unto those foolish enough to run them willy-nilly. Look inside to see if it says 'devede' all over the place. If it is, then it is probably your uninstall script. Look it over, see if you can convince yourself it is the unistall script, and then run it.

If locate does not find your uninstall script then the next option would be to 
download  devede-3.6.tar.bz2 (again) from [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html).

Crack it open this way:

```
bzip2 -dc devede-3.6.tar.bz2 | tar xf -
cd devede-3.6
./uninstall.sh

```

Again, it is a good idea to look over the uninstall script before running it.

One possible snag: Your version of devede might be different than 3.6. In that case, this uninstall script may or maynot work for you. It looks to me like the directories match up pretty well with your Snapshot.png though, but I'm not sure.

---

