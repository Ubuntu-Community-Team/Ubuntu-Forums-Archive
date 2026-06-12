---
title: "sudo apt-get install.....problems?????"
date: 2005-08-07
forum: General Help
---

### Post by storybookhero on 2005-08-07
I tried to do the apt get install commans in the terminal to retrieve various files i.e p2p programs, java and others and I keep getting this message 

jeff@ubuntu:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  akregator: Depends: libkdepim1 (>= 4:3.4.0) but it is not going to be installe d
             Depends: libktnef1 (>= 4:3.4.0) but it is not going to be installed
  juk: Depends: akode (>= 4:3.4.0) but it is not going to be installed
  kaddressbook: Depends: libkdepim1 (>= 4:3.4.0) but it is not going to be insta lled
                Depends: libktnef1 (>= 4:3.4.0) but it is not going to be instal led
  kalarm: Depends: libkdepim1 (>= 4:3.4.0) but it is not going to be installed
          Depends: libktnef1 (>= 4:3.4.0) but it is not going to be installed
  karm: Depends: libkdepim1 (>= 4:3.4.0) but it is not going to be installed
        Depends: libktnef1 (>= 4:3.4.0) but it is not going to be installed
  kdemultimedia: Depends: akode (>= 4:3.4.0-0ubuntu3) but it is not going to be installed
  kdepim: Depends: libkdepim1 (>= 4:3.4.0-0ubuntu10) but it is not going to be i nstalled
          Depends: libktnef1 (>= 4:3.4.0-0ubuntu10) but it is not going to be in stalled
  kdepim-kfile-plugins: Depends: libktnef1 (>= 4:3.4.0) but it is not going to b e installed
  kdepim-kio-plugins: Depends: libkdepim1 (>= 4:3.4.0) but it is not going to be  installed
                      Depends: libktnef1 (>= 4:3.4.0) but it is not going to be installed
  kdepim-wizards: Depends: libkdepim1 (>= 4:3.4.0) but it is not going to be ins talled
                  Depends: libktnef1 (>= 4:3.4.0) but it is not going to be inst alled
  kicker-applets: Depends: libglib1.2 (>= 1.2.0) but it is not going to be insta lled
                  Depends: libgtk1.2 (>= 1.2.10-4) but it is not going to be ins talled
  kitchensync: Depends: libkdepim1 (>= 4:3.4.0) but it is not going to be instal led
               Depends: libktnef1 (>= 4:3.4.0) but it is not going to be install ed
  kmail: Depends: libkdepim1 (>= 4:3.4.0) but it is not going to be installed
         Depends: libktnef1 (>= 4:3.4.0) but it is not going to be installed
  knode: Depends: libkdepim1 (>= 4:3.4.0) but it is not going to be installed
         Depends: libktnef1 (>= 4:3.4.0) but it is not going to be installed
  knotes: Depends: libkdepim1 (>= 4:3.4.0) but it is not going to be installed
          Depends: libktnef1 (>= 4:3.4.0) but it is not going to be installed
  konq-plugins: Depends: imagemagick but it is not going to be installed
  konsolekalendar: Depends: libkdepim1 (>= 4:3.4.0) but it is not going to be in stalled
                   Depends: libktnef1 (>= 4:3.4.0) but it is not going to be ins talled
  kontact: Depends: libkdepim1 (>= 4:3.4.0) but it is not going to be installed
           Depends: libktnef1 (>= 4:3.4.0) but it is not going to be installed
  korganizer: Depends: libkdepim1 (>= 4:3.4.0) but it is not going to be install ed
              Depends: libktnef1 (>= 4:3.4.0) but it is not going to be installe d
  kpilot: Depends: libktnef1 (>= 4:3.4.0) but it is not going to be installed
  ksync: Depends: libktnef1 (>= 4:3.4.0) but it is not going to be installed
  ktnef: Depends: libktnef1 (>= 4:3.4.0) but it is not going to be installed
  libcvsservice0: Depends: cvs but it is not going to be installed
  libkcal2a: Depends: libkdepim1 (>= 4:3.4.0) but it is not going to be installe d
             Depends: libktnef1 (>= 4:3.4.0) but it is not going to be installed
  libkpimexchange1: Depends: libktnef1 (>= 4:3.4.0) but it is not going to be in stalled
  libkpimidentities1: Depends: libkdepim1 (>= 4:3.4.0) but it is not going to be  installed
                      Depends: libktnef1 (>= 4:3.4.0) but it is not going to be installed
  xmms: Depends: libglib1.2 (>= 1.2.0) but it is not going to be installed
        Depends: libgtk1.2 (>= 1.2.10-4) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s olution).
jeff@ubuntu:~$

does any one know what the heck this is all about? my friend installed everything the same way on his machine and everything worked smooth. 
if someone could help  that would be awesome

---

### Post by grim42 on 2005-08-07
Have you set up the extra repositories?

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

