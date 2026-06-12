---
title: "What's up with the apt-get repositories????"
date: 2005-10-17
forum: General Help
---

### Post by shadow07 on 2005-10-17
I'm trying to install some packages off of the Breezy Main and Universe repositories, and I keep getting either "404 Not Found" or "Connection Reset by Peer".

Here's my sources.list file:

> ## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse 

Also, there appears to be a GPG issue with us.archive.ubuntu.com:

> W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release: The following signatu res were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key < [email]ftpmaster@ubuntu.com[/email]>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following  signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signi ng Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


---

### Post by ecobuntu on 2005-10-17
if you run 

[/code]
sudo apt-get update
[/code]

That should take care of the GPG error.  Regarding the other error, maybe the repositories are down\

---

### Post by towsonu2003 on 2005-10-17
having same problem here. can't even download the repositories mentioned.

---

### Post by frobroj on 2005-10-17
Yup me too when I run " sudo apt-get update "... :(

---

### Post by andril on 2005-10-17
Problem, still persists and all is down the drain for me. Can the Repository Handlers correct this?:confused:

---

### Post by trey on 2005-10-17
run:

apt-get clean
apt-get update

---

### Post by cytoplasm on 2005-10-17
trey,

I tried the `clean` and `update` as you suggested and I'm still getting the `BADSIG` errors.

---

### Post by frobroj on 2005-10-17
Ditto! on 3 seperate boxes!

---

### Post by teaker1s on 2005-10-17
check wilki if you can't get 'synaptic' to work  i've suggested that breezy badger synaptic has dns issue and also disable back ports in your sources list file

---

### Post by dbott67 on 2005-10-17
Also, try changing your /etc/apt/sources.list file to this:
```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

Then reload the packages and search away! :)

-Dave

---

### Post by dbott67 on 2005-10-17
By the way, the above sources.list has worked for others with similar problems, as noted in [this thread]("http://www.ubuntuforums.org/showthread.php?p=411974").

-Dave

---

### Post by cytoplasm on 2005-10-17
My apt.sources looks the same but the BADSIG still shows up.

---

### Post by metallikop on 2005-10-17
Tested the above fix, works fine now.

---

### Post by towsonu2003 on 2005-10-17
[QUOTE=metallikop]Tested the above fix, works fine now.[/QUOTE]

not working for me

---

### Post by frobroj on 2005-10-17
DAVE Thanks! copied your sources.list file over and it worked great...

Thanks again!
fro

---

### Post by towsonu2003 on 2005-10-17
[QUOTE=towsonu2003]not working for me[/QUOTE]

I take it back, my bad. Works well. Thanks!

---

### Post by cytoplasm on 2005-10-17
Okay, I realized one difference.  This resolved the BADSIG issue: remove the "us" from the URLs in the sources.list file; and when update is run again all will be well.  There must be a problem with the US mirror.

---

### Post by trey on 2005-10-17
[QUOTE=cytoplasm]trey,

I tried the `clean` and `update` as you suggested and I'm still getting the `BADSIG` errors.[/QUOTE]

weird, to be honest, i did this:

cd /var/lib/apt
rm -fr lists
mkdir -p lists/partial

then i did:

apt-get update

I saw clean and update on #ubuntu ;-)

---

### Post by trey on 2005-10-17
[QUOTE=trey]weird, to be honest, i did this:

cd /var/lib/apt
rm -fr lists
mkdir -p lists/partial

then i did:

apt-get update

I saw clean and update on #ubuntu ;-)[/QUOTE]


oh yeah and you might want to take out/disable the first line in /etc/apt/sources.conf to disable the cdrom (unless u wanna pop it in)

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release Candidate i386 (20051005)]/ breezy main restricted

---

### Post by dbott67 on 2005-10-17
[QUOTE=metallikop]Tested the above fix, works fine now.[/QUOTE]

Great!

-Dave

---

### Post by dbott67 on 2005-10-17
[QUOTE=frobroj]DAVE Thanks! copied your sources.list file over and it worked great...

Thanks again!
fro[/QUOTE]

You're welcome.  Glad it's working.

-Dave

---

### Post by dbott67 on 2005-10-17
[QUOTE=towsonu2003]I take it back, my bad. Works well. Thanks![/QUOTE]

You're also welcome.

I noticed that the mirrors were giving me all sorts of errors on Thursday and Friday of last week (mine had a CA, instead of US), do I removed them & everything seemed to work after that.

-Dave

---

### Post by GameManK on 2005-10-17
removing the "us." fixed the 404 errors

annoying.

---

### Post by shadow07 on 2005-10-17
Thanks for everyone's reply.  I removed the "us." prefix, and I no longer get the error messages.

---

### Post by ecobuntu on 2005-10-17
[QUOTE=dbott67]You're also welcome.

I noticed that the mirrors were giving me all sorts of errors on Thursday and Friday of last week (mine had a CA, instead of US), do I removed them & everything seemed to work after that.

-Dave[/QUOTE]

I am running the Canadian archives with no problem now.  I did have one minor GPG key issue earlier today but re-ran apt-get update and voila gone!

---

### Post by ecobuntu on 2005-10-17
I figured I post this as well since I just checked a minute ago and they are working.  So we don't over load the main server!
in /etc/apt/sources.list add

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

## Major bug fix updates produced after the final release of the distribution
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted multiverse universe

---

### Post by stepore on 2005-10-18
[QUOTE=ecobuntu]I figured I post this as well since I just checked a minute ago and they are working.  So we don't over load the main server!
in /etc/apt/sources.list add

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse[/QUOTE]

curious -- where did you get the canadian repos from? where's the list for ubuntu servers and repos per country?

btw i'm canadian, too.
cheers.

---

### Post by ekravche on 2005-10-18
[QUOTE=dbott67]Also, try changing your /etc/apt/sources.list file to this:
```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

Then reload the packages and search away! :)

