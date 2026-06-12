---
title: "Installing Seamonkey"
date: 2016-05-02
forum: General Help
---

### Post by J_Templeton on 2016-05-02
I am a longtime old Netscape/Mozilla browser user and have been using Seamonkey the past several years.  It used to be easy to install i Ubuntu but it seems it is no longer included in the sources.  I have already unlocked the restricted sources in sources.list but can't seem to install it.  If I download it from the Seamonkey website, how do i go about installing it?  I have searched this but everything I come across seems out of date.

---

### Post by lisati on 2016-05-02
There are instructions on the Seamonkey website.

[http://www.seamonkey-project.org/doc/install-and-uninstall#install_linux](http://www.seamonkey-project.org/doc/install-and-uninstall#install_linux)

---

### Post by J_Templeton on 2016-05-02
Thanks lisati.  I followed the method outlined in the above link but using ```
./seamonkey
``` yelds the response ```
No such file or directory
```.  It is definitely there though.  I am not an expe[FONT=arial]rt, but doesn't the tar command merely extract the files or is there an argument (jxvf) included for installing the program?[/FONT]

---

### Post by vasa1 on 2016-05-02
Also [Installing the light-weight web browser seamonkey]("http://ubuntuforums.org/showthread.php?t=2281120").


> **J_Templeton said:**
> ... I followed the method outlined in the above link but using ```
./seamonkey
``` yelds the response ```
No such file or directory
```.  It is definitely there ...
Please provide the actual steps you followed. It's possible there could be some unwanted differences.

From which folder did you run */.seamonkey*?

---

### Post by J_Templeton on 2016-05-03
i followed the directions from [http://www.seamonkey-project.org/doc...#install_linux]("http://www.seamonkey-project.org/doc/install-and-uninstall#install_linux") exactly.  Apparently I forgot the "2" when I tried to run it, thus 'no such file etc.' But from ~/seamonkey2 i get the response```
./seamonkey: Is a directory
```

Is the Install Seamonkey script still reliable?  

I tried adding [http://sourceforge.net/p/ubuntuzilla.../#installation](http://sourceforge.net/p/ubuntuzilla.../#installation) to sources.list but when I try to update it the terminal responds that it is malformed.  I suppose I am missing something there; I was hoping I could simply install via apt-get with the repository.

I'll try installing the latest deb from sourceforge: the link above appears to be outdated.

---

### Post by J_Templeton on 2016-05-03
I was able to install the deb and there is even an icon in the menu but MATE returns the error "failed to execute child process "seamonkey" (No such file or directory.  I can't see how to redirect the icon (if it is possible) to the correct directory.

---

### Post by sudodus on 2016-05-03
Maybe this link can help you: [Installing the light-weight web browser seamonkey](http://ubuntuforums.org/showthread.php?t=2281120)

---

### Post by J_Templeton on 2016-05-03
Problem solved.  I added the current repository to sources.list, removed the previous installation and re-installed via apt-get.  The links were definitely a help.  Thanks, James

---

### Post by &amp;KyT$0P# on 2016-07-11
I use SeaMonkey from tarballs and I can say that the instructions on the SeaMonkey website seem unnecessarily complicated and convoluted.  Just extract the tarball to home directory (or /opt for system-wide installs) - it should extract into its own subdirectory named "seamonkey".  Then, to start SeaMonkey, run the "seamonkey" executable inside that directory (it's not an install script).

If you get this error
> "failed to execute child process "seamonkey" (No such file or directory.
it means you've downloaded the wrong architecture tarball (i686 is 32-bit; x86_64 is for 64-bit only).
(note that linux 64-bit SeaMonkey is listed only under "Contributed Builds")

To get SeaMonkey in the list of applications for your desktop, all you need to do is create a file named seamonkey.desktop either in ~/.local/share/applications (or /usr/share/applications for system-wide install), and give it this contents:
```

[Desktop Entry]
Encoding=UTF-8
Name=SeaMonkey
Exec=/home/user/seamonkey/seamonkey
Icon=/home/user/seamonkey/chrome/icons/default/default48.png
StartupNotify=true
Type=Application
Terminal=0
Categories=Network

```
Obviously, replacing '/home/user' with the full path to the place you extracted SeaMonkey, whether it be your home directory or /opt or wherever you chose.

See how easy this is? :)

Hope this helps, cheers.

---

