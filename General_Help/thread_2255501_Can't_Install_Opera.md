---
title: "Can't Install Opera"
date: 2014-12-05
forum: General Help
---

### Post by Rick St. George on 2014-12-05
Attempting to install Opera browser on current Ubuntu, and open with Software Center. 
The "busy circle" goes round-n-round for a litle while, then ... Poof it disappears and no Opera.

Need to install, other than Firefox, and good browser in Unbuntu to handle, a heavily dependent Java-based, Market Center Trading Platform.

Any suggestions?
Thanks!
Rick

---

### Post by deadflowr on 2014-12-05
How are you trying to get it?
from the software center, or did you download the installation file from opera.

I do not believe opera is in the software center by default.
Here's the latest opera, though it still considers it beta since it's the newly redesigned version
[http://www.opera.com/developer](http://www.opera.com/developer)

I've used it, and find it stable enough...

---

### Post by Frogs Hair on 2014-12-05
There is now a stable version of the latest incarnation of Opera for Linux unless you want the developer version. You could try the gdebi package installer which I prefer for non repository packages   .```
sudo apt-get install gdebi
``` Right click the .deb pkg and select open with gdebi package installer

[http://www.opera.com/computer/linux](http://www.opera.com/computer/linux)

---

### Post by Rick St. George on 2014-12-05
Clicked on DOWNLOAD from [www.oper.com/download](www.oper.com/download)
and chose to open with Ubuntu Software Center.

So how do i install it as it is not in the repository?
I saved the file - Opera-Developer_27.0.1689.22_AMD64.deb
from your Link above.

Thanks!

---

### Post by dragonfly41 on 2014-12-05
As advised above use GDebi Package Installer which you can install from Ubuntu Software Centre.   
GDebi appears in menus here ...
Applications > System Tools > GDebi Package Installer.

Then for i386 (your installation may be different) go here .. [http://www.opera.com/download/guide/?os=linux-i386](http://www.opera.com/download/guide/?os=linux-i386)

opera_12.16.1860_i386.deb
Note: This is not the Developer version.

(choose to suit your platform .. I have 32bit installation).

Using GDebi > File .. select the newly downloaded *.deb file (e.g. located in ~/Downloads) and click "Install Package"

After installation Opera appears in Applications > Internet > Opera.

---

### Post by Frogs Hair on 2014-12-05
This link is for Opera 26 stable not 12.16 

[http://www.opera.com/computer/linux](http://www.opera.com/computer/linux)

---

### Post by Paulgirardin on 2014-12-05
There seems to be,let's say an "idiosyncrasy" with the Opera install.I have installed it into several Ubuntu fresh installs and I always encounter the following behaviour.
Open the .deb file downloaded from the Opera website with Software Center.Click install.The installation process proceeds and then stops part way,the software center does not change "install" button to "remove" and does not flag the application as installed.
That is: until you search for Opera in the dash and start the application.You then get the EULA and click agree.From then on everything is normal.

btw.   The new Opera for Linux Computers is  the new Chromium based browser and does not have the built in email client.If you want the email client,you have to install the earlier version.

---

### Post by deadflowr on 2014-12-05
> **Frogs Hair said:**
> This link is for Opera 26 stable not 12.16 

[http://www.opera.com/computer/linux](http://www.opera.com/computer/linux)

Sweet!
Thanks for the link.
Now I have opera-stable and opera-developer installed.
Because both run under different names the don't interfere with one another.
Much like firefox and firefox-nightly(via mozilla ppa)

---

### Post by Rick St. George on 2014-12-05
WOW - I don't want the Chromium. Heard too many bad things about it.
And what is the "dash" anyway?  Opera doesn't show up anywhere.
Have Ubuntu-Studio flavor installed.

Thanks

---

### Post by Rick St. George on 2014-12-05
Tried installing gdebi", but Software Center closed and disappeared like half way through install. 
Same as when trying to install Opera.  What could be going on?

Rick

---

### Post by Frogs Hair on 2014-12-05
The unsupported Opera 12.16 is the last version based on the presto engine and many of the services hot-linked in the browser are closed down. The new version uses the blink engine as does Chromium and Google Chrome   . Iv'e had no problems on Ubuntu or Win 7 even with the developer version. Dash is a feature of the unity desktop in Ubuntu. Remember to identify the Ubuntu flavor in use when you tag your posts or it could be assumed you are using default Ubuntu. Try starting Opera from the terminal. ```
 opera
```


Edit: For best results fully download and _save _ the package and then install it from the downloads folder.

---

### Post by deadflowr on 2014-12-05
> **Rick St. George said:**
> Tried installing gdebi", but Software Center closed and disappeared like half way through install. 
Same as when trying to install Opera.  What could be going on?

Rick

Ubuntu Studio?
I don't think studio uses Unity,which is what uses what is called the dash(It's unity's menu system)

Hm, If you try running the update manager (I do not know what it would be called in studio, be most likely just that -update manager)
Is it running correctly, or do you see errors or problems?
Sometimes when the software center or other installers don't work right, it has something to do with the package management system, and the update manager is a good place to look and see.
If that too does not seem to be working right try the update commands
```
sudo apt-get update
sudo apt-get upgrade
```

You can also try installing the old command line way
```
cd Downloads
sudo dpkg -i opera_12.16.1860_i386.deb
```
I'm guessing the download is in the Downloads folder, and you still have the 12.16.xxx version, or that is the one you want to install.

One way or another we'll figure it out.

---

### Post by Rick St. George on 2014-12-05
Ahhh !   
Tried again WITHOUT the Firefox browser opened and it worked.

Ubuntu Software Center installed GDEBI,  then
GDEBI installed Opera v26 for AMD64.

Running this on an old Dell Precision 390 workstation with 1GB Ram, and 250GB HD.

Thanks!
Case Closed.
Rick

---

### Post by Paulgirardin on 2014-12-05
Are you running Ubuntu Unity?
The Dash is the gobal search window that opens when you tap the super key.

---