-Dave[/QUOTE]

this worked for me thanx! :)

---

### Post by cbudden on 2005-10-18
Are their UK mirrored repositories?

---

### Post by Sslaxx on 2005-10-18
[QUOTE=cbudden]Are their UK mirrored repositories?[/QUOTE]

Yup!
```
http://gb.archive.ubuntu.com/
```

---

### Post by hajk on 2005-10-18
After getting many GPG-errors and corrupted Sources/Packages files from the Dutch mirror, I also got tough by cleaning out the /var/lib/apt/lists directory, by removing the "nl" from the mirror in /etc/apt/sources.list, doing a fresh "sudo apt-get update" -- and all's well!

Thanks Dave, only in Canada eh? 

(Signed: un Canadien errant)

---

### Post by dbott67 on 2005-10-18
You're welcome, hajk.

- Dave

Yep, only in Canada.  Pity. :)

---

### Post by gbusse on 2005-10-18
Greetings,

I am in Canada and originally had a ca. in front of my repositories. I tried removing the ca. from the beginning of my repositories wherever it was listed so that now they read archive.ubuntu.com instead. I also removed everything from the /var/lib/apt/lists directory after which I got an error about missing  directory called "partial". I recreated this directory and ran apt-get update and am still getting errors when running apt-get update. I really hope this gets fixed soon!?!?!

Thanks,
Gord

---

### Post by dictator88 on 2005-10-18
LISTEN, is there anyone in here that knows what is going on, or what is going to be going on with the repositories? I've read 1000 plus pages about hundreds of people having "the" problem. IT ISN"T WORKING.  From what I've read this is all based on some legal problem, but I don't know for sure since no-one at ubuntu is really pointing out the real problem or its solution. A fresh install of 5.10 is now "what you see is what you get" situation. The apt-get is worthless. Even java, flash, ssh (for gods sakes), and the list goes on. Now,,,, for those who say "I don't see a problem",  either your doing someing differnent then ALL the documentation is stating to do, or you walk on water on your off nights! Which leads me to my question/statment. Is this problem going to be fixed?, or is all 10,000 pieces of documentation on ubuntu now junk? PLEASE! Somebody who knows what the h*ll is going on at least put a statement on ubuntu's front web PAGE!!!!!! (You know, the place support and product information goes)

---

### Post by loon on 2005-10-18
[QUOTE=dictator88]rant.[/QUOTE]


You know you can install these yourself rather through apt-get.
Plus, you might learn some things from the CLI (command-line interface) and other usefull information.

-loon

---

