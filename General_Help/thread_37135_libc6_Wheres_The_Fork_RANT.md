---
title: "libc6 Wheres The Fork? RANT"
date: 2005-05-26
forum: General Help
---

### Post by TorQ on 2005-05-26
Just as I was starting to jam with this Linux thing I hit a brick wall!  Suddenly darn near every package I want to install requires a new libc6!  Of course I advised by the good people on this forum that an upgrade will break my system.  I suppose this has something with the release of Debian Sarge.  Or not, I don't know.  What is a body to do ?  This is one of the big problems with Linux that I always seem to run into after things seem to be going well.  Version incompatability with packages.  I admit that things were much worse in RPM land but these are not problems you have in windows.  I guarantee you that most people (like my girlfriend) are much less forgiving of this sort of thing.  Things on windoz just work.  Simple fact.  I did, in fact, put some time into trying to install some of these packages from source but I'm no genius.  I really do appreciate what I gain from using Linux but sometimes my loss of time from tracking down and fixing its shortcomings is downright disheartening!

---

### Post by angkor on 2005-05-26
[QUOTE=TorQ]Things on windoz just work.  Simple fact. [/QUOTE]

 :roll: 

And the question is....?

---

### Post by petrol on 2005-06-14
I belive a good question can come by this rant. I got the same sickening feeling when I broke my compiler. I put on a newer version of libc6 and the next time I ran apt-get it broke gcc. 
configure: error: C compiler cannot create executables

I can't go back to windows mostly for the lack of control. I do however practice extreme patience when dealing with problems like this.

Is there an easy way to fix your compiler after breaking it by upgrading libc6?
 ](*,)

---

### Post by desdinova on 2005-06-14
Did you add Debian repositories - if so, you can expect this.... 

And as to Windows "just works" - well thats news to me after 12 years of sysadmin'ing it... I found Exchange "just breaks" on a regular basis, SQL Server "just falls over" when you least expect it ;-)

---

### Post by petrol on 2005-06-14
Well, my problem stems from needing the ICA client. This required libmotif3. This required a newer version of libc6 than I was getting on the repositories listed below. I loaded the latest libc6 from a .deb. Was I supposed to do without programs that require the latest libc6? :-| 

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## Marillat
# deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

---

### Post by Takis on 2005-06-14
[QUOTE=TorQ]Things on windoz just work.  Simple fact.[/QUOTE]
DVD player? Need to go out and buy a program.
DVD burner? Need to go out and buy a program.
Office suite? Need to go out and buy a program.
Graphics editor? Need to go out and buy a (thousands of dollars) program.

You get the idea, anyway. Imagine you're at home at 10pm one night and decide you'd like to watch a DVD on your Windows machine. If you weren't lucky enough to get a DVD player shipped with your DVD drive, tell me, how does Windows just work then?

---

### Post by az on 2005-06-14
If you stick with ubuntu repositories, you do not have a problem.  In a windows world, you would not be given a choice - the app would not be available at all.   In your situation, you can compile the app yourself using your version of libc6 and happily run the app.  This is backporting.

Why is the app not already in the backports?  Probably because you have not yet asked.

Too complicated to compile?  that is why there are binary packages.  You cannot expect a binary release every week, so you gotta live with packages that are a few months old.

---

