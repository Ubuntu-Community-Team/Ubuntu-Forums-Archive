---
title: "Ubuntu is running in low-graphic mode"
date: 2013-01-01
forum: General Help
---

### Post by barnettgs on 2013-01-01
> Your screen, graphic card, and inpirt device settings could not be detected correctly  You will need to configure these yourself.

I have already searched for similar problems on this forums but whenever I type 'sudo apt-get......', I get dpkg --configure error, something like that.  I am not sure why sudo apt-get commands won't work?

What's the first command should I use for this display problem?  It is intel integrated graphic and this PC is booted up fine using live CD.  Ubuntu is around 2 years old I believe but I don't know which version.

I am doing this for my friend's cousin.

---

### Post by JiuJitsu500 on 2013-01-01
'sudo apt-get' means you're asking the computer to run apt-get (ubuntu's aptitude) as root (necessary in linux to change package info) to grab something from the internet... but if your package info is messed up, linux is at least smart enough to tell you that it cannot and will not modify the system without reconfiguring it so it can't mess it up.

the dpkg --configure means you need to run the very command it's telling you is wrong, should be:

sudo dpkg --configure -a
OR
sudo dpkg-reconfigure

I seriously don't know where I got that first command from, but I'm pretty sure I've used it before. Try the second one first.

This will reconfigure your entire package database, then allow the debian packager to properly mess with the system... so apt-get will work again.

I still think that's all magic under the hood, and I've never really learned why you'd need to reconfigure it either. But, ti's worked for me a number of times before, mostly from something stopping the dpkg from finishing. The at-get is most likely what you'll need to re-install the basic video drivers so you can get out of low-graphics. I've been stuck there for days on end, and it's very annoying. Once you do that, I can look to see what those package names are (vesa, etc drivers) and post a command for you from there. First though, reconfigure that mess! Might actually be all you need to do is re-configure...hmmm...

---

### Post by barnettgs on 2013-01-01
> **JiuJitsu500 said:**
> sudo dpkg --configure -aThanks!

That did the trick.  It was exactly the first command I saw but I did not understand it and I thought I was doing it wrong.

UPDATE: The desktop is loaded fine and a pop up saying something about a partial upgrade. I was just told that the PC was turned off while the Ubuntu was in the process of upgrading/updating so this explains why it has happened.

Now doing a partial upgrade and hopefully this should fix the mess.

It is Ubuntu 11.04 (I think) and a pop up saying it is no longer supported.  Should it be upgraded to 11.10 or can it be upgraded to other similar but latest distro such as Linux Mint LTS?

Cheers

---

