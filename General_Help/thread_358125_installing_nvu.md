---
title: "installing nvu"
date: 2007-02-10
forum: General Help
---

### Post by simple_mind on 2007-02-10
I am a recent convert from Windows and noticed that installing programs in Ubuntu is a lot more involved than my previous OS. 

Could someone please give me some simple instructions on installing nvu? 

I have looked at some other guides for installing programs on Ubuntu, but I cannot follow all of what they are saying.

Thank you.

---

### Post by llamakc on 2007-02-10
Open a terminal.

Type:

sudo apt-get install nvu

---

### Post by Maestro23 on 2007-02-10
Nvu is available thru Synaptic. Enter your Synaptic thru GUI and search Nvu. OR

Command line:
#sudo aptitude nvu or 
#sudo apt-get nvu

These links are ones you should read: How-To's on Installing

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If you don't find Nvu, you might have to enable some extra Repositories: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Another helpful link for someone new: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Good luck. Remember, this Linux not Windows.  You must unlearn everything Windows. LOL

---

### Post by simple_mind on 2007-02-10
> **llamakc said:**
> Open a terminal.

Type:

sudo apt-get install nvu

Here is the terminal response after trying "apt-get install nvu"

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvu
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8574kB of archives.
After unpacking 27.1MB of additional disk space will be used.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe nvu 1.0final-2ubuntu2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/n/nvu/nvu_1.0final-2ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/n/nvu/nvu_1.0final-2ubuntu2_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by Maestro23 on 2007-02-10
> **simple_mind said:**
> Here is the terminal response after trying "apt-get install nvu"

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvu
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8574kB of archives.
After unpacking 27.1MB of additional disk space will be used.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe nvu 1.0final-2ubuntu2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/n/nvu/nvu_1.0final-2ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/n/nvu/nvu_1.0final-2ubuntu2_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

What does your /etc/apt/sources.list file look like?

#cat /etc/apt/sources.list

Post the results here for us.

---

### Post by simple_mind on 2007-02-10
> **Maestro23 said:**
> What does your /etc/apt/sources.list file look like?

#cat /etc/apt/sources.list

Post the results here for us.

How do I get these results for you? I do not know how to do that.

---

### Post by Maestro23 on 2007-02-10
> **simple_mind said:**
> How do I get these results for you? I do not know how to do that.

Open up a terminal.
Type:

> #cat /etc/apt/sources.list

Copy and paste(with your mouse) the results here.

---

### Post by simple_mind on 2007-02-10
> **Maestro23 said:**
> Open up a terminal.
Type:



Copy and paste(with your mouse) the results here.

I wrote what you asked for in the terminal but when I pressed enter nothing happened. It only displayed the same prompt:

home@EdgyEft:~$ #cat/etc/apt/sources.list
home@EdgyEft:~$

---

### Post by Maestro23 on 2007-02-10
> **simple_mind said:**
> I wrote what you asked for in the terminal but when I pressed enter nothing happened. It only displayed the same prompt:

home@EdgyEft:~$ #cat/etc/apt/sources.list
home@EdgyEft:~$

#cat(space in between) /etc/apt/sources.list

---

### Post by simple_mind on 2007-02-10
> **Maestro23 said:**
> #cat(space in between) /etc/apt/sources.list

home@EdgyEft:~$ #cat /etc/apt/sources.list
home@EdgyEft:~$

---

### Post by Maestro23 on 2007-02-10
> **simple_mind said:**
> home@EdgyEft:~$ #cat /etc/apt/sources.list
home@EdgyEft:~$

Confusing you, sorry. In the forums, whenever you see #(root) or $(normal user), this is the terminal prompt(no need to type it again in your terminal).

So for you, just type:

cat /etc/apt/sources.list

---

### Post by TheWizzard on 2007-02-10
> **simple_mind said:**
> home@EdgyEft:~$ #cat /etc/apt/sources.list
home@EdgyEft:~$
try
```
cat /etc/apt/sources.list
```

---

### Post by TheWizzard on 2007-02-10
> **Maestro23 said:**
> Confusing you, sorry. In the forums, whenever you see #, this is the command prompt(no need to type it again in your terminal).

So for you, just type:

cat /etc/apt/sources.list


the $ is for a normal prompt, # is for root

---

### Post by Maestro23 on 2007-02-10
> **TheWizzard said:**
> the $ is for a normal prompt, # is for root

Thanks for the correction.  Don't know what I was thinking.  One too-many Killian's Irish Reds today...:)

---

### Post by simple_mind on 2007-02-10
> **Maestro23 said:**
> Thanks for the correction.  Don't know what I was thinking.  One too-many Killian's Irish Reds today...:)

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by Maestro23 on 2007-02-10
> **simple_mind said:**
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe


## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[COLOR="Red"]# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
[/COLOR]
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

In a text editor (gedit, nano, vi, etc..) delete the # from the front of these 2 lines in red.  Save it.  

Ex: sudo nano /etc/apt/sources.list (This will open the file up in nano). Make the changes. Save it and exit.

Then
sudo apt-get update
sudo apt-get install nvu

---

### Post by llamakc on 2007-02-10
Make that last command:

sudo apt-get install nvu

---

### Post by simple_mind on 2007-02-10
> **Maestro23 said:**
> In a text editor (gedit, nano, vi, etc..) delete the # from the front of these 2 lines in red.  Save it.  

Ex: sudo nano /etc/apt/sources.list (This will open the file up in nano). Make the changes. Save it and exit.

Then
sudo apt-get update
sudo apt-get install nvu

I removed the two # symbols and then I tried installing again. This is the terminal response:

home@EdgyEft:~$ sudo apt-get install nvu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvu
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8574kB of archives.
After unpacking 27.1MB of additional disk space will be used.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe nvu 1.0final-2ubuntu2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/n/nvu/nvu_1.0final-2ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/n/nvu/nvu_1.0final-2ubuntu2_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
home@EdgyEft:~$

---

### Post by TheWizzard on 2007-02-10
[http://www.google.nl/search?q=Could+not+connect+to+localhost%3A4001+(127.0.0.1](http://www.google.nl/search?q=Could+not+connect+to+localhost%3A4001+(127.0.0.1))

---

### Post by TheWizzard on 2007-02-10
try
```
sudo -s
apt-get install nvu
```

---

### Post by TheWizzard on 2007-02-10
please post the output of
```
echo $http_proxy
```

---

### Post by simple_mind on 2007-02-10
> **TheWizzard said:**
> please post the output of
```
echo $http_proxy
```

Here is the output:

home@EdgyEft:~$ echo $http_proxy
[http://localhost:4001](http://localhost:4001)
home@EdgyEft:~$

---

### Post by TheWizzard on 2007-02-11
did you install some proxy software? 
check
[http://forums.debian.net/viewtopic.php?t=310&](http://forums.debian.net/viewtopic.php?t=310&)

---

### Post by GrumpyBob on 2007-02-11
type in the terminal:
cat /etc/apt/sources/list

(The # in the xamples given represents your shell prompt.

Robert

---

### Post by bingotailspin on 2008-02-28
NVU has had a name change!  This works for me on Gutsy 7.10... :)

sudo apt-get install kompozer

---

