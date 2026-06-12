---
title: "Most basic question EVER"
date: 2007-12-05
forum: General Help
---

### Post by A-dogg on 2007-12-05
I'm trying to install Celtx (screenwriting program as root so that it's accessible by every user. Here's what the Celtx wiki instructs:

"If you want all users to have access to it, Celtx must be installed and run once as the root user. A typical installation from an administrator account is done as follows:

cd /usr/local

sudo tar zxf /path/to/Celtx.tar.gz

(enter your password)

sudo /usr/local/celtx/celtx

    If you get an error error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory then you need to install a package that contains libstdc++.so.5. On Redhat and Ubuntu, this is the compat-libstdc++ package. On Gentoo, it's just called lib-compat. You might be able to install it using yum install compat-libstdc++ 

Now any user can run it using /usr/local/celtx/celtx. "

I have celtx.tar.gz downloaded to the desktop, so I open a terminal and do as follows:

"sudo tar xzf /Desktop/Celtx.tar.gz
[sudo] password for alexander:
tar: /Desktop/Celtx.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors"

and now I'm stuck. I'm just getting used to this whole terminal thing (I do as much from the package manager, etc as possible)...

Any advice would be great!

---

### Post by PurposeOfReason on 2007-12-05
the command should be 

```
sudo tar xzf ~/Desktop/Celtx.tar.gz
```

Notice the ~.

If that doesn't work:
```
cd /home/USERNAME/Desktop
sudo tarxzf Celtx.tar.gz
```
Then you'll have to move what is extracted to the desired folder
```
sudo mv FOLDERNAME /usr/local
```

If that still doesn't work, check the filename, make sure it is on the desktop, and all caps are the same. Linux is case sensitive.

---

### Post by BLTicklemonster on 2007-12-05
> **A-dogg said:**
> I'm trying to install Celtx (screenwriting program as root so that it's accessible by every user. Here's what the Celtx wiki instructs:

"If you want all users to have access to it, Celtx must be installed and run once as the root user. A typical installation from an administrator account is done as follows:

cd /usr/local

sudo tar zxf /path/to/Celtx.tar.gz

(enter your password)

sudo /usr/local/celtx/celtx

    If you get an error error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory then you need to install a package that contains libstdc++.so.5. On Redhat and Ubuntu, this is the compat-libstdc++ package. On Gentoo, it's just called lib-compat. You might be able to install it using yum install compat-libstdc++ 

Now any user can run it using /usr/local/celtx/celtx. "

I have celtx.tar.gz downloaded to the desktop, so I open a terminal and do as follows:

"sudo tar xzf /Desktop/Celtx.tar.gz
[sudo] password for alexander:
tar: /Desktop/Celtx.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors"

and now I'm stuck. I'm just getting used to this whole terminal thing (I do as much from the package manager, etc as possible)...

Any advice would be great!

cd /home/*yourname*/Desktop

sudo tar xzf Celtx.tar.gz

So you can't just double click on it and extract it?

---

### Post by BLTicklemonster on 2007-12-05
Dangit Purp! You beat me!

---

### Post by A-dogg on 2007-12-05
I extracted it fine -- it's sitting on the desktop and I ran it once. It works. I guess I'm just used to XP, where all programs are cosmetically "hidden" in the "Program Files" directory so I can keep "My Documents" clean and only have my pix/songs/docs in there. 

Is it just standard practice that in Linux the "Home" folder will have documents and programs in it?

I guess the reason I wanted to install it as root was so that it would get put into the filesystem, not in the Home folder (I realize the Home folder is in the filesystem) -- not sure if this makes any sense.

Just being anal, I suppose...

I'll give your directions a try -- thanks!

EDIT: I think I see what you're saying -- that sudo tar... just unzips it. Is it the second command "sudo /usr/local/celtx/celtx" that moves it to the directory where all other programs (those installed through synaptic) are stored?

I basically just want to know the easy way to move programs I've downloaded and installed (nopt through add/remove or package manager) from the desktop to system folders.


Sorry for the ramble!

---

### Post by dagnabit dang doohickey on 2007-12-05
Installing to /usr/local is odd. Installing to /opt then creating a symbolic link to celtx from /usr/local/bin makes more sense for a program that has a directory full of goodies, as celtx does.

