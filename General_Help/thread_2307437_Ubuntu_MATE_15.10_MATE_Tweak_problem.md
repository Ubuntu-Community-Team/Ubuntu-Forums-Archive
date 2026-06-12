---
title: "Ubuntu MATE 15.10 MATE Tweak problem"
date: 2015-12-24
forum: General Help
---

### Post by timmy8 on 2015-12-24
I can't open MATE Tweak Tool with the "Vertex Icons" Why is this and issue in Ubuntu MATE? I don't see why this is a problem to use Tweak tool

Here's what i get in termainal

mate-tweak
Window Manager is: marco
Traceback (most recent call last):
  File "/usr/bin/mate-tweak", line 815, in <module>
    MateTweak()
  File "/usr/bin/mate-tweak", line 669, in __init__
    img = theme.load_icon(sidePage.icon, 36, 0)
GLib.Error: gtk-icon-theme-error-quark: Icon 'preferences-system-windows' not present in theme Vertex-Icons (0)


If anybody can help me to fix this. Thank you

---

### Post by QDR06VV9 on 2015-12-25
Hi timmy8
I have no problems with the "Vertex Icons" and using Mate-Tweak.
I am not sure how you installed them and be aware these are still in Beta Stage.


> Note: This is an unfinished beta version. It may not work as expected in some cases.

So that said my install method was as follows..


```
git clone git://github.com/horst3180/Vertex-Icons.git --depth 1

```

Then I copied the New "Vertex Icons" that was in my home directory to .icons also in my home directory and no issues here.
If you feel this is a bug 


