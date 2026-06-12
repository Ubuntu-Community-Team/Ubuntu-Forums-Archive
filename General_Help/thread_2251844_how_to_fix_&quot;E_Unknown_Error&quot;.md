---
title: "how to fix &quot;E: Unknown Error&quot;?"
date: 2014-11-07
forum: General Help
---

### Post by yi-ren-labri on 2014-11-07
Hello all,

After upgrading Ubuntu from version 10.04.4 LTS (Lucid Lynx) to 	 14.04.1 LTS (trusty), I got the following errer : 

/usr/lib/update-notifier/apt-check --human-readable
Error in function update
E: Unknown Error: '<type 'exceptions.TypeError'>' (update() takes exactly 2 arguments

Can any expert point me out how to fix it?

I tried apt-get from command line, it failed to resolve this problem.

Thanks in advance!

---

### Post by matt_symes on 2014-11-07
Hi

Sounds like a python issue.

Does apt-get update/upgrade work from the command line ? I assume so but it's worth asking.

Can you post back the results of these commands into your next post.

```
dpkg -S apt-check apt-check.py
```

```
dpkg -l update-notifier-common
```

```
/use/lib/update-notifier/apt_check.py --human-readable | tail -n 30
```

Kind regards

---

### Post by yi-ren-labri on 2014-11-07
Thanks for your reply                                                                                      [**[COLOR=#DD4814][B]matt_symes**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1067998")

---------------------------------------------------------------------
$ dpkg -S apt-check apt-check.py
update-notifier-common: /usr/lib/update-notifier/apt-check
dpkg-query: no path found matching pattern *apt-check.py*

---------------------------------------------------------------------

$ dpkg -l update-notifier-common
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  update-notifie 0.119ubuntu8 all          Files shared between update-notif


---------------------------------------------------------------------
$ /use/lib/update-notifier/apt_check.py --human-readable | tail -n 30
bash: /use/lib/update-notifier/apt_check.py: No such file or directory
---------------------------------------------------------------------
Yes, sudo apt-get *** etc command works as nomal as before upgrading to 14.04.1 LTS (trusty):

```
$ sudo apt-get update
[sudo] password ...
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
Get:1 [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg [933 B]                  
Get:2 [http://archive.canonical.com](http://archive.canonical.com) trusty Release [9,359 B]                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease                         
Get:3 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages [5,566 B]      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease                        
Get:4 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en [3,919 B]     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                               
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg [933 B]            
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty InRelease              
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security Release.gpg [933 B]
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release.gpg            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release [62.0 kB]       
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release             
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main i386 Packages    
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security Release [62.0 kB]        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en_US
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources [136 kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources [1,408 B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Sources [3,517 B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources [89.3 kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [350 kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [5,820 B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages [9,546 B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages [217 kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en [161 kB]   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en           
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Sources [49.5 kB]        
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Sources [14 B]     
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Sources [698 B]    
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Sources [11.2 kB]    
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main i386 Packages [147 kB]   
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse i386 Packages [1,401 B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe i386 Packages [51.2 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Translation-en          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_US                
Fetched 1,379 kB in 13s (103 kB/s)                                             
Reading package lists... Done
```

---

### Post by yi-ren-labri on 2014-11-07
Plus, all small icons at top-right corner sometimes disappear from the top bar, that I have to run:

$ unity &

to re-activate them.

---

### Post by matt_symes on 2014-11-07
Hi

> **yi-ren-labri said:**
> $ dpkg -S apt-check apt-check.py
update-notifier-common: /usr/lib/update-notifier/apt-check
dpkg-query: no path found matching pattern *apt-check.py*

There is actually a typo on the command above. It should have been 

```
dpkg -S apt-check apt**_**check.py
```

I blame my phone for that as it's auto-incorrecting all my typing at the moment.

Anyway, as the apt-check symlink is there, i assume that the file apt**_**check.py is also there and the symlink is pointing to it. You can check with

```
readlink -f /usr/lib/update-notifier/apt-check
```

It should point to 

```
/usr/lib/update-notifier/apt_check.py
```

Post back if this is *not* the case.

> $ dpkg -l update-notifier-common
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  update-notifie **0.119ubuntu8** all          Files shared between update-notif

This is what i find interesting. I have bolded the version you have installed on your system.

This is the version i have installed on my 14.04.1 version of Xubuntu. 

```
ii  update-notifier-common      **0.154.1ubuntu1**     all                Files shared between update-notifier and other packages
```

This package should be pretty much the same if both our installations are up to date as update-notifier should be similar/same.

> 
$ /use/lib/update-notifier/apt_check.py --human-readable | tail -n 30
bash: /use/lib/update-notifier/apt_check.py: No such file or directory

The above was due to my typo earlier. /usr has been magically changed in /use :) My phone thinks it's smarter than me :0. It quite possibly is.

> Yes, sudo apt-get *** etc command works as nomal as before upgrading to 14.04.1 LTS (trusty):

So it looks like maybe the problem is not with apt itself but only with update-notifier. This is good if it's true.

To check some things, please post the output of

```
cat /etc/lsb-release
```

```
uname -a
```

```
python --version
```

```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

```
apt-cache policy update-notifier-common
```

Kind regards

---

### Post by ian-weisser on 2014-11-07
> **yi-ren-labri said:**
> After upgrading Ubuntu from version 10.04.4 LTS (Lucid Lynx) to      14.04.1 LTS (trusty)

What method did you use to upgrade across four years of changes? Reinstall? Using 12.04 as an intermediate? Some other way?

---

### Post by yi-ren-labri on 2014-11-07
I have not been using this computer for almost 2 years until recently I picked it up.

I did upgrade totally from commande line : Ubuntu 10.04 -> Ubuntu 12.04 -> 14.04.1 LTS (trusty)

But I was waiting for upgrading OS until 14.04**.1** release.

Thanks for your help...

---

### Post by yi-ren-labri on 2014-11-07
```
$ dpkg -S apt-check apt_check.py
update-notifier-common: /usr/lib/update-notifier/apt-check
update-notifier-common: /usr/lib/update-notifier/apt_check.py

```
-----------------------------------------------------------
```

$  /usr/lib/update-notifier/apt_check.py --human-readable | tail -n 30
Error in function update
E: Unknown Error: '<type 'exceptions.TypeError'>' (update() takes exactly 2 arguments (1 given))

```
-----------------------------------------------------------
```

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"

```
-----------------------------------------------------------
```

$ uname -a
Linux boxname 3.2.0-67-generic-pae #101-Ubuntu SMP Tue Jul 15 18:04:54 UTC 2014 i686 i686 i686 GNU/Linux

```
-----------------------------------------------------------
```

$ python --version
Python 2.7.6
```
-----------------------------------------------------------
```

$ grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:7:deb http://archive.ubuntu.com/ubuntu trusty main restricted multiverse
/etc/apt/sources.list:8:deb-src http://archive.ubuntu.com/ubuntu trusty main restricted multiverse
/etc/apt/sources.list:12:deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted multiverse
/etc/apt/sources.list:13:deb-src http://archive.ubuntu.com/ubuntu trusty-updates main restricted multiverse
/etc/apt/sources.list:18:deb http://archive.ubuntu.com/ubuntu trusty universe
/etc/apt/sources.list:19:deb-src http://archive.ubuntu.com/ubuntu trusty universe
/etc/apt/sources.list:20:deb http://archive.ubuntu.com/ubuntu trusty-updates universe
/etc/apt/sources.list:21:deb-src http://archive.ubuntu.com/ubuntu trusty-updates universe
/etc/apt/sources.list:46:deb http://archive.ubuntu.com/ubuntu trusty-security main restricted multiverse
/etc/apt/sources.list:47:deb-src http://archive.ubuntu.com/ubuntu trusty-security main restricted multiverse
/etc/apt/sources.list:48:deb http://archive.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:49:deb-src http://archive.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list.d/dropbox.list:1:deb http://linux.dropbox.com/ubuntu trusty main
/etc/apt/sources.list.d/dropbox.list.save:1:deb http://linux.dropbox.com/ubuntu trusty main
/etc/apt/sources.list.d/lucid-partner.list:4:deb http://archive.canonical.com/ubuntu trusty partner
/etc/apt/sources.list.d/lucid-partner.list.distUpgrade:4:deb http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list.d/lucid-partner.list.save:4:deb http://archive.canonical.com/ubuntu trusty partner



```
-----------------------------------------------------------
```

$ apt-cache policy update-notifier-common
update-notifier-common:
  Installed: 0.119ubuntu8.7
  Candidate: 0.154.1ubuntu1
  Version table:
     0.154.1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
     0.154.1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
 *** 0.119ubuntu8.7 0
        100 /var/lib/dpkg/status

```
-----------------------------------------------------------

---

### Post by yi-ren-labri on 2014-11-09
Should I delete package: ** update-notifier-common**

Files shared between update-notifier and other packages
- update-notifier-common

Apt setup and reboot notification scripts between update-notifier and other packages, notably for server use cases.

Canonical provides critical updates for Files shared between update-notifier and other packages until May 2019.

---

### Post by ian-weisser on 2014-11-09
> **yi-ren-labri said:**
> ```

update-notifier-common:
  Installed: 0.119ubuntu8.7
  Candidate: 0.154.1ubuntu1
  Version table:
     0.154.1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
     0.154.1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
 *** 0.119ubuntu8.7 0
        100 /var/lib/dpkg/status

```

The 0.119 version if from 12.04.
The 0.154 version is from 14.04.
```
$ rmadison -u ubuntu update-notifier-common
 update-notifier-common | 0.119ubuntu8.7  | precise-updates | all
 update-notifier-common | 0.154.1ubuntu1  | trusty-updates  | all
```

If you still have 12.04 packages on your 14.04 system, then apparently your 12.04 --> 14.04 upgrade was not completely successful. Do you recall any errors during the upgrade ?

When you try to upgrade manually using apt-get instead of Software Updater (sudo apt-get upgrade), do you get any error messages?

---

### Post by yi-ren-labri on 2014-11-09
Re: When you try to upgrade manually using apt-get instead of Software  Updater (sudo apt-get upgrade), do you get any error messages?

I remember that there are errors for LaTex related packages : TexLive etc, in shell error messages like : The installed packages have unmet dependencies.

Then I have issued the following commands to fix them:
```

sudo apt-get clean
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get -f install

```

I just re-install pakage: update-notifier-common, now :
```

$ rmadison -u ubuntu update-notifier-common
 update-notifier-common | 0.99.3          | lucid           | all
 update-notifier-common | 0.99.3ubuntu0.1 | lucid-security  | all
 update-notifier-common | 0.99.3ubuntu0.1 | lucid-updates   | all
 update-notifier-common | 0.119ubuntu8.1  | precise         | all
 update-notifier-common | 0.119ubuntu8.7  | precise-updates | all
 update-notifier-common | 0.154.1         | trusty          | all
 update-notifier-common | 0.154.1ubuntu1  | trusty-updates  | all
 update-notifier-common | 3.157           | utopic          | all
 update-notifier-common | 3.157           | vivid           | all


$ apt-cache policy update-notifier-common
update-notifier-common:
  Installed: 0.154.1ubuntu1
  Candidate: 0.154.1ubuntu1
  Version table:
 *** 0.154.1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
        100 /var/lib/dpkg/status
     0.154.1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages

```

---

### Post by Bashing-om on 2014-11-09
yi-ren-labri; Hi !

Show us the outputs - Between Code Tags - of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```
Thus we see the errors in context, enabling us to advise directly.

[INDENT][INDENT]there is a way that seems right, but
[/INDENT][/INDENT]

---

### Post by yi-ren-labri on 2014-11-09
Thanks for your quick reply.

```

$ sudo apt-get update
Ign http://archive.canonical.com trusty InRelease                              
Hit http://archive.canonical.com trusty Release.gpg                            
Ign http://archive.ubuntu.com trusty InRelease                               
Hit http://archive.canonical.com trusty Release                              
Ign http://archive.ubuntu.com trusty-updates InRelease                       
Ign http://linux.dropbox.com trusty InRelease                         
Ign http://archive.ubuntu.com trusty-security InRelease
Hit http://archive.canonical.com trusty/partner i386 Packages
Hit http://archive.canonical.com trusty/partner Translation-en
Hit http://archive.ubuntu.com trusty Release.gpg
Hit http://linux.dropbox.com trusty Release.gpg
Get:1 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://linux.dropbox.com trusty Release                
Hit http://archive.ubuntu.com trusty-security Release.gpg
Hit http://linux.dropbox.com trusty/main i386 Packages
Hit http://archive.ubuntu.com trusty Release
Get:2 http://archive.ubuntu.com trusty-updates Release [62.0 kB]      
Hit http://archive.ubuntu.com trusty-security Release                    
Hit http://archive.ubuntu.com trusty/main Sources                      
Hit http://archive.ubuntu.com trusty/restricted Sources
Hit http://archive.ubuntu.com trusty/multiverse Sources
Hit http://archive.ubuntu.com trusty/universe Sources
Ign http://linux.dropbox.com trusty/main Translation-en_US
Hit http://archive.ubuntu.com trusty/main i386 Packages
Ign http://linux.dropbox.com trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/restricted i386 Packages
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty/universe i386 Packages
Hit http://archive.ubuntu.com trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                 
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Hit http://archive.ubuntu.com trusty/universe Translation-en                   
Get:3 http://archive.ubuntu.com trusty-updates/main Sources [136 kB]           
Get:4 http://archive.ubuntu.com trusty-updates/restricted Sources [1,408 B]    
Get:5 http://archive.ubuntu.com trusty-updates/multiverse Sources [3,517 B]    
Get:6 http://archive.ubuntu.com trusty-updates/universe Sources [89.3 kB]      
Get:7 http://archive.ubuntu.com trusty-updates/main i386 Packages [349 kB]     
Get:8 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:9 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [9,546 B]
Get:10 http://archive.ubuntu.com trusty-updates/universe i386 Packages [217 kB]
Hit http://archive.ubuntu.com trusty-updates/main Translation-en               
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en           
Hit http://archive.ubuntu.com trusty-security/main Sources                     
Hit http://archive.ubuntu.com trusty-security/restricted Sources               
Hit http://archive.ubuntu.com trusty-security/multiverse Sources               
Hit http://archive.ubuntu.com trusty-security/universe Sources                 
Hit http://archive.ubuntu.com trusty-security/main i386 Packages               
Hit http://archive.ubuntu.com trusty-security/restricted i386 Packages         
Hit http://archive.ubuntu.com trusty-security/multiverse i386 Packages         
Hit http://archive.ubuntu.com trusty-security/universe i386 Packages           
Hit http://archive.ubuntu.com trusty-security/main Translation-en              
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en        
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en        
Hit http://archive.ubuntu.com trusty-security/universe Translation-en          
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Fetched 874 kB in 23s (37.2 kB/s)                                              
Reading package lists... Done

```
---------------------------------------------------------------------
```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  html2text
Use 'apt-get autoremove' to remove it.
The following packages have been kept back:
  activity-log-manager-control-center aisleriot akonadi-backend-mysql
  akonadi-server akregator anjuta anjuta-common ant-gcj ant-optional-gcj
  apparmor apparmor-utils apport apport-gtk aptitude apturl apturl-common
  audacious audacious-plugins autogen bamfdaemon bind9-host blt brasero
  brasero-cdrkit brasero-common browser-plugin-gnash bsh byobu catfish cdrdao
  cervisia clang codeblocks codeblocks-common codeblocks-dbg colord
  command-not-found couchdb-bin cpp cpp-4.6 cups cups-filters ddd
  default-jdk-doc deja-dup devhelp dia dia-common dia-libs digikam
  digikam-data dnsutils docutils-common dolphin duplicity eclipse-jdt
  eclipse-pde eclipse-platform eclipse-platform-data eclipse-rcp emacs23
  emacs23-bin-common emacs23-common enblend enfuse erlang-base erlang-crypto
  erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl
  erlang-syntax-tools erlang-xmerl evince evince-common fakeroot g++ g++-4.6
  gbrainy gcc gcc-4.6 gcc-4.6-base gcc-4.6-doc gcc-4.6-multilib gcc-doc
  gcc-multilib geany geany-common geany-plugin-addons geany-plugin-codenav
  geany-plugin-debugger geany-plugin-doc geany-plugin-extrasel
  geany-plugin-gendoc geany-plugin-gproject geany-plugin-insertnum
  geany-plugin-latex geany-plugin-lipsum geany-plugin-lua geany-plugin-macro
  geany-plugin-numberedbookmarks geany-plugin-pg geany-plugin-prettyprinter
  geany-plugin-prj geany-plugin-sendmail geany-plugin-shiftcolumn
  geany-plugin-spellcheck geany-plugin-tableconvert geany-plugin-treebrowser
  geany-plugin-updatechecker geany-plugin-vc geany-plugin-webhelper
  geany-plugin-xmlsnippets geany-plugins geany-plugins-common gedit
  gedit-common gedit-dev gedit-latex-plugin gedit-plugins gettext gettext-base
  gfortran gfortran-4.6 gimp gimp-data gir1.2-folks-0.6 gir1.2-gtksource-3.0
  gir1.2-json-1.0 gir1.2-rb-3.0 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0
  gnash gnash-common gnome-disk-utility gnome-orca gnome-sudoku gnomine
  gnuplot-nox gnuplot-x11 gobjc gobjc-4.6 grace graphviz grub-common grub-pc
  grub-pc-bin grub2-common gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gthumb
  gthumb-data gufw gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons
  gvfs-fuse gvfs-libs gwenview gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  hugin hugin-data hugin-tools hunspell-fr ibus-pinyin imagemagick
  indicator-applet indicator-applet-complete indicator-applet-session
  indicator-appmenu indicator-messages inkscape iptables k3b k3b-data
  kde-baseapps-bin kde-baseapps-data kde-runtime kde-runtime-data
  kdepim-runtime kdepimlibs-kio-plugins kgpg khelpcenter4 kipi-plugins
  kipi-plugins-common knode kompare konqueror kubuntu-debug-installer
  language-pack-kde-en latex-cjk-common latexila latexila-data
  libakonadi-calendar4 libakonadi-contact4 libakonadi-kcal4 libakonadi-kde4
  libakonadi-kmime4 libakonadi-notes4 libakonadiprotocolinternals1
  libanjuta-3-0 libarpack2 libatk-adaptor libatlas3gf-base libaudclient2
  libaudcore1 libav-tools libavcodec-dev libavdevice53 libavformat-dev
  libavutil-dev libblas-dev libblas3gf libbonobo2-0 libbonobo2-common
  libbonobo2-dev libbonoboui2-0 libbonoboui2-dev libbrasero-media3-1
  libcalendarsupport4 libcommons-compress-java libequinox-osgi-java libgcj-bc
  libgdl-3-common libgettextpo0 libgimp2.0 libgimp2.0-dev libgladeui-common
  libgnome2-0 libgnome2-dev libgpgme++2 libgpgme11 libgpod-common libgpod4
  libgraph-readwrite-perl libgraphviz-dev libgstreamer-plugins-bad0.10-0
  libgtksourceview-3.0-common libgtksourceview-3.0-dev
  libgtksourceviewmm-3.0-0 libgv-python libhttp-message-perl
  libincidenceeditorsng4 libitext-java libjhdf5-jni libjoda-time-java
  libjs-sphinxdoc libjson-glib-1.0-0 libk3b6 libkabc4 libkalarmcal2 libkcal4
  libkcalcore4 libkcalutils4 libkcddb4 libkdepim4 libkdepimdbusinterfaces4
  libkgeomap1 libkholidays4 libkimap4 libkldap4 libkleo4 libkmbox4 libkmime4
  libkpgp4 libkpimidentities4 libkpimtextedit4 libkpimutils4 libkresources4
  libktnef4 liblapack-dev liblapack3gf libmailcommon4 libmailtools-perl
  libmailtransport4 libmessagecomposer4 libmessagecore4 libmessageviewer4
  libmicroblog4 libnb-apisupport3-java libnb-ide14-java libnb-java5-java
  libnetfilter-conntrack3 libobjc3 libopts25 libopts25-dev liborbit2
  liborbit2-dev libparpack2 libpathplan4 libpostproc52 libqgpgme1 libqt4-core
  libqt4-dbus libqt4-declarative libqt4-declarative-gestures
  libqt4-declarative-particles libqt4-designer libqt4-dev libqt4-gui
  libqt4-help libqt4-network libqt4-opengl libqt4-opengl-dev libqt4-qt3support
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns
  libqtbamf1 libqtcore4 libqtgui4 libqtwebkit-dev libqtwebkit4 libquicktime2
  libsane libsane-common libsasl2-2 libsmbclient libstdc++6-4.6-dev
  libsvn-java libsvn1 libsvnclientadapter-java libsvnkit-java libswscale-dev
  libswscale2 libswt-cairo-gtk-3-jni libswt-glx-gtk-3-jni
  libswt-gnome-gtk-3-jni libswt-gtk-3-java libswt-gtk-3-jni
  libswt-webkit-gtk-3-jni libtemplateparser4 libtiff4-dev libtotem0 libv4l-0
  libv4l-dev libv4lconvert0 libvlc5 libxdot4 libxine-dev libxine1 libxine1-bin
  libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-x
  lilypond-doc linux-generic-pae linux-headers-generic
  linux-headers-generic-pae linux-image-generic-pae lp-solve lyx lyx-common
  mahjongg marble-plugins modemmanager mplayer mysql-server-5.5
  mysql-server-core-5.5 ndiswrapper-utils-1.9 netbeans network-manager
  network-manager-gnome nmap nvidia-common okular onboard oneconf orbit2
  overlay-scrollbar phonon-backend-gstreamer pitivi
  plasma-scriptengine-javascript pm-utils poppler-data postgresql
  postgresql-client procps protobuf-compiler pulseaudio-module-bluetooth
  python-debian python-docutils python-gconf python-gnome2 python-imaging
  python-imaging-tk python-kde4 python-keyring python-numpy
  python-piston-mini-client python-pyorbit python-qt4 python-reportlab
  python-sip python-smbc python-sphinx python-tk python-ubuntu-sso-client
  python-wxgtk2.8 qapt-batch qdbus qt4-demos qt4-designer qt4-dev-tools
  qt4-linguist-tools qt4-qmake qt4-qmlviewer qt4-qtconfig qtcreator qtoctave
  r-base-core r-base-dev r-cran-abind r-cran-boot r-cran-car r-cran-chron
  r-cran-class r-cran-cluster r-cran-codetools r-cran-colorspace
  r-cran-effects r-cran-foreign r-cran-hmisc r-cran-kernsmooth r-cran-lattice
  r-cran-lmtest r-cran-mass r-cran-matrix r-cran-mgcv r-cran-multcomp
  r-cran-mvtnorm r-cran-nlme r-cran-nnet r-cran-rcmdr r-cran-relimp r-cran-rgl
  r-cran-rpart r-cran-sandwich r-cran-sm r-cran-spatial r-cran-strucchange
  r-cran-survival r-cran-zoo r-recommended rapidsvn rhythmbox rhythmbox-data
  rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rocs rpm rpm-common rpm2cpio
  rsyslog samba-common samba-common-bin scilab scilab-cli scilab-data
  scilab-full-bin scilab-minimal-bin screen-resolution-extra scribus
  sessioninstaller shotwell smbclient software-properties-common
  software-properties-gtk software-properties-kde speech-dispatcher
  sphinx-common subversion system-config-printer-gnome tcl8.4 tcl8.5 texinfo
  texmaker texmaker-data tk8.4 tk8.5 tomboy totem totem-common totem-mozilla
  totem-plugins transmission-common transmission-gtk ttf-dejavu ttf-jsmath
  ttf-lyx ttf-wqy-microhei ttf-wqy-zenhei ubuntu-restricted-addons
  ubuntu-sso-client ubuntu-wallpapers update-manager update-manager-core
  update-manager-kde upower usb-creator-common usb-creator-gtk usbmuxd vinagre
  vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse whoopsie winff
  wxmaxima xdiagnose xmhtml1 xpdf xserver-xorg-video-all xz-utils
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin apt apt-transport-https
  apt-utils aptdaemon aptdaemon-data bash bsdutils cups-bsd cups-client
  cups-common cups-ppdc dbus dbus-x11 debhelper evolution-data-server
  evolution-data-server-common exuberant-ctags firefox firefox-globalmenu
  firefox-locale-en firefox-locale-zh-hans firefox-locale-zh-hant fonts-droid
  fonts-opensymbol gcalctool gcc-4.9-base gdb gdb-doc
  gir1.2-gnomebluetooth-1.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-panelapplet-4.0 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-webkit-3.0
  gnome-bluetooth gnome-calculator gnome-keyring gnome-panel gnome-panel-data
  gnome-session-fallback gnome-session-flashback hardening-includes
  hunspell-en-ca hyphen-fr icedtea-6-jre-cacao icedtea-6-jre-jamvm irqbalance
  language-selector-common lib64gcc1 libapt-inst1.5 libapt-pkg4.12 libblkid1
  libc-bin libc-dev-bin libc6 libc6-amd64 libc6-dbg libc6-dev libc6-dev-amd64
  libcamel-1.2-45 libcommons-el-java libcups2 libcupscgi1 libcupsimage2
  libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls libdbus-1-3 libdbus-1-dev
  libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16
  libedata-book-1.2-20 libedata-cal-1.2-23 libedataserver-1.2-18 libgcc1
  libgcrypt11 libgcrypt11-dev libglib2.0-0 libglib2.0-bin libglib2.0-data
  libglib2.0-dev libglib2.0-doc libgnome-bluetooth11 libgudev-1.0-0
  libgweather-3-6 libgweather-common libharfbuzz-dev libharfbuzz-gobject0
  libharfbuzz-icu0 libharfbuzz0b libindicator3-7 libindicator7
  libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0 libkworkspace4abi2
  liblua5.1-0 libmount1 libmysqlclient18 libnspr4 libnspr4-0d libnss3
  libnss3-1d libnss3-nssdb libnux-4.0-0 libnux-4.0-common libpam-gnome-keyring
  libpam-systemd libpanel-applet-4-0 libpango-1.0-0 libpango1.0-0
  libpango1.0-dev libpango1.0-doc libpangocairo-1.0-0 libpangoft2-1.0-0
  libpangoxft-1.0-0 libpeas-1.0-0 libpeas-dev libphonon4 libpoppler-glib8
  libpoppler44 libpurple-bin libpurple0 libreoffice-avmedia-backend-gstreamer
  libreoffice-base libreoffice-base-core libreoffice-base-drivers
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-emailmerge libreoffice-gnome libreoffice-gtk
  libreoffice-help-en-gb libreoffice-help-en-us libreoffice-help-zh-cn
  libreoffice-help-zh-tw libreoffice-impress libreoffice-java-common
  libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-l10n-zh-cn
  libreoffice-l10n-zh-tw libreoffice-math libreoffice-pdfimport
  libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb libreoffice-style-human
  libreoffice-style-tango libreoffice-writer libruby1.9.1 libssl-dev
  libssl-doc libssl1.0.0 libsystemd-daemon0 libsystemd-journal0
  libsystemd-login0 libudev1 libunity-2d-private0 libunity-control-center1
  libunity-core-6.0-9 libuuid1 libvncserver0 libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libxml2
  libxml2-dev libxml2-utils linux-firmware linux-libc-dev lshw man-db mount
  multiarch-support myspell-en-gb myspell-en-za mysql-client-5.5
  mysql-client-core-5.5 mysql-common mysql-server mythes-en-us mythes-fr
  nux-tools openjdk-6-doc openjdk-6-jdk openjdk-6-jre openjdk-6-jre-headless
  openjdk-6-jre-lib openjdk-7-jdk openjdk-7-jre openjdk-7-jre-headless
  openoffice.org-hyphenation openssl phonon pidgin pidgin-data poppler-utils
  python-apport python-aptdaemon python-aptdaemon-gtk
  python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-cupshelpers
  python-libxml2 python-problem-report python-software-properties
  python3-aptdaemon python3-requests python3-uno ruby1.9.1
  system-config-printer-common system-config-printer-udev systemd-services
  thunderbird thunderbird-globalmenu thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-gb thunderbird-locale-en-us
  thunderbird-locale-zh-cn thunderbird-locale-zh-hans
  thunderbird-locale-zh-hant thunderbird-locale-zh-tw tzdata tzdata-java udev
  unity unity-2d unity-2d-common unity-control-center unity-services uno-libs3
  ure util-linux uuid-runtime wget wpasupplicant xchat xchat-common
  xchat-gnome xchat-gnome-common xserver-common xserver-xorg-core
  xserver-xorg-video-intel
252 upgraded, 0 newly installed, 0 to remove and 534 not upgraded.
Need to get 394 MB of archives.
After this operation, 9,962 kB of additional disk space will be used.
Do you want to continue? [Y/n] 

```
---------------------------------------------------------------------
```

$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

---

### Post by Bashing-om on 2014-11-09
yi-ren-labri; Yikes !


Did the release upgrade complete successfully ?
> 
After upgrading Ubuntu from version 10.04.4 LTS (Lucid Lynx) to 14.04.1 LTS (trusty), I got the following errer : 

And the output of "apt-get upgrade", wow, a great number of packages that are in a 'held' state ; make it questionable that the release upgrade completed.

Try; in this order:
```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean

#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,A dist-upgrade will install new dependencies for packages already installed and may remove packages if they are no longer needed. This will not bring you to a new release of ubuntu. 
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

```

In the hope that all dependencies are now satisfied, and you are now up on 14.04.

[INDENT][INDENT]maybe yes.
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by yi-ren-labri on 2014-11-09
Thanks all. This problem has been resolved.

---

### Post by Bashing-om on 2014-11-12
yi-ren-labri; Great !

As the situation is now under control;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]we do something different next time
[/INDENT][/INDENT]

---

