---
title: "Where to install Thunderbird..?"
date: 2004-11-04
forum: General Help
---

### Post by Verlager on 2004-11-04
I want to [COLOR=DarkGreen]install thunderbird-0.9-i686-linux-gtk2+xft.tar.gz[/COLOR] in a location universally accessable to all users. If I just untar it with: 

[COLOR=Blue]tar -xzf thunderbird-0.9-i686-linux-gtk2+xft.tar.gz
cd thunderbird  
thunderbird
[/COLOR]
It works, but then only I can use it. 

How do I install it to a more general location, not in a home directory? 

Where (and how) should I typically install system-wide applications like this?

---

### Post by SyL on 2004-11-04
I think in /opt

---

### Post by Verlager on 2004-11-04
How and why do I install in /opt ? I never heard of that, btw.

---

### Post by SyL on 2004-11-04
/opt is a directory for add-on. It's here that you can install apps which are not support by your os.
like thunderbird 0.9

---

### Post by Juergen on 2004-11-04
[QUOTE=Verlager]How and why do I install in /opt ? I never heard of that, btw.[/QUOTE] /opt is meant for software that doesn't go to the standard /usr/bin, /usr/lib etc., but creates it's own directory(-structure) as your thunderbird-package seems to do. OpenOffice is another example if you use their installer.

I put software that doesn't use the distro's package management (self-compiled or just untarred as in your case) into /usr/local.
If it creates it's own dir, I create a symlink to the executable(s) in /usr/local/bin so that I don't have to change $PATH to include everything.

Just untar your package in /usr/local/bin and create a symlink (as root). 
/usr/local/bin should be in the $PATH of everyone.

---

### Post by Verlager on 2004-11-04
I think I see....I appreciate your help, btw! I did this as root:

cd /home/verlager
tar -xzf thunderbird-0.9-i686-linux-gtk2+xft.tar.gz

Now do I move the thunderbird dir to /usr/local or to /usr/local/bin ?
mv thunderbird /usr/local/bin or mv thunderbird /usr/local/ ?

> 
I put software that doesn't use the distro's package management (self-compiled or just untarred as in your case) into /usr/local.
If it creates it's own dir, I create a symlink to the executable(s) in /usr/local/bin so that I don't have to change $PATH to include everything.

It creates its own directory (thunderbird). I'm still confused. BTW, I will be installing dozens of programs as per these instructions, so what you tell me is the method I will use, and I hope it's a good one.

---

### Post by jdong on 2004-11-04
Why not grab it from the repository? Isn't thunderbird at least in Universe?

---

### Post by Juergen on 2004-11-04
[QUOTE=Verlager]cd /home/verlager
tar -xzf thunderbird-0.9-i686-linux-gtk2+xft.tar.gz

Now do I move the thunderbird dir to /usr/local or to /usr/local/bin ?
mv thunderbird /usr/local/bin or mv thunderbird /usr/local/ ?[/QUOTE]
It's your computer, so do it the way you like ;-) 

I'd put it in /usr/local/bin just to keep the basic /usr/local structure clean, but you really are free to find your own way - you could even create something like /usr/local/appdirs and use that.

And if you decide to move these app-dirs later on, the only things to adjust are the symlinks in /usr/local/bin, so just go ahead - it won't hurt  ;)

---

### Post by mercurus on 2004-11-04
[QUOTE=Verlager]I think I see....I appreciate your help, btw! I did this as root:

cd /home/verlager
tar -xzf thunderbird-0.9-i686-linux-gtk2+xft.tar.gz

Now do I move the thunderbird dir to /usr/local or to /usr/local/bin ?
mv thunderbird /usr/local/bin or mv thunderbird /usr/local/ ?


It creates its own directory (thunderbird). I'm still confused. BTW, I will be installing dozens of programs as per these instructions, so what you tell me is the method I will use, and I hope it's a good one.[/QUOTE]

Personally, I'd move the whole unpacked, thunderbird directory to /opt (as root). The result would be an /opt/thunderbird/ directory. Within that directory, you need to find the binary that actually runs thunderbird - probably called mozilla-thunderbird or similar. Once you've located that file, you need to create a symbolic link from the /usr/local/bin tree to the /opt/thunderbird directory.
```
sudo ln -s /opt/thunderbird/thunderbird-binary /usr/local/bin/thunderbird
```
Once that link is established, you should add a link to /usr/local/bin/thunderbird to your applications menu, or desktop shortcuts as appropriate.

However, **The Easy Way** TM is to open Synaptic, make sure it is using the Universal Repository, and then install the mozilla-thunderbird package. This will download, unpack, and integrate thunderbird into the filesystem, make it available on your desktop, and do all the nasty, complex, detailed stuff for you. This is the joy of apt ! I'd strongly recommend this, unless you have a compelling reason to use the binary package provided by the thunderbird project.

