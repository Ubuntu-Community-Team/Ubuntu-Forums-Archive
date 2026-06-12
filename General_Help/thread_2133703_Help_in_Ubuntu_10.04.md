---
title: "Help in Ubuntu 10.04"
date: 2013-04-08
forum: General Help
---

### Post by PlasticoBolha on 2013-04-08
Hi all.
First of all, I'm new in Linux so give me a slack :)

I know that I'm not using the latest version of ubuntu but I'm using Backtrack. The base is Ubuntu 10.04 (Lucid).

Now the problem. I'm trying to install WxPython (python is allready installed). When I try to install that or other GUI program it appears one error.

The following packages have unmet dependencies:
gtk2-engines-pixbuf: Depends: libgtk2.0-0 (= 2.20.1-0ubuntu2.1) but 2.20.0-0ubuntu4 is to be installed (...)

I've tried many things but all those failed solutions got in common "(= 2.20.1-0ubuntu2.1) but 2.20.0-0ubuntu4 is to be installed". So the problem is that. 

Can someone please guide me to the solution? Have I installed a newer version of something and I need to downgrade?

Again, I'm new so thanks in advance for all the help.

Cheers

---

### Post by PlasticoBolha on 2013-04-08
update:
I was trying to install an Alarm Clock program and it appears the same:

The following packages have unmet dependencies:
  gtk2-engines-pixbuf: Depends: libgtk2.0-0 (= 2.20.1-0ubuntu2.1) but 2.20.0-0ubuntu4 is to be installed
  libgail18: Depends: libgtk2.0-0 (= 2.20.1-0ubuntu2.1) but 2.20.0-0ubuntu4 is to be installed
  libgtk2.0-bin: Depends: libgtk2.0-0 (>= 2.20.1-0ubuntu2.1) but 2.20.0-0ubuntu4 is to be installed
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.20.1-0ubuntu2.1) but 2.20.0-0ubuntu4 is to be installed

So it's obvious that I screwed ubuntu up. Please help me reversing the situation...

---

### Post by mörgæs on 2013-04-08
Like all questions regarding 10.04 or similar almost-obsolete versions: Fresh install of a new one, in this case Backtrack 5 R3.

---

### Post by PlasticoBolha on 2013-04-08
> **mörgæs said:**
> Like all questions regarding 10.04 or similar almost-obsolete versions: Fresh install of a new one, in this case Backtrack 5 R3.

It is Backtrack 5 R3 (Gnome)...

---

### Post by mörgæs on 2013-04-08
Ok, so let's see... Please post the output from ```
sudo apt-get update
``` in CODE tags.

---

### Post by PlasticoBolha on 2013-04-09
> **mörgæs said:**
> Ok, so let's see... Please post the output from ```
sudo apt-get update
``` in CODE tags.


```


Hit http://ubuntu.mirror.cambrium.nl lucid Release.gpg
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ lucid/main Translation-en_US      
Ign http://ubuntu.mirror.cambrium.nl/ubuntu/ lucid/universe Translation-en_US  
Hit http://apt.wxwidgets.org lucid-wx Release.gpg                              
Ign http://apt.wxwidgets.org/ lucid-wx/main Translation-en_US                  
Hit http://ubuntu.mirror.cambrium.nl lucid Release                             
Hit http://apt.wxwidgets.org lucid-wx Release                                  
Hit http://ubuntu.mirror.cambrium.nl lucid/main Packages                       
Hit http://apt.wxwidgets.org lucid-wx/main Packages                            
Hit http://ubuntu.mirror.cambrium.nl lucid/universe Packages                   
Hit http://apt.wxwidgets.org lucid-wx/main Sources                             
Hit http://all.repository.backtrack-linux.org revolution Release.gpg           
Ign http://all.repository.backtrack-linux.org/ revolution/main Translation-en_US
Ign http://all.repository.backtrack-linux.org/ revolution/microverse Translation-en_US
Hit http://source.repository.backtrack-linux.org revolution Release.gpg
Ign http://source.repository.backtrack-linux.org/ revolution/main Translation-en_US
Ign http://source.repository.backtrack-linux.org/ revolution/microverse Translation-en_US
Hit http://32.repository.backtrack-linux.org revolution Release.gpg
Ign http://32.repository.backtrack-linux.org/ revolution/main Translation-en_US
Ign http://32.repository.backtrack-linux.org/ revolution/microverse Translation-en_US
Ign http://all.repository.backtrack-linux.org/ revolution/non-free Translation-en_US
Ign http://all.repository.backtrack-linux.org/ revolution/testing Translation-en_US
Hit http://all.repository.backtrack-linux.org revolution Release     
Ign http://source.repository.backtrack-linux.org/ revolution/non-free Translation-en_US
Ign http://source.repository.backtrack-linux.org/ revolution/testing Translation-en_US
Hit http://source.repository.backtrack-linux.org revolution Release  
Ign http://32.repository.backtrack-linux.org/ revolution/non-free Translation-en_US
Ign http://32.repository.backtrack-linux.org/ revolution/testing Translation-en_US
Hit http://32.repository.backtrack-linux.org revolution Release
Hit http://all.repository.backtrack-linux.org revolution/main Packages
Hit http://source.repository.backtrack-linux.org revolution/main Packages
Hit http://32.repository.backtrack-linux.org revolution/main Packages
Hit http://all.repository.backtrack-linux.org revolution/microverse Packages
Hit http://all.repository.backtrack-linux.org revolution/non-free Packages
Hit http://all.repository.backtrack-linux.org revolution/testing Packages
Hit http://source.repository.backtrack-linux.org revolution/microverse Packages
Hit http://source.repository.backtrack-linux.org revolution/non-free Packages
Hit http://source.repository.backtrack-linux.org revolution/testing Packages
Hit http://32.repository.backtrack-linux.org revolution/microverse Packages
Hit http://32.repository.backtrack-linux.org revolution/non-free Packages
Hit http://32.repository.backtrack-linux.org revolution/testing Packages
Reading package lists... Done



```

---

### Post by ppjdee on 2013-04-09
Edit: wrong info

---

### Post by Cheesemill on 2013-04-09
For some reason you have added the Ubuntu 10.04 repository’s to your BackTrack installation.
This is a sure fire way to break your system which is why the BackTrack developers advise you not to do it.

[http://www.backtrack-linux.org/wiki/index.php/FAQ#Why_cant_I_just_add_the_Backtrack_repositories_to_my_Ubuntu_install_or_the_Ubuntu_repositories_to_my_Backtrack_install_.3F](http://www.backtrack-linux.org/wiki/index.php/FAQ#Why_cant_I_just_add_the_Backtrack_repositories_to_my_Ubuntu_install_or_the_Ubuntu_repositories_to_my_Backtrack_install_.3F)

---

