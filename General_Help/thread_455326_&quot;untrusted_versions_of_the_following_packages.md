---
title: "&quot;untrusted versions of the following packages will be installed!&quot;"
date: 2007-05-26
forum: General Help
---

### Post by yang on 2007-05-26
For some reason, yesterday I started getting these "untrusted" error messages. It all started yesterday when I clicked on the update notification icon in my tray. It listed the updates as usual, but after clicking Install and entering my password, I was warned:

"Warning

You are about to install software that can't be authenticated! Doing this could allow a malicious individual to damage or take control of your system."

When I clicked on Show Details, it pretty much listed every single one of the update packages.

I decided to Cancel until I could post here.

Then, today, I tried installing nmap:

```

yang@dell600:~$ sudo aptitude install nmap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  kdebase-bin kdebase-kio-plugins kdesktop konsole libkonq4 python2.5 python2.5-dev python2.5-minimal 
The following packages have been kept back:
  hwdb-client-common hwdb-client-gnome python python-gdbm python-minimal unattended-upgrades 
The following NEW packages will be installed:
  nmap 
0 packages upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
Need to get 750kB of archives. After unpacking 2707kB will be used.
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  nmap 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No":

```

What's going on? Please help, thanks.

---

### Post by fragos on 2007-05-26
This would normally mean that a repository you've specified doesn't have an associate athentification.  You won't see the message unless there is an update from that repository.  If you look at "Software Sources" Authentification tab you will see the registered authentifications and will be able to add additional ones.  Authentifications for the Ubuntu repositories should have been created during the install.

---