### Post by dictator88 on 2005-10-18
SURE! As a matter of fact,,, since I got myself in the mindset of walking backwards, why not install DOS 6.22 on my machine? What do you think Loon? As if apt-get was really a "windows" apt to begin with. Seriouslly. Ubuntu has everthing going for it and I hate to see one of the first OS's that could grow to fight microcrap fall by the way side because too many people get to frustrated or loose faith in it before it starts to make a dent. I sell 1000's of PC's and would give my left nut to be able to push microsoft out since 90% of the people only browse and check email anymore. But even if linux (ubuntu) does get close to making a dent, then the "system" itself has to be made known what is going on for those who "really" want to know, to help those who don't "really" care.

---

### Post by Crazy Man on 2005-10-18
dictator88 -> [http://www.ubuntuforums.org/showthread.php?t=58017](http://www.ubuntuforums.org/showthread.php?t=58017)

I'm sure I'm not the only one here sitting here and thinking this....

---

### Post by dictator88 on 2005-10-19
Crazy man ----  Point taken.

---

### Post by santino on 2005-10-19
Hello,

Are there any Netherlands based mirrors?

Cheers and thanks for the help.

---

### Post by TiMBuS on 2005-10-19
[quote=dictator88]*Blah*[/quote]

My apt-get is just fine. Ha.

The only 404 errors are backport related. Because they aren't ready yet. If you have other errors non-breezy-backport related, maybe you should try another repository.. Or just install them yourself. Its not hard.

---

### Post by towsonu2003 on 2005-10-19
[QUOTE=TiMBuS]My apt-get is just fine. Ha.

The only 404 errors are backport related. Because they aren't ready yet. If you have other errors non-breezy-backport related, maybe you should try another repository.. Or just install them yourself. Its not hard.[/QUOTE]

Is this "install it your self" a new motto? what happened to "just works"? 

At least someone finally pointed out the problem with backports etc...

---

### Post by dbott67 on 2005-10-19
[QUOTE=dictator88]...you walk on water on your off nights![/QUOTE]

Walking on water is not so amazing (well, in Canada anyways.  We can walk on water for 4+ months a year in most places... as long as the lakes are frozen). :)

Anyhow, here's my **/etc/apt/sources.list** file --- it works perfectly.  Copy & paste it over yours.  Re-start Synaptic and press ***RELOAD***.  You should be good to go.

```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb http://archive.ubuntu.com/ubuntu breezy main restricted
 deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://archive.ubuntu.com/ubuntu breezy universe
 deb-src http://archive.ubuntu.com/ubuntu breezy universe

 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe

# deb ftp://ftp.nerim.net/debian-marillat/ etch main

```

Note: this last line that is commented out (*# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main*) is for backports and other "unofficial Ubuntu apps" (such as w32codecs, etc.).  Just uncomment the line, re-start Synaptic, and then press RELOAD to search the new repos.

Be sure to put the # back in before doing any other updates, as you can really bork your system. 

-Dave

---

### Post by TiMBuS on 2005-10-19
[QUOTE=towsonu2003]Is this "install it your self" a new motto? what happened to "just works"? 

At least someone finally pointed out the problem with backports etc...[/QUOTE]

Considering I need to install my own modem drivers, compile my own kernel, make my own nvidia drivers, and - until Breezy - I had to make my own sound card module as well, I'll say the 'It just works' motto was never my thing.
However, after using gentoo, I'd say that the fact Ubuntu has an X-Terminal and a precompiled kernel on first boot, 'It just works - alot more than you think'
Plus you have to manually install stuff on windows all the time.

Also, yes the backports are then only screwed repos. It takes a lot of time for the ubuntu guys to get the hundreds of unsupported programs, and make, plus upload and maintain a nice tidy cross-linked package that will self-install for your gain.

Not to sound harsh, but apt-get is a free service for you. You're getting much, much more than what you paid for.

---

### Post by Crazy Man on 2005-10-19
[QUOTE=TiMBuS]
Not to sound harsh, but apt-get is a free service for you. You're getting much, much more than what you paid for.[/QUOTE]

I personally think portage gives you more, but aptitude comes in at a close second. :p

---

### Post by dictator88 on 2005-10-21
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)


This is what I get with the exact copy of the sources.list you gave me,, soooooo ??

---

