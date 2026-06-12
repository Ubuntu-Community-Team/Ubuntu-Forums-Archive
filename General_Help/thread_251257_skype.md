---
title: "skype"
date: 2006-09-05
forum: General Help
---

### Post by emmaclose on 2006-09-05
i'm having problems downloading skype - tried to download it from the website - all went fine but the archive manager couldn't open it - something about it not being supported. any help would be great!

em

---

### Post by arkangel on 2006-09-05
which version are you downloading ?  .deb .rpm .tgz

---

### Post by emmaclose on 2006-09-05
i downloaded .deb - this was the version that it said to download for ubuntu

---

### Post by arkangel on 2006-09-05
download  the deb 

open a terminal and go to the directory it is located and type 

sudo dpkg -i skype_1.2.0.18-2_i386.deb

assuming  that it the version you have downloaded

---

### Post by emmaclose on 2006-09-05
the reply from this is

dpkg: error processing skype_1.2.0.18-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype_1.2.0.18-2_i386.deb

---

### Post by arkangel on 2006-09-06
hi  the file is not in that location , you must be sure  that the file is in the directory you are running the commnad dpkg

if you have downloaded the file  in Desktop folder (this is an example )
type in a terminal 
        cd ~/Desktop
then type
        sudo dpkg  -i sky
and press tab  for the autocompleting , this way you will be sure that the fiel is the correct one , there must be no space  when tyiping the last option your terminal should look like this 
      myuser@ubuntu> sudo dpkg -i sky|   [and press tab]


Note:  this symbol "~"  it is an alias and it is equivalent to your home directory .

---

### Post by macewan on 2006-09-08
wget [http://download.skype.com/linux/skype-beta-1.3.0.37-1_i386.deb](http://download.skype.com/linux/skype-beta-1.3.0.37-1_i386.deb)

***now let's see that it is there***

*** ls (lower case LS) is the command to use to list the contents of the directory you are currently in. ***

macewan@westinghouse:~$ **ls sk*.deb**
**skype-beta-1.3.0.37-1_i386.deb**

ah, there we see the skype file so let's install it now.

macewan@westinghouse:~$ **sudo dpkg -i sky*.deb**
Selecting previously deselected package skype.
(Reading database ... 81675 files and directories currently installed.)
Unpacking skype (from skype-beta-1.3.0.37-1_i386.deb) ...
Setting up skype (1.3.0.37-1) ...
macewan@westinghouse:~$ **skype**


it will start in a few seconds

:cool:

---

