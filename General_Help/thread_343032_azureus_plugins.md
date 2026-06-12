---
title: "azureus plugins"
date: 2007-01-20
forum: General Help
---

### Post by shickidyshade on 2007-01-20
Hey guys im trying to install Safepeer for azureus and i downloaded the file from the plugins in the menu 

but it didn't install into the plugins folder how do i create a folder and move them in there its located in opt/azureus/plugins 
](*,) 
also azureus wants to update and installed the .jar but everytime it keeps asking me to install it 

Help plz

Thanks alot

---

### Post by TrinitronX on 2007-01-21
I just installed this by putting the 3 files it lists in the readme into ~/.azureus/plugins/safepeer/.

Here's a mini script to do it for you.
It first makes the safepeer directory in ~/.azureus/plugins/
Then it gets the zip file for safepeer (this script puts it in /tmp to keep your home clean), unzips the needed files to the safepeer plugin directory, and cleans up the leftover zip file.

Just copy/paste it into a new text file with your favorite text editor, and name it something like: safepeer.sh
Then, make it executeable with: chmod +x safepeer.sh, and run ./safepeer.sh
(this is assuming you're working in the same directory that you made the file in, adjust file paths if not.
```

#!/bin/bash
mkdir ~/.azureus/plugins/safepeer
cd /tmp
wget http://azureus.sourceforge.net/plugins/safepeer_2.5.1.zip
unzip safepeer_2.5.1.zip -x License.txt Readme.txt history.txt plugin.properties azureus.sig -d ~/.azureus/plugins/safepeer
rm safepeer_2.5.1.zip

```

---

### Post by shickidyshade on 2007-01-21
so two questions what is the ~ for why is it not opt and two why is there a .azureus mine is opt/azureus/plugins

---

### Post by shickidyshade on 2007-01-21
also shouldnt there be a sudo since it wont just let me create and copy a new folder in that directory

---

### Post by shickidyshade on 2007-01-21
Hey guys does anybody know how to do this i know it can;'t be that hard


Thanks

---

### Post by TrinitronX on 2007-01-22
~ stands for your home directory, so if your username was: someuser,
then it'd stand for /home/someuser.  It's also equivalent to the $HOME shell variable.
I made the script so it would only install the plugin for your user, but if you want to install it for all users, then yes you should put the files into /opt/azureus/plugins/safepeer instead, and then it would need sudo.  The ".azureus" directory is a hidden directory in your home directory, if you were to do a: "ls -A" in your homedir, you'd see loads of them which are used for settings and config files for many programs.  Any file beginning with a "." in linux is a hidden file.
As far as I know, the /tmp directory can be written to by anything really, since it's usually used for temporary files by programs.  Also, since the ~ stands for your homedir, then you should have permissions to make a directory there and write to it, so it doesn't need sudo.

---

### Post by Tim T on 2007-01-30
just used the script and all worked perfectly. I love the vast amount of knowledge on this site! in 3 short days, i'm already figuring out more than i ever did with mandriva. and the terminal is starting to get a lot less scary. thx!

---

### Post by bred on 2008-02-24
Hello,
I'm new user on Linux, so sorry for too many questions guys :)
well I'm trying to update my safepeer on asureus p2p programme, but smth its not working- I guess? :)
I ve made the script as TrinitronX sugested...
instead of ~ I put my user name (hmr) - here we are:

#!/bin/bash
mkdir /home/hmr/.azureus/plugins/safepeer
cd /tmp
wget [http://azureus.sourceforge.net/plugins/safepeer_2.5.1.zip](http://azureus.sourceforge.net/plugins/safepeer_2.5.1.zip)
unzip safepeer_2.5.1.zip -x License.txt Readme.txt history.txt plugin.properties azureus.sig -d ~/.azureus/plugins/safepeer
rm safepeer_2.5.1.zip

I saved that in Text Editor naming **safepeer.sh** Then this file(safepeer.sh) I moved with Ctrl+X in hmr/.azureus/plugins/safepeer folder

Than when I tryed to make it executable with: **chmod +x safepeer.sh, and run ./safepeer.sh**

AND the result here in the Terminal :
[B]hmr@hmr-laptop:~$ chmod +x safepeer.sh
chmod: cannot access `safepeer.sh': No such file or directory
hmr@hmr-laptop:~$ [/B]

What can I do else, or any suggestions pls?
Thx in advance. :guitar:


> **TrinitronX said:**
> I just installed this by putting the 3 files it lists in the readme into ~/.azureus/plugins/safepeer/.

Here's a mini script to do it for you.
It first makes the safepeer directory in ~/.azureus/plugins/
Then it gets the zip file for safepeer (this script puts it in /tmp to keep your home clean), unzips the needed files to the safepeer plugin directory, and cleans up the leftover zip file.

Just copy/paste it into a new text file with your favorite text editor, and name it something like: safepeer.sh
Then, make it executeable with: chmod +x safepeer.sh, and run ./safepeer.sh
(this is assuming you're working in the same directory that you made the file in, adjust file paths if not.
```

#!/bin/bash
mkdir ~/.azureus/plugins/safepeer
cd /tmp
wget http://azureus.sourceforge.net/plugins/safepeer_2.5.1.zip
unzip safepeer_2.5.1.zip -x License.txt Readme.txt history.txt plugin.properties azureus.sig -d ~/.azureus/plugins/safepeer
rm safepeer_2.5.1.zip

```

---

