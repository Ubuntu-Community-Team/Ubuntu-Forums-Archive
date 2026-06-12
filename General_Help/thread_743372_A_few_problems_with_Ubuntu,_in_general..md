---
title: "A few problems with Ubuntu, in general."
date: 2008-04-02
forum: General Help
---

### Post by ac3raven on 2008-04-02
Long story short, I've been trying to fix flash in firefox (I don't get sound) for about a month now, with no luck.  Well, through my efforts, I just caused more stuff to go wrong.  Firstly, I removed libssl via the terminal; that was a mistake.  I saw the terminal removing all my applications (seriously all of them), so, not knowing how to kill the command or revert the changes, I restarted my comp before it was finished removing and to my dismay there was no gui so I reinstalled libssl and libssl-dev and I figured reinstalling gnome would bring the gui back, so I did, then restarted.  thankfully it booted with a gui, but now I have gnome apps like ekiga, totem, evolution and what not, but when I try to remove them, synaptic wants to take gnome with it, which would be of course not a good thing.  Somehow these apps are connected to the actual desktop manager and removing them would remove gnome.  So how do I remove them without doing that?

Secondly, I noticed that when I try to use Inkscape (Awesome program), it maximizes beyond the top panel, so I figured I'd try to fix that and I ended up messing something up with gdm and now my applets are gone (weather, cpu monitor, Geyes, trash, etc) and when I tried to re-add them, I simply can't.

Thirdly, when I try to play a dvd with Totem, it asks me to install libdvdcss so that it can read the encrypted dvd, but I can't seem to find it, and I do have libdvdread, which does the exact same thing, but I can't figure out how to point totem to that package rather than libdvdcss.  I don't like mplayer and I honestly don't know how to open a dvd with vlc (which I prefer).

Here's my thread for my problems with Flash:

[http://ubuntuforums.org/showthread.php?t=730486](http://ubuntuforums.org/showthread.php?t=730486)

I've been using Ubuntu for about a month or two, so yeah, I'm a bit of a noob.  But solving as many problems as I have has made me a little more knowledgeable than a "noob" but still, ANY help would be GREATLY appreciated.

---

### Post by sekinto on 2008-04-02
I can answer your last two problems.

Opening a DVD in VLC:
> 1) Insert your DVD
2) Start VLC
3) File>Open Disc
4) If the device location is wrong, change it
5) Press ok

Installing libdvdcss:
> Do this in a terminal:
1) sudo wget [http://www.medibuntu.org/sources.list.d/YOUR](http://www.medibuntu.org/sources.list.d/YOUR) VERSION OF UBUNTU.list -O /etc/apt/sources.list.d/medibuntu.list
2) wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
Then do this:
1) Open Synaptic Package Manager
2) Click search
3) Type "libdvdcss" in the name field and select "name" instead of "name and discription"
4) Select "libdvdcss" to be installed and hit apply

Edit:
Where it says "YOUR VERSION OF UBUNTU" replace that with the version of Ubuntu you use, example: Feisty, Gusty, Hardy, et cetera.

---

### Post by ac3raven on 2008-04-02
what's the public key for that?

---

### Post by sekinto on 2008-04-02
[http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg)

---

### Post by ac3raven on 2008-04-02
okay, one down.

---

### Post by sekinto on 2008-04-02
About flash not working in Firefox:
What version of Firefox are you using (Firefox 3b4, Firefox 2, et cetera)?
And did you use the official Adobe Flash installer or did you use Synaptic to install it?

---

### Post by ac3raven on 2008-04-03
I'm using the latest version of FF 2.  And I don't remember if I installed it via the website or synaptic, what's the difference?

---

### Post by ac3raven on 2008-04-03
okay, I fixed my applets, though I don't quite know how I did that, and I reinstalled flash via the website, and it's working fine...for now, hopefully it will stay that way.

---

### Post by ac3raven on 2008-04-03
Flash stopped working.  So I guess that wasn't a real solution.  Back to square (or circle) 1 with my flash issue.

---

