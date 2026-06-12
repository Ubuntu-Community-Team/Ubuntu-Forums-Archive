---
title: "Installing a HP P1005 laserjet printer"
date: 2012-12-10
forum: General Help
---

### Post by rapattack1 on 2012-12-10
Hi ubuntu popped up that it was installing the driver for the printer but there error is as in the attached image.
Then i went to the HP site and downloaded the installer but i got this at the end of the command line stuff:
DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --assume-yes libcups2-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #1...
Running 'sudo apt-get install --assume-yes libcups2-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #2...
Running 'sudo apt-get install --assume-yes libcups2-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #3...
Running 'sudo apt-get install --assume-yes libcups2-dev'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y
Running 'sudo apt-get install --assume-yes libcups2-dev'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? 

This is the page i was using :
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

There are things i didn't understand so i just kept going but maybe its a simple process. Maybe a permission issue? Maybe repositories? I am just not that experienced in either i am afraid so would appreciate the help thanks :0)

---

### Post by Ms. Daisy on 2012-12-11
For my HP printer, I had the best luck going to the HP website and finding the linux driver for my particular model.  I recommend installing the driver first.

If you also want to install HPlip, you can do so from the software center after you installed the driver.

---

### Post by rapattack1 on 2012-12-12
Ok no matter the laserjet this is the page i download from [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)
then i went thru the steps on the page and when it got to step 6 to enable universe/multiverse i looked in synaptic. It showed that 'community maintained open-source software (universe)' is checked plus also 'software restricted by copyright or legal issues (multiverse) is also checked. Is that what they were talking about?
so i end up with the same stuff as i posted. So i am not getting anywhere

---

### Post by Mark Phelps on 2012-12-12
I have a couple of different HP printers, although not a Laserjet, and I installed them both through CUPS and Gutenprint  The latter, I believe, is not installed by default -- so add it from the Software Center or (better yet) install Synaptic and add it from there.

When you start CUPS (using a Browser pointed at localhost:631), you will see menus, one of which will allow you to add a printer.

CUPS should find your printer and you add the driver by selecting it from a list of drivers in CUPS.

---

### Post by Frogs Hair on 2012-12-12
The HP site points to a page for downloading HPLIP which is in the Ubuntu repository if not already installed. Other links suggest that the pinter is or was supported in Linux.  [http://hplipopensource.com/hplip-web/index.html?](http://hplipopensource.com/hplip-web/index.html?)

---

### Post by rapattack1 on 2012-12-12
OK cups was installed and seemed to have installed the printer thanks. Just don't seem to be able to print a test page from it :0(

---

### Post by Ms. Daisy on 2012-12-12
Do you have a firewall enabled?

---

### Post by rapattack1 on 2012-12-13
No idea. I can't remember if i interacted with one on this distro or not.

---

### Post by rapattack1 on 2013-01-04
Well this one is solved. I was using Ubuntu 10 and now upgraded to 12.04. The Hp thing popped up straight away when i plugged the printer in, downloaded what it needed and i printed a test page :0) Happy that the upgrade solved that and a few other minor issues i was having :0)

---

