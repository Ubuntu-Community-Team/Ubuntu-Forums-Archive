---
title: "Was trying PlayonLinux install on 15.04 (64 bit), now error: brokencount &gt;0"
date: 2015-06-19
forum: General Help
---

### Post by firebelle on 2015-06-19
Hello, 

I messed up somewhere. 

History of what I was trying to do: 

I was trying to install PlayonLinux to play King's Quest 1 and I was following instructions on this page ([http://wiki.playonlinux.com/index.php/Installing_PlayOnLinux](http://wiki.playonlinux.com/index.php/Installing_PlayOnLinux)) that said:

> **On Ubuntu Precise (and higher)**

[COLOR=#252525][FONT=sans-serif]To install wine:i386 on Ubuntu, you must first enable support for this architecture (with dpkg configuration file). You can then update the repository and install wine:i386[/FONT][/COLOR]
[COLOR=#252525][FONT=sans-serif][TABLE="width: 1028"]
[TR]
[TD="class: gutter"][RIGHT]1
2
3[/RIGHT]
[/TD]
[TD="class: code"]sudo echo "foreign-i386 architecture"> /etc/dpkg/dpkg.cfg.d/multiarch
sudo apt-get update
sudo apt-get install wine:i386
[/TD]
[/TR]
[/TABLE]

[/FONT][/COLOR]


But then, I read this page which said that was an old way of doing it: [http://askubuntu.com/questions/633654/how-do-i-add-i386-architecture-in-ubuntu-mate-15-04](http://askubuntu.com/questions/633654/how-do-i-add-i386-architecture-in-ubuntu-mate-15-04)

and it suggested: 

> [COLOR=#111111][FONT=Ubuntu]To resolve it, run this command:[/FONT][/COLOR]
sudo dpkg --add-architecture i386
[COLOR=#111111][FONT=Ubuntu]Or, if fails, you can still add it using the other answer's method below.[/FONT][/COLOR]


So I did this:

```
uname -m
sudo sh -c "echo 'foreign-architecture i386' > /etc/dpkg/dpkg.cfg.d/multiarch"



```

And then I tried to do the PlayonLinux instructions to install wine:i386. But it didn't work and now I've messed something up. 

Now I have the little red no icon up in the bar and the phrase: 
> 
An error occurred, please run Package Manager....  Error: BrokenCount > 0....

I am now feeling quite foolish and am not sure how to fix this. Normally I would just reinstall and start ubuntu over again, but I really need to stop doing that and actually learn where I messed up.

---

### Post by mörgæs on 2015-06-20
First I would have installed Wine from the repositories but this is too late, I know...

What happens if you boot the computer and run ```
sudo apt-get update
``` and ```
sudo apt-get dist-upgrade
```? 

Please post the output in CODE tags.

---

### Post by firebelle on 2015-06-20
Thank you [COLOR=#000000]mörgæs for your response. It set me on the way to fix it. This is going to be a very long post because I'm going to post everything I did to fix it in case someone else ever needs it. 


I started off using the commands you suggested:

[/COLOR]```
sudo apt-get update
```
which updated the packages:
```

Ign http://ca.archive.ubuntu.com vivid InRelease
Ign http://security.ubuntu.com vivid-security InRelease
Ign http://ca.archive.ubuntu.com vivid-updates InRelease
Hit http://security.ubuntu.com vivid-security Release.gpg
Ign http://ca.archive.ubuntu.com vivid-backports InRelease
Hit http://security.ubuntu.com vivid-security Release
Hit http://ca.archive.ubuntu.com vivid Release.gpg
Get:1 http://ca.archive.ubuntu.com vivid-updates Release.gpg [933 B]
Hit http://ca.archive.ubuntu.com vivid-backports Release.gpg
Hit http://ca.archive.ubuntu.com vivid Release
Hit http://security.ubuntu.com vivid-security/main Sources           
Get:2 http://ca.archive.ubuntu.com vivid-updates Release [63.5 kB]   
Hit http://security.ubuntu.com vivid-security/restricted Sources       
Hit http://security.ubuntu.com vivid-security/universe Sources           
Hit http://ca.archive.ubuntu.com vivid-backports Release      
Hit http://security.ubuntu.com vivid-security/multiverse Sources               
Hit http://ca.archive.ubuntu.com vivid/main Sources                            
Hit http://security.ubuntu.com vivid-security/main amd64 Packages              
Hit http://ca.archive.ubuntu.com vivid/restricted Sources     
Hit http://security.ubuntu.com vivid-security/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com vivid/universe Sources
Hit http://security.ubuntu.com vivid-security/universe amd64 Packages
Hit http://ca.archive.ubuntu.com vivid/multiverse Sources
Hit http://security.ubuntu.com vivid-security/multiverse amd64 Packages
Hit http://ca.archive.ubuntu.com vivid/main amd64 Packages
Hit http://security.ubuntu.com vivid-security/main Translation-en
Hit http://security.ubuntu.com vivid-security/multiverse Translation-en
Hit http://ca.archive.ubuntu.com vivid/restricted amd64 Packages
Hit http://security.ubuntu.com vivid-security/restricted Translation-en
Hit http://ca.archive.ubuntu.com vivid/universe amd64 Packages
Hit http://security.ubuntu.com vivid-security/universe Translation-en
Hit http://ca.archive.ubuntu.com vivid/multiverse amd64 Packages
Hit http://ca.archive.ubuntu.com vivid/main Translation-en_CA
Hit http://ca.archive.ubuntu.com vivid/main Translation-en
Hit http://ca.archive.ubuntu.com vivid/multiverse Translation-en
Hit http://ca.archive.ubuntu.com vivid/restricted Translation-en
Hit http://ca.archive.ubuntu.com vivid/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com vivid/universe Translation-en
Get:3 http://ca.archive.ubuntu.com vivid-updates/main Sources [44.0 kB]
Get:4 http://ca.archive.ubuntu.com vivid-updates/restricted Sources [28 B]
Get:5 http://ca.archive.ubuntu.com vivid-updates/universe Sources [22.0 kB]
Get:6 http://ca.archive.ubuntu.com vivid-updates/multiverse Sources [1,964 B]
Get:7 http://ca.archive.ubuntu.com vivid-updates/main amd64 Packages [114 kB]
Get:8 http://ca.archive.ubuntu.com vivid-updates/restricted amd64 Packages [28 B]
Get:9 http://ca.archive.ubuntu.com vivid-updates/universe amd64 Packages [68.4 kB]
Get:10 http://ca.archive.ubuntu.com vivid-updates/multiverse amd64 Packages [3,494 B]
Get:11 http://ca.archive.ubuntu.com vivid-updates/main Translation-en [57.0 kB]
Hit http://ca.archive.ubuntu.com vivid-updates/multiverse Translation-en  
Hit http://ca.archive.ubuntu.com vivid-updates/restricted Translation-en
Get:12 http://ca.archive.ubuntu.com vivid-updates/universe Translation-en [37.3 kB]
Hit http://ca.archive.ubuntu.com vivid-backports/main Sources             
Hit http://ca.archive.ubuntu.com vivid-backports/restricted Sources
Hit http://ca.archive.ubuntu.com vivid-backports/universe Sources
Hit http://ca.archive.ubuntu.com vivid-backports/multiverse Sources
Hit http://ca.archive.ubuntu.com vivid-backports/main amd64 Packages
Hit http://ca.archive.ubuntu.com vivid-backports/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com vivid-backports/universe amd64 Packages
Hit http://ca.archive.ubuntu.com vivid-backports/multiverse amd64 Packages
Hit http://ca.archive.ubuntu.com vivid-backports/main Translation-en
Hit http://ca.archive.ubuntu.com vivid-backports/multiverse Translation-en
Hit http://ca.archive.ubuntu.com vivid-backports/restricted Translation-en
Hit http://ca.archive.ubuntu.com vivid-backports/universe Translation-en
Fetched 412 kB in 4s (95.9 kB/s)
Reading package lists... Done

```


Then did as you suggested:


```
sudo apt-get dist-upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 wine1.6 : Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu8) but it is not installable
E: Unmet dependencies. Try using -f.

```


So then I tried: 


```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  fonts-horai-umefont fonts-unfonts-core fonts-wqy-microhei
  gnome-exe-thumbnailer icoutils libcapi20-3 libgif4 libodbc1 libosmesa6
  libwine-development linux-headers-3.19.0-15 linux-headers-3.19.0-15-generic
  linux-headers-generic linux-image-3.19.0-15-generic
  linux-image-extra-3.19.0-15-generic linux-image-generic odbcinst
  odbcinst1debian2 p7zip thermald ttf-wqy-microhei unixodbc wine-development
  wine-gecko2.21 wine-mono0.0.8 wine64-development winetricks
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libwine-development wine-development wine64-development
Suggested packages:
  wine64-development-preloader
Recommended packages:
  libwine-gecko-2.24 wine32-development
The following packages will be REMOVED:
  playonlinux wine wine1.6 wine1.6-amd64
The following NEW packages will be installed:
  libwine-development wine-development wine64-development
0 upgraded, 3 newly installed, 4 to remove and 7 not upgraded.
Need to get 18.7 MB of archives.
After this operation, 4,914 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ vivid/universe libwine-development amd64 1.7.29-4 [18.6 MB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ vivid/universe wine64-development amd64 1.7.29-4 [4,518 B]                                                                                    
Get:3 http://ca.archive.ubuntu.com/ubuntu/ vivid/universe wine-development amd64 1.7.29-4 [22.2 kB]                                                                                      
Fetched 18.7 MB in 8s (2,269 kB/s)                                                                                                                                                       
dpkg: error: configuration error: /etc/dpkg/dpkg.cfg.d/multiarch:1: unknown option 'foreign-architecture'
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

so then I did:

```
ls /etc/dpkg/dpkg.cfg.d/
multiarch
```

And at that point I reversed what I did previously with:

```
sudo rm /etc/dpkg/dpkg.cfg.d/multiarch
```

and reran:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

The Brokencount >0 error went away and everything seems find now. I think if I uninstall playonlinux and wine I should be able to start over again but this time just installing from the repositories and not following the PlayonLinux instructions. 


Thank  you -- please let me know if I need to tag anything differently in this post or change it in some way to be useful to others.

---

### Post by mörgæs on 2015-06-21
> **firebelle said:**
> please let me know if I need to tag anything differently in this post or change it in some way to be useful to others.

Marking it SOLVED is fine. Thanks for thinking of future readers.

When the system has been stable for some days you could run the autoremove command as shown in the output above.

---

