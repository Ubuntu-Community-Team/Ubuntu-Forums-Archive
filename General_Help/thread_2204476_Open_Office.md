---
title: "Open Office"
date: 2014-02-08
forum: General Help
---

### Post by moses65 on 2014-02-08
I want to run Open Office instead of Libre Office.  How do I do that ?

---

### Post by bapoumba on 2014-02-08
Thread moved to General help.

---

### Post by Sef on 2014-02-08
One set of directions for installing OpenOffice is [here]("http://www.tecsysadmin.com/how-to-install-apache-openoffice-4-0-in-ubuntudebianzorin-os/").

Check out [OpenOffice.org]("http://www.openoffice.org/").

---

### Post by deadflowr on 2014-02-08
Libre and Open don't like each other(not really, but they share a few common files so a blanket install of open office usually borks).
To install, as pointed out on various threads and possibly on openoffice site is this
purge libre
```
sudo apt-get purge libreoffice*
```
then download openoffice
When open is downloaded extract the files somewhere then move into the folder DEBS
and run
```
sudo dpkg -i *.deb
```
this will install the packages.
Then move into the folder  called desktop-integration and run the command again.
Now you have openoffice.

Quick break down
Extract it
 ```
tar xvf <path to the tar package>
```
Move into the DEBS folder
```
cd <your path/en-US(or whatever the locale you have is)/DEBS
```
then run dpkg to install
```
sudo dpkg -i *.deb
```
then when that is done move into the folder desktop-integration and run
```
sudo dpkg -i *.deb
```
again.

If not sure where you are in the file system use ls and pwd.

---

### Post by moses65 on 2014-02-08
Thank you. Seems to me that some of the functions in Open Office work much better than they do in Calc in LIbre Office, and also I use Open Office on the Mac.

---

### Post by moses65 on 2014-02-10
Right, I have carefuly followed all the instructions you kindly gave me and the ones from Open Office themselves and changing the version to 4.0.1 ! and the installation seemed to go perfectly but on restart no sign of anything.  Open Office is being chosen by the UK Government as the new Standard so it is really important that we can install it.  Any ideas ?

---

### Post by Gordonbp531 on 2014-02-10
> **moses65 said:**
> Open Office is being chosen by the UK Government as the new Standard 

I don't think you'll find that's correct. What is being introduced as standard is **ODF**
not any specific application.
So you don't *have* to install Open Office.

---

### Post by deadflowr on 2014-02-10
> **moses65 said:**
> Right, I have carefuly followed all the instructions you kindly gave me and the ones from Open Office themselves and changing the version to 4.0.1 ! and the installation seemed to go perfectly but on restart no sign of anything.  Open Office is being chosen by the UK Government as the new Standard so it is really important that we can install it.  Any ideas ?

I am going to be under the assumption that you are using standard Ubuntu, okay.

So when you press the windows key on the keyboard to open up the dash, what shows up if you type "Writer'?
Is anything there, or does it say Apache-blah-blah, or is it still libreoffice writer?

---

### Post by moses65 on 2014-02-10
You, Sir, are an Ace.  Got it locked into the launcher now.  Thank you very much indeed !

---

