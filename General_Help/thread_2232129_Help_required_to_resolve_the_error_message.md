---
title: "Help required to resolve the error message"
date: 2014-06-30
forum: General Help
---

### Post by vkadal on 2014-06-30
I received the following error message in Ubuntu 14.04. Kindly guide me to resolve this issue. The following is the error message

Data files for somepackages could not be downloaded 


The followingpackages requested additional data downloads after packageinstallation, but the data could not be downloaded or could not beprocessed. 


ttf-mscorefonts-installer


This is a permanentfailure that leaves these packages unusable on your system.  You mayneed to fix your Internet connection, then remove and reinstall thepackages to fix this problem.

---

### Post by plucky on 2014-06-30
> **vkadal said:**
> I received the following error message in Ubuntu 14.04. Kindly guide me to resolve this issue. The following is the error message

Data files for somepackages could not be downloaded 


The followingpackages requested additional data downloads after packageinstallation, but the data could not be downloaded or could not beprocessed. 


ttf-mscorefonts-installer


This is a permanentfailure that leaves these packages unusable on your system.  You mayneed to fix your Internet connection, then remove and reinstall thepackages to fix this problem.

What does ```
sudo apt-get install -f
``` in a terminal window do for you?

Please post the whole output if any errors.

Good Luck

---

### Post by 3rdalbum on 2014-06-30
You need an internet connection open and then run this command:

sudo apt-get install --reinstall ttf-mscorefonts-installer

---

### Post by varunendra on 2014-06-30
> **3rdalbum said:**
> You need an internet connection open and then run this command:

sudo apt-get install --reinstall ttf-mscorefonts-installer

..and After running the above command, you need to have some patience (or a LOT of patience if the connection is slow) because the installer does not show any progress bar or other indication that the font download/installation is in progress. The terminal appears to be hung at a particular stage until the installation is finished (or begun? Don't remember correctly). Just wait and let it finish its job. If you have not already "Agreed" to MS-EULA (Licence agreement), you'll also be prompted for that and the process will go forward only after you answer (in 'Yes') to the prompt.

The process is simple, just a bit confusing due to the download activity being 'hidden'.

---

### Post by vkadal on 2014-06-30
Thanks Varun. It is showing the licence agreement. I am unable to accept it. How to say "Yes" / ok to the agreement? There is no button to click and no window to type

---

### Post by buzzingrobot on 2014-06-30
> **vkadal said:**
> Thanks Varun. It is showing the licence agreement. I am unable to accept it. How to say "Yes" / ok to the agreement? There is no button to click and no window to type

You'll need to use the Tab key to move the cursor there.  Just tap Tab and the cursor will move between the alternatives. Press Enter when the correct selection is highlighed,  There are two screens you need to deal with. 

Then, the installation of the fonts will continue.  As mentioned, it can be slow:  Each font package is downloaded individually from an non-Ubuntu server.

---

### Post by vkadal on 2014-06-30
Thanks buzzingrobot. After tab and accepting licence agreement, the installation has completed within few minutes. This issue is resolved

---

