---
title: "Executable Program in /usr/bin Not Executing"
date: 2015-10-13
forum: General Help
---

### Post by jakeclarkphoto on 2015-10-13
Hey everyone,

I'm trying to get a playlist-making program called "Select-o-Magic 3000" set up on my Lubuntu 14.04 system, and after following the installation readme, I appear to have hit a bit of a snag - the executable file won't execute, neither from the launcher I created for the program nor when I click on the executable file in its folder (/usr/bin). When I try to execute in terminal, I get this output:

```
main.c          1800   480: main()                    Select-o-Magic 3000 v1.8.0
main.c          1800   483: main()                    Compiled with GTK+ v2.20.1
main.c          1800   486: main()                      Linked with GTK+ v2.24.23
init.c          1800    73: initSelect()              (...)
configsom3k.c   1800   368: configRead()              configRead()
configsom3k.c   1800   128: loadDefaults()              loadDefaults
configsom3k.c   1800   379: configRead()                Config file not found - using defaults
select.c        1800   174: selectInitMasterTree()    Init Master Tree ******************************
main.c          1800   399: initMainWindow()          Config Window Size: 800x500, Pane: 192
main.c          1800   223: addDefaultIcons()         
cbsavecrit.c    1800    96: listReadDirectory()       Directory: /home/jake/.som3000/criteria
cbsavecrit.c    1800    99: listReadDirectory()       Can't opendir( /home/jake/.som3000/criteria )
```

I'm guessing it may be a permissions issue, but since I'm a bit of a noob, I'm reluctant to go fiddling around with the permissions without knowing exactly what I'm doing. I've attached a screenshot of the permissions for the file.

Here are the readme installation instructions that I followed:

"Installation:

        1) Move or copy the executable file to a directory in your 
           PATH environment. 

           ie: sudo mv som3000 /usr/bin

           or: sudo cp -pv som3000 /usr/bin

        2) Create the folder/directory ~/.som3000

           ie: mkdir ~/.som3000

        3) Move or copy the icon image file som3000icon.png to ~/.som3000

           ie: mv som3000icon.png ~/.som3000

           or: cp som3000icon.png ~/.som3000"


I tried reaching out to the program's ... programmer? ... for help, but I haven't gotten a reply in the few days since I sent my e-mail. I'd appreciate any help!

---

### Post by buzzingrobot on 2015-10-13
Doesn't look like a permissions issue, since it's starting up and then quitting.

Does >  /home/jake/.som3000/criteria exist? 


If not, create it manually and run the program again from the terminal to see if it gets beyond that last "Can't opendir..." message.

---

### Post by jakeclarkphoto on 2015-10-13
Oh, ha, that did it - I used "mkdir" to create "criteria". Was that the right way to have gone about that? 

I had considered trying to create "criteria", but at the same time I thought it was weird that I'd have to do that if the installation readme hadn't specifically instructed me to do it. I guess I should have gone ahead and tried it. Thanks, buzzingrobot.

---

### Post by jakeclarkphoto on 2015-10-13
UPDATE: Ok, so, apparently it did compile, despite the terminal output seeming to suggest to me that it hadn't compiled. Everything is up and working now!

Uh, well, that seemed to have fixed it, but the plot has thickened - the executable file opens, but the program doesn't actually function. Upon further investigation, it appears that I had only downloaded the executable file from sourceforge, and that I should have also downloaded a separate source.tar.gz file, and without the source.tar.gz files being installed, the program doesn't actually work, even with the executable running. So I've now downloaded said source.tar.gz... but I'm having trouble getting ./configure to work. Here's the terminal output:

```
jake@jake-Latitude-D630:~/Downloads/som3000$ ls
aclocal.m4  config.log     INSTALL      manualinstall.txt  som3000icon.png
AUTHORS     config.status  m4           NEWS               src
autogen.sh  configure      Makefile     README
ChangeLog   configure.ac   Makefile.am  ReadMe.txt
config      COPYING        Makefile.in  som3000
jake@jake-Latitude-D630:~/Downloads/som3000$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: in `/home/jake/Downloads/som3000':
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
jake@jake-Latitude-D630:~/Downloads/som3000$
```

I tried a couple of alternative compiler options (**./configure CC="cc"** and **./configure CC="cc -nodtk"**) as per the installation readme's instructions, but neither has resulted in ./configure going all the way through. 

Would you, buzzingrobot, or anyone else, have any idea how I can get ./configure to work?

Thanks again!

---