Cheers
mercurus

---

### Post by jwb on 2004-11-04
If you're the only user on the box...... make it easy on yourself.

Make a directory under your home directory called "Programs". (Or don't......) :-)

Extract the Thunderbird directory there. You should have ~/Programs/thunderbird.

Make a link to the executable ("shortcut") whereever you'd like..... desktop, say. 

Right click on Desktop -> Create Launcher -> Name=Thunderbird, Command= /home/yourusername/Programs/thunderbird/thunderbird and click "OK".

(Adjust the icon if you wish..... it's in the tbird directory under icons/.)

Now you can launch Thunderbird. Next time there's an update, rename the old thunderbird folder "thunderbird-old" or sumfin like that, drop in the new thunderbird folder, and away you go. this way, as soon as they release a new one, you upgrade immediately. if it breaks, delete the folder, rename the old one back to thunderbird, and you are back in bidness.

Of course..... like you said..... if you wanna install for multiple users, do that other stuff in the other answers. :-)

---

### Post by Verlager on 2004-11-04
Hmmmm. OK, I installed the thunderbird directory into /usr/local/bin and now I need to create a symlink within the user path that refers to the executable (thunderbird) which is in the /usr/local/bin/thunderbird directory.

**[COLOR=DarkGreen]sudo ln -s /usr/local/bin/tbird  /usr/local/bin/thunderbird/thunderbird[/COLOR]**

So, as a user, I should be able to type:** tbird **and the symbolic link  _/usr/local/bin/tbird_ should invoke the executable _/usr/local/bin/thunderbird/thunderbird_ because the user is pathed to that tbird symlink. (stop me anytime if you think I'm wrong)

verlager@ubuntu:~ $[COLOR=DarkGreen] **$PATH**[/COLOR]
**bash: /usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games: No such file or directory**
Path looks OK,  except for the last entry of /usr/games which I would love to permanently edit out, btw.

verlager@ubuntu:~ $[COLOR=DarkGreen]** tbird**[/COLOR]
**[COLOR=Red]bash: tbird: command not found[/COLOR]**
verlager@ubuntu:~ $[COLOR=DarkGreen] **ls /usr/local/bin**[/COLOR]
**tbird  thunderbird**

[SIZE=3]**Yet, it doesn't work. Why? **[/SIZE]

---

### Post by BugsyMalone on 2004-11-04
[QUOTE=jwb]If you're the only user on the box...... make it easy on yourself.

Make a directory under your home directory called "Programs". (Or don't......) :-)

Extract the Thunderbird directory there. You should have ~/Programs/thunderbird.

Make a link to the executable ("shortcut") whereever you'd like..... desktop, say. 

Right click on Desktop -> Create Launcher -> Name=Thunderbird, Command= /home/yourusername/Programs/thunderbird/thunderbird and click "OK".

(Adjust the icon if you wish..... it's in the tbird directory under icons/.)

Now you can launch Thunderbird. Next time there's an update, rename the old thunderbird folder "thunderbird-old" or sumfin like that, drop in the new thunderbird folder, and away you go. this way, as soon as they release a new one, you upgrade immediately. if it breaks, delete the folder, rename the old one back to thunderbird, and you are back in bidness.

Of course..... like you said..... if you wanna install for multiple users, do that other stuff in the other answers. :-)[/QUOTE]
 jwb, that's a terrific idea. I never thought of doing something like that.  Thanks for the tip.

---

### Post by Rui Pais on 2004-11-04
Hi
>  Hmmmm. OK, I installed the thunderbird directory into /usr/local/bin and now I need to create a symlink within the user path that refers to the executable (thunderbird) which is in the /usr/local/bin/thunderbird directory.

**[COLOR=DarkGreen]sudo ln -s /usr/local/bin/tbird  /usr/local/bin/thunderbird/thunderbird[/COLOR]** 

is not the other way around?

**ln -s  /usr/local/bin/thunderbird/thunderbird  /usr/local/bin/tbird**

to remove /usr/games from your path, i suppose that you need to eleminate it from  /etc/profile. (sudo gedit /etc/profile, or vi instead of gedit....)

I use Thunderbird but installed with synaptic (from Universe?...) it's a 0.8 but is ok. I suppose its possible to have both... I have the ubuntu 0.9 Firefox and the new RC2 at /opt... but 2 thunderbird means 2 copies of messages eating disc space...

---

### Post by Verlager on 2004-11-04
Since the theme is now symbolic links, instead of target installation directories, I will post the fresh theme in a new topic. Thank you all for helping!

---

