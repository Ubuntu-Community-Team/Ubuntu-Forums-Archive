---
title: "[SOLVED] what avasys driver is needed for epson v100 and ubuntu"
date: 2008-07-03
forum: General Help
---

### Post by tunznath on 2008-07-03
Hi
I have been to the avasys site to get a driver for my epson v100 - it doesnt have a very clear way of figuring out which driver to use for ubuntu - has anyone installed a driver from avasys that can tell me what I need to get.

thanks

---

### Post by tunznath on 2008-07-08
Still no answers - bump

---

### Post by rbmorse on 2008-07-08
From the Ubuntu repositories, use synaptic to install or verify that the following are installed:

		sane 
		libsane 
		sane-utils 
		xsane 
		xsane-common    
		alien
		libstdc5++
		build-essential

Then, in your web browser, go here:

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

Scroll down to the section titled "form for download" 

Check the button for "V100 Photo"
selecet "debian" in the next pull down
select "other" in the next pull down
answer the three questions about how you will use the download and click "next" to go to the download page. 

Download the both the iscan and the driver .rpm files to your desktop. **The iscan package must be installed even if you plan to use another scanning application**. 

Close/minimize the browser window and open a terminal window

cd Desktop

```
sudo alien --to-deb --scripts iscan_*your version*.i386.rpm
sudo alien --to-deb --scripts iscan-plugin-*your version*.i386.rpm
```

Alien will create two .deb packages from the ,rpm files. Use dpkg to install them. In a terminal window:

```
sudo dpkg -i iscan-plugin-*your version*.deb
sudo dpkg -i iscan_*your version*.deb
```

Close/minimize the terminal window and open the user manager (system > administration > users and groups)

Add your user ID to the group "scanner"

reboot.

---

### Post by tunznath on 2008-07-10
rbmorse Many Many thanks - did it and it worked out great - Your simple steps helped - even though i couldnt find libstdc5++ - scanner works and now i am 1 step closer to losing windows.
OK now I need to know how to give you a thanks and make this post solved

once again thanks
Nathan

---

### Post by rbmorse on 2008-07-20
Great!

I made typo.  The file you could not find is libstdc5+ +  (+ space +), but if the scanner is working, maybe it isn't needed after all.

---

### Post by oygle on 2008-09-15
> **rbmorse said:**
> From the Ubuntu repositories, use synaptic to install or verify that the following are installed:

		sane 
		libsane 
		sane-utils 
		xsane 
		xsane-common    
		alien
		libstdc5++
		build-essential


I'm trying to get the same scanner going. I do have xsane installed, and in regards to the other packages listed above, I can't find them under the 'add/remove'. Does that indicate they are not supported by the Ubuntu community.

How 'safe' are these other packages ?

**edit:** Found a thread on another scanner, and a suggestion to check permissions for the username, I checked and my username wasn't allowed to use a scanner, so that is now fixed.

Also, for some reason, I never could find 'sane' under the 'add/remove' side of things, even though it is in universe repository, and I had universe checked under synaptic. Anyway, went into Synaptic and installed sane from there.

I will install those other packages, and then log off/on, so my username picks up as being allowed to use a scanner.

---

### Post by oygle on 2008-09-15
rbmorse: Thanks very much for those instructions, I can now scan okay with the Epson V100. I'd add a 'thanks' but it seems disabled.

The (image) file is saved with a .PNM extension, I don't know what that is, but no doubt I can easily create it to JPG or other. Must admit I have a lot to learn about apps and packages, and now realise why 'sane' wasn't appearing in the apps, simply because it isn't one I guess.

The only packages I didn't install were:

libstdc5++
build-essential

and it all seemed to work okay. Thanks very much.  :)

---

### Post by oygle on 2009-04-20
The latest version now has the DEB package, so no need for the 'alien' part.

---

### Post by oygle on 2009-04-20
Downloaded the DEB for Ubuntu 8.10 and got this message when trying to install

> 
$ sudo dpkg -i iscan_2.19.0-4_i386.deb
(Reading database ... 201213 files and directories currently installed.)
Unpacking iscan (from iscan_2.19.0-4_i386.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 29: Bad substitution
dpkg: error processing iscan_2.19.0-4_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
Processing triggers for menu ...
Errors were encountered while processing:
 iscan_2.19.0-4_i386.deb


---

### Post by oygle on 2009-04-20
The earlier version of the DEB was okay, the thread at [http://ubuntuforums.org/showthread.php?t=1000341&page=2](http://ubuntuforums.org/showthread.php?t=1000341&page=2) solved the problem

---

