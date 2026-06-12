---
title: "Terminal, Confusion?"
date: 2008-06-25
forum: General Help
---

### Post by DualBooted on 2008-06-25
Hey guys, I'm on my newly installed Ubuntu, I spent the last few days getting wireless work work, and after learning about the Synaptic Package Manager I installed NDISWrapper and I got a Broadcom Popup asking me to install the drivers, so I did along with FW-Cutter and wahla, it worked. Anyway that isn't the problem. I need help with..

[SIZE="6"]The Terminal![/SIZE]

OK, I need to learn how to Download packages off the web, I can do that using wget so far, but now, I have the problems unzipping and installing. If anyone could help me on here, or add my MSN, that would be great and I appreciate every bit of help I get.

[SIZE="3"]Just for the record, of what I've seen so far on Ubuntu, it's great.[/SIZE]

Either Post Here or Add My MSN:
[email]disusedrhythm@hotmail.com[/email] (Slow Reply Due To Using Pidgin)

Thankyou :D

---

### Post by dracayr on 2008-06-25
hi,

If you want to install software, apt-get is the best choice. don't download you package manually and extract and install it, but simply run this command:

```
sudo apt-get install *insert package name here*
```

the package will then automatically download and install

dracayr

---

### Post by oldos2er on 2008-06-25
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by DualBooted on 2008-06-25
OK, but dude. How about if something isnt on the package manager? How do i install it then?

---

### Post by ibuclaw on 2008-06-25
If it is a deb file you downloaded.
```
sudo dpkg -i **filename**.deb
```

And to check and install any missing dependancies (incase of an install fail).
```
sudo apt-get install -f
```
Regards
Iain

---

### Post by issih on 2008-06-25
Ok, happy to tell you stuff about the terminal if thats what you want, but why are you using it for these tasks as a new user?

More importantly why are you downloading packages manually? Do you understand about synaptic and the repositories? or are you just behaving as you would under windows?

To install a program in ubuntu go through the following procedures.

First open add/remove programs under the Applications menu. There are masses of programs available there, which can be installed simply by ticking them and hitting apply, ubuntu will manage everything for you.

If the thing you want isn't there, then look in Synaptic Package Manager under (System->Administration), which is a large repository of packages specifically for your version of ubuntu, ready to be downloaded and installed simply by ticking a box.

If the package you want is still elusive, go out and google for a .deb file if at all possible, these will install automatically when clicked on.

After that you are in the realms of things being a bit complicated, either having to convert rpm packages to deb ones or compilation from source code, but you should be able to avoid that 90-99% of the time.

Finally archived files (zip, tar.gz,bz,etc) can be viewed and extracted entirely within the gui, just by clicking on the file and choosing extract.

Anyway, I'm not trying to tell you not to use the terminal, its an amazing and powerful tool, but for installing software we have several layers of package management built into debian/ubuntu, you really should use them.

Terminal Tips.

tar.gz files are unzipped with "tar -xvzf <filename>"
zip files are unzipped with "unzip <filename>"

after that it will depend entirely on what you have in the archive.

Seriously though, see if you can get it by one of the easy methods first. If you want to play with the terminal, then you can try installing using the package management from within the terminal:

"sudo apt-get install <packagename>" will install a package if its in the repositories.

"sudo apt-get remove <packagename>" will uninstll it.

Hope that helps, and sorry for ranting :)

---

### Post by DualBooted on 2008-06-25
That was a tutorial and a half, thanks so much. Is their any chance you can PM me your MSN Messenger Email so I can contact you if I need any simple help?
Thankyou So Much :D

---

### Post by Taxman415a on 2008-06-25
DualBooted, what you really need to do is just read some of the background on how to install software on Ubuntu. It really is different and easier than on Windows and Mac. It's already packaged and set up for you and there are several ways to do it. The easiest is to go to your Applications menu and run the Add/Remove...  but for the background, these are the basic documents:

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)
[https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

They have links to the additional details you may want as well.

---

