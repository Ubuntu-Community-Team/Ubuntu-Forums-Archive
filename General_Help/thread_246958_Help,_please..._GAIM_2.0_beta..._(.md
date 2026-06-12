---
title: "Help, please... GAIM 2.0 beta... :("
date: 2006-08-30
forum: General Help
---

### Post by Roasted on 2006-08-30
I don't know what I did, but I hope someone can help me out here. I got a pair of SATA drives that I eventually plan to set up RAID 1. But for now, GAIM has me so pissed off I'm working on this first.

I want the latest beta of gaim, which I believe is 2.0. I have it on my IDE drive and I love it. So, what do I do? I got the tar.gz package, but the readme instructions kind of suck, or else I just don't know enough yet. I enabled all of my binary repositories to be multiverse/universe. Other than that, I'm on a completely fresh installation of Linux on this new hard drive.

So can someone help me...

---

### Post by anubix on 2006-08-30
sudo apt-get install gaim

---

### Post by Jagot on 2006-08-30
Add these lines to your sources.list to obatin it:

```
deb http://repository.debuntu.org/ dapper multiverse
deb-src http://repository.debuntu.org/ dapper multiverse
```

---

### Post by Roasted on 2006-08-30
I know about sudo apt-get install gaim, but that won't get me the latest 2.0 beta, will it? I thought it would just get me 1.5...

And how do I get to my sources list again? I've been using DOS so much lately I can't stop thinking about it to fix these Linux issues.

Also, after I do that, what do I do? sudo apt-get install gaim? Would it install 2.0?

---

### Post by Jagot on 2006-08-30
Enter this command in terminal:

```
sudo gedit /etc/apt/sources.list
```

Now you should need to enter your password and you will be presented with the file which contains the sources used to obtain packages.  Now at the bottom you can copy and paste those links, so your sources.list should look something like this:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free

deb http://repository.debuntu.org/ dapper multiverse
deb-src http://repository.debuntu.org/ dapper multiverse
```

Now save the file and close it.  Go to terminal again and type this:

```
sudo aptitude update
sudo aptitude upgrade
```

It'll look for the latest version of Gaim in any repositories you have as you should already have 1.5 installed, so it will upgrade this to 2 beta 3 from the new repository you have added.

---

### Post by Roasted on 2006-08-30
Okay. I forget what I did but somehow I came upon this error.

[IMG]http://i2.photobucket.com/albums/y36/Roasted/Screenshot-1-2.png[/IMG]

No idea what that means, but figured I'd ask.

In the end I got the newest version of gaim to run. For some reason I couldn't get it installed right. But I went into synaptic which I rarely do, I like tinkering around in terminal more, and I found 2 uninstalled files from gaim that said something about 2.0 in the version so I marked them for installation. Now, gaim seems to be fully working on the newest version.

The problem is, when I go to apps and internet, I have 2 gaim files listed. I tried to completely COMPLETELY ditch gaim, I did everything. apt-get uninstall, aptitude uninstall, purge, remove. Now I just did it again. I ditched gaim completely, but I still had 1 gaim file listed in internet. When I clicked it, it was obvious that gaim wasn't installed. So I reinstalled gaim, now I have gaim 2.0 in, but I also have 2 gaims listed in internet. Why.

By the way, both of the gaim things listed in internet are usable and will open gaim 2.0 fine. 






btw is there anything else in here I should have installed??

[IMG]http://i2.photobucket.com/albums/y36/Roasted/Screenshot-2-1.png[/IMG]

---

### Post by Dinerty on 2006-08-30
```
gpg --keyserver subkeys.pgp.net --recv 0E46617OBCF1FC29
      gpg --export --armor 0E46617OBCF1FC29 | sudo apt-key add -
```

Hope this helps solve the error key problem :)

---

### Post by Roasted on 2006-08-30
How'd you figure that out, and do I just run that in terminal?

---

### Post by Dinerty on 2006-08-30
Had the same problem myself, a forum poster helped me and told me to do the same, yes just copy it into the terminal

```
gpg --keyserver subkeys.pgp.net --recv 0E46617OBCF1FC29
```

Then

```
 gpg --export --armor 0E46617OBCF1FC29 | sudo apt-key add -
```

---

### Post by AirRaven on 2006-08-30
If you want the Gaim 2.0 Beta, you're being send down entirely the wrong path. It's not in the official repositories.

The easiest method I can reccomend is that you install Automatix by adding this to your /etc/apt/sources.list:

```
deb http://www.beerorkid.com/automatix/apt dapper main
```

Then just run apt-get install automatix. Run automatix from the terminal, and choose to install Gaim. That'll sort it for you.

---

### Post by Roasted on 2006-08-31
I know about automatix. I use it, and have it. I'm just trying to avoid using it to learn some new stuff.

Anyway, I added the repositories for gaim 2.0. I saved them, did a sudo apt-get update then sudo apt-get upgrade. About 10 seconds later, it said I have an update in the upper right corner. I clicked it, and saw gaim listed there for the upgrade. I installed them. All is good now!

---

### Post by Roasted on 2006-08-31
Also. I realized at the end of a sudo apt-get update I did it showed that key error. I ran the two things from earlier in terminal, and I got this result:



W: GPG error: [http://repository.debuntu.org](http://repository.debuntu.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E466170BCF1FC29
W: You may want to run apt-get update to correct these problems
jason@jason-desktop:~$ gpg --keyserver subkeys.pgp.net --recv 0E46617OBCF1FC29
gpg: "0E46617OBCF1FC29" not a key ID: skipping
jason@jason-desktop:~$  gpg --export --armor 0E46617OBCF1FC29 | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
jason@jason-desktop:~$


:confused:

---

### Post by ThrobbingBrain66 on 2006-08-31
I can't seem to get the public key verified for this repo....

I keep getting this message/error:

gpg: requesting key BCF1FC29 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

what do i do?!

---

### Post by lorendwilson on 2007-07-15
That is not the key.  The key is in a file at [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt).
This information is found in the repository list at the Trevino Blog with the instructions how to
add it.  This is a case where the key is given in a URL.

As per the instructions, issue the command:

wget [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt)  --quiet  -0 -  |  sudo apt-key add  -

as specified under "instructions if you have a key given by a URL" in the header of Trevino's
list.

---

