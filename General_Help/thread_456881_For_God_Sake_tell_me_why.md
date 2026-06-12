---
title: "For God Sake tell me why"
date: 2007-05-28
forum: General Help
---

### Post by gozalo on 2007-05-28
I don;t know if this is the right place to post this, but I have installed ubuntu from wubi so...?! 

anyway, my problem is about the font.. I have noitced that the font here is diff. than it;s in windows, do i have to install something or something to make the font looks like what it's on windows?? 

The font in one of the sites I checked is Tahoma but when using Ubuntu it looks like if it's another font, the same thing with "Times New Roman" 

any idea?

---

### Post by ArieT on 2007-05-28
Install msttcorefonts (with sudo apt-get install msttcorefonts ) and if this doesn't help ask your question in 'Absolute Beginner Talk'.

---

### Post by Sushubh on 2007-05-28
try installing fonts through automatix. most windows fonts are installed that ways.

---

### Post by gozalo on 2007-05-29
ArieT
Sushubh

Thank You Very Much

BUT, excuse my ignorance, how can I install it? from where? link plz?

Thanx again

---

### Post by Sushubh on 2007-05-29
umm. it's not the recommended way to do it coz ubuntu officially does not support automatrix.

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by DougieFresh4U on 2007-05-29
> **ArieT said:**
> Install msttcorefonts (with sudo apt-get install msttcorefonts ) and if this doesn't help ask your question in 'Absolute Beginner Talk'.

Isn't msttcorefonts in Synaptic Package Manager?
I see it in my Synaptic Package Manager

---

### Post by gozalo on 2007-05-29
I googled and found this [http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html](http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html)

 so i typed this in the terminal

sudo aptitude install msttcorefonts 

and got this msg
```

E: Type '&#8220;deb' is not known on line 46 in source list /etc/apt/sources.list
E: The list of sources could not be read.
```

---

### Post by gozalo on 2007-05-29
> **Sushubh said:**
> umm. it's not the recommended way to do it coz ubuntu officially does not support automatrix.

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
done and the result is

&#8220;deb' is not known on line 46 in source list /etc/apt/sources.list
gozalo@ubuntu:~$ sudo apt-get install automatix2
E: Type '&#8220;deb' is not known on line 46 in source list /etc/apt/sources.list
E: The list of sources could not be read.

---

### Post by gozalo on 2007-05-29
I think i messed up with the terminal coz when i try to open the Synaptic Package Manager i got this error msg

E: Type '&#8220;deb' is not known on line 46 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

[http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html](http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html)

---

### Post by ago on 2007-05-29
You probably edited /etc/apt/sources.list and it's now not correct. Post it here and we will correct it.

---

### Post by gozalo on 2007-05-29
> **ago said:**
> You probably edited /etc/apt/sources.list and it's now not correct. Post it here and we will correct it.
where can i find it? 

ps:if u wanna help me u have to be paient coz i'm the clueless-est techno. ever.

all what I was doing is searching, geting codes, copying it and pasting it in the terminal..

---

### Post by ago on 2007-05-29
sudo gedit /etc/apt/sources.list

---

### Post by xtang on 2007-05-29
something like this?

[http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

---

### Post by gozalo on 2007-05-29
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main&#8221;
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main&#8221;
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

---

### Post by gozalo on 2007-05-29
> **xtang said:**
> something like this?

[http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)
Good morning!! ):P yes something like that

but i wont try it now, let me first correct the list 

thank you

---

### Post by ago on 2007-05-29
```

# &#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main&#8221;
# &#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main&#8221;
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
```

---

### Post by gozalo on 2007-05-29
removed it!!

THANK YOU really thanx alot ago :)

---

### Post by gozalo on 2007-05-29
ok now about the font what should i do?

xtang: it didnt work for me i got this msg

khawlah@ubuntu:~$ sudo apt-get install msttcorefonts
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
khawlah@ubuntu:~$ sudo tar xvjpf fontconfig.tbz -C /etc/fonts/
tar: fontconfig.tbz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
khawlah@ubuntu:~$ 

:confused:

---

### Post by DougieFresh4U on 2007-05-29
Have you looked in Synaptic for msttcorefonts? I don't know how, but it's in both my Feisty & Gutsy machines

---

### Post by ago on 2007-05-29
> **gozalo said:**
> 
khawlah@ubuntu:~$ sudo tar xvjpf fontconfig.tbz -C /etc/fonts/
tar: fontconfig.tbz: Cannot open: No such file or directory


You have to download the fontconfig.tbz file first then run the above command

---

### Post by gozalo on 2007-05-29
> **DougieFresh4U said:**
> Have you looked in Synaptic for msttcorefonts? I don't know how, but it's in both my Feisty & Gutsy machines
hmmm i think it's there, i reinstalled it.. but cant see any changes

---

### Post by DougieFresh4U on 2007-05-29
> **gozalo said:**
> hmmm i think it's there, i reinstalled it.. but cant see any changes

Funny thing is, I have it installed , but I don't know where to find and/or use :confused:

---

### Post by gozalo on 2007-05-29
i downloaded both and still getting the same msg

