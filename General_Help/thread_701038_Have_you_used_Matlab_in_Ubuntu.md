---
title: "Have you used Matlab in Ubuntu?"
date: 2008-02-18
forum: General Help
---

### Post by Lucretia on 2008-02-18
This is quite a general question. I had problems with my Matlab installation (2006A) in Feisty. It seemed to be mostly a Matlab GUI issue, but it made any plotting impossible. Searching the forums just now, it seems that a few people are successfully using Matlab 2007 versions in 7.10. I should point out that Matlab used to work fine (even in Beryl and Compiz once some Java stuff was sorted out), and suddenly after an Ubuntu update, there were problems.

On top of that, people here may or may not know that Matlab doesn't really run at all in Fedora 8 (which is the standard Linux distro used in my department) without serious messing around with the OS (potentially breaking a lot of things). Obviously this is a big problem. If people are successfully using Matlab in Ubuntu, then I think people in my department would consider switching.

So, if you successfully use Matlab in any Ubuntu release, can you please post what version of Matlab you were using and what version of Ubuntu? Also, please say if you had to do any messing around with libraries or anything else if Matlab didn't work right out of the box.

This is very much appreciated!

---

### Post by radiocognition on 2008-02-18
I have just installed Matlab 2007.a on my Gutsy install just two weeks ago.  Took a little bit of work though.  I mounted an ISO of the Matlab UNIX install disk and ran the scripts as described by the manual (also on the disk).  The Matlab installation finished, but for some reason (something having to do with root permissions, even though I ran the installer as super user), the open matlab script failed.  On my insall, the terminal command "matlab" is supposed to open a new matlab session, and executes the file ~matlabroot/bin/matlab where matlabroot is the directory that you choose for your install.  I had to make a symbolic link to the script and place it in my homefolder.  Then I created a Launcher and excecuted the linked file to open the program.  Let me know if you have the same issues.

When I open the program, a terminal window pops open with it (cant quite figure out how to get rid of it).  Other than that, Matlab runs beautifully.  I have had no problems with 2 & 3D graphing, or any of the help files.

---

### Post by amd-64 on 2008-02-18
I have MATLAB R2007b, the current release running without any issues in Gutsy 7.10. 

It is, of course, much cleaner and faster that the Windows version. Matlab keeps  the entire installation in one folder and does not add any links in other locations such as /usr/bin or /etc or /usr/share. So while it is not a deb install, it is quite easy to manage.

The only issue I had was during installation was caused by an out of date license server. I am using a concurrent license, and the issue was resolved with a new license.dat file.

---

### Post by amd-64 on 2008-02-18
> **radiocognition said:**
> I have just installed Matlab 2007.a on my Gutsy install just two weeks ago.  Took a little bit of work though.  I mounted an ISO of the Matlab UNIX install disk and ran the scripts as described by the manual (also on the disk).  The Matlab installation finished, but for some reason (something having to do with root permissions, even though I ran the installer as super user), the open matlab script failed.  On my insall, the terminal command "matlab" is supposed to open a new matlab session, and executes the file ~matlabroot/bin/matlab where matlabroot is the directory that you choose for your install.  I had to make a symbolic link to the script and place it in my homefolder.  Then I created a Launcher and excecuted the linked file to open the program.  Let me know if you have the same issues.

When I open the program, a terminal window pops open with it (cant quite figure out how to get rid of it).  Other than that, Matlab runs beautifully.  I have had no problems with 2 & 3D graphing, or any of the help files.

matlab command ~matlabroot/bin/matlab does not work because matlab folder is not installed in /usr/bin or somewhere on the path. Instead of linking in your home folder, you could link it to /usr/bin

sudo ln -s ~matlabroot/bin/matlab /usr/bin/matlab

and then executing matlab should start the GUI

---

### Post by radiocognition on 2008-02-18
> **amd-64 said:**
> matlab command ~matlabroot/bin/matlab does not work because matlab folder is not installed in /usr/bin or somewhere on the path. Instead of linking in your home folder, you could link it to /usr/bin

sudo ln -s ~matlabroot/bin/matlab /usr/bin/matlab

and then executing matlab should start the GUI

Thank you, that did the trick and was much simpler than my previous method

---

### Post by Lucretia on 2008-02-18
Please also add if you are using 64-bit or 32-bit Ubuntu if you haven't already.

---

### Post by radiocognition on 2008-02-19
I am running 32-bit

---

### Post by amd-64 on 2008-02-19
I am running 64-bit on an intel quad core desktop and a core 2 laptop.

---

