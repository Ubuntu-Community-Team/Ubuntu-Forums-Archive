---
title: "problems"
date: 2005-07-30
forum: General Help
---

### Post by sazplayer on 2005-07-30
after attempting to auto-upgrade the various packages on my machine i ran into some problems. after rebooting the normal login screen wouldn't load, instead it gave me the error: "error loading the theme 'human'" and took me to a default login screen from which i cannot login. i was, however, successful in loging in via the command line. i then attempted to upgrade again on the advice of a friend (who has been using unix-like systems for a couple of decades). i used apt-get install -f which attempted to install 'python2.4' and gave a number of errors including "failed to fetch http://ftp.us.debian.org/debian/pool/main/p/python2.4/python2.4_2.4.1-2_i386.deb".
all of my problems seem to center around this python2.4.1-2 package and i don't know what to do (even my friend doesn't know what's going on).
any advice would be helpful. i am relatively new to linux (only a couple of months) so i'm still not entirely confident with regards to command line stuff.

---

### Post by Xian on 2005-07-30
My first question would be why are you sourcing a ftp.us.debian.org repo?

---

### Post by sazplayer on 2005-07-30
it is with great embarassment (read as 'mortification) that i say "i do not understand the question" (when i said new i meant new)

---

### Post by Xian on 2005-07-30
[QUOTE=sazplayer]i used apt-get install -f which attempted to install 'python2.4' and gave a number of errors including "failed to fetch http://ftp.us.debian.org/debian/pool/main/p/python2.4/python2.4_2.4.1-2_i386.deb"[/QUOTE]
See where you are pulling pkgs from a debian mirror (ftp.us.debian.org)?

Apt would only do this if told to do so in the sources.list.
You should not be sourcing any repositories other than Ubuntu.

Please read and follow the guide to set your [Apt source list](http://ubuntuguide.org/#extrarepositories).

---

### Post by varunus on 2005-07-30
Can you log in without graphics and post the output of "cat /etc/apt/sources.list" at the prompt?

It seems that you've been set up on your computer to mix debian and ubuntu packages (two different distros, same packaging system though...).  You're going to have to reinstall if this is the case...sorry.  Its not recommended at all to mix the packages...

---

### Post by Xian on 2005-07-30
If for any reason that How-To is not clear then you can do this:

1. Backup your sources.list
Open a termial (Applications > System Tools > Terminal)
```
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
2. Open a text editor and load the sources.list
```
$ sudo gedit /etc/apt/sources.list
```
3. Replace everything in that file with the list below
```
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

##Security Mirrors
deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

#Ubuntu Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

##Backport Extras
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
```
4. Save the file then issue the following commands in the terminal
```
$ sudo apt-get update
$ sudo apt-get -f install
```

---

### Post by sazplayer on 2005-07-31
it seems to be set up to get packages from debian only, i don't know why (note: i didn't set up this machine, it was done by my friend). if i have to reinstall i will have to transfer all my files to another disc (some are of extreme importance) and i don't have any useable ones lying around.

ps: i'm a chemist, not a hacker. so i'm kind of like a fish out of water here.

---

### Post by sazplayer on 2005-07-31
also, i think that part of the problem may be misunderstood (possibly because i'm using this forum right now), the X on the machine in question seems to be broken so it can only be used as a terminal right now. (i am using a different machine right now)

also: i was wrong, it is set up to retrieve pkgs from both ubuntu and debian, i'll try to change that now.

---

### Post by varunus on 2005-07-31
Even if you can change back the apt sources to just Ubuntu, it may not fix your system depending on what happened.  (Unless you can pinpoint every broken package and use aptitude (command-line synaptic) to downgrade them all to the Ubuntu version.)  Go tell your friend not to mix Ubuntu and debian like that, it breaks systems like crazy.  (Different versions.)

Not only are the versions different, but sometimes, the naming convention itself for versions can be different (so debian version 43 can be older than ubuntu 42.3).  But apt will get the debian version, which can break programs that really need the newest version of things.

---

### Post by sazplayer on 2005-07-31
he agrees that it's a problem. i don't think it was done intentionally.

---

### Post by graynz on 2005-08-15
i too have the exact same problem .... even though this is a stagnent thread, i thought  I'd post this plea for help anyway. So, if there is anyone out there with info .... please post (or email)
cheers from downunder / Graham

---

### Post by OzOle on 2005-08-16
I suspect we are many with this problem!!!

I really don't get it! I'm new to Ubuntu also and have only installed it this last week. I like the enthusiasm that comes from Ubuntu's site and it sounds very promising.

I previously have been using SuSE Linux but since they have become very commercial in their attitude toward users, I decided to look around for another Linux version. After some consideration I decided to install Debian Linux and was generally pleased with it, however, the installation procedure is somewhat lacking. I then came across Ubuntu and as I said above, I was impressed with the enthusiasm and the stated goals.

Like the other users in this thread I installed Ubuntu and subsequently KDE and was pleased with it.

Now I'm in the situation of needing packages that are not in Ubuntu's catalog, so like the others started installing packages from Debian.

**BIG MISTAKE!!!** 

But how was I to know that?
I don't remember reading anywhere that I should not download programs from Debian, and it doesn't seem obvious when you remember that Ubuntu clearly states that it is based on Debian. I think it is perfectly understandable if SAZPLAYER, rocket.nz, brian g, [email]steven@heimann.com.au[/email] and probably others beside myself think that it is ok to use packages from Debian and perhaps from other sources as well.

[B]My suggestion to Ubuntu: 
Quick! Change Ubuntu's versions of synaptic and apt-get so that it is NOT possible to make changes in the sources list.[/B]

Right now I'm running the Ubuntu Live CD which I downloaded and I notice the Application Installer where one can add or remove applications. That's it! Only those packages shown there may be installed!  Nothing else! Of course that makes Ubuntu a restricted destribution but what is there is at least going to work.

Sadly, this kind of problem is what is making it hard to get people with little or no computer experience to switch over to Linux from you-know-who.

I'm sorry, but I'm a bit disappointed here, I had such great expectations of Ubuntu.

Still Ubuntu is a very neat destribution if one only requires a basic installation with the usual things like office programs, some games, sound and graphics and a few other bits.

Greetings from Australia,
Ole

---

### Post by OzOle on 2005-08-16
I would like to confirm one thing:

If I boot up the computer with a "live" Linux CD so that I can get access to the damaged Ubuntu partition, is it still not possible to fix the installation so that I can get back to where I was? Or am I absolutely required to reinstall Ubuntu from scratch?

Can anyone tell me if that can be done and, if so, how?

Thanks in advance,

Ole
[email]ole.eskildsen@gmail.com[/email]

---

### Post by OzOle on 2005-08-17
[QUOTE=Xian]See where you are pulling pkgs from a debian mirror (ftp.us.debian.org)?

Apt would only do this if told to do so in the sources.list.
You should not be sourcing any repositories other than Ubuntu.

Please read and follow the guide to set your [Apt source list](http://ubuntuguide.org/#extrarepositories).[/QUOTE]


Xian,

I think you are being rather unkind in your comments!
How are we Ubuntu newbies to know that we are not allowed to use the facilities available in the synaptic and apt-get utilities for specifying other source repositories, especially Debian? After all, Ubuntu is based on and closely linked with Debian!

Also, what is this then:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
???
Here you can find packages which do not show up in synaptic/apt-get!
Is it safe to download and install these packages then?

Kind regards,

Ole

PS.  I have given up waiting for a reply from the Ubuntu "experts" and am now reinstalling Ubuntu from scratch!

---

