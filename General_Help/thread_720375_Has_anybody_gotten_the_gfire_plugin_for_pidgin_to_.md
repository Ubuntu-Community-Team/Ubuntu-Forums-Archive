---
title: "Has anybody gotten the gfire plugin for pidgin to work"
date: 2008-03-10
forum: General Help
---

### Post by k420 on 2008-03-10
I have been trying for awhile to get  this to work.  I am using Gutsy and pidgin v2.4.0 and i installed the gutsy package for pidgin from the gfire sourceforge  page[http://gfire.sourceforge.net/snapshots/]("http://gfire.sourceforge.net/snapshots/") but have not had any luck.  I dont really need it for playing games i need to talk to the people in my clan while not in front of my vista box

---

### Post by ibuclaw on 2008-03-10
Hi, yes I have... a ubuntu deb file of it is availiable here...

[http://getdeb.net/app/gaim-xfire]("http://getdeb.net/app/gaim-xfire")

And it's availiable for both 32 and 64 bit systems.

I've tried it and it works... no probs...
When you reload pidgin and click "Add", you'll see "Xfire" in your protocol list.

Iain

---

### Post by k420 on 2008-03-10
when i try to install that one gdebi says i have a later version already install

---

### Post by ibuclaw on 2008-03-10
Sorry, I didn't realise that you installed the SVN  deb file.

Okay, first purge the installed gaim-xfire on your system. You'll find it in synaptic under "gaim-xfire".
Right-click and select "Mark for Completely Removal"  
Apply the settings and then install the deb file from getdeb.net.

And you're all set.

Iain

---

### Post by k420 on 2008-03-10
thanks for the help but i got an error  installArchives() failed  well the error i have is for a broken package for my printer which i never got to work.  mfc9700lpr and i can't remove it cause it says it didnt install right

---

### Post by ibuclaw on 2008-03-10
This is most bizarre...

Erm. Perhaps:

a) check that you package cache is clean (unless you specifically keep all packages for backup).
b) re-download the file, it may be an MD5Sum error caused it?
c) make sure you're system is up to date, or maybe:
```
 sudo apt-get install -f 
```

To be honest, I've never seen this error before, so I can only take a blind guess.

Regards
Iain

[EDIT]
Oh, broken package for printer... that makes some sense then.
sudo apt-get install -f shouldl fix any broken dependancies, unless you want to keep it broken for whatever reason you have (ie: a program only works if you have it that way).

---

### Post by k420 on 2008-03-10
yeah thats till doesnt work i been fighting with this for bout 6 months now here is what i get```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kaffeine libxine1-gnome
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mfc9700lpr
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 297597 files and directories currently installed.)
Removing mfc9700lpr ...
/var/lib/dpkg/info/mfc9700lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc9700lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc9700lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by k420 on 2008-03-10
Ok so i fixed my package issue and removed the file like you told me then i installed the one from getdeb then rebooted and xfire is still not showiung up in my list of protocols

---

### Post by ibuclaw on 2008-03-10
I suppose as a last resort option, you could try manually installing it in on your filesystem.

If you right click the .deb file and click "Extract Here".
Enter the newly created folder and extract the "data.tar.gz" file.

Then become root in nautilus
```
 sudo nautilus 
```

and copy the extracted "usr" folder into your "/" filesystem. Just click "Replace all".
If you feel unnerving doing this, you can always examine the contents throughly before you do. Just to be sure.

But to note, that any dependencies for it won't be installed (unless they already were when you got the snapshot version).

else:
This ought to do it:
```
 sudo apt-get install libc6 libglib2.0-0 libssl0.9.8 libpurple0 
```

As for the broken dependency, I recommend that you open up a new thread for it, and let someone else solve the problem for you, as that shouldn't happen :(

here is an image of mine:
[[IMG]http://img507.imageshack.us/img507/4807/xfirenk3.th.png[/IMG]](http://img507.imageshack.us/my.php?image=xfirenk3.png)

Regards
Iain

---

