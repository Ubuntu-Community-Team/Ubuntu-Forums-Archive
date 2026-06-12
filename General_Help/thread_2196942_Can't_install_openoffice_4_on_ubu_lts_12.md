---
title: "Can't install openoffice 4 on ubu lts 12"
date: 2014-01-01
forum: General Help
---

### Post by geharder on 2014-01-01
I cannot install openoffice in ubuntu lts 12.04, it apears the following message: Package operation failed The installation or removal of a software package failed. What I am doing wrong. I am a windows user, so I don't have much experience with ubuntu.

Thanks

---

### Post by deadflowr on 2014-01-01
You have to completely remove libreoffice in order to install openoffice.
Try
```
sudo apt-get purge libreoffice*
```
if you haven't already purged libre.

---

### Post by geharder on 2014-01-01
The shows follow text's

openoffice-debian-menus installed

These programs are running from a terminal
openoffice4, openoffice4-printeradmin

But I cant find openoffice to start it

---

### Post by deadflowr on 2014-01-01
Open the dash and type openoffice.
If it's installed, you should get a few entries for openoffice, like writer and base, calc.

To open the dash click the top icon in the panel on the left side.

Anyway, how did you install it?

---

### Post by geharder on 2014-01-01
Hi,
In the dash is noting,
I did download it and extract the file to the download folder. After that a doubleclic on Downloads/en-US/DEBS/desktop-integration/openoffice4.0-debian-menus_4.0-9714_all.deb
Ubuntu opens automatily theSoftware centre and clic on install.

---

### Post by deadflowr on 2014-01-01
Okay.
You need to do this
in a terminal run
```
sudo dpkg -i /home/**username**/[COLOR=#000000]Downloads/en-US/DEBS/*.deb[/COLOR]
```
replace the username with your username.
It should install the openoffice packages.
Then when it finishes, 
Run
```
[COLOR=#000000]sudo dpkg -i /home/**username**/Downloads/en-US/DEBS/desktop-integration/openoffice4.0-debian-menus_4.0-9714_all.deb[/COLOR]
```

This is all done in a terminal.
It could be done in the software center, but if you look at the contents of the folder DEBS, it has a lot of files.
Those files need to be installed and using the above terminal command does that faster than using the software center.

When using the terminal, the sudo part gives it the command to use elevated rights.
It will ask for a password.
Enter the password you created when you installed Ubuntu.
The password filed will appear to be blank or not writing.
It is simply invisible so type the password as best you remember it.

Post any problems you have if any.

---

### Post by geharder on 2014-01-01
Now its works and thanks for your help, I didn't know that I was back in the '90s working whit DOS, but  thanks for your help, in Windows is it only a doubleclic on .exe

---

### Post by deadflowr on 2014-01-01
> **geharder said:**
> Now its works and thanks for your help, I didn't know that I was back in the '90s working whit DOS, but  thanks for your help, in Windows is it only a doubleclic on .exe

Normally, software is easier to install.
Openoffice is an extreme exception.
Ubuntu use to include openoffice, but because of [Oracle's]("http://en.wikipedia.org/wiki/Oracle_Corporation") purchase of [Sun]("http://en.wikipedia.org/wiki/Sun_Microsystems"), issues came up.
The linux community forked openoffice and started[ the Document Foundation]("http://www.documentfoundation.org/"), which develops libreoffice.
But because they use a lot of the same packages, there are some conflicts, which is why you have to remove libreoffice to install openoffice.
And probably why openoffice isn't in the repository system.
[Apache]("http://www.apache.org/") now controls the development of openoffice.

---

### Post by geharder on 2014-01-01
The Openoffice and Libreoffice problem shows how the Linux and Free programing society works, the are not able to work together and make compromise. And everyone makes his own OS, Internet browser, Office suite because the can't accept the opinion from a other person. If we look at central and southamerica we have a lot of small countrys but if we look to USA the make from 48 countrys only one big country and everyone notes the diference and all these linux programers works the same way, every clan his own king.

---

### Post by Bucky Ball on 2014-01-01
> **geharder said:**
> The Openoffice and Libreoffice problem shows how the Linux and Free programing society works, the are not able to work together and make compromise. And everyone makes his own OS, Internet browser, Office suite because the can't accept the opinion from a other person. If we look at central and southamerica we have a lot of small countrys but if we look to USA the make from 48 countrys only one big country and everyone notes the diference and all these linux programers works the same way, every clan his own king.

Completely off-topic and ill-informed. The Libreoffice/Openoffice situation was explained already on this thread in reasonable detail. If you want to know more about that exception to the rule, do some research on it. The solution is VERY simple and if you would have known, you would have completely purged Libreoffice prior to installing Openoffice. That way, Openoffice would have installed from the .deb just like an .exe.  

Your issue on this thread is solved, so:

*Thread closed.*

If you wish to share opinions regarding the state of open-source software development and its problems, please do so in one of the non-support areas of the forums.

Incidentally, LO and OO are virtually identical, so there are no real advantages in installing one over the other unless you rely on an OO function that doesn't exist in LO.

---