### Post by yang on 2007-05-30
I seem to have the correct keys installed, don't I? (See attachment.) If I don't, how do I get them installed? If I do...what the heck is going on? (Yes, I'm still getting this problem, and it's killing me because I can't update my system with security patches or install new software.)

---

### Post by fragos on 2007-05-30
You have keys for Ubuntu CD, Ubuntu repositories and Medibuntu.  Do you have any additional 3rd party software?  If you recognize the source when authentification fails you can still accept the update.

---

### Post by yang on 2007-05-30
Sorry, I'm getting very confused by this response. Aren't all the updates/packages I mentioned from the main Ubuntu repository?

And given the fact that I'm being warned that these are "untrusted", how do I know I can recognize/trust the source? This is precisely what MITM attacks exploit, and what the key verification is designed to protect against - users who think they recognize a third party, but the third party is actually not what it claims to be.

And finally, even if the source is trustworthy, is it really acceptable to just do this forever in the future? The user will become desensitized to the warnings, even when at some point the warning is of a real danger.

I would like to get to the bottom of this.

---

### Post by fragos on 2007-05-30
The ones in your thumbnail are indeed Ubuntu repositories.  Without seing the 3rd party tab I have no way of seeing if you have others.  When I first added Medibuntu I didn't add the authentification and got that message until I did.  I haven't seen the default Ubuntu repositories create this message so I thought your issue related 3rd paty repositories added without the authentification.  I don't know this to be true but perhaps the authentification reflects the physical server in some way.  I use "Server for United States" but others are available.  Just a guess but that's the only reason I can think of that makes any sense.  Did you install with an upgrade off the web or from a CD?  I used a CD and did a clean install.

---

### Post by yang on 2007-05-30
But 3rd party servers only matter if you're pulling packages from those servers - these packages aren't. (They're critical updates I get via the update notification tray icon, and nmap.)

I installed the previous version of Ubuntu with CD and updated to the latest distribution version using apt-get. But this all happened a long time ago, and I had been using Ubuntu fine for a long time since.

---

### Post by FuturePilot on 2007-05-30
If you installed something from a third party repo and they updated that package in the repo which you also have installed, it's going to come through the Update Manager. And if you don't have a gpg key for that repo you're going to get this warning. So it would be helpful to know if you have any 3rd party repos.

---

### Post by yang on 2007-05-31
I'm fairly certain this is buggy behavior. After rebooting, the problem went away on its own, and I just verified that my set of keys remains the same. (It is extremely inconvenient for me to take the system down.)

FuturePilot: I would expect to get this warning only for the packages from those third-party repos.

Thanks anyway for your help!

---

### Post by fragos on 2007-05-31
You've got a lot more stuff in 3rd party than I do and now I see you're on Edgy.  I'm runing Feisty so to some extent we're apples and oranges.  You may have better luck if you upgrade.  I'm very happy with 7.04.

---

### Post by yang on 2007-05-31
Uh...that's something I never noticed, and that's bad.

I'm *supposed* to be using 7.04:

```
$ cat /etc/issue
Ubuntu 7.04 \n \l
```

What is going on? Why didn't Ubuntu update my sources? What should I do?

---

### Post by zvacet on 2007-05-31
Take a look at your sources list and if it is still Edgy change it to Feisty

```
  sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```

---

### Post by tvst on 2007-06-10
i have been getting the same error for the past few days. this is a clean feisty install from maybe a couple of days before the warnings started. this is my etc/apt/sources.list:

-------------8<---------------------8<-----------------------8<-------------------
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty           main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates   main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security  main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-proposed  main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

# beryl
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main
-------------8<---------------------8<-----------------------8<-------------------

i get the warnings only from ubuntu sources, not beryl. for example, i just got the warning from an 'apt-get install unrar'.

when i look at the 'authentication' tab under software sources i see i have three keys:
-------------8<---------------------8<-----------------------8<-------------------
Ubuntu archive automatic key signing <ftpmaster@ubuntu.com>
Ubuntu CD image automatic key signing <cdimage@ubuntu.com>
Nicholas Thomas (repository signing key) <root@lupine.me.uk>
-------------8<---------------------8<-----------------------8<-------------------

that last key is probably from beryl. i want to re-acquire my ubuntu keys to see if the problem gets solved. do you know how i can do that?

---

### Post by merlinus on 2007-06-10
This is from my sources.list:

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

So it would seem that anything installed from universe and multiverse would trigger the warnings.

But.... I re-installed Gnome Network Manager via Synaptic and got the warning.  Now that seems very off!

BTW, this is after the latest kernel update.

:o

-merlin

---

### Post by yang on 2007-06-11
OK, so I've seen this problem rear its head once or twice since my last post, and I've found the solution: simply run apt-get/aptitude update, and the warning goes away. I can't explain why this is happening, though. Since others are experiencing it too, it looks like a bug.

As for my using Edgy or having Edgy sources...that's all false. Fragos said I had Edgy sources based on my screenshot, but note that the boxes are *unchecked* (leftovers from when I was actually running Edgy). But his assertion threw me off too, hence my confused reply.

---

### Post by fragos on 2007-06-11
I must be honest that I'd never before seen Edgy repositories in with with third party ones.  And yes they weren't checked.  Correcting help that might have been based on a misinterpretation is a good thing but blaming people that attempt to help you is hardly a way to garner help from others in the community.

---

### Post by tvst on 2007-06-11
> **yang said:**
> I've found the solution: simply run apt-get/aptitude update

i can confirm that updating the package list works for me.

---

### Post by AusIV4 on 2007-06-12
I had the same problem on Feisty, it was solved by running an aptitude update.

---

### Post by tvst on 2007-06-13
> **AusIV4 said:**
> I had the same problem on Feisty, it was solved by running an aptitude update.

the issue is that the problem comes back after a while, so always updating isn't a solution. unless this is purposely meant to force you to update, of course.

---

### Post by amanda on 2008-03-26
I've been having the same problem for a while. I just disabled all my third party repositories and had no trouble installing the package that was giving me "untrusted version" errors before. 

Logical or no, it was successful. 

I'd love to know why (are there duplicate packages somewhere? Or is aptitude just saying "i can't verify all your repositories, even ones you won't use in this install"?) but it did work to disable extra repositories for the moment.

---

### Post by fragos on 2008-03-26
The quality and character of a 3rd party repository is clearly the repository creaters.  I for one am careful about whose repositories I add.  When you add a repository its best to also enter the authorization key.  I have one repository which I trust but doesn't have an authorization key and there are always warnings generated for updates from that repository.

---

