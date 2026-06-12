---
title: "Is there a ppa for ApacheOffice 4.0"
date: 2013-12-24
forum: General Help
---

### Post by Henry04 on 2013-12-24
Hi richardsdma,

I was looking for info regarding OO install on Ubuntu (I use Ubuntu Studio)... Please look carefully, regarding the command to install from into the DEBS folder (minute difference of one little space!). Correct command is: **sudo dpkg -i *.deb**. I had to go to the AOO install page to get this... Hope this helps (someone).

But thanks for your help other ways.

Regards,
Henry04

[https://wiki.openoffice.org/wiki/Documentation/FAQ/Installation/How_do_I_install_OpenOffice.org_on_Linux%3F](https://wiki.openoffice.org/wiki/Documentation/FAQ/Installation/How_do_I_install_OpenOffice.org_on_Linux%3F)

P.s., I used gdebi to install the desktop integration package.

---

### Post by Smallwheels on 2014-01-04
Why must LibreOffice be removed first? 
How is that done? 
What will happen to all of my current LibreOffice files if I delete the program that opens them?

Making numbered lists in LibreOffice is just buggy when it gets to the number 10. It is as if the thing hits tab every time it gets to that double digit. I can't get rid of that space in fonts other than the default. That is why I want to try OpenOffice.

---

### Post by cariboo on 2014-01-04
Moved to a thread of it's own, as this question isn't about Trusty.

---

### Post by deadflowr on 2014-01-04
> **Smallwheels said:**
> Why must LibreOffice be removed first? 
How is that done? 
What will happen to all of my current LibreOffice files if I delete the program that opens them?

Making numbered lists in LibreOffice is just buggy when it gets to the number 10. It is as if the thing hits tab every time it gets to that double digit. I can't get rid of that space in fonts other than the default. That is why I want to try OpenOffice.

1) There are conflicting files between libreoffcie and openoffice.
Having libreoffice installed causes the installation of openoffice to fail.
The Why? is something the devs of both need to workout.

2)
```
sudo apt-get purge libreoffice*
```

3)Your files will be where ever you saved them, as long as your files aren't part of libreoffice's core system files.
Most likely, they'll be in the Documents folder where you left 'em.
You should still be able to open them in openoffice, without trouble.

4)No comment on the bugginess of libreoffice.

---

### Post by Smallwheels on 2014-01-04
Where did the instructions go for installing OpenOffice? I will need them. There was some mention of dragging something into the terminal. Was that correct? I've copied and pasted things into a terminal but never dragged something into it. I just ask for help and follow instructions exactly as stated, hoping the advice is correct. So far things have worked. 

Please add the installation instructions again. 

Thank you for your help.

---

### Post by Smallwheels on 2014-01-04
I forgot to ask. Is java installed on Ubuntu 13.04? I read that it is needed for Open Office to work.

---

### Post by monkeybrain20122 on 2014-01-04
> **Smallwheels said:**
> I forgot to ask. Is java installed on Ubuntu 13.04? I read that it is needed for Open Office to work.

Not by default, you can install it from the repo yourself (OpenJDK)

BTW, you can install up to date Libreoffice from ppa. [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

---

### Post by monkeybrain20122 on 2014-01-04
> **Smallwheels said:**
> Where did the instructions go for installing OpenOffice? I will need them. There was some mention of dragging something into the terminal. Was that correct? I've copied and pasted things into a terminal but never dragged something into it. I just ask for help and follow instructions exactly as stated, hoping the advice is correct. So far things have worked. 

Please add the installation instructions again. 

Thank you for your help.

Well just as deadflower said remove LO

```
sudo apt-get --purge remove libreoffice*

```
Download the tarball from AOO, extract

cd into the extracted folder

run 

```
sudo dpkg -i *.deb
```

Aside:This just basically installs a whole bunch of debs simultaneously, if you have only one you can just right click it or "sudo dpkg -i nameofdeb.deb"

Then there may be a subfolder called DEB for desktop integration, go in there and click to install the .deb (or cd into it and run "sudo dpkg -i *.deb" again)

Then delete the extracted folder as well as the AOO tarball.

I have not used AOO, but these are  the steps to install LO and the old OOO from downloaded tarball, I suppose it would be similar for AOO.

Edited: I assume they do provide a tarball with .debs for debian and that you don't need to compile it. If they only provide source tarball then you need to compile, or if they only provide rpm (as did OOO at first) then you need alien to convert the rpms to debs.

---

### Post by deadflowr on 2014-01-04
> **Smallwheels said:**
> Where did the instructions go for installing OpenOffice? I will need them. There was some mention of dragging something into the terminal. Was that correct? I've copied and pasted things into a terminal but never dragged something into it. I just ask for help and follow instructions exactly as stated, hoping the advice is correct. So far things have worked. 

Please add the installation instructions again. 

Thank you for your help.



monkeybrain20122 ninja'd what I posted.
But to add to it
after installing the debs in DEB move into the desktop-integration folder and run the sudo dpkg command again.
```
cd desktop-integration
```
```
sudo dpkg -i *.deb
```
This will complete the install.

---

### Post by deadflowr on 2014-01-04
> **monkeybrain20122 said:**
> 
I have not used AOO, but these are  the steps to install LO and the old OOO from downloaded tarball, I suppose it would be similar for AOO.

Edited: I assume they do provide a tarball with .debs for debian and that you don't need to compile it. If they only provide source tarball then you need to compile, or if they only provide rpm (as did OOO at first) then you need alien to convert the rpms to debs.

Point one, it is the same as before, and as you posted.(instruction wise)
The one thing, though is , if I remember, because I'm not on a machine with AOO installed, I think the menu's are non global menu.
Meaning normal non-unity menu's.

Point Two, it's debian packages. So no need to worry about converting or compiling.

---

### Post by Smallwheels on 2014-01-05
I searched for Java through the dash and found Open JDK Java 7 Policy Tool. Does that mean my computer already has Java? When I originally loaded 13.04 I also got that package with the restricted extras.

---

