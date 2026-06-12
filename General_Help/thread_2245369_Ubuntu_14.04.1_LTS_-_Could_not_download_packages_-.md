---
title: "Ubuntu 14.04.1 LTS - Could not download packages - Muon Package Manager"
date: 2014-09-23
forum: General Help
---

### Post by ronnie-vc10 on 2014-09-23
*[SIZE=4][SIZE=4]Hello, my desktop pc is ´successfully´ running Ubuntu 14.04.1 LTS. During downloading regular updates for [/SIZE][/SIZE]*[SIZE=4]*[SIZE=4]Muon Package Manager, got the following message:-[/SIZE]*[B]

Could not download packages[/B][/SIZE]

 

 cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/dists/precise/main/binary-amd64/Packages  

 

 Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/dists/precise/restricted/binary-amd64/Packages  

 

 Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/dists/precise/main/binary-i386/Packages  
 

 Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/dists/precise/restricted/binary-i386/Packages  

[SIZE=4][SIZE=4] [I]i) What is the function of the above?

ii) Do I use the Terminal, and just type apt-cdrom...or do I have to do some other [/I][/SIZE][/SIZE]*?*

---

### Post by ibjsb4 on 2014-09-23
Open your software-sources from your menu or open it from terminal:
```
software-properties-kde
```
And uncheck CD/DVD-rom, then update.
Should be good to go :)

---

### Post by ronnie-vc10 on 2014-09-23
> **ibjsb4 said:**
> Open your software-sources from your menu or open it from terminal:
```
software-properties-kde
```
And uncheck CD/DVD-rom, then update.
Should be good to go :)

  	 	 	 	   Hello I used terminal as suggested. I could not find your ref ¨uncheck CD/DVD-rom, then update¨.
 

 My pc does not have a CDROM/DVD drive installed.
 

 Anyway, I tried above, but still getting same message: ¨Could not download packages¨?

---

### Post by Bashing-om on 2014-09-23
ronnie-vc10; Hey;

We can do this the old fashioned way, and directly edit the sources.list file.
Post back -Between Code Tags- the output of terminal command;
```

cat -n /etc/apt/sources.list

``` and we will direct your attention to the line that should be "commented" out.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

