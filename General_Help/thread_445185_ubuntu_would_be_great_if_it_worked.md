---
title: "ubuntu would be great if it worked"
date: 2007-05-15
forum: General Help
---

### Post by crshbndct on 2007-05-15
i like the interface, i like how stable it is, and i like how adaptable it is.

what i do not like is the fact that i have downloaded upwards of 50mb of crap which is in various states of failed install/half there half not just to get a bit torent client which will let me download a single file from within a torrent. the file is 48.2mb, i have now officially downloaded more stuff to try to get it to work (dependencies which get installed first, then install fails anyway) than the actual file itself. not to mention that i have been trying to get this working for a week. when i started, i had 1155 packages installed on my system. i now have 1207, which have all be attempts to install various dependencies to get various clients to work, and so far, no success at decent gui based torrent client,

for referrence, on windows, i was able to download and install a client in under 2 minutes, and less than 500kb to download. 

and i cant get adobe acrobat reader to install either. at least i have installed it, all went well, bu ti have no shortcuts, "acrobat" at the command line doesnt work and double clicking a pdf file does nothing,

so i am going to give about another week, then linux is gone from my box forever.

---

### Post by eentonig on 2007-05-15
strange, I had a perfectly well working bittorentclient after installing the default Ubuntu. And it has been like that ever since Breezy Badger.

And concerning adobe acrobat reader, I never saw the need to install it, since pdf files were read also from the default install.

Must be something stupid I did.

---

### Post by Ateo on 2007-05-15
*sigh*

Why do people whine so much? Do they think their problems will magically fix themselves with no effort?

---

### Post by artesvida on 2007-05-15
It would be great if you were a little more specific re: the problems you're having.  I know nothing about BitTorrent, but I have successfully installed Acrobat Reader.  (The default PDF reader didn't support javascript-enabled PDF forms).  It wasn't as easy as Windows, but it wasn't that hard.

If you actually want some assistance, you should post more specific information:  what you did, what errors or other messages you encountered, etc.  But perhaps you just want to complain...

---

### Post by wdaniels on 2007-05-15
I agree that there doesn't seem to be many good torrent clients for linux. ktorrent isn't too bad if you're using kubuntu, but utorrent always seems much faster to me and it runs well under wine so long as you're careful to change the settings to "close to tray" instead of "minimise to tray" (otherwise you can end up not being unable to unhide the window).

As for all the package dependencies, yes there can be a lot of extra stuff to install initially but on the other hand, it can eventually save a lot of bandwidth compared to the Windows model where any non-default dependencies always need to be distributed in the installation package for each application.  And if you're bothered by having collected additional software through the dependencies of these other torrent applications now you should be able to clear out any automatically installed dependencies with sudo apt-get autoremove.

You seem to be looking quite pessimistically at a specific case here, remember this is not a commercial product that has been sold to you, it's a community effort and I think you could try to be a little more constructive.

---

### Post by magcius on 2007-05-15
**Number one: Don't compare apples and oranges.**

Applications and Programs are not the same as Packages.

A package could be anything, the equivalent of a DLL file (a system requirement), to a whole office suite. It is just called a "package" for convenience, uploaded to a main server, and downloaded when needed.

I am sure you have, when installing a game, see "You need DirectX X.X for this application to work." or "This program requires QuickTime X.X to work. Install it?" This is what is called a dependency, because the programs depends on it to work correctly. I bet at most 100 of the packages installed on your system are applications, and the rest dependencies.

Dependencies _DO NOT_ slow down the computer at all.

(P.S., on a typical everyday Linux system, that package count would be around 5,000 or 6,000)

**Number two: You probably have a bittorrent client or pdf reader already installed, and do not know it.**

On almost any Linux distribution there will be at least 5 clones of any commercial "name-brand" software.

Example: When I first installed Linux as a test operating system, I tried to get WinZIP to install, little did I know that a "tarball" manager had already come installed on the system. I was used to having to install WinZIP on every windows system I installed.

---

### Post by crshbndct on 2007-05-15
i fully agree with all that, but i am just frustrated that the bittorrent clinet that comes with ubuntu does not have the ability to download a single file from within a torrent. and so far all attempts to install one have failed despite following instructions to to the letter.

if however, someone can tell me how to enable internet access with wine i will be happy as larry.

thanks everyone

---

### Post by zodmaner on 2007-05-15
For you bittorrent solution, I recommend [Deluge]("http://deluge-torrent.org/"). It's (almost) like Azureus that eats less resources. I've use it and it work fine for me (I can't use Azureus because for some unknow reason it stopped downloading a torrent after a while, with Deluge I didn't encounter this error).

---

### Post by zvacet on 2007-05-15
You have Bit torrent,Bit tornado in add/remove,and you can try Deluge or something else.I prefer utorrent runing with wine (it is only way because there is no linux version) and it serve me very well.if you want to installall dependencies when you are install package use aptitude

```
sudo aptitude install file_name
```

and for Acrobat you can install it like this

```
sudo aptitude install acroread
```

---

### Post by crshbndct on 2007-05-15
> **zodmaner said:**
> For you bittorrent solution, I recommend [Deluge]("http://deluge-torrent.org/"). It's (almost) like Azureus that eats less resources. I've use it and it work fine for me (I can't use Azureus because for some unknow reason it stopped downloading a torrent after a while, with Deluge I didn't encounter this error).


yeah i tried deluge

installed all the dependencies, and then attempted to build and install it but just got a bunch of errors.
4 - 5 hours later, after numerous searches i gave up on deluge.

but as i said, how do i enable internet access under wine? i got utorrent working with that, just need to get it to connect to the net now.. :)

---

### Post by DoktorSeven on 2007-05-15
I recommend **ktorrent** for torrenting.  Lets you download single files and everything.  It's in the repos, so run synaptic and search for it or just do **sudo apt-get install ktorrent**.

But if you want to use utorrent under wine, just start up your internet access as normal, and wine should use whatever access you have.

---

### Post by crshbndct on 2007-05-15
thanks a lot guys its all sorted now
i had been having a massive problem with my repos and so i had no multiverse or universe apps.

that was why i had got inot the habit of just downloading source and build/installing stuff.
but its all good now. downloading is going good

---

### Post by spartan777 on 2007-05-15
if you install automatix, you can pick from a lot of different bt clients, including Azureus, which i love to use on both windows and ubuntu. here's a link to install automatix:

[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.3-7.04feisty_i386.deb](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.3-7.04feisty_i386.deb)

there are many other clients. heres a link to download deluge, a client that's been gaining a lot of steam:

[http://www.getdeb.net/download.php?release=735&fpos=0](http://www.getdeb.net/download.php?release=735&fpos=0)

and here's another one called kTorrent. its made for kde, but should work on regular gnome ubuntu too:

[http://www.getdeb.net/download.php?release=792&fpos=0](http://www.getdeb.net/download.php?release=792&fpos=0)

and another bt client called transmission. its very lightweight, the ubuntu analog to uTorrent:

[http://www.getdeb.net/download.php?release=798&fpos=0](http://www.getdeb.net/download.php?release=798&fpos=0)

and again, there are a lot of others to choose from under automatix. you may have taken 2 seconds to dl a good client in windows because all your friends use that, but there is a plethora of good clients for ubuntu, if you'd just look. there's the client that's built in (its installed already), and the ones on synaptic and automatix. also, you don't have to worry about spyware or irritating clients that try to get you to buy them. (like bitlord if I remember).

---

