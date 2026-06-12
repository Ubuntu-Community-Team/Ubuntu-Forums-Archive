---
title: "LibreOffice upgrade"
date: 2017-06-30
forum: General Help
---

### Post by Liamdale on 2017-06-30
I have LibreOffice 5.0.0.4  This week some of my calc files began crashing.  I had been thinking for a while to upgrade my libreoffice to the most recent stable version.  The site had 5.2 as the stable version.  In the past I had to remove the old version of LibreOffice to install a new version. My notes indicate:

> sudo apt-get purge LibreOffice?

install LibreOffice
1. Unpack the Downloaded Archive
2. Change to the unpacked directory:
~/Downloads/LibreOffice_4.4.1.2_Linux_x86_deb/DEBS
3. Enter the following command to have your system incorporate and recognise the
installation (you will be prompted to enter your root password before the command
will be executed):
4. execute command : sudo dpkg -i *.deb

Since my notes were old, I checked the net on the most recent information on LibreOffice installation

several sites recommended not to use the previous method but the following:

> sudo add-apt-repository ppa: libreoffice/ppa
sudo add update; sudo apt dist-upgrade
[COLOR=#333333][FONT=&amp]sudo apt install libreoffice-gtk2 libreoffice-gnome[/FONT][/COLOR]

[http://tipsonubuntu.com/2016/08/03/libreoffice-5-2-released-how-to-install/](http://tipsonubuntu.com/2016/08/03/libreoffice-5-2-released-how-to-install/)

I did but no change of version has occurred.  LibreOffice icons still indicate version 5.0.0.4 (and About dialogue).
One change though the calc files which crashed do not seem to crash.

I have tried to find any reference to the LibreOffice 5.2 in the dash but only 5.0 is indicated.

The terminal installation seems to have went well.

My questions:
Should I return to the older method dispite the recommendations?
Does anyone have an idea of what happened in my current installation attempt?

One last note: verification of the /opt folder shows LibreOffice 5.0 still present.

---

### Post by kc1di on 2017-06-30
you should use this```
 ppa sudo add-apt-repository ppa:libreoffice/ppa
```
it will ugrade you to version 5.3 and works very well.
for more info see[ here.]("http://ubuntuhandbook.org/index.php/2017/02/install-libreoffice-5-3-ppa-snap-in-ubuntu-16-04/")

---

### Post by howefield on 2017-06-30
> **Liamdale said:**
> I did but no change of version has occurred.

"*sudo add update*" may be a typo in your post here but if it is what you typed in the terminal it won't work and the system will be unaware of the available packages from the ppa that you added.

Use sudo apt update (as I'm sure you know and meant to)

---

### Post by Liamdale on 2017-06-30
I will be marking this threat as solved but it probably isn't.

I found several other sites concerning the installation of LibreOffice and found the following instructions:
> 
sudo apt remove libreoffice-gtk
sudo apt-get remove --purge libreoffice*


sudo add-apt-repository ppa:libreoffice/ppa
sudo apt update
sudo apt dist-upgrade
sudo apt-get install libreoffice
sudo apt install libreoffice-gtk2 libreoffice-gnome


I tried them out and LibreOffice 5.3 was installed but Writer refused to load.  Calc loaded fine and using the New menu command, I could load Writer ... weird

I realized my error :  I assumed that the old LibreOffice was removed when I used the command : 
> sudo apt install libreoffice-gtk2  
but it only removed the libreoffice-gtk

Other considerations is my old 32 bit computor, so instead of playing around with this, I downloaded the 32bit libreoffice 5.2 and installed it the old fashion way

I remove libreoffice 5.3 and installed the deb files in the extracted folder using :> sudo dpkg -i *.deb

I have what I wanted.

One last thing: Howefield you are right: *sudo add update  *&#8203;is a typo.

Thanks everyone for your input.

---

### Post by kc1di on 2017-06-30
Glad you got it :)

---

