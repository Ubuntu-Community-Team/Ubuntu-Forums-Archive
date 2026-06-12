---
title: "Flash Player"
date: 2019-05-26
forum: General Help
---

### Post by simonf2 on 2019-05-26
I am knew to Ubuntu.  Firefox will not play certain videos because there is no flash player.  I know all the arguments against flash but what is the most straightforward way to enable it please?  Coming from Windows (don't shout) where I am moderately competent I am finding things a tad confusing so if you can help, please spell it out very simply!  Thanks.

---

### Post by Frogs Hair on 2019-05-26
Copy and paste  the following command in the terminal ,restart the browser, and try again.

 ```
sudo apt install ubuntu-restricted-extras
```

---

### Post by Impavidus on 2019-05-27
The above command will install some software, including flash, that cannot be installed by default for legal reasons. I've never installed restricted-extras, but I think it may ask you to accept an end user agreement. You should be able to use the tab and enter keys to do so.

Some new users get confused by terminal-based menus.

---

### Post by Holger_Gehrke on 2019-05-27
I don't believe installing this will help. ubuntu-restricted-extras depends on ubuntu-restricted-addons, and the changelog for current versions of that package states that the dependency on flash was dropped because flash will EOL before the support for 18.04 ends. The right package to install is probably flashplugin-installer, at least that's what I installed to get flash to work.

```
 sudo apt install flashplugin-installer
```

Holger

---

### Post by Frogs Hair on 2019-05-27
The description below could be outdated. If it fails to install Flash use the command above there are useful codecs included with URE regardless.  


> This collection of packages includes:
  - MP3 and other audio codec software to play various audio formats
   (mplayer plugins)
 - software to install the Microsoft Web fonts
 - the Adobe Flash plugin




---

### Post by mshym on 2019-05-27
hi all,
i am having the same issue, but i heard in another threat that the new version of glibc is causing the issue. flash is not working with 19.04, i have tested it with several browser to start a flash game which i played for years. its not working anymore. i hope someone can fix the problem with glibc, i am a totally newbie to do so.
thank you in advance.

---

### Post by simonf2 on 2019-05-27
Ok, so first apologies for time lag and thanks for the posts.  I ticked notifications for this thread but nothing has come through so I thought there were no answers.

I am a total newbie to Linux although not a complete dummy with computers - sort of reasonably able.  However, as much as I want to get away from MS I feel on a steep learning curve with Ubuntu.  So ... am very grateful for these forums.

In fact I installed Chromium after my post and that played the videos fine.  So hang flash, I'll see if I get on ok with this browser.  

However, I'll see if I get told off by anyone for using this thread to achieve an answer to a related point.  When you use the terminal (I assume you have to type everything like the Windows command line) and then hit return should you get a response?  When I was trying to install flash using instructions off the net, I would type in a command and hit return and nothing seemed to happen!

Thanks for any thoughts.

---

### Post by deadflowr on 2019-05-27
> When I was trying to install flash using instructions off the net, I would type in a command and hit return and nothing seemed to happen!

What commands and from where?

---

### Post by simonf2 on 2019-05-27
Well one was 
$ sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"

Like I say, total newbie and just trying to understand - if you enter something at the prompt and hit return how does the terminal respond?

---

### Post by Frogs Hair on 2019-05-27
Open software & updates / other software and make sure the Canonical Partners repository is enabled as in the screen shot, then open the terminal and enter the following command followed by your password which will be invisible when typed. Press y and enter and when prompted to continue.

```
sudo apt install adobe-flashplugin 
```

When complete the output will look as follows. 

```
d-book@d-book-hp:~$ sudo apt install adobe-flashplugin 
[sudo] password for d-book: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  adobe-flash-properties-gtk
Suggested packages:
  x-ttcidfont-conf ttf-bitstream-vera | ttf-dejavu ttf-xfree86-nonfree xfs
  libnspr4-0d libnss3-1d
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,961 kB of archives.
After this operation, 36.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.canonical.com/ubuntu disco/partner amd64 adobe-flashplugin amd64 1:20190514.1-0ubuntu0.19.04.1 [9,818 kB]
Get:2 http://archive.canonical.com/ubuntu disco/partner amd64 adobe-flash-properties-gtk amd64 1:20190514.1-0ubuntu0.19.04.1 [143 kB]
Fetched 9,961 kB in 4s (2,613 kB/s)                 
Selecting previously unselected package adobe-flashplugin.
(Reading database ... 245865 files and directories currently installed.)
Preparing to unpack .../adobe-flashplugin_1%3a20190514.1-0ubuntu0.19.04.1_amd64.deb ........................................................................] 
Unpacking adobe-flashplugin (1:20190514.1-0ubuntu0.19.04.1) ................] 
Selecting previously unselected package adobe-flash-properties-gtk..........] 
Preparing to unpack .../adobe-flash-properties-gtk_1%3a20190514.1-0ubuntu0.19.04.1_amd64.deb ...
Unpacking adobe-flash-properties-gtk (1:20190514.1-0ubuntu0.19.04.1) ...
Setting up adobe-flashplugin (1:20190514.1-0ubuntu0.19.04.1) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode
Setting up adobe-flash-properties-gtk (1:20190514.1-0ubuntu0.19.04.1) ...
Processing triggers for desktop-file-utils (0.23-4ubuntu1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
d-book@d-book-hp:~$ 

```

---

### Post by Holger_Gehrke on 2019-05-27
> **simonf2 said:**
> Well one was 
$ sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"

Like I say, total newbie and just trying to understand - if you enter something at the prompt and hit return how does the terminal respond?

The Unix command line -- and therefore Linux, too -- works on the principle of "No news is good news." If something goes wrong, the program **will** tell you, otherwise it just returns you to the prompt. You can check the exit status of the last command you ran in the foreground with 'echo $?', a value of 0 means ok, any other number means some kind of error occurred.

And not to be a nitpicker, but the terminal doesn't respond at all. It just offers a text-based interface to programs that need it. The program interpreting and executing your commands is the shell - a separate program which gets run by the terminal and uses it for input and output. You can have a terminal running another program than the shell and you can have a shell without a terminal (when running a script, for example).

Holger

---

