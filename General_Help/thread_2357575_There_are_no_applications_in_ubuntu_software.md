---
title: "There are no applications in ubuntu software"
date: 2017-04-03
forum: General Help
---

### Post by juvinao on 2017-04-03
Today I go to "Software Of Ubuntu" and don't see the apps, either I see the app I have installed and appear the message "No application data found".


Help me please

---

### Post by Autodave on 2017-04-03
Have you updated recently? Try it manually:  in a terminal, type:  *sudo apt-get update* and hit ENTER. Input your password. When that is done, type:  *sudo apt-get upgrade  *and again the ENTER key. Let that finish and exit the terminal. Now try the software center again.

---

### Post by juvinao on 2017-04-03
> **Autodave said:**
> Have you updated recently? Try it manually:  in a terminal, type:  *sudo apt-get update* and hit ENTER. Input your password. When that is done, type:  *sudo apt-get upgrade  *and again the ENTER key. Let that finish and exit the terminal. Now try the software center again.

I already did what it suggests but the error persists

---

### Post by RobGoss on 2017-04-03
> **juvinao said:**
> I already did what it suggests but the error persists

What error are you getting when you run those commands?

Run the commands again that was advised and post the error message you received using the code tags..

---

### Post by juvinao on 2017-04-03
> **RobGoss said:**
> What error are you getting when you run those commands?

Run the commands again that was advised and post the error message you received using the code tags..

When I run  sudo apt-get update the appear next:

Des:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Obj:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Obj:4 [http://ppa.launchpad.net/geary-team/releases/ubuntu](http://ppa.launchpad.net/geary-team/releases/ubuntu) xenial InRelease     
Obj:6 [http://co.archive.ubuntu.com/ubuntu](http://co.archive.ubuntu.com/ubuntu) xenial InRelease                     
Obj:7 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease                              
Obj:8 [http://ppa.launchpad.net/linrunner/tlp/ubuntu](http://ppa.launchpad.net/linrunner/tlp/ubuntu) xenial InRelease           
Obj:9 [http://co.archive.ubuntu.com/ubuntu](http://co.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Obj:10 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) xenial InRelease   
Obj:11 [http://co.archive.ubuntu.com/ubuntu](http://co.archive.ubuntu.com/ubuntu) xenial-backports InRelease          
Obj:12 [http://ppa.launchpad.net/noobslab/icons2/ubuntu](http://ppa.launchpad.net/noobslab/icons2/ubuntu) xenial InRelease        
Obj:13 [http://ppa.launchpad.net/noobslab/macbuntu/ubuntu](http://ppa.launchpad.net/noobslab/macbuntu/ubuntu) xenial InRelease
Obj:14 [http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu](http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu) xenial InRelease
Obj:15 [http://ppa.launchpad.net/snwh/pulp/ubuntu](http://ppa.launchpad.net/snwh/pulp/ubuntu) xenial InRelease
Obj:16 [http://ppa.launchpad.net/tista/adapta/ubuntu](http://ppa.launchpad.net/tista/adapta/ubuntu) xenial InRelease
Reading package list ... Done



When I run sudo apt-get upgrade appear the next:




Reading package list ... Done
Creating dependency tree
Reading the status information ... Done
Calculating the update ... Done
0 upgraded, 0 new upgraded, 0 removed and 0 not upgraded.

---

### Post by juvinao on 2017-04-03
Solved problem

---

### Post by QIII on 2017-04-03
Hello!

Would you please share your solution so that others who have the same problem might be helped?

Thanks!

---

