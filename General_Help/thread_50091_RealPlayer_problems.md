---
title: "RealPlayer problems"
date: 2005-07-19
forum: General Help
---

### Post by diffuser78 on 2005-07-19
Hello all,

I am trying to play music from [www.raaga.com](www.raaga.com) , it needs realplayer. I have it installed on my Ubuntu but it gives me the following error.

" Could not find appropriate hxplay or realplay in the system path to use as an embedded player "

Dont know what to do.........I love listening to music while working. 

Please help me and tell me correct solution,

Thanks for your help guys,

---

### Post by jesse on 2005-07-19
How did you install real player? 

If you installed it by downloading the executable from real.com, get rid of it manually. Then add the following line to your sources.list

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

To do this, open a terminal and type 

sudo gedit /etc/apt/sources.list

Once you've done this, start synaptic package manager and reload the repositories. Then do a search for "real" and you should find the real player 10 package. 

Install it using synaptic. Then launch it and from the help menu choose "player reset". This should start the Real Player installation program, which will enable you to install browser plugins, etc.

---

### Post by jesse on 2005-07-19
Alternatively, if you want the latest release of real player, you can download the rpm version of Real Player 10 from real.com, convert it to deb with alien and then install it using dpkg. 

To do this do the following: 

1. Remove any version of Real Player you currently have installed (recommended)
2. download the rpm from real.com
3. make sure you have alien installed. If not, you can install it by typing 

sudo apt-get install alien 

at a terminal or by using synaptic. 

4. Then convert the rpm you downloaded to a deb package. Open a terminal and go to the directory where you saved it. For example "cd /home/madonna" will get you to user Madonna's home directory if it's saved there. Then once you're in that directory type "sudo alien -d completefilename.rpm" and wait till the deb package is generated. 

5. Once the deb is generated, install it by typing "sudo dpkg -i filename.deb"

6. Then you should be all set. Once you launch it ("realplay"), don't forget to choose "player reset" from the help menu to launch the installation program so that the browser plugins get installed. 

7. If you find after the installation that Real Player isn't starting, open "nautilus" from a root terminal, navigate to the "plugins" folder for Real Player (probably /user/local/RealPlayer/plugins) and delete swfrender.so and swfformat.so as you don't need these and they sometimes cause Real Player to hang.

---

### Post by diffuser78 on 2005-07-20
[QUOTE=jesse]Alternatively, if you want the latest release of real player, you can download the rpm version of Real Player 10 from real.com, convert it to deb with alien and then install it using dpkg. 

To do this do the following: 

1. Remove any version of Real Player you currently have installed (recommended)
2. download the rpm from real.com
3. make sure you have alien installed. If not, you can install it by typing 

sudo apt-get install alien 

at a terminal or by using synaptic. 

4. Then convert the rpm you downloaded to a deb package. Open a terminal and go to the directory where you saved it. For example "cd /home/madonna" will get you to user Madonna's home directory if it's saved there. Then once you're in that directory type "sudo alien -d completefilename.rpm" and wait till the deb package is generated. 

5. Once the deb is generated, install it by typing "sudo dpkg -i filename.deb"

6. Then you should be all set. Once you launch it ("realplay"), don't forget to choose "player reset" from the help menu to launch the installation program so that the browser plugins get installed. 

7. If you find after the installation that Real Player isn't starting, open "nautilus" from a root terminal, navigate to the "plugins" folder for Real Player (probably /user/local/RealPlayer/plugins) and delete swfrender.so and swfformat.so as you don't need these and they sometimes cause Real Player to hang.[/QUOTE]


Hey Jesse,

I did exactly the same things you said. It worked partially. Though now I can play music in real player I cannot play music on the website for music like [www.raaga.com](www.raaga.com)

Maybe you wanna try .... try going to [www.raaga.com/hindi](www.raaga.com/hindi)

try playing any song...check if u can get it running in ur real player automatically.

Thanks for your help Jesse,

Dan

---

### Post by diffuser78 on 2005-07-20
Can somebody guide me how to get the realplayer working for playing music on websites like [www.smashits.com](www.smashits.com)  or [www.raaga.com](www.raaga.com) in Ubuntu

---

### Post by diffuser78 on 2005-07-21
Can somebody guide me how to get the realplayer working for playing music on websites like [www.smashits.com](www.smashits.com) or [www.raaga.com](www.raaga.com) in Ubuntu

---

### Post by diffuser78 on 2005-07-21
Still waiting if some pro could help me solve the above mentioned problem,

Dan

---

