---
title: "my apt-get command won't install any app"
date: 2013-05-01
forum: General Help
---

### Post by phapmai on 2013-05-01
Hi, I'm completly new to ubuntu. I just started using it several days ago. I'm currently using ubuntu 13.04. Everything went fantastic so far, the only problem irritating me the most is that i cannot get the get-apt install to work. I tried to install this package 
[COLOR=#333333][FONT=arial]sudo add-apt-repository ppa:ferramroberto/gnome3[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]sudo apt-get update[/FONT][/COLOR]
[FONT=arial][COLOR=#333333]sudo apt-get install gnome-shell-extensions-user-theme[/COLOR][/FONT]

[FONT=arial][COLOR=#333333]I did updated after then use to install comand. However I alway ended up with this msg:[/COLOR][/FONT]
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
E: Unable to locate package gnome-shell-extensions-user-theme
daniel@daniel-System-Product-Name:~$ 

This happen to any app I try to install not just the shell-extensions-user-theme.
Any help would be appreciated. Thank you in advance

---

### Post by ibjsb4 on 2013-05-01
Im not seeing any 13.04 sources.

[https://launchpad.net/~ferramroberto/+archive/gnome3](https://launchpad.net/~ferramroberto/+archive/gnome3)

---

### Post by matt_symes on 2013-05-01
Hi

The quickest way to see what is going on with your system is to use the terminal. 

First, let's take a look at you sources. Open a terminal and type (copy copy and paste into the terminal).

```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

Copy and paste the output form the terminal into your next post by highlighting the text -> right click -> copy.

Please use code tags around the pasted text in you next post. The code tags button is the # button above where you type your reply.

After that, please post the output of

```
apt-cache search gnome-shell-extensions-user-theme
```

Finally post the output of

```
sudo apt-get install htop
```

htop is a lightweight system monitor. I'm more interested in seeing the output of the install command than htop itself.

Kind regards

---

### Post by JebusWankel on 2013-05-01
Go to Software Sources in Settings. From there you should be able to remove that PPA since it's not doing anything for you and check that the normal repositories are enabled. This won't reload them though so you'll have to run ```
sudo apt-get update
``` after you make changes.

---

### Post by phapmai on 2013-05-02
Hi [matt_symes]("http://ubuntuforums.org/member.php?u=1067998").THank you for reply. This is what i got for the source lists

```

/etc/apt/sources.list:5:deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring main restricted
/etc/apt/sources.list:6:deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring main restricted
/etc/apt/sources.list:10:deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring-updates main restricted
/etc/apt/sources.list:11:deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring-updates main restricted
/etc/apt/sources.list:16:deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring universe
/etc/apt/sources.list:17:deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring universe
/etc/apt/sources.list:18:deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring-updates universe
/etc/apt/sources.list:19:deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring-updates universe
/etc/apt/sources.list:26:deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring multiverse
/etc/apt/sources.list:27:deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring multiverse
/etc/apt/sources.list:28:deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring-updates multiverse
/etc/apt/sources.list:29:deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring-updates multiverse
/etc/apt/sources.list:36:deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring-backports main restricted universe multiverse
/etc/apt/sources.list:37:deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring-backports main restricted universe multiverse
/etc/apt/sources.list:39:deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring-security main restricted
/etc/apt/sources.list:40:deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring-security main restricted
/etc/apt/sources.list:41:deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring-security universe
/etc/apt/sources.list:42:deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring-security universe
/etc/apt/sources.list:43:deb [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring-security multiverse
/etc/apt/sources.list:44:deb-src [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) raring-security multiverse
/etc/apt/sources.list:55:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
/etc/apt/sources.list:56:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
/etc/apt/sources.list:57:deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
/etc/apt/sources.list:58:deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
/etc/apt/sources.list.d/ferramroberto-gnome3-raring.list:1:deb [http://ppa.launchpad.net/ferramroberto/gnome3/ubuntu](http://ppa.launchpad.net/ferramroberto/gnome3/ubuntu) raring main
/etc/apt/sources.list.d/ferramroberto-gnome3-raring.list.save:1:deb [http://ppa.launchpad.net/ferramroberto/gnome3/ubuntu](http://ppa.launchpad.net/ferramroberto/gnome3/ubuntu) raring main
/etc/apt/sources.list.d/folke-schwinning-personal-raring.list:1:deb [http://ppa.launchpad.net/folke-schwinning/personal/ubuntu](http://ppa.launchpad.net/folke-schwinning/personal/ubuntu) raring main
/etc/apt/sources.list.d/folke-schwinning-personal-raring.list.save:1:deb [http://ppa.launchpad.net/folke-schwinning/personal/ubuntu](http://ppa.launchpad.net/folke-schwinning/personal/ubuntu) raring main
/etc/apt/sources.list.d/freyja-dev-unity-tweak-tool-daily-raring.list:1:deb [http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu](http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu) raring main
/etc/apt/sources.list.d/freyja-dev-unity-tweak-tool-daily-raring.list.save:1:deb [http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu](http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu) raring main
/etc/apt/sources.list.d/gnome3-team-gnome3-raring.list:1:deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) raring main
/etc/apt/sources.list.d/gnome3-team-gnome3-raring.list.save:1:deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) raring main
/etc/apt/sources.list.d/medibuntu.list:2:deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) raring free non-free #Medibuntu - Ubuntu 13.04 "raring ringtail"
/etc/apt/sources.list.d/medibuntu.list.save:2:deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) raring free non-free #Medibuntu - Ubuntu 13.04 "raring ringtail"
/etc/apt/sources.list.d/noneed4anick-cuttlefish-raring.list:1:deb [http://ppa.launchpad.net/noneed4anick/cuttlefish/ubuntu](http://ppa.launchpad.net/noneed4anick/cuttlefish/ubuntu) raring main
/etc/apt/sources.list.d/noneed4anick-cuttlefish-raring.list.save:1:deb [http://ppa.launchpad.net/noneed4anick/cuttlefish/ubuntu](http://ppa.launchpad.net/noneed4anick/cuttlefish/ubuntu) raring main
/etc/apt/sources.list.d/ricotz-testing-raring.list:1:deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) raring main
/etc/apt/sources.list.d/ricotz-testing-raring.list.save:1:deb [http://ppa.launchpad.net/ricotz/testing/ubuntu](http://ppa.launchpad.net/ricotz/testing/ubuntu) raring main
/etc/apt/sources.list.d/tualatrix-ppa-raring.list:1:deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) raring main
/etc/apt/sources.list.d/tualatrix-ppa-raring.list.save:1:deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) raring main
/etc/apt/sources.list.d/webapps-preview-raring.list:1:deb [http://ppa.launchpad.net/webapps/preview/ubuntu](http://ppa.launchpad.net/webapps/preview/ubuntu) raring main
/etc/apt/sources.list.d/webapps-preview-raring.list.save:1:deb [http://ppa.launchpad.net/webapps/preview/ubuntu](http://ppa.launchpad.net/webapps/preview/ubuntu) raring main
/etc/apt/sources.list.d/webupd8team-gnome3-raring.list:1:deb [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu) raring main
/etc/apt/sources.list.d/webupd8team-gnome3-raring.list.save:1:deb [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu) raring main
/etc/apt/sources.list.d/webupd8team-java-raring.list:1:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) raring main
/etc/apt/sources.list.d/webupd8team-java-raring.list.save:1:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) raring main
/etc/apt/sources.list.d/xorg-edgers-ppa-raring.list:1:deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) raring main
/etc/apt/sources.list.d/xorg-edgers-ppa-raring.list.save:1:deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) raring main

```

After i inputed the code [FONT=Ubuntu Mono][COLOR=#000000]

[/COLOR][/FONT]```
[FONT=Ubuntu Mono][COLOR=#000000]apt-cache search gnome-shell-extensions-user-theme[/COLOR][/FONT]
[FONT=Ubuntu Mono][COLOR=#000000]it doesn't show anything.[/COLOR][/FONT]
```

[FONT=Ubuntu Mono][COLOR=#000000]And finally this is what i get for the following code: 

[/COLOR][/FONT]```
[FONT=Ubuntu Mono][COLOR=#000000]
[/COLOR][/FONT][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install htop
[/FONT][/COLOR]Reading package lists... Done
Building dependency tree       
Reading state information... Done
htop is already the newest version.
The following packages were automatically installed and are no longer required:
  libmozjs185-1.0 linux-image-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Thank you 
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by phapmai on 2013-05-02
Hi [JebusWankel]("http://ubuntuforums.org/member.php?u=150909"), Thank you for reply I already try to update using that command several times. that does not solve my problem though.

---

### Post by matt_symes on 2013-05-02
Hi

As ibjsb4 pointed out, there is no raring repo in that PPA at the moment.

The best thing you can do is to disable it. 

You can do this from the software center.

If you want to do it from the terminal, open one and then type (or copy and paste).

```
sudo sed -i 's/^/#/g' /etc/apt/sources.list.d/ferramroberto-gnome3-raring.list
```

You also have the same problem for these PPAs.

```
/etc/apt/sources.list.d/noneed4anick-cuttlefish-raring.list
/etc/apt/sources.list.d/webapps-preview-raring.list
```

After that

```
sudo apt-get update
```

Also there is some maintainence you can do. Removing unused packages.

```
sudo apt-get autoremove
```

Then try to install something.

Kind regards

---

### Post by ibjsb4 on 2013-05-02
Matt

I found a sacrificial PPA and did a  

sudo sed -i 's/^/#/g' /etc/apt/sources.list.d/ <package>

Didn't see any change :confused: 

What am I not seeing?  Thanks

---

### Post by matt_symes on 2013-05-02
Hi

> **ibjsb4 said:**
> Matt

I found a sacrificial PPA and did a  

sudo sed -i 's/^/#/g' /etc/apt/sources.list.d/ <package>

Didn't see any change :confused: 

What am I not seeing?  Thanks

I'm not sure why you did not see a change. What it should do is put a # infront of each line. Check this out...

```
matthew-S206:/home/matthew % cat tmp    
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu raring main
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu raring main
matthew-S206:/home/matthew % sed -i 's/^/#/g' tmp
matthew-S206:/home/matthew % cat tmp             
#deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu raring main
#deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu raring main
matthew-S206:/home/matthew % 
```

Kind regards

---

### Post by ibjsb4 on 2013-05-02
It did, it did :)  I was looking at the package and not sources.list.d, its hashed out.  Thanks

---