> Bug reporting
If you find a bug, please report it at github.
 [https://github.com/horst3180/Vertex-icons/issues](https://github.com/horst3180/Vertex-icons/issues)

You might be lacking the Theme engine that is needed by the system.
See this  [http://www.noobslab.com/2015/04/ceti-vertex-are-perfect-themes-for-your.html](http://www.noobslab.com/2015/04/ceti-vertex-are-perfect-themes-for-your.html)
 To install you will need his PPA installed
```
sudo add-apt-repository ppa:noobslab/themes
sudo apt-get update
sudo apt-get install vertex-theme

```

Good Luck && Kind Regards

---

### Post by timmy8 on 2015-12-25
> **runrickus said:**
> Hi timmy8
I have no problems with the "Vertex Icons" and using Mate-Tweak.
I am not sure how you installed them and be aware these are still in Beta Stage.



So that said my install method was as follows..


```
git clone git://github.com/horst3180/Vertex-Icons.git --depth 1

```

Then I copied the New "Vertex Icons" that was in my home directory to .icons also in my home directory and no issues here.
If you feel this is a bug 


You might be lacking the Theme engine that is needed by the system.
See this  [http://www.noobslab.com/2015/04/ceti-vertex-are-perfect-themes-for-your.html](http://www.noobslab.com/2015/04/ceti-vertex-are-perfect-themes-for-your.html)
 To install you will need his PPA installed
```
sudo add-apt-repository ppa:noobslab/themes
sudo apt-get update
sudo apt-get install vertex-theme

```

Good Luck && Kind Regards


Thanks runrickus. That where i got the icons from  is git i just downloaded theme and put theme in .icons also but no luck  still?   I also tried that noobslab ppa for the vertex-theme. But the  last command did not install in Ubuntu 15.10 I even tried to manually  put it in .themes in my home folder and in /usr/share/themes  but that  one did not go in for some reason do not think that is completable with  Ubuntu 15.10 yet.


Still don't know why the icons would effect  that. The MATE Tweak tool still having problems so if you or anybody  else here on forum could help. DEVELOPER or somebody it would be great  thank you

Happy holidays to you guys on Ubuntu

---

### Post by QDR06VV9 on 2015-12-25
@timmy8 I sent the link with it so that you would hopefully pick up on the Version of that PPA Vivid(15.04)
So for that ppa to install the needed GTK Theme, and by the way the focus of the author was for Gnome but I find no Quirks using them on Trusty(14.04)MATE
So long story short you will have to **edit your /etc/apt/sources.list** and edit the [B]ppa:noobslab/themes to vivid.
[/B]So Now they read like this
> [COLOR=#333333]deb [/COLOR][http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu)[COLOR=#333333] [/COLOR][COLOR=#333333]wily[/COLOR][COLOR=#333333] main 
[/COLOR][COLOR=#333333]deb-src [/COLOR][http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu)[COLOR=#333333] [/COLOR][COLOR=#333333]wily[/COLOR][COLOR=#333333] main [/COLOR]

Then update
```
sudo apt-get update 

```



Followed by 
```
sudo apt-get install vertex-theme

```
Now You need to note Vivid will [B]fall out of support in January 2016.
[/B]He should have his PPA updated for Wily by then..
Regards
**EDIT:the **[COLOR=#000000]**DEVELOPERS usually do not hang out here in the forums** but his link is attached in the link that sent in my first post. 
and very few will help with problems like this so be nice when or if you contact him..[/COLOR]

---

### Post by v3.xx on 2015-12-26
Installed as per runrickus (git) and seem to work ok in 16.04 also.

[ATTACH=CONFIG]266383[/ATTACH]

---

### Post by timmy8 on 2015-12-26
> **runrickus said:**
> @timmy8 I sent the link with it so that you would hopefully pick up on the Version of that PPA Vivid(15.04)
So for that ppa to install the needed GTK Theme, and by the way the focus of the author was for Gnome but I find no Quirks using them on Trusty(14.04)MATE
So long story short you will have to **edit your /etc/apt/sources.list** and edit the [B]ppa:noobslab/themes to vivid.
[/B]So Now they read like this


Then update
```
sudo apt-get update 

```



Followed by 
```
sudo apt-get install vertex-theme

```
Now You need to note Vivid will [B]fall out of support in January 2016.
[/B]He should have his PPA updated for Wily by then..
Regards
**EDIT:the **[COLOR=#000000]**DEVELOPERS usually do not hang out here in the forums** but his link is attached in the link that sent in my first post. 
and very few will help with problems like this so be nice when or if you contact him..[/COLOR]

I I'm using Ubuntu 15.10 MATE not 15.04 vivid not 14.04. So what would you like me to try your post wasn't clear to me I did not understand

---

### Post by QDR06VV9 on 2015-12-26
[COLOR=#000000]I know what Version you are using[/COLOR];)[COLOR=#000000]
So long story short you will have to [/COLOR][B]edit your /etc/apt/sources.list and edit the [B]ppa:noobslab/themes to vivid.
So Now they read like this
[/B][/B]> [B][I][COLOR=#333333]deb [/COLOR][http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) vivid[COLOR=#333333] main 
[/COLOR][COLOR=#333333]deb-src [/COLOR][http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) vivid[COLOR=#333333] main[/COLOR][/I]
[/B]To do this open terminal
```
gksudo gedit  /etc/apt/sources.list
```
And copy theese two lines in place of the wily lines
> [B][I][COLOR=#333333]deb [/COLOR][http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) vivid[COLOR=#333333] main 
[/COLOR][COLOR=#333333]deb-src [/COLOR][http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) vivid[COLOR=#333333] main[/COLOR][/I][/B]
Close and Save..And then update and install
```
sudo apt-get update
sudo apt-get install vertex-theme

```

---

### Post by timmy8 on 2015-12-26
What would you like me to do. I do not see noobslab in here


```
# deb cdrom:[Ubuntu-MATE 15.10 _Wily Werewolf_ - Release amd64 (20151021)]/ wily main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ wily main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ wily main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ wily universe
deb-src http://us.archive.ubuntu.com/ubuntu/ wily universe
deb http://us.archive.ubuntu.com/ubuntu/ wily-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ wily multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ wily multiverse
deb http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu wily-security main restricted
deb-src http://security.ubuntu.com/ubuntu wily-security main restricted
deb http://security.ubuntu.com/ubuntu wily-security universe
deb-src http://security.ubuntu.com/ubuntu wily-security universe
deb http://security.ubuntu.com/ubuntu wily-security multiverse
deb-src http://security.ubuntu.com/ubuntu wily-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu wily partner
# deb-src http://archive.canonical.com/ubuntu wily partner
```

---

### Post by timmy8 on 2015-12-26
Never mind ](*,) i found it was in /etc/apt/sources.list.d/noobslab-ubuntu-themes-wily.list

So i just blocked the wily ones like this ##  and added the vivid two you gave me. Then updated and it installed now! Now going to check to see if its in the Themes in MATE which should be now

So all i have to do is going to noobs lab is check the ppa if it says wily then i just block the vivid ones and use the wily ppa's to install stuff if used vice versa 

Thanks i will let you know if it fixed my problem):P

---

### Post by timmy8 on 2015-12-26
OK i still get the same output in terminal. Tweak tool is still not opening. Vertex themes are installed

Window Manager is: marco
Traceback (most recent call last):
  File "/usr/bin/mate-tweak", line 815, in <module>
    MateTweak()
  File "/usr/bin/mate-tweak", line 669, in __init__
    img = theme.load_icon(sidePage.icon, 36, 0)
GLib.Error: gtk-icon-theme-error-quark: Icon 'preferences-system-windows' not present in theme Vertex-Icons (0)

---

### Post by QDR06VV9 on 2015-12-26
I am lost as to what is wrong here??
The only thing more I can offer here is to uninstall 'mate-tweak' and reinstall it.  
```
sudo apt-get --purge remove mate-tweak
```
The above command will remove it and all global (i.e., systemwide) configuration files.
Maybe even a restart of the computer.
Then reinstall 'mate-tweak'
```
sudo apt-get install mate-tweak

```
I do not know why you are getting that error, I have them installed on Trusty(14.04) Wily(15.10) Xenial(16.04) and Arch Mate..

---

### Post by timmy8 on 2015-12-26
I figured it out =d>

Had to change this in the vertex-icons. In the index-theme

```

[Icon Theme] Name=Vertex-Icons Inherits=Moka,gnome,hicolor Comment=Vertex Icon theme

```

since i didn't have Moka it was reverting to gnome. and my gnome icons are broken shows a little paper in MATE icons preview. So i think that the problem right if it shows paper not the image right

So i simple changed it to this

```

[Icon Theme] Name=Vertex-Icons Inherits=mate,gnome,hicolor Comment=Vertex Icon theme

```

And now the MATE tweak open up.

I'm just curious now what happened to my gnome icons now

---

### Post by timmy8 on 2015-12-26
My gnome icons are fixed now and my adwaita icons are fixed now. It was simple missing packages from the gnome icon set. After i installed gnome icons colors full and adwaita icons full in package manager it was fixed. So now everything is fixed now :guitar:

---

