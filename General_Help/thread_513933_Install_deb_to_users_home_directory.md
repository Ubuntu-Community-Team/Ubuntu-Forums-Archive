---
title: "Install deb to users home directory?"
date: 2007-07-31
forum: General Help
---

### Post by HarrisonHopkins on 2007-07-31
I'm making a deb, and I can't find out how to get it to install to the users home directory. I have tried using $HOME and $USER, but all those do are make new folders.

How can I make it so it will install to *any* users home directory, no matter what their name?

---

### Post by HarrisonHopkins on 2007-07-31
I guess I'll bump this.

---

### Post by mikewhatever on 2007-07-31
You can't really chose where to install debs. The installations is usually scattered on the file system, and that's the way it goes. A directory, usually .program_name, is also created in the home directory. Can you explain why you need it localized to the home directory?

---

### Post by HarrisonHopkins on 2007-07-31
No, I didn't mean "Okay so I've got *program names* .deb file. Can I install it to the home directory?

What I meant was that I am making a .deb, and I need some of the files to install into the home directory.

---

### Post by HarrisonHopkins on 2007-07-31
I guess I will bump again.

---

### Post by dfreer on 2007-07-31
Hmmm, the problem is a debian package isn't really suited to install files to any users home directory. The program itself should do so. For example, for zsnes it will save all of the user's information (savestates, screenshots, etc) to ~/.zsnes/. But the package to install zsnes does not do this, zsnes upon being run by a user will create the files for that user only.
That being said, you could possibly hack a preinst file together to install your files if it absolutely needs done. Basically, create a script that will scan /home for folders, and place files in each folder. This really isn't an elegant way to do things, so perhaps you could re-examine why you need to place files in the home folder using the debian package anyways? We could help you if you give some more information about all that. Good luck!

EDIT: Upon reading your initial post, I realized I don't quite understand what you want to do. You want to install a entire program in every user's home directory? Why do you need to do this, it's a better idea to install to a central location, say /usr/local or somewhere.
Also, you can use $USER in your debian package. Let's say your username is harrison, and your uid/gid is 1000:1000. If you create a ./home/$USER/programname folder, although it will have the name "harrison", it will be owned by 1000:1000 and if you were to create the package, install it, it should place the programname folder inside the home directory of the user whose uid/gid is equal to 1000. Although this won't really help because you want the program installed to all user's home folders.

---

### Post by HarrisonHopkins on 2007-07-31
Well, I could install it to somewhere else. Main reason I wanted it to install to the users home directory for for ease of use and... I didn't know how to add a menu item. If someone could tell me how to make the .deb add a menu item, it would be appreciated.

---

### Post by az on 2007-07-31
That is is not possible.  There are strict guidelines as to where Debian packages are allowed to install stuff.  You are not allowed to install applications into a home drive.

---

### Post by stchman on 2007-07-31
> **HarrisonHopkins said:**
> I'm making a deb, and I can't find out how to get it to install to the users home directory. I have tried using $HOME and $USER, but all those do are make new folders.

How can I make it so it will install to *any* users home directory, no matter what their name?

When I write scripts I use the:

```

cd ~

```

This will change directory to the home directory of the current logged in user.  Say for example that joe is logged in by typing cd ~ that is the same as typing cd /home/joe.

You can further do things like cd ~/Desktop as this is the same thing as typing cd /home/joe/Desktop.

$USER will tell you who the current user logged in is.  $HOME will tell you the home directory of the currently logged in user.  The $ commands are mainly used for shell scripting.

Now as to installing programs to the users home directory I don't recommend that at all.  Simple fact is that another user cannot access it.  A good place to install programs in the /opt folder and put a shell script in the /usr/bin directory.

---

### Post by Kodfish on 2007-07-31
dude, a naked cd like ```
cd
``` will take you to your home dir.

---

### Post by dfreer on 2007-08-01
To install menu icons, simply create a file called yourpackagename.desktop, and install it to /usr/share/applications/
You'll need to add specific things, especially across WM (KDE, Gnome, etc). Here's an example of my (poorly written, most likely) /usr/share/applications/psx.desktop file:
```
[Desktop Entry]
Version=0.5
Encoding=UTF-8
Name=pSX32
Name[en]=pSX32
Name[en_US]=pSX32
GenericName=Playstation Emulator
GenericName[en]=Playstation Emulator
GenericName[en_US]=Playstation Emulator
Comment=Play Playstation games using original CD's or images
Exec=/usr/local/games/psx32/pSX
Terminal=false
Type=Application
Icon=/usr/share/pixmaps/pSX.png
Categories=GNOME;GTK;Application;Game;

```

Try looking at other .desktop files in your /usr/share/applications/ folder, or search online on the correct way to make one. Anything else you need help with?

BTW. it would be far eaiser to create a directory somewhere other than an user's home folder, and then create (1) your .desktop file (2) put the program name into the path of the user (like symbolic link the binary to /usr/bin/ or something like that.

> **az said:**
> That is is not possible.  There are strict guidelines as to where Debian packages are allowed to install stuff.  You are not allowed to install applications into a home drive.

You should try to follow the debian guidelines for making a package as much as possible, simply to get into the habit. But the above is only true if you *want* to follow debian guidelines :P you can do whatever you want with your own package, just don't be surprised if you can't get it into a repository.

---

### Post by darkmaster on 2007-11-27
Ok, I've got very similar problems. But I'm going to explain WHY I need this done :)
I'm creating deb packages for Geubuntu, now, the problem is that I've got some configuration files needed by Enlightenment to run the "geubuntu way". That is, I've got to tell E17 which applications to autostart and which to add to Ibar. The problem is that installing those configuration files to the proper dir only, that is:

usr/share/enlightenment/data

won't be enough. That's because E17 creates a .e dir in the home folder of any user with some configuration files inside that are not the same as those I install! Why it does it, is only understandable to the creators of E17 I guess.

So I need my package to be able to delete the .e dir in any home dir and replace it with MY .e geubuntish dir, after the package installs. So I guess I have to do it using a postinst script of some kind. Any idea, any suggestion, any help in general? Could anyone give me an hint on how to create such a script? Or how to solve this problem in another way if you can ;)

Thank you very much to all!

---

### Post by darkmaster on 2007-11-27
> **darkmaster said:**
> Ok, I've got very similar problems. But I'm going to explain WHY I need this done :)
I'm creating deb packages for Geubuntu, now, the problem is that I've got some configuration files needed by Enlightenment to run the "geubuntu way". That is, I've got to tell E17 which applications to autostart and which to add to Ibar. The problem is that installing those configuration files to the proper dir only, that is:

usr/share/enlightenment/data

won't be enough. That's because E17 creates a .e dir in the home folder of any user with some configuration files inside that are not the same as those I install! Why it does it, is only understandable to the creators of E17 I guess.

So I need my package to be able to delete the .e dir in any home dir and replace it with MY .e geubuntish dir, after the package installs. So I guess I have to do it using a postinst script of some kind. Any idea, any suggestion, any help in general? Could anyone give me an hint on how to create such a script? Or how to solve this problem in another way if you can ;)

Thank you very much to all!

I tried with the following script as a postinst:

```
#!/bin/sh

sudo rm -d -r -f ~/.e
mkdir ~/.e
mkdir ~/.e/e
cp -f -r /usr/share/enlightenment/data/* ~/.e/e/
```

But it didn't work, as I suspected even before trying, because when a deb is installed the system considers itself as root, so the operation was successfull but the files where copied into the /root/.e/e dir, that is the root home dir. So using the symbol ~ won't work during a deb package installation because it points to the root home dir. Any other idea?

---

