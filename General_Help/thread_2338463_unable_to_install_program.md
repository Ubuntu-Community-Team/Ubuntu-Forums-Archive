---
title: "unable to install program"
date: 2016-09-28
forum: General Help
---

### Post by nwpll on 2016-09-28
Hi

Recently while doing an system update i had a power failure here in Portugal. In the top right of the screen i have an icon like a no entry sign below is a screen shot of the Error message.

This is stopping me from installing updates etc.

The message i get is An error occurred, please run package manager from the right-click menu or apt-get in a terminal to see what was wrong. The error message was   Error. brokencount>0    This usually means that your installed packages have unmet dependencies 

Could someone help or do i need to install 16.04 again?

Peter

---

### Post by ian-weisser on 2016-09-28
Open a terminal.
Please show us the complete output of :
```
sudo apt update
sudo apt upgrade
```

---

### Post by nwpll on 2016-09-28
Hi Ian-Weisser

I have included the Sudo apt upgrade first and then the Sudo apt update i did the Update before the Upgrade in a terminal 

Thanks

Peter

```
peter@peter-System-Product-Name:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic : Depends: linux-headers-generic (= 4.4.0.36.38) but 4.4.0.34.36 is installed
E: Unmet dependencies. Try using -f.
peter@peter-System-Product-Name:~$ 

peter@peter-System-Product-Name:~$ sudo apt update
[sudo] password for peter: 
Sorry, try again.
[sudo] password for peter: 
Hit:1 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) xenial InRelease                     
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]    
Hit:3 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Ign:4 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable InRelease                    
Hit:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:6 [http://ppa.launchpad.net/samoilov-lex/gnome-twitch/ubuntu](http://ppa.launchpad.net/samoilov-lex/gnome-twitch/ubuntu) xenial InRelease
Get:7 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) xenial-backports InRelease [92.2 kB] 
Ign:8 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty InRelease                     
Hit:9 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release                      
Hit:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                    
Hit:12 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty Release                      
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [95.7 kB]  
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [92.2 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [388 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [149 kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [327 kB]
Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [114 kB]
Fetched 1,353 kB in 26s (51.9 kB/s)                                            
Reading package lists... Done
Building dependency tree       
Reading state information... Done
131 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11 (restricted/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11 (multiverse/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11 (universe/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target DEP-11 (restricted/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:78
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:78
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:78
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:78
W: Target DEP-11 (universe/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:78
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:78
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:80
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:80
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:80
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:80
W: Target DEP-11 (multiverse/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:80
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:80
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11 (restricted/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11 (multiverse/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11 (universe/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:37
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target DEP-11 (main/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target DEP-11 (restricted/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:76
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:78
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:78
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:78
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:78
W: Target DEP-11 (universe/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:78
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:78
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:80
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:80
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:80
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:80
W: Target DEP-11 (multiverse/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:80
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:35 and /etc/apt/sources.list:80
```

---

### Post by ian-weisser on 2016-09-28
Before we go any farther, let's fix your /etc/apt/source.list and get rid of all those warnings.

Please post the contents of your /etc/apt/sources.list here.
Please use [code] tags to contain the output.

---

### Post by nwpll on 2016-09-29
Hi Ian 

Sorry for delay but i have only just found the  /etc/apt/source.list

Please use [code] tags to contain the output. 		Sorry i don't understand what you mean by this.


/etc/apt/sources.list.d/samoilov-lex-ubuntu-gnome-twitch-xenial.list
/etc/apt/sources.list.d/samoilov-lex-ubuntu-gnome-twitch-xenial.list.save

/etc/apt/sources.list.d/google-earth.list
/etc/apt/sources.list.d/google-earth.list.distUpgrade
/etc/apt/sources.list.d/google-earth.list.save

Peter

---

### Post by Bucky Ball on 2016-09-29
Just a point. Always run 'sudo apt update' *first*. You defeat the purpose running it second and not much point.__

---

### Post by ian-weisser on 2016-09-29
We need the *contents *of the file.

Use [code] tags to make long terminal output readable. See [this guide]("https://ubuntuforums.org/showthread.php?t=2171721").

---

### Post by nwpll on 2016-09-29
Hi Ian

Sorry reading about code tags is proving impossible i don't have a clue what it all means. 
Would it not be better to just reinstall 16.04 but it's difficult as my internet is only 0.65mbps..

Sorry i find this difficult

I used Gedit to open the file in Ect/apt/source.list

Peter

deb [http://ppa.launchpad.net/samoilov-lex/gnome-twitch/ubuntu](http://ppa.launchpad.net/samoilov-lex/gnome-twitch/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/samoilov-lex/gnome-twitch/ubuntu](http://ppa.launchpad.net/samoilov-lex/gnome-twitch/ubuntu) xenial main

---

### Post by Bucky Ball on 2016-09-29
For how to add ```
 tags go to [your post #3]("https://ubuntuforums.org/showthread.php?t=2338463&p=13550740&viewfull=1#post13550740") and 'Edit Post' to see how oldos2er has done it. ;)

It is important that you get the spelling correct and use upper and lower case when when instructed using terminal commands. *It makes a difference*. Trying to open 'Ect/apt/source.list' will not get you far. 

So. Open a terminal, copy and paste this into the terminal. Use control+shift+v to paste to a terminal:

[CODE]sudo nano /etc/apt/sources.list
```

Hit enter. You will be asked for your password. Type it in. It will be invisible. This is normal. To use gedit to view the file:

```
gksudo gedit /etc/apt/sources.list
```

Copy ALL of the contents in that file (the output after you issue that command, type in the password and hit 'enter') and paste it here, between code tags please. Then run:

```
sudo apt update
```

... and post the output of that also, please, between another set of code tags. Thanks.

---

### Post by ian-weisser on 2016-09-29
@nwpll,

Your two problems seem very easy to fix so far. Reinstalling seems vastly too intrusive.

It's challenging and sometimes frustrating to learn new skills - and that is exactly what you are doing.

When you can pull the needed information from your system, and when you can usefully show us that information by using [code], then we will be able to safely and quickly help you fix your system.

---

### Post by nwpll on 2016-09-29
Hi Guys

I know you are doing your best to help but i can't or don't understand about opening and putting code tags i think it best i download 16.04 and do an new install. I have wasted your time and i haven't a clue what i am trying to do.

Thanks for your help but at 67 years of age everything is a little harder to learn.

Peter

---

