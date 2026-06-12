---
title: "evolution 2.12.1 is quite buggy"
date: 2007-11-11
forum: General Help
---

### Post by ctsdownloads on 2007-11-11
Well, Gutsy has been fairly good with the exception of Evolution 2.12.1. Seriously, Evolution in Feisty, Edgy and even Dapper just worked. But here is the problem with 2.12.1:

Whether it be one POP Account or all of my POP accounts, there is a NASTY bug that has it prompting for the POP password every time I start the program. Very sloppy and unneeded. If this bug is not fixed, it will mean that Ubuntu's default mail program is bothersome and buggy to point of being a distraction out of the box.

No, it is not the password, the mail servers or me - this is a bug that needs to be dealt with. Too bad it has been marked as low priority...because apparently having our email program become NAGWARE is not that big a deal.

Seriously, would **love** a work-a-round or a deb package for Evolution from Feisty. :mad:

---

### Post by Nano Geek on 2007-11-11
Did you tell it to remember the password when it asks?

---

### Post by ctsdownloads on 2007-11-11
Sure did - and thanks for responding. :) Any other thoughts?

Still tinkering,  it's almost like it only does this when I have my exchange server enabled along side the POP Servers. So I am doing some more testing there.

---

### Post by ctsdownloads on 2007-11-11
Did more tinkering, it turns out that if you are using any number of POP accounts, it will prompt for a password every time, yet during a send receive, things are just fine. Lovely...

And the Exchange account was disabled, so this is a pop mail issue.

Anyone have the older, I mean working version of Evolution from Feisty that can be installed into Gutsy. 2.12.1 is sucking harder by the moment. :confused:

---

### Post by Nano Geek on 2007-11-11
You could use an older version of Evolution. Here's the link.
[http://www.gnome.org/projects/evolution/previous.shtml](http://www.gnome.org/projects/evolution/previous.shtml)

If you don't know how to compile it I'll tell you.

---

### Post by ctsdownloads on 2007-11-11
Willing to give it a try, assuming it does not mean chasing down too many dependencies besides build-essential, which I have. How is no one else screaming about such a painfully obvious bug with Evolution?

[https://bugs.launchpad.net/evolution/+bug/140460](https://bugs.launchpad.net/evolution/+bug/140460)

This is exactly what happens and how one has to work around it:


> ...click Cancel on all of them (for each accounts on different pop3 servers) and then click on Send / Receive there is no problems.

---

### Post by Nano Geek on 2007-11-11
Yes it is annoying, but I think they gave it a low priority is because it doesn't cause any large problems that could cause your computer to crash or something like that.

And for Evolution dependencies, just run **sudo apt-get build-dep evolution** and you should be all set.

---

### Post by ctsdownloads on 2007-11-11
LOL, this takes me back - literally two minutes and already I had to install bison and something called "atk", which apt did not find, with all main repos enabled...

Not sure what sudo apt-get build-dep evolution was supposed to do...

> E: Build-dependencies for evolution could not be satisfied.

---

### Post by ctsdownloads on 2007-11-11
Alrightly, looks like compiling is not happening - spent the better part of two hours battling error after unknown dependency, the "released" version in Gutsy is a mess and everyone seem fine with it. Wonderful. I guess I will advice my clients that Evolution is simply not dependable and recommend something that Ubuntu/GNOME devs have not "improved" like Thunderbird....sigh. ](*,)

---

### Post by Nano Geek on 2007-11-11
> **ctsdownloads said:**
> Alrightly, looks like compiling is not happening - spent the better part of two hours battling error after unknown dependency, the "released" version in Gutsy is a mess and everyone seem fine with it. Wonderful. I guess I will advice my clients that Evolution is simply not dependable and recommend something that Ubuntu/GNOME devs have not "improved" like Thunderbird....sigh. ](*,)If you still want it, here's the link to the .deb packages for all of the versions of Evolution since Dapper.
[http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/)

---

### Post by ctsdownloads on 2007-11-12
asjdfwejqrfjcvm msz34rq33, thank you much. :) I will give this a shot, thanks for all your help. Seriously, I really appreciate your help with this.

-----

_Note to devs:_

I certainly hope that 'minor' issues like this are not even closed to be acceptable in the next LTR (Heron) as Ubuntu will lose out to other distros because of this. 