downloaded from here [http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

---

### Post by gozalo on 2007-05-29
> **DougieFresh4U said:**
> Funny thing is, I have it installed , but I don't know where to find and/or use :confused:
system -> Administration -> Synaptic Package Manager 
you will find it there, but how to use it? I have no idea :d

---

### Post by gozalo on 2007-05-30
```
khawlah@ubuntu:~$ sudo apt-get install msttcorefonts
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
khawlah@ubuntu:~$ sudo tar xvjpf fontconfig.tbz -C /etc/fonts/
tar: fontconfig.tbz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
khawlah@ubuntu:~$ sudo apt-get install msfonts.tbz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package msfonts.tbz

 
```

msfonts.tbz is on my desktop
fontconfig.tbz also on my desktop
so why i'm getting this msg? do I have to do something before typing the command in the terminal?

---

### Post by minhmeoke on 2007-05-30
> msfonts.tbz is on my desktop
fontconfig.tbz also on my desktop
so why i'm getting this msg? do I have to do something before typing the command in the terminal?
When you run the command "sudo tar xvjpf fontconfig.tbz -C /etc/fonts/", you get the error message "fontconfig.tbz: Cannot open: No such file or directory" because it expects the files to be in your home directory, but they are actually in the Desktop directory. Open up a terminal, and change your directory to your Desktop so it can see the files using the following command:
```
cd ~/Desktop
```
Your prompt should now look like "khawlah@ubuntu:~/Desktop$". Now you can run this command to extract the actual font files to the /etc/fonts/ directory:
```
sudo tar xvjpf fontconfig.tbz -C /etc/fonts/
```

> "E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"
The solution to this problem is usually to turn off the Synaptic Package Manager, or any other package manager you may be using (ie Adept) before you apt-get something in the terminal.

Hope that helps.

---

### Post by gozalo on 2007-05-31
how can I change it to desktop? step by step plz

thank you minhmeoke :-)

---

### Post by gozalo on 2007-05-31
okay done

i'll log out now to check

---

### Post by gozalo on 2007-05-31
okay the font have change but still not like the one in Windows XP

```

khawlah@ubuntu:~$ cd Desktop
khawlah@ubuntu:~/Desktop$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
khawlah@ubuntu:~/Desktop$ sudo aptitude install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
khawlah@ubuntu:~/Desktop$ 



```
what's 0B and how can i get of arcives?

---

### Post by gozalo on 2007-05-31
Do I have to do something with the files on my desktop (msfonts.tbz and fontconfig.tbz) ? extract?

---

### Post by minhmeoke on 2007-05-31
> msttcorefonts is already the newest version.
Ok, this means that you've successfully installed the msttcorefonts package, which can handle MS font files. However, you still need to extract the font files themselves. Extract the contents of fontconfig.tbz to /etc/fonts/ using the following steps (I am assuming that the fontconfig.tbz is on your Desktop):

Open up a terminal, and change your directory to your Desktop so it can see the files using this command:
```
cd ~/Desktop
```

Your prompt should now look like "khawlah@ubuntu:~/Desktop$". Now you can run this command to extract the actual font files to the /etc/fonts/ directory:
```
sudo tar xvjpf fontconfig.tbz -C /etc/fonts/
```

Ok, now check to see if the files have been extracted correctly to the /etc/fonts/ directory by opening a file browser using the following command in the terminal:
```
nautilus /etc/fonts/ &
```

There should be files and folders visible in the file browser. Check for if the following 4 files are in the directory: alias.conf, local.conf, misc.conf, msfonts-rules.conf. They should have a blue square rotated 45 degrees as their icons. If you do not see them, then redownload the files from [**here**]("http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz"), and repeat the steps that I have just listed.

Ok, now log out, and log back in. The fonts on the menus, clock, and icons on your desktop should have changed, I think that the default is Arial. If you want something different as your default, go to the System menu (top-left corner of your Desktop), scroll down to Preferences, and then select Font, and change everything to your heart's content. If you still cannot get it to work, come back, and I'll try to walk you through another way to change the fonts.

---

### Post by gozalo on 2007-06-01
Minhmeoke Thanx alot

it worked but for the English fonts only (most of), however, the arabic font still not like the one in Windows XP. I'm confused coz the font i'm talking about is "tahoma" and  I can see the tahoma.tt in the list of MSfonts.tbz but it does not appear here..

and I did the same steps you gave me above for the msfonts, I extracted to the /etc/fonts/ directory and checked if it was there and then i logged out but still no changes..

---

### Post by minhmeoke on 2007-06-01
It seems that there is a bug with the Tahoma font in the msttcorefonts package.
The bug report is: [https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/50529]("https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/50529")
Someone attempted to fix it, but it is still problematic: [http://ubuntuforums.org/showthread.php?t=431063]("http://ubuntuforums.org/showthread.php?t=431063")

As a result, I think that a better solution would be installing the TrueType msfonts.tbz, made by the GNU/Linux community. Although they might slightly different from the fonts you have in Windows, since they are not made by Microsoft, they should be very similar to XP's Tahoma. I am assuming that you downloaded msfonts.tbz onto your desktop.

1) Open a terminal.

2) Remove the 4 files that you extracted from fontconfig.tbz by entering the following:
```
sudo rm /etc/fonts/alias.conf
sudo rm /etc/fonts/local.conf
sudo rm /etc/fonts/misc.conf
sudo rm /etc/fonts/msfonts-rules.conf
```

2) Change the directory to Desktop:
```
cd ~/Desktop
```

3) Extract the files:
```
sudo tar xvjpf msfonts.tbz -C /usr/share/fonts/truetype/
```

4) Log out, then log back in.

5) In the menu on the top-left, go to System > Preferences > Font, and then change the fonts to Tahoma.

I tried it in English, and didn't find any errors; hopefully it will work in Arabic too. Good Luck!

---

### Post by gozalo on 2007-06-01
Minhmeoke thanx alot
it's working, I didnt do step 5, I can see the tahoma now, it's not like the one in windows (this one is bold) but at least it's there.. the english fonts have change now, it was better before, but it's okay.. 

Thanx again, apprecaited really :)

---