### Post by sonmez on 2005-07-23
I followed the directions on [http://www.ubuntuforums.org/showthread.php?t=7017&page=3&pp=10&highlight=real+player](http://www.ubuntuforums.org/showthread.php?t=7017&page=3&pp=10&highlight=real+player)
 on the massage titled [b]Re: What's wrong with my Realplayer?
and it worked for me. I use Ubuntu 5.04.
Good luck
Sonmez

[/b]

---

### Post by diffuser78 on 2005-07-24
[QUOTE=sonmez]I followed the directions on [http://www.ubuntuforums.org/showthread.php?t=7017&page=3&pp=10&highlight=real+player](http://www.ubuntuforums.org/showthread.php?t=7017&page=3&pp=10&highlight=real+player)
 on the massage titled [b]Re: What's wrong with my Realplayer?
and it worked for me. I use Ubuntu 5.04.
Good luck
Sonmez

[/b][/QUOTE]


Did realplayer word for you as a mozilla plugin ??

Thats my problem, I just cant get realplayer working as a mozilla plugin...


Dont know what to do ?? Its been  more than a week ..I am trying anf havent got any concrete solution...


Dan

---

### Post by sonmez on 2005-07-24
Yes it has been working fine.

---

### Post by Omnios on 2005-07-24
I got RealPlayer from the web a real long time ago and had to go into the realplayer directory and put a plug in file from there into the Mozzila-Firefox Directory. Mind you this was a long time ago so not shure if its the same. I copy and pasted it. Anyways go to the realplayer site click Linux version on the bottom and there should be a read me there if I remember propery. Also there seems to be sites where it doesn't seem to work!

---

### Post by sonmez on 2005-07-24
so why don't you uninsall it and try to follow the posting I was talking before. I remember Having problem trying to install it before. but now it seems that the problem has been resolved.

---

### Post by NeoChaosX on 2005-07-25
diffuser78: Go into Firefox, type in "about:plugins" in the address box, and tell me if you see a section with the header **Helix DNA Plugin: RealPlayer G2 Plug-In Compatible**.

---

### Post by diffuser78 on 2005-07-25
[QUOTE=NeoChaosX]diffuser78: Go into Firefox, type in "about:plugins" in the address box, and tell me if you see a section with the header **Helix DNA Plugin: RealPlayer G2 Plug-In Compatible**.[/QUOTE]

Hey , yes I do see this section. This looks as follows



Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

File name: nphelix.so
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.552 built with gcc 3.2.0 on May 13 2005

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes




Please help,

Dan

---

### Post by oghanchi on 2005-07-25
Hi diffuser78:

I had the same problem with [http://www.musicindiaonline.com](http://www.musicindiaonline.com)

I discovered that the site would only work with a specific version of RealPlayer, i.e. version 10.0.1.435 or RealPlayer Gold. Here are the steps I had to take:

Download the RPM of the above version of RealPlayer from realplayer.com
Convert the rpm to deb using alien
Install the package

Then do the following:

link the nphelix.so to /usr/lib/mozilla-firefox/plugins

sudo ln -s /usr/local/RealPlayer/plugins/nphelix.so /usr/lib/mozilla-firefox/plugins

link the nphelix.xpt to /usr/lib/mozilla-firefox/components

sudo ln -s /usr/local/RealPlayer/plugins/nphelix.xpt /usr/lib/mozilla-firefox/components

This did the trick for me.

---

### Post by NeoChaosX on 2005-07-25
..why are people saying to downloading the RPM version? For the love of all that is holy, there's a .bin which you can run and install RP from the command line. It's easier than using Alien to convert the RPM. Heck, there's even a RealPlayer deb package avalible in Multiverse.

---

### Post by oghanchi on 2005-07-26
The website(s) in question require a specific version of RealPlayer; 10.0.1.435. A deb package of this version can not be found anywhere in multiverse.  Multiverse has a newer version. This is why the only solution is to convert the RPM package.

I hope this answers your question!  :neutral:

---

### Post by chajuram on 2005-08-07
Hi,

I have a couple of questions. 

The FAQ section on musicindiaonline shows an example screenshot with the real player version being 10.0.1.555. They also say "the version should be 10 or higher", isn't this be true? 

Secondly there is just one RPM from real player site, how do I get the version (435) I want? 

Thanks in advance.

Chajuram.

---

### Post by karthik085 on 2005-11-27
I had the same problem, of not able to play ram files from a website.

This helped me:
[http://www.linuxquestions.org/questions/showthread.php?threadid=343721](http://www.linuxquestions.org/questions/showthread.php?threadid=343721)

---

### Post by mishranurag on 2005-11-28
I am also a newbie to Ubuntu and complex solutions or no solutions to such simple problem are still not letting me use the UBuntu full time.
Anurag

---

### Post by mishranurag on 2005-12-12
Did nobody like me comment or they just accept it :)
Anurag

[quote=mishranurag]I am also a newbie to Ubuntu and complex solutions or no solutions to such simple problem are still not letting me use the UBuntu full time.
Anurag[/quote]

---

### Post by karma on 2005-12-14
I installed real player using the following method...but I am not able to see it listed in the start panel menu.

How do I launch real player?


```
Alternatively, if you want the latest release of real player, you can download the rpm version of Real Player 10 from real.com, convert it to deb with alien and then install it using dpkg.

To do this do the following:

1. Remove any version of Real Player you currently have installed (recommended)
2. download the rpm from real.com
3. make sure you have alien installed. If not, you can install it by typing

sudo apt-get install alien

at a terminal or by using synaptic.

4. Then convert the rpm you downloaded to a deb package. Open a terminal and go to the directory where you saved it. For example "cd /home/madonna" will get you to user Madonna's home directory if it's saved there. Then once you're in that directory type "sudo alien -d completefilename.rpm" and wait till the deb package is generated.

5. Once the deb is generated, install it by typing "sudo dpkg -i filename.deb"

6. Then you should be all set. Once you launch it ("realplay"), don't forget to choose "player reset" from the help menu to launch the installation program so that the browser plugins get installed.

7. If you find after the installation that Real Player isn't starting, open "nautilus" from a root terminal, navigate to the "plugins" folder for Real Player (probably /user/local/RealPlayer/plugins) and delete swfrender.so and swfformat.so as you don't need these and they sometimes cause Real Player to hang.
```

---

### Post by spencer on 2005-12-15
[QUOTE=jesse]Alternatively, if you want the latest release of real player, you can download the rpm version of Real Player 10 from real.com, convert it to deb with alien and then install it using dpkg. 

To do this do the following: 

1. Remove any version of Real Player you currently have installed (recommended)
2. download the rpm from real.com
3. make sure you have alien installed. If not, you can install it by typing 

sudo apt-get install alien 

at a terminal or by using synaptic. 

4. Then convert the rpm you downloaded to a deb package. Open a terminal and go to the directory where you saved it. For example "cd /home/madonna" will get you to user Madonna's home directory if it's saved there. Then once you're in that directory type "sudo alien -d completefilename.rpm" and wait till the deb package is generated. 

5. Once the deb is generated, install it by typing "sudo dpkg -i filename.deb"

6. Then you should be all set. Once you launch it ("realplay"), don't forget to choose "player reset" from the help menu to launch the installation program so that the browser plugins get installed. 

7. If you find after the installation that Real Player isn't starting, open "nautilus" from a root terminal, navigate to the "plugins" folder for Real Player (probably /user/local/RealPlayer/plugins) and delete swfrender.so and swfformat.so as you don't need these and they sometimes cause Real Player to hang.[/QUOTE]


I did as all the steps and RealPlayer installed. When I try to open Realplayer with "realplay command nothing happens; I even deleted the two plugins and still nothing. Here is the message I receive:


```
nomo@ubuntu:~$ realplay
bash: realplay: command not found
```

Anyone Please? Thank you.

-spencer

---

### Post by mishranurag on 2005-12-15
Looks like real player is the "Real" problem creating  software :)
Wonder how nice the world would be without it :)
Anurag


[quote=spencer]I did as all the steps and RealPlayer installed. When I try to open Realplayer with "realplay command nothing happens; I even deleted the two plugins and still nothing. Here is the message I receive:
-spencer[/quote]

---

### Post by spencer on 2005-12-23
Hi!, I just added the "deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main" to sources.list method recommended by "jesse". That worked just fine and Real Player now works. I immediatly deleted "deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main" from sources.list and now everything's peachy. :D  Thanks jesse.

-spencer

---

### Post by sridharm on 2007-03-16
I'm on 64Bit (amd64) ubuntu fiesty and this is what I did to play songs on raaga.com

- Download and install RealPlayer10GOLD.bin under /usr/local/RealPlayer 
when the installer prompts to create symbolic links, say yes.

- go to /usr/lib/mozilla/plugins directory. sudo nspluginwrapper -i `pwd`/nphelix.so, which creates a file npwrapper.nphelix.so

- go to /usr/lib/mozilla-firefox/plugins directory and create a symbolic link to npwrapper.nphelix.so created above.

restart firefox and you should be good to go.

---