I love Ubuntu, but anytime a bug takes place with anything to do with the big three uses of an OS - *browsing, email or office*, it needs to be given _serious priority_, imho. Again, I use and covert people to desktop Linux professionally, so it make me look stupid when this type of obvious application bug is given a green light to pass into a released version. At the very least, a know bug in the release notes would have been appropriate, so I can then use Kontact.

If Canatical things that the next LTR can have this kind of bug as "not a big deal" in the business world, they are sorely mistaken - people will not switch to a client like this which a bug that is soooooo obvious. Very disappointing.

---

### Post by ctsdownloads on 2007-11-12
> If you still want it, here's the link to the .deb packages for all of the versions of Evolution since Dapper.
[http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/)

Very cool. Think there will be any issues with shared libs if I try to use an older version? I suspect so, but will give it a try regardless.

---

### Post by Nano Geek on 2007-11-12
> **ctsdownloads said:**
> Very cool. Think there will be any issues with shared libs if I try to use an older version? I suspect so, but will give it a try regardless.I kinda doubt there would be, but there's only one way to find out. :)

---

### Post by ctsdownloads on 2007-11-12
> I kinda doubt there would be, but there's only one way to find out.

Too true. ;)

I am also looking into Frankensteining two Ubuntu releases together, perhaps we should call it Ubuntu "Geisty"? [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

Gutsy's kernel and Feisty's working apps. Hell, the only thing about Gutsy that I found compelling was the new wireless stack. That, was worth the upgrade for sure, once I immediate dumped NM for Wicd, of course, as it works with more than just wext WPA drivers.

---

### Post by ctsdownloads on 2007-11-12
Well, tried installing 2.10.3 and here is the result:

> ~$ evolution
evolution: error while loading shared libraries: libplds4.so: cannot open shared object file: No such file or directory

The only fix is to disable automatic checking for mail, which makes reverting back to another email app or blending the two releases together like I mentioned previously seem like the only alternative. Hope this is resolved before Heron or we are going to see a lot of enterprise Ubuntu users dumping this distro, its really too bad. We'll see how it works out, though. :(

---

### Post by Nano Geek on 2007-11-12
> **ctsdownloads said:**
> Well, tried installing 2.10.3 and here is the result:



The only fix is to disable automatic checking for mail, which makes reverting back to another email app or blending the two releases together like I mentioned previously seem like the only alternative. Hope this is resolved before Heron or we are going to see a lot of enterprise Ubuntu users dumping this distro, its really too bad. We'll see how it works out, though. :(What packages did you install from that site? It could be that there's another one that Evolution needs to work properly.

---

### Post by ctsdownloads on 2007-11-12
evolution_2.10.1-0ubuntu2_i386.deb
evolution-common_2.10.1-0ubuntu2_all.deb
evolution-plugins_2.10.1-0ubuntu2_i386.deb

And before doing this, I had already made sure to:

> sudo apt-get remove evolution evolution-common evolution-data-server evolution-data-server-common libexchange-storage libedata-ca libedata-book

as not to cause any conflicts and start off fresh. After re-installing the current version I also tried:

> sudo apt-get remove evolution evolution-common

as to leave the other pieces there, just for giggles.

---

### Post by Nano Geek on 2007-11-12
> **ctsdownloads said:**
> evolution_2.10.1-0ubuntu2_i386.deb
evolution-common_2.10.1-0ubuntu2_all.deb
evolution-plugins_2.10.1-0ubuntu2_i386.deb

And before doing this, I had already made sure to:



as not to cause any conflicts and start off fresh. After re-installing the current version I also tried:



as to leave the other pieces there, just for giggles.The only thing that I can think of is to download the older versions of all those programs that you un-installed.  It could be that Evolution is missing something that's provided in one of those packages.

---

### Post by ctsdownloads on 2007-11-12
Thought of this, too. Did a search and replace gutsy with feisty in the sources.list - no go. It'll download, but there is something shared with the GNOME desktop that has this hitting a wall I think.

---

### Post by Nano Geek on 2007-11-13
> **ctsdownloads said:**
> Thought of this, too. Did a search and replace gutsy with feisty in the sources.list - no go. It'll download, but there is something shared with the GNOME desktop that has this hitting a wall I think.You might want to try sticking with Feisty then. I'm sure that the problem will be cleared up in time for Hardy. I've often had small little bugs like this pop up in one release and then be gone in the next. Sorry I couldn't help you get it working.

---

