---
title: "Add Extra Category Folders"
date: 2016-10-30
forum: General Help
---

### Post by ray42 on 2016-10-30
I want to add app folders but I can't find the 'app-folder-entries' entry in dconf Editor.

I have followed the instructions here:  [http://www.omgubuntu.co.uk/2013/05/add-categories-to-gnome-shell-dashboard](http://www.omgubuntu.co.uk/2013/05/add-categories-to-gnome-shell-dashboard)

---

### Post by CantankRus on 2016-10-31
Probably because the tutorial is 3 years old. Things change.
Look in dconf @ org.gnome.desktop.app-folders

---

### Post by ray42 on 2016-11-01
OK thats great.

I am having some issues with some folders that I set-up using the software centre but didn't appear. They however do appear in dconf.

How do I delete these rogue entries in the dconf settings.

---

### Post by CantankRus on 2016-11-01
Is this in 16.10?
I read your gnome blog link but didn't see a way to create folders in gnome-software in 16.04.

Just delete using your omgubuntu link as a guide.
Multiple entries in dconf are usually of the form... 
```
['entry1', 'entry2', 'entry3']
```
Each surrounded by single quotes separated by a comma followed by a space.

---

### Post by ray42 on 2016-11-01
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
NAME="Ubuntu"
VERSION="16.04.1 LTS (Xenial Xerus)"

Ok having difficulty some errors have crept in and cannot remove some entries. See pics

[https://1drv.ms/i/s!Al9fZuCczxxShC-_xOrvceqdNJp1](https://1drv.ms/i/s!Al9fZuCczxxShC-_xOrvceqdNJp1)

[https://1drv.ms/i/s!Al9fZuCczxxShC65sAETeCFlK8Qn](https://1drv.ms/i/s!Al9fZuCczxxShC65sAETeCFlK8Qn)
[URL="https://1drv.ms/i/s!Al9fZuCczxxShDDljjSTR2Y8z8rp"]
https://1drv.ms/i/s!Al9fZuCczxxShDDljjSTR2Y8z8rp[/URL]
[URL="https://1drv.ms/i/s!Al9fZuCczxxShC-_xOrvceqdNJp1"]
https://1drv.ms/i/s!Al9fZuCczxxShC-_xOrvceqdNJp1[/URL]

[https://1drv.ms/i/s!Al9fZuCczxxShDFiXBvkcYsF3n9w](https://1drv.ms/i/s!Al9fZuCczxxShDFiXBvkcYsF3n9w)

[https://1drv.ms/i/s!Al9fZuCczxxShDN4bEhldxuvqyoZ](https://1drv.ms/i/s!Al9fZuCczxxShDN4bEhldxuvqyoZ)

[https://1drv.ms/i/s!Al9fZuCczxxShDQkrWjxsAlWspGB](https://1drv.ms/i/s!Al9fZuCczxxShDQkrWjxsAlWspGB)


I hope these pics are self explanatory.

---

### Post by CantankRus on 2016-11-02
I don't think there is an easy way to remove dconf keys.
The solution in the link below works but if you're not comfortable with using paths and cd in terminal **don't** attempt.
Also where it says to remove **~/.config/dconf/user** in the first block of code, this must be done after logging out and logging into tty1 console.
[http://askubuntu.com/a/582663/558350]("http://askubuntu.com/a/582663/558350")

---

### Post by vasa1 on 2016-11-02
> **CantankRus said:**
> I don't think there is an easy way to remove dconf keys.
The solution in the link below works but if you're not comfortable with using paths and cd in terminal **don't** attempt.
Also where it says to remove **~/.config/dconf/user** in the first block of code, this must be done after logging out and logging into tty1 console.
[http://askubuntu.com/a/582663/558350]("http://askubuntu.com/a/582663/558350")

Nice! After installing *dump*, I can finally see what's inside that mysterious file.

---

### Post by ray42 on 2016-11-03
This is looking a bit complex, not wanting to mess it up so...
Looking at the site: [http://askubuntu.com/questions/45535/how-do-i-clean-up-my-dconf-database/582663#582663](http://askubuntu.com/questions/45535/how-do-i-clean-up-my-dconf-database/582663#582663)

The reply underneath give an option to install from the software centre "[B]gconf-cleaner".

[/B]> Install gconf-cleaner from the software center.

sudo apt-get install gconf-cleaner

In their own words "GConf Cleaner is a tool to clean your Gconf database up that is possibly cluttered with unnecessary or invalid keys."

I can't get past the software centre as it shows the wrong app. See link to pic: [https://1drv.ms/i/s!Al9fZuCczxxShDpYLKlAUrU1rQvr](https://1drv.ms/i/s!Al9fZuCczxxShDpYLKlAUrU1rQvr)[COLOR=#222222]

I tried installing from the Terminal, but I get an error. See link to pic.

[/COLOR][COLOR=#222222][https://1drv.ms/i/s!Al9fZuCczxxShDiedUvzj_e_s_Bi](https://1drv.ms/i/s!Al9fZuCczxxShDiedUvzj_e_s_Bi)



[/COLOR]

---

### Post by CantankRus on 2016-11-03
gconf is the old gnome way of storing configs.
dconf is what gnome3 uses.

In my newsfeeds just noticed there is a new app called meow to edit gnome menus.
Be aware that it needs and will install java.
As with new third party apps it may be buggy.
[http://www.omgubuntu.co.uk/2016/11/meow-gnome-menu-manager](http://www.omgubuntu.co.uk/2016/11/meow-gnome-menu-manager).

The method I linked to earlier really isn't that dangerous.
Just make a copy of ~/.config/dconf/user...before you start.
These aren't system critical settings.
This is just where user changes are stored.

Command to make a backup....
```
cp ~/.config/dconf/user ~/.config/dconf/user.bak
```

If you deleted **~/.config/dconf/user** it would reset any changes you made to the Gnome menu
and any other user changes.
It would be like logging in to a fresh account.

If you want to start afresh, let me know and I'll post the method.

PS: Your ms links in post #8 require login. ( ...and going anywhere near MS gives me a rash :P)

---

### Post by ray42 on 2016-11-03
> [COLOR=#000000]If you want to start afresh, let me know and I'll post the method.[/COLOR]

Yes please.

Also I dont know what is going on with these links they are set for permissions for anyone to view. Perhaps I should use dropbox links / photos. Will these work?

---

### Post by CantankRus on 2016-11-03
Ok, all we need do is rename the **~/.config/dconf/user** file.
This must be done from a non graphical session because it will be recreated when you logout.

Log out and at the greeter press ctrl+alt+F1
Enter your username then your password.

Now you should see the command prompt, the same as your terminal in ubuntu.
So you're logged into your account but not in a graphical session.

Rename ~/.config/dconf/user  to  ~/.config/dconf/user.bak....
```
mv ~/.config/dconf/user ~/.config/dconf/user.bak
```
*Note the space between **mv** and **~/.config/dconf/user** and the space between **~/.config/dconf/user** and **~/.config/dconf/user.bak**
Type in "exit" and press Enter.

Press ctrl+alt+F7 to take you back to the greeter and log in.



As for posting images, you can upload images to the forums to attach.
When replying, hit the "Go advanced" button and then click on the paper clip.
In the attachment window, click on "choose file" then hit the upload button.
Pics will be attached to bottom of your post.

---

### Post by vasa1 on 2016-11-04
> **vasa1 said:**
> Nice! After installing *dump*, I can finally see what's inside that mysterious file.

Oops! Just realised that the "dump" in question is a *dconf* command:> Dump an entire subpath to stdout. The output is in a keyfile-like
           format, with values in GVariant syntax.and there's no need to install the program *dump* which is a backup utility.

---

