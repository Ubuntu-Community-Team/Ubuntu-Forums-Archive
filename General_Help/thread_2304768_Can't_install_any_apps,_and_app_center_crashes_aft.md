---
title: "Can't install any apps, and app center crashes after attempting theme install"
date: 2015-11-29
forum: General Help
---

### Post by petergriffin011 on 2015-11-29
[COLOR=#111111][FONT=Ubuntu]I just installed Ubuntu alongside windows 10 yesterday. Everything was fine until I tried following some instructions to download the Arch theme via terminal. After this, the Ubuntu App Center crashes (App grid works but I can't install anything because the error shows up). The following is the error I'm met with which I typed as shown in my notifications.
[I]
An error occurred, please run Package Manager from the right-click menu in apt-get in a terminal to see what is wrong.[/I]
***The error message was: 'Unknown error: ' (E:Malformed line 1 in source list/etc/apt/sources.list.d/arc-theme.list (URI))'.***
*This ususally means that your installed packages have unmet dependencies*

[/FONT][/COLOR]

---

### Post by CantankRus on 2015-11-29
Run this in terminal to show added sources...
```
find /etc/apt/sources.list.d -name \*.list | cut -f 5 -d '/' | sort
```

Also what Ubuntu release are you running....
```
lsb_release -r
```

---

### Post by petergriffin011 on 2015-11-29
Thanks CantankRus, I tried what you said and this is what I got:



atlanta-thinkpad@atlantathinkpad-ThinkPad-X220:~$ find /etc/apt/sources.list.d -name \*.list | cut -f 5 -d '/' | sort
appgrid-stable-wily.list
arc-theme.list
google-chrome.list
kilian-ubuntu-f_lux-wily.list
noobslab-ubuntu-themes-wily.list
atlanta-thinkpad@atlantathinkpad-ThinkPad-X220:~$ lsb_release -r
Release:    15.10
atlanta-thinkpad@atlantathinkpad-ThinkPad-X220:~$

---

### Post by CantankRus on 2015-11-29
Ok... you can just delete the arc-theme source you added via terminal....
```
sudo rm /etc/apt/sources.list.d/arc-theme.list
```

Then update sources...
```
sudo apt-get update
``` 

You can install and try the arc-theme by downloading a deb file directly from the repository.
Go [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://software.opensuse.org/download.html?project=home%3AHorst3180&package=arc-theme"), click on the Ubuntu logo and at the bottom of the page you will find a heading "**Grab binary packages directly**"

---

### Post by petergriffin011 on 2015-11-29
> **CantankRus said:**
> Ok... you can just delete the arc-theme source you added via terminal....
```
sudo rm /etc/apt/sources.list.d/arc-theme.list
```

Then update sources...
```
sudo apt-get update
``` 

You can install and try the arc-theme by downloading a deb file directly from the repository.
Go [**_[COLOR=#B22222]HERE[/COLOR]_**]("http://software.opensuse.org/download.html?project=home%3AHorst3180&package=arc-theme"), click on the Ubuntu logo and at the bottom of the page you will find a heading "**Grab binary packages directly**"



Thanks so much! That worked, although I had to get rid of the f.lux package with the format you gave me because that was causing problems with downloading updates. Now my computer works again!

---

### Post by CantankRus on 2015-11-30
Ok. Good.
Take care when copying and pasting commands.
eg on the above page I linked to there are 3 separate commands but they are spread over 4 lines.
The command that adds the arc-theme source repo is on lines 1 and 2 and should be pasted in the terminal as...
```
sudo sh -c "echo 'deb [COLOR="#FF0000"]http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10/[/COLOR] /' >> /etc/apt/sources.list.d/arc-theme.list"
```
[ATTACH=CONFIG]265846[/ATTACH]

This forum and others can automatically shorten long urls.
The link address is correct when clicked on, but if you highlight and copy, it will copy exactly what you see and therefore an invalid URI.

_Pasted in forum without code tags:_
sudo sh -c "echo 'deb [COLOR="#FF0000"][http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10/[/COLOR]](http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10/[/COLOR]) /' >> /etc/apt/sources.list.d/arc-theme.list"
sudo apt-get update
sudo apt-get install arc-theme

_Pasted  in forum with code tags:_
```
sudo sh -c "echo 'deb [COLOR="#FF0000"]http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.10/[/COLOR] /' >> /etc/apt/sources.list.d/arc-theme.list"
sudo apt-get update
sudo apt-get install arc-theme
```

---

