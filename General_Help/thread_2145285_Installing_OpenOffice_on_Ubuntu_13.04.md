---
title: "Installing OpenOffice on Ubuntu 13.04?"
date: 2013-05-15
forum: General Help
---

### Post by markw10 on 2013-05-15
I have the newest version of Ubuntu and I realize it comes with LibreOffice but I really like OpenOffice so I'd like to use that. I looked at the Software Center and did a search and am unable to find OpenOffice.  Is it possible to install OpenOffice on Ubuntu 13.04?  Thanks!

---

### Post by Deuce1912 on 2013-05-15
I googled "open office" and went to their website at [http://openoffice.org](http://openoffice.org)

If you click on "I want to download OpenOffice" it will take you to the download section.  

Here is the download link, all you need to do is click the green area to go to the download page.

You will have to manually install it by double clicking on it.

Hope this helps,

- Deuce1912

Edit:  My bad, I forgot the link - [http://www.openoffice.org/download/](http://www.openoffice.org/download/)

Also Claracc's PPA method will work even better as it will keep Open Office up to date as updates/bug fixes roll out.

---

### Post by claracc on 2013-05-15
> **markw10 said:**
> I have the newest version of Ubuntu and I realize it comes with LibreOffice but I really like OpenOffice so I'd like to use that. I looked at the Software Center and did a search and am unable to find OpenOffice.  Is it possible to install OpenOffice on Ubuntu 13.04?  Thanks!

You cannot have at same time libreoffice and apache openoffice in your system. So first of all you will have to remove libreoffice.

The easier method is to install apache openoffice through a ppa, I think.
Here, [http://www.upubuntu.com/2013/01/install-apache-openoffice-341-from-ppa.html](http://www.upubuntu.com/2013/01/install-apache-openoffice-341-from-ppa.html), you have a step by step guide to remove libreoffice and install openoffice from ppa.

---

### Post by Hagar Delest on 2013-11-11
You can run both LibO and AOO on a system but you need to install both with the .deb provided by their websites.
To install, see: [[Tutorial] Installing Apache OpenOffice on GNU/Linux]("https://forum.openoffice.org/en/forum/viewtopic.php?f=74&t=50119")

---

### Post by ping-wu on 2013-11-11
There is no ppa for 4.0.x version of Apache OpenOffice.  The commands to install are:

sudo apt-get purge libreoffice*

sudo dpkg -i en-US/DEBS/*.deb

sudo dpkg -i en-US/DEBS/desktop-integration/*.deb

Although it "appears" that LibreOffice can co-exist with Apache OpenOffice, at least for me (who run a law office), there is no need to keep both.

---

### Post by Hagar Delest on 2013-11-12
Of course, it's pointless. But it can help at the beginning to decide which one is the best depending on your needs.

---

### Post by Eugene King on 2013-12-17
This I will try. I used commands from a older post.........Yours looks like 1/3 the commands. 

While installing 4.0.1 on my USB drive I ran into a file conflict with libreoffice and had to completely remove it.

---

### Post by carloschizzo on 2013-12-17
Hi guys, I have a problem to install new version of openoffice (4.0.1).
I have openoffice 3.4.1 installed on my Ubuntu  I tried to remove it through the command 
sudo apt-get purge openoffice*.*

It seemed work but when I click on a .doc file I have already openoffice istalled

If I try to execute again the command sudo apt-get purge openoffice*.* the result is 
```
carlitos@ThinkPad-L420:~$ sudo apt-get purge openoffice*.*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'openoffice.org-hunspell' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-xh' for regex 'openoffice*.*'
Note, selecting 'openoffice.org2-thesaurus' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-en-us' for regex 'openoffice*.*'
Note, selecting 'libopenoffice-oodoc-perl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-zu' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-en-us' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-core' for regex 'openoffice*.*'
Note, selecting 'mozilla-openoffice.org' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-updatedicts' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-dmaths' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-ca' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-writer' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-cs' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-de' for regex 'openoffice*.*'
Note, selecting 'openoffice.org' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-de-ch' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-fr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-hu' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-en-au' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-it' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-fr-fr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-impress' for regex 'openoffice*.*'
Note, selecting 'openoffice-debian-menus' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-af' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-ne' for regex 'openoffice*.*'
Note, selecting 'libming-fonts-openoffice' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-de-at' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-ca' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-cs' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-da' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-de' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-pl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-de-ch' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-an' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-de-de' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-el' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-bundled' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-en' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-es' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-ca' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-ro' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-fi' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-ru' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-fr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-ga' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-sk' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-hr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-eo' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-hu' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-dtd-officedocument1.0' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-es' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-eu' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-id' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-fi' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-is' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-fo' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-it' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-gl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-lt' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-calc' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-nl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-pl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-pt' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-common' for regex 'openoffice*.*'
Note, selecting 'openofficeorg-desktop-integration' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-en-us' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-nb' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-nn' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-nr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-ns' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-ro' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-ru' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-sh' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-sk' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-sl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-sr' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-kde' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-sv' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-ui' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-uk' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-ss' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-st' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-dev-doc' for regex 'openoffice*.*'
Note, selecting 'kde-thumbnailer-openoffice' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-tl' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-tn' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-uz' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-ve' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-base' for regex 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-zu' for regex 'openoffice*.*'
Package 'openoffice.org-thesaurus-it' is not installed, so not removed
Note, selecting 'dictionaries-common' instead of 'openoffice.org-updatedicts'
Package 'openoffice.org-hunspell' is not installed, so not removed
Package 'openoffice.org-core' is not installed, so not removed
Note, selecting 'hunspell-an' instead of 'openoffice.org-spellcheck-an'
Package 'openoffice.org' is not installed, so not removed
Package 'openoffice.org-spellcheck-en-us' is not installed, so not removed
Note, selecting 'hunspell-eu-es' instead of 'openoffice.org-spellcheck-eu'
Note, selecting 'hunspell-gl-es' instead of 'openoffice.org-spellcheck-gl'
Note, selecting 'hunspell-uz' instead of 'openoffice.org-spellcheck-uz'
Package 'openoffice.org-writer' is not installed, so not removed
Note, selecting 'hyphen-af' instead of 'openoffice.org-hyphenation-af'
Note, selecting 'hyphen-ca' instead of 'openoffice.org-hyphenation-ca'
Note, selecting 'hyphen-de' instead of 'openoffice.org-hyphenation-de'
Note, selecting 'hyphen-en-us' instead of 'openoffice.org-hyphenation-en-us'
Package 'openoffice.org-hyphenation-hr' is not installed, so not removed
Note, selecting 'hyphen-hu' instead of 'openoffice.org-hyphenation-hu'
Note, selecting 'hyphen-it' instead of 'openoffice.org-hyphenation-it'
Note, selecting 'hyphen-pl' instead of 'openoffice.org-hyphenation-pl'
Note, selecting 'hyphen-ro' instead of 'openoffice.org-hyphenation-ro'
Note, selecting 'hyphen-ru' instead of 'openoffice.org-hyphenation-ru'
Note, selecting 'hyphen-sh' instead of 'openoffice.org-hyphenation-sh'
Note, selecting 'hyphen-sl' instead of 'openoffice.org-hyphenation-sl'
Note, selecting 'hyphen-sr' instead of 'openoffice.org-hyphenation-sr'
Package 'openoffice.org-hyphenation-zu' is not installed, so not removed
Note, selecting 'hyphen-zu' instead of 'openoffice.org-hyphenation-ui'
Package 'openoffice.org-base' is not installed, so not removed
Package 'openoffice.org-common' is not installed, so not removed
Package 'openoffice.org-dev-doc' is not installed, so not removed
Note, selecting 'myspell-ca' instead of 'openoffice.org-spellcheck-ca'
Note, selecting 'myspell-eo' instead of 'openoffice.org-spellcheck-eo'
Note, selecting 'myspell-es' instead of 'openoffice.org-spellcheck-es'
Note, selecting 'myspell-fo' instead of 'openoffice.org-spellcheck-fo'
Note, selecting 'myspell-nb' instead of 'openoffice.org-spellcheck-nb'
Note, selecting 'myspell-nn' instead of 'openoffice.org-spellcheck-nn'
Note, selecting 'myspell-nr' instead of 'openoffice.org-spellcheck-nr'
Note, selecting 'myspell-ns' instead of 'openoffice.org-spellcheck-ns'
Note, selecting 'myspell-ss' instead of 'openoffice.org-spellcheck-ss'
Note, selecting 'myspell-st' instead of 'openoffice.org-spellcheck-st'
Note, selecting 'myspell-tn' instead of 'openoffice.org-spellcheck-tn'
Note, selecting 'myspell-ve' instead of 'openoffice.org-spellcheck-ve'
Note, selecting 'myspell-xh' instead of 'openoffice.org-spellcheck-xh'
Note, selecting 'myspell-zu' instead of 'openoffice.org-spellcheck-zu'
Note, selecting 'mythes-ca' instead of 'openoffice.org-thesaurus-ca'
Note, selecting 'mythes-cs' instead of 'openoffice.org-thesaurus-cs'
Note, selecting 'mythes-de' instead of 'openoffice.org-thesaurus-de'
Note, selecting 'mythes-de-ch' instead of 'openoffice.org-thesaurus-de-ch'
Note, selecting 'mythes-en-au' instead of 'openoffice.org-thesaurus-en-au'
Note, selecting 'mythes-en-au' instead of 'openoffice.org2-thesaurus'
Note, selecting 'mythes-en-us' instead of 'openoffice.org-thesaurus-en-us'
Note, selecting 'mythes-fr' instead of 'openoffice.org-thesaurus-fr'
Note, selecting 'mythes-hu' instead of 'openoffice.org-thesaurus-hu'
Note, selecting 'mythes-ne' instead of 'openoffice.org-thesaurus-ne'
Note, selecting 'mythes-pl' instead of 'openoffice.org-thesaurus-pl'
Note, selecting 'mythes-ro' instead of 'openoffice.org-thesaurus-ro'
Note, selecting 'mythes-ru' instead of 'openoffice.org-thesaurus-ru'
Note, selecting 'mythes-sk' instead of 'openoffice.org-thesaurus-sk'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-cs'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-da'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-el'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-es'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-fi'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-ga'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-id'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-is'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-nl'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-pt'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-sk'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-sv'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-uk'
Package 'openoffice.org-calc' is not installed, so not removed
Package 'mozilla-openoffice.org' is not installed, so not removed
Package 'openoffice.org-kde' is not installed, so not removed
Note, selecting 'ming-fonts-opensymbol' instead of 'libming-fonts-openoffice'
Note, selecting 'myspell-fi' instead of 'openoffice.org-spellcheck-fi'
Note, selecting 'myspell-fr-gut' instead of 'openoffice.org-spellcheck-fr-fr'
Note, selecting 'myspell-tl' instead of 'openoffice.org-spellcheck-tl'
Package 'openoffice.org-dmaths' is not installed, so not removed
Package 'openoffice.org-impress' is not installed, so not removed
Package 'openoffice-debian-menus' is not installed, so not removed
Package 'openoffice.org-bundled' is not installed, so not removed
Package 'openofficeorg-desktop-integration' is not installed, so not removed
Package 'openoffice.org-hyphenation' is not installed, so not removed
Package 'kde-thumbnailer-openoffice' is not conpletelyinstalled, so not removed
Package 'libopenoffice-oodoc-perl' is not installed, so not removed
Package 'openoffice.org-hyphenation-lt' is not installed, so not removed
Package 'openoffice.org-dtd-officedocument1.0' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 222 not upgraded.
```

Could you help me to remove completely openoffice?
Thanks
Carlo

---

### Post by GraysonPeddie on 2013-12-17
I have provided steps to install OpenOffice:

[http://graysonpeddie.com/how-to-install-openoffice-4-in-ubuntu/](http://graysonpeddie.com/how-to-install-openoffice-4-in-ubuntu/)

---

### Post by carloschizzo on 2013-12-17
Hi [**[COLOR=#000000]GraysonPeddie[/COLOR]**]("http://ubuntuforums.org/member.php?u=609683"),
thanks for answered me,
I reed your post but I didn't find anything about to remove old version of openoffice.
More or less I did the same thing to remove libreoffice but I try to open a .doc file I have already openoffice.
Could you explain me how I could remove definitely openoffice 3.4.1?
Thanks a million
Carlo

---

### Post by GraysonPeddie on 2013-12-17
I don't know how you got OpenOffice 3.4.1 installed... Sometimes you may have to try to reinstall Ubuntu. It is pretty much the only solution that I can offer so I'm sorry I cannot be of help.

Maybe someone in here can help you.

---

### Post by jimmyh1972 on 2013-12-17
try it [http://askubuntu.com/questions/298781/how-can-i-install-openoffice](http://askubuntu.com/questions/298781/how-can-i-install-openoffice)
it works fine

---

### Post by philinux on 2013-12-17
> **GraysonPeddie said:**
> I don't know how you got OpenOffice 3.4.1 installed... Sometimes you may have to try to reinstall Ubuntu. It is pretty much the only solution that I can offer so I'm sorry I cannot be of help.

Maybe someone in here can help you.

I reinstall only as a last resort.  Purging an app should not require a reinstall.

---

### Post by deadflowr on 2013-12-17
> **carloschizzo said:**
> Hi guys, I have a problem to install new version of openoffice (4.0.1).
I have openoffice 3.4.1 installed on my Ubuntu  I tried to remove it through the command 
sudo apt-get purge openoffice*.*

It seemed work but when I click on a .doc file I have already openoffice istalled

If I try to execute again the command sudo apt-get purge openoffice*.* the result is 

Could you help me to remove completely openoffice?
Thanks
Carlo
Try running the purge command with simple openoffice*, instead of with the openoffice*.*
```
sudo apt-get purge openoffice*
```
or use dpkg.

---

### Post by Hagar Delest on 2013-12-17
Or install Synaptic and filter with openoffice and you'll see if there is any package left.

---

### Post by deadflowr on 2013-12-17
> **Hagar Delest said:**
> Or install Synaptic and filter with openoffice and you'll see if there is any package left.
+1
or install synaptic, regardless.
Nifty little program, there.

---

### Post by ping-wu on 2013-12-17
Yes, run Synaptic and run a search on openoffice.  Best way to remove a set of packages.

---

### Post by carloschizzo on 2013-12-18
Thanks Hagar,
I installed Synaptic and I removed the package left!!!

---

### Post by richardsdma on 2013-12-18
there is no need to remove old openoffice. just install the new one and it will upgrade by itself.

---

