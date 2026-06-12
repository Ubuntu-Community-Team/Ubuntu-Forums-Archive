---
title: "running programs"
date: 2008-01-30
forum: General Help
---

### Post by steve984 on 2008-01-30
Hi I am new to linux and was wondering how do you install programs I get from the web.  I downloaded them ( like dvr 3.9 and firefox 3.0 beta) and I get the files but they don't have an exacutable or an install option or file.  Do I need to compile them and how exactly do I do that I searched the forums and I can't seem to find an answer thanks steve

---

### Post by p_quarles on 2008-01-30
Firefox 3 should be an executable, if it's the one from Mozilla's site. To run it, you'll need to specify the full path to the file, since it's not in any of your standard executable directories. So, let's say it was in a folder called "Downloads." To run it from the terminal, you would type something like this:
```
/home/*username*/Downloads/firefox-*rest-of-filename*
```

---

### Post by aoakley on 2008-01-30
Installing programs that are not in official repositories is risky and may damage your system. Ensure that you have backups of any valuable files and that your backups actually work.

Ideally, you should install programs through the Applications menu - Add Remove Programs. This ensures the programs you install are supported in Ubuntu. You can also do this with System - Administration - Synaptic Package Manager.

If you want something that isn't in an official repository, try to find a third-party repository (look it up with your favourite search engine). Once you've found a repository (which will look like a website address [http://something/something](http://something/something) ), do System - Administration - Synaptic Package Manager - Settings - Repositories - Third Party Software - Add . Then update Synaptic using the Update button, and install your program from there.

If you want something that isn't in any suitable repository, and you must download a program straight from the web, and you are confident about accepting the possible consequences, it will typically be installed one of three different ways; .deb , .bin and .tar.gz .

Firstly start a command line (Accessories - Terminal) and change directory to the folder where you've downloaded the file.

For .deb files, do:

# sudo dpkg -i filename.deb

For .bin files, just run it directly:

# ./filename.bin

For .tar.gz files that contain source code, do:

# tar xvzf filename.tar.gz
# cd filename
# ./configure
# make
# make install

Compiling from source may require you to install other stuff you don't already have. These can usually be installed from Synaptic Package Manager, but sometimes you may need to install that separately too. It can all go a bit circular, which is why it is better to stick with stuff in official repositories.

If you screw up your system, don't complain to me. I told you right at the start it was risky. I told you to stick to the official repositories. I told you to make backups and check that the backups actually work. Having said all that, I congratulate you for being keen to LEARN! If you never try anything new, you will never learn anything.

---

### Post by p_quarles on 2008-01-30
There's nothing risky about running the Firefox 3 Beta binary as long as you downloaded it from Mozilla. The worst it could do is temporarily disable some Firefox settings that are no longer supported in 3.

---

### Post by steve984 on 2008-01-30
I downloaded firefox 3 from the web site extracted it then clicked the .bin file and nothing happens do I need to run it through the command line.  also when I go to terminal program it shows steve@steve-desktop:~$ 
Where is that in relation to my desktop when I try to exacute a command it say file not found and I download and extract everything to my desktop.  I run the dir command and it doesn't show any of my files thanks steve

---

### Post by p_quarles on 2008-01-30
What's the precise name of the .bin file?

---

### Post by steve984 on 2008-01-30
its firefox.bin i extracted it to my desktop I tried moving around in terminal (cd desktop) and it says no file found. thanks steve

---

### Post by p_quarles on 2008-01-30
This should do it:
```
~/Desktop/firefox.bin
```
Try that first. If it doesn't work, run this:
```
chmod u+x ~/Desktop/firefox.bin
```
Then try step one again.

If it still doesn't work, post the error messages you got.

---

### Post by steve984 on 2008-01-30
thanks I tried that and it keeps saying "no such file or directory'

---

### Post by p_quarles on 2008-01-30
Hmm. Can you post the results of this command?:
```
ls -a Desktop
```

---

### Post by steve984 on 2008-01-30
steve@steve-desktop:~$ ls -a desktop
ls: desktop: No such file or directory
steve@steve-desktop:~$ ls ~a desktop
ls: ~a: No such file or directory
ls: desktop: No such file or directory
steve@steve-desktop:


is there a guide for ubuntu coammnds i can download and thanks again for the help

---

### Post by p_quarles on 2008-01-30
Linux is case sensitive. Type the command exactly as I gave it, with a capital D.

---

### Post by steve984 on 2008-01-30
ok now I got 
499_Gman_wall39_GracePark4.jpg  dvr-3.99.3.tar.bz2  firefox-3.0b2.tar.bz2
..  dvr-3.99.3                      firefox

---

### Post by p_quarles on 2008-01-30
Okay, run this:
```
cd Desktop/firefox
```
Then:
```
./firefox.bin
```

---

### Post by steve984 on 2008-01-30
I tried the .bin command and I got no such file I then tried firefox-bin and I got 
steve@steve-desktop:~/Desktop/firefox$ ./firefox-bin
./firefox-bin: error while loading shared libraries: libxul.so: cannot open shared object file: No such file or directory
steve@steve-desktop:~/Desktop/firefox$

---

### Post by p_quarles on 2008-01-30
Not sure what to tell you about that. I'm assuming you already have Firefox 2 installed, correct? It's looking for an object that it can't find, and I had been under the impression that the uncompressed archive would contain everything needed to run it.

---

### Post by steve984 on 2008-01-30
me too but thanks I guess i will wait for the regular program the synaptic has the alpha I downloaded and I could not get it to work but thanks again for all the help I learned alot steve

---

### Post by p_quarles on 2008-01-30
The other option here is to install Swiftweasel, which is a recompiled version of the Firefox source code designed specifically for Ubuntu and Debian. This is what I use:
[http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=231607](http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=231607)

I didn't suggest it at first because it can be a bit complicated to choose the correct build. If you want to tell me what type of processor you're running, though, I can tell you which one would work best.

---

### Post by steve984 on 2008-01-30
I have an amd xp200 with 768mb of ram stve

---

### Post by p_quarles on 2008-01-30
Okay. If you installed the 64-bit version of Ubuntu, then you'll need the first one in the list I linked to. If you installed the 32-bit version, the second one on the list. 

Assuming you download it to the desktop, you can install it like so:
```
cd Desktop
```
Then:
```
sudo dpkg -i swiftweasel-3.02b_[i]rest-of-file-name[i].deb
```
In case it doesn't automatically get added to your menu, the command to run it is:
```
swtrunk
```
Hope you have better luck with this one.

---

### Post by PmDematagoda on 2008-01-30
From what I have seen, you need a newer version of the xulrunner to run or install Firefox 3, what Ubuntu release are you using?

---

### Post by steve984 on 2008-01-30
hey I checked the site and downloaded the xp version(I'm using it now) wow this much faster . I have an 32 bit processor.  thanks for the link I might try the beta 3 now.  this is as fast as ie thats what I was looking for firefox 2 runs slower and all the plugin are working too this is great thanks again steve

---

