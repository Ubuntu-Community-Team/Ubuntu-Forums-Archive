---
title: "Hamachi for Linux"
date: 2007-02-20
forum: General Help
---

### Post by Bob Sugar on 2007-02-20
does anyone know of a preconfigured installer / installer script for [Hamachi]("http://www.hamachi.cc/download/list.php") including the gui ([gHamachi]("http://www.penguinbyte.com/software/ghamachi/")) for  Ubuntu?

While we're on the subject of Windows file sharing, does anyone have an easy answer for how to access my Ubuntu box from a Windows machine - it keeps asking me for user/password info which I don't have - I can access windows from Linux with no problems, however.

Thanks in advance, any and all assistance is greatly appreciated.

---

### Post by kelbizzle on 2007-02-20
I don't know about the installer script. I just checked out both links. They both seem pretty simple to install. I checked out the hamachi one.  For that all you have to do is...
Download it
Unzip it to the desktop
Open Terminal and cd to ~/Desktop/Hamachi*
Then run make install.  

For the Gnome Front end just....
Unpack the downloaded tar file
Open Terminal
Make 'ghamachi' executable: chmod +x ghamachi
To run the app: ./ghamachi 

The username and passord should be the name and password of your user. If that doesn't work.  This howto might help you with your samba issue.   [http://ubuntuforums.org/showthread.php?t=26438](http://ubuntuforums.org/showthread.php?t=26438)

---

### Post by Bob Sugar on 2007-02-21
thanks, I'll look into it - one question though - what do you mean by "run make install"?.

As you've probably gathered by now, I'm still pretty new at this...

---

### Post by justin whitaker on 2007-02-21
> **Bob Sugar said:**
> thanks, I'll look into it - one question though - what do you mean by "run make install"?.

As you've probably gathered by now, I'm still pretty new at this...

In a terminal, cd (change directory) to where ever you put ghamachi, and type "make install" then hit enter.

---

### Post by hikaricore on 2007-02-21
> **justin whitaker said:**
> In a terminal, cd (change directory) to where ever you put ghamachi, and type "make install" then hit enter.

make install will probably have to be run as:

**sudo make install**

unless this by some chance installs to a non standard location

---

### Post by Bob Sugar on 2007-02-21
Thanks all, got it running. I need to do a little more work using the command lines, but I think I'm picking them up.

Now, the only thing left to do is figure out why I can't open the share in Hamachi.... c'est la vie.

---

### Post by moon2js on 2007-03-30
I set up Windows sharing in Edgy/Gnome (the easy GUI way), but I still had to go to console with...

```
sudo smbpasswd -a *myusername*
```

...to make it work. Then I access my share from another machine with username and password.

Maybe I did something wrong, but wouldn't it make sense if the GUI way at least let you know that you have to take further action to make the share work?

---

