---
title: "Lacks obvious applcation defaults (.deb and .run)"
date: 2013-01-15
forum: General Help
---

### Post by Time Sheep on 2013-01-15
I have been coming and going to and from Ubuntu since version 6-something and have been wondering about the very same thing each time, and I still do.
Ubuntu claims to be extremely userfriendly and intuitive to use, but the first thing you have to do is to install the video card drivers.
This is probably the least userfriendly, yet the most daring and complex operation I have ever, and will ever carry out.
Either way, I wanted to ask why the default file handler for .run files is GEdit and .deb files just ask which application you'd like to start them with.
Both AMD and NVidia supply their drivers through scripts, saved as .run files, and when you download it and double-click it to run (Which any normal pc-user would do) you get a text file you don't understand, when you just expected the installer to start.
Same goes for deb packages. Why isn't the default action for those to be opened using dpkg? It works, and it's the only ideal thing to do with a deb-file anyway.

I really can't figure this out. What is the logical reason for this mess? I don't find it userfriendly, in fact I spend 1-2 hours getting the video driver working every time I install it on a new PC.

---

### Post by dino99 on 2013-01-15
do you really need to understand, or are simply whining and insulting the Debian/Ubuntu people here ?

---

### Post by Time Sheep on 2013-01-15
> **dino99 said:**
> do you really need to understand, or are simply whining and insulting the Debian/Ubuntu people here ?

No, I don't understand. I'm asking a question because I don't see the connection.
I like Ubuntu, and I like the community. I'd love to be able to use Ubuntu, but it's always been a hassle to me. Mainly due to this, and failing drivers, it scares me away. I like Unity, I like the open source and most of all I like Linux because it goes well with my servers. I just never succeeded in using a Linux-based desktop system without fighting this kind of issues.

---

### Post by dino99 on 2013-01-15
Sorry to have been rude, but i was having some doubt.

Here is how im doing installation:

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

so, the installer detect the hardware and then install & configure the required drivers, thats it.

but in some cases, we need to change the default settings when:
- the hardware is too new, and the kernel is not uptodated enough
- some hardware are not supported at all: either too new, or too old (so we need to install either the latest kernel from trunck; or an old one when that hardware was supported)
- some hardware like Via are badly supported

To conclude, watching the compatible hardware list is a good idea before installing. But the iso also let you test before installing. Googling around "ubuntu+hourhardwaremodel" can also help.

Of course, you need to be "flexible" enough to think linux instead of windows or mac

---

### Post by 3rdalbum on 2013-01-15
> **Time Sheep said:**
> I have been coming and going to and from Ubuntu since version 6-something and have been wondering about the very same thing each time, and I still do.
Ubuntu claims to be extremely userfriendly and intuitive to use, but the first thing you have to do is to install the video card drivers.
This is probably the least userfriendly, yet the most daring and complex operation I have ever, and will ever carry out.

You're doing it wrong, then.

For quite a few years, Ubuntu has come with a program that can automatically identify what drivers you need, download them, and install them for you. It's one of the easiest things you can do on Linux. Sorry you haven't noticed this program? It's been known under various names ("Restricted drivers", "Additional Drivers", "Jockey" etc) but now if you go to Software Center, go to the Edit menu and then go to Software Sources, you'll find it as the last tab. It's not as obvious as it was in 12.04, but there's an indicator and notification bubble that pop up on first boot to draw your attention to it.

If you decide to use the manual method, it's not Ubuntu's fault - and the fact that the manual method is more difficult than it needs to be, is the fault of Nvidia and AMD, not Ubuntu.

> Either way, I wanted to ask why the default file handler for .run files is GEdit and .deb files just ask which application you'd like to start them with.

There's no file handler for ".run" files any more than there is a file handler for ".xyzheylookatme" files. ".run" is nothing - it's not a standard, it's not anything specific. When faced with a file that the system knows nothing about ("What the heck is a .run file?") it makes the best guess it can.

