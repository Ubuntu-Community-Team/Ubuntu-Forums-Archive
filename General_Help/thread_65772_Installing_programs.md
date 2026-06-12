---
title: "Installing programs?"
date: 2005-09-15
forum: General Help
---

### Post by 68Firebird on 2005-09-15
Ok I know this is probably a noob question but I very new to linux and my head is already hurting me, lol. I am trying to intall java and flash into firefox. I went to the Ubuntu guide and it says, "General Notes

   1. This is an Unofficial Ubuntu 5.04 Starter Guide. It is not associated with Ubuntu and Canonical Ltd.
   2. Guide is tested on a full installation of the Ubuntu 5.04 x86 Install CD (Hoary Hedgehog)
   3. If you see black box, means you have to execute the commands in Terminal mode (Applications -> System Tools -> Terminal)
   4. To reduce typo mistakes, copy and paste the commands into Terminal mode (right click on the commands -> "Copy" or "Paste")"

I downloaded java and flash to my desk top and when I type the above commands for the program in black into Terminal I get a error saying cant find file. What am I doing wrong????

---

### Post by 68Firebird on 2005-09-15
Ok I must be a idiot or something cause I cannot get anything I try to install to install. I keep getting messages like this in Terminal,

steven@antecireliveSTEVE:~$ sudo apt-get install gnome-vlc
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gnome-vlc
steven@antecireliveSTEVE:~$

steven@antecireliveSTEVE:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
steven@antecireliveSTEVE:~$ java -version

steven@antecireliveSTEVE:~$ sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
steven@antecireliveSTEVE:~$


Good Lord, I just want to install some simple programs. What does it take to get programs to install??????? This is enough to drive me back to windows in a hurry. I am reading the guides till my eyes bleed and its just not helping. Someone explain to me. Treat me like I am a moron. I don't care. Just do it in terms I can understand.

---

### Post by myha on 2005-09-15
Do you have extra repository?
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by 68Firebird on 2005-09-15
[QUOTE=myha]Do you have extra repository?
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)[/QUOTE]

Yes. I was looking at that but I do not understand what the heck I am supposed to do with any of that infomation. Its all chinese to me.

# Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

What am I supposed to do with any of this info?? I have no idea??? Damn I must be a moron I don't know.

---

### Post by 68Firebird on 2005-09-15
[QUOTE=68Firebird]Yes. I was looking at that but I do not understand what the heck I am supposed to do with any of that infomation. Its all chinese to me.[/QUOTE]
# Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

What am I supposed to do with any of this info?? I have no idea??? Damn I must be a moron I don't know.

---

### Post by myha on 2005-09-15
Well...
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` 
This makes a backup of your default list of sources, which are placed in the /etc/apt/ directory, filename is sources.list
```
sudo gedit /etc/apt/sources.list
``` 
With this you edit sources.list in /etc/apt/ directory with text editor for gnome.
And than u simply copy code from guide and replace the part with the new code, as described in guide.
Save it and exit.
```
sudo apt-get update
``` 
Do this so apt-get will be aware of the new repositories....
And thats it!

Regards, Miha

---

### Post by myha on 2005-09-15
[QUOTE=68Firebird]Yes. I was looking at that but I do not understand what the heck I am supposed to do with any of that infomation. Its all chinese to me.

What am I supposed to do with any of this info?? I have no idea??? Damn I must be a moron I don't know.[/QUOTE]
You dont have to do anything with this, exept to find described section in sources.list and replace it with the new lines from guide.

---

### Post by 68Firebird on 2005-09-15
ahh, lol. I told you I was a moron. Now I understand what that info is. It just was not registering in my brain. 
Ok I followed the directions and got jre and flash installed. Jre runs correctly. Now I can play yahoo games. 
But still having a problem with flash. I got it to install. But My yahoo dsl home page is not displaying flash correctly in FF. Its sort of half assed working. It works with FF in windows. So I dont know what the problem is yet in Ubuntu. Any ideas??

Thanks for your patience with me.  :)

---

### Post by myha on 2005-09-15
Im happy you managed to install it...

About flash I dont know what is wrong, im pretty new to linux also and have only the base knowledge... So someone else will have to help you on this...

Regards,
Miha

---