```
cd /opt
sudo tar xzvf ~/Desktop/Celtx.tar.gz
cd ~/
sudo ln -s /opt/celtx/celtx /usr/local/bin/celtx
```

Celtx can now be run just by calling celtx instead of /usr/local/celtx/celtx as per your instructions.

BTW: the reason why the first command in the instructions is cd is because tar extracts the archive to the directory that you're currently in.

---

### Post by LaRoza on 2007-12-05
> **A-dogg said:**
> 

Is it just standard practice that in Linux the "Home" folder will have documents and programs in it?


No, home usually only has configuration files (which are hidden, press Ctrl + H to see them), and personal files. Programs are usually installed elsewhere, /usr/bin, /usr/sbin, /opt

---

### Post by DirtDawg on 2007-12-05
> **A-dogg said:**
> I extracted it fine -- it's sitting on the desktop and I ran it once. It works. I guess I'm just used to XP, where all programs are cosmetically "hidden" in the "Program Files" directory so I can keep "My Documents" clean and only have my pix/songs/docs in there. 

Is it just standard practice that in Linux the "Home" folder will have documents and programs in it?

I guess the reason I wanted to install it as root was so that it would get put into the filesystem, not in the Home folder (I realize the Home folder is in the filesystem) -- not sure if this makes any sense.

Just being anal, I suppose...

I'll give your directions a try -- thanks!

EDIT: I think I see what you're saying -- that sudo tar... just unzips it. Is it the second command "sudo /usr/local/celtx/celtx" that moves it to the directory where all other programs (those installed through synaptic) are stored?

I basically just want to know the easy way to move programs I've downloaded and installed (nopt through add/remove or package manager) from the desktop to system folders.


Sorry for the ramble!

Just a suggestion. Any app that I do not install system wide I place in a folder I call "localapps". So, for example, SooperApp would be in home/USERNAME/localapps/SooperAp/sooperapp.bin. That way, I keep all local apps in my home folder without making a mess.

---

### Post by A-dogg on 2007-12-06
wow -- thank you EVERYONE! It worked (obviously)!

I'm gonna study the directions you guys gave me so I can keep learning.

Thanks!

EDIT: last questions -- now how do you change the icon in the applications menu? I can change it in the opt folder, but the icon files are .png and it looks like they have to be .svn for the applications menu to recognize/use them?

---

### Post by DirtDawg on 2007-12-06
> **A-dogg said:**
> wow -- thank you EVERYONE! It worked (obviously)!

I'm gonna study the directions you guys gave me so I can keep learning.

Thanks!

EDIT: last questions -- now how do you change the icon in the applications menu? I can change it in the opt folder, but the icon files are .png and it looks like they have to be .svn for the applications menu to recognize/use them?

Right Click the Applications menu and choose "Edit Menus." You should be able to use '.png' or '.svg'. You can find icons in /usr/share/pixmaps and /usr/share/icons.

---

### Post by A-dogg on 2007-12-06
Everybody -- seriously, thank you VERY much. :)

---

### Post by A-dogg on 2007-12-07
weird -- seems like it won't let me choose .svg icons... I guess I'll have to find out how to convert .svg to .png

---

### Post by Gavla on 2007-12-15
Now this post I have found enlightening.
What would I have to do If I then wanted to make a menu icon that would appear to all users by default, as do the icons of newly installed packages made for Ubuntu and the apps that come with it?

---

### Post by Yfrwlf on 2008-01-04
> **A-dogg said:**
> weird -- seems like it won't let me choose .svg icons... I guess I'll have to find out how to convert .svg to .png

I'm using 7.10 and svg images show up for me when browsing for menu icons.  If you have some specific svg icons that aren't showing up, perhaps the formatting is different.  Of course, it *shouldn't* be if they are both svg files, but you never know...

> **Gavla said:**
> Now this post I have found enlightening.
What would I have to do If I then wanted to make a menu icon that would appear to all users by default, as do the icons of newly installed packages made for Ubuntu and the apps that come with it?

Of course the answer would be someplace not in the user's home directories. ;)  By default though, when you install a DEB package that contains menu link information, by default it installs it for all users to my knowledge.  Did you install something in which a link was only made for you and not for other users too?  I'd Google it, I'm sure that's a question that exists out there someplace, sorry I can't help. :P  Search "Gnome add menu link for all users" ;)

---