When you make the file executable, though, the system first tries executing it, at which point the magic happens.

> Same goes for deb packages. Why isn't the default action for those to be opened using dpkg? It works, and it's the only ideal thing to do with a deb-file anyway.

The default is to open it with Ubuntu Software Center for installation. If it doesn't work on your computer, you should report a bug.

Ubuntu has sanely handled this since Ubuntu 6.06, and had the driver installer thingy since - well, I think it was in 8.04, but it might have appeared earlier.

If you're using a version of Ubuntu that predates 6.06, then of course you'll have a bad time.

---

### Post by asmoore82 on 2013-01-15
> **Time Sheep said:**
> the first thing you have to do is to install the video card drivers.

"Have to do" is a loaded statement in this context. You go on to mention clicking on ".run" and ".deb" files and not getting the expected result. If your GUI is up and running sufficiently enough to where you *can* click on anything, then strictly speaking, you don't "have to do" anything further with video drivers.

That being said, I fully understand wanting to get the most performance out of high-end video cards even if it requires the use of non-free modules. But it is important for everyone to understand that the reason these cannot be "baked in" to Ubuntu seamlessly to begin with is precisely because they are "non-free" modules.

And on top of that all, Ubuntu is by far the easiest system I've ever seen to get the right video drivers installed on, Windows included. I never fiddle around with AMD or nVidia's web sites any more. I just let Ubuntu's "Hardware Driver's" tool do it's magic.

I almost caught myself agreeing with you on the default actions for .run and .deb files, but on 2nd thought, they can be dangerous operations and are likely unnecessary. As strange as it sounds, running into something unexpected here and asking for help may be the best thing for completely new users. Or else they can spend years using */Linux to act out obsolete paradigms of other OS's.

---

### Post by Time Sheep on 2013-01-15
My point was that I started using Ubuntu when it was around version 6.06, not that I'm using that one now.

Last time I tried Ubuntu, which was at 12.04 LTS, I used the restricted drivers tool and installed the recommended driver for my NVidia card, which was a 9800 GTX+. This didn't work as expected and I couldn't boot Ubuntu, so I formatted and tried again. At this point I went for the beta release and proceeded like this through the list of drivers, all of them producing their own special error.
I supposed it was my old graphics card and tried with a GTX 5xx-series encountering the same amount of problems, but actually got it working with the shell scripts presented on NVidia's website. Now I'm sitting with an AMD Radeon HD 7970 and Ubuntu 12.10.
I guess my main issue was my inability to find the drivers, because I expected the notification like the one on 12.04.

I clearly understand why the drivers aren't included, I was merely commenting on the means of installing these with scripts and DEB packages.

As for the DEB packages, mine defaulted to opening them with Archive manager for as long as I remember. I always ended up at a terminal and ran dpkg path/to/package.deb.
I honestly haven't tried it this time.

Thanks for the clarification on the .run thing. First time I saw it, I didn't think it was a standard either (And I normally dub my shellscripts .sh), but I've seen them so often that I believed it must be some sort of standard.
I guess not.

Again, thanks, I'll try finding the drivers in the software center on this computer then. If it works, I just want to get around the other problem I have with the interface and then I'll do the switch (I've been waiting for Steam for years now) :)

EDIT: And this would happen to be my other issue: [http://ubuntuforums.org/showthread.php?t=2105160](http://ubuntuforums.org/showthread.php?t=2105160)

---

### Post by oldos2er on 2013-01-15
Much has changed since 6.06, as I'm sure you know. In newer versions, double-clicking a *.deb should open it in Software Center with the option to install it. 

It's a good rule to follow the official and community wiki for the latest info: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

A *.run file is text file (similar to a shell script), so naturally it opens in gedit. If one intended to run it as an executable file, you'd do this in a terminal by setting the executable bit first. I agree this is not newbie-friendly, but this should not be necessary for anyone, newbie or not, unless you have some unusually odd hardware. Nvidia cards, unless they're quite old, wouldn't fit that description.

---

