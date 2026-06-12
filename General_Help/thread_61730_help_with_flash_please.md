---
title: "help with flash please"
date: 2005-09-01
forum: General Help
---

### Post by Scottcollins89 on 2005-09-01
Can some one tell me how to install flash, im like really new to this.  :???:

---

### Post by plb on 2005-09-01
[QUOTE=][/QUOTE]
 sudo apt-get install flashplayer-mozilla

---

### Post by Scottcollins89 on 2005-09-03
i get a error that says this. 

root@ubuntu:/home/scott #  sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla

???

---

### Post by plb on 2005-09-03
Hrm I'm not sure I don't use ubuntu much on debian its called flashplugin-nonfree

here ya go, enable multiverse and apt-get install flashplugin-nonfree

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=flashplug&searchon=names&subword=1&version=hoary&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=flashplug&searchon=names&subword=1&version=hoary&release=all)

---

### Post by Scottcollins89 on 2005-09-03
well i got flash working but i dont have any sound for it now?? anyone might know what the problem is? ](*,)

---

### Post by plb on 2005-09-03
I believe flash looks for esd first then oss, you can also try using the installer from the flash website you may have better luck

---

### Post by cedarbarn on 2005-09-03
[QUOTE=Scottcollins89]well i got flash working but i dont have any sound for it now?? anyone might know what the problem is? ](*,)[/QUOTE]

Hi, another noob, first day using Linux!  I had the same problem when I installed Flash today, no sound.  This is what I did...

under system dropdown, chose preferences, chose sound, and unchecked "enable sound server startup"

Now I have sound with Flash.

I found the instructions for this somewhere on this forum.  Thanks to whomever originally posted them!!

---

