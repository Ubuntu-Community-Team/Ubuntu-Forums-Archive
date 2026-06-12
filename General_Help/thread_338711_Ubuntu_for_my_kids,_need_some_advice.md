---
title: "Ubuntu for my kids, need some advice"
date: 2007-01-14
forum: General Help
---

### Post by Negative on 2007-01-14
Greetings and salutations.

I am currently downloading Ubuntu to install on a new computer.  Here's the deal:  I run 5 computers between work and home.  2 of the 4 are dual boot with WinXP and Fedora Core.  One at home (my desktop) and one at work.  the 2 others are sole WinXP systems (work laptop, and wifes laptop).  I run FC because I do like all the initial proggies and developer apps that is comes with.  I also like the ability to choose to use KDE or Gnome, etc.

I am NOT here to start a flavor war, or anything like that, I am merely seeking some advice.  The 4th computer is a little desktop build I made for my 3 kids.  Ages are 12, 14 and 16.  2 boys (12 and 14) and a girl (16).  I was doing some thinking and decided I want them to have their own computer.  However, I am not happy with Windows, so I thought about setting them up with a nice *Nix distro.  After some research I decided on Ubuntu (I think they will enjoy Gnome more than KDE, but mainly because I do :) )  Anyway, I have been with FC since it's inception, and have never had to worry about what to install or not install etc.  I have never EVER had to manually download an RPM or anything like that.  Everything I need comes on the initial install disks with FC.

But I feel that FC is a bit overwhelming for the kids.  the youngest, just got an interest in computers at all, the other 2 know MSN messenger and myspace, some Word and power point.  That's about it.

What I am looking for is some advice on what you know of that would be nice to make sure is on the Ubuntu Harddrive for the kids.  This will be their computer, and their computer only.  Except I will be there to help as much as I can, but I work mainly over night, so when they are on it I will be asleep :)

I am interested in programs, games, and such that might not be easily accessible to them right off the bat.

Keep in mind that although I can fiddle my way around FC, I am no Linux geek (although I hope to be one day!)  I am primarily a Windows guy, but I try to learn more every day.  It is a bit tough I will admit, but I won't give up.  Anyway, back to my issue.

I want the kids to have internet, open office, and drawing program capabilities.  So I have firefox and epiphany, openoffice and Gimp.  That much I know.  But I also want them to ENJOY being on their computer, and to learn from it as well as play with it.

So I reach out to you and ask what I should ensure is readily available to them when I have Ubuntu installed?

Any comment or advice is welcomed!

Thank you in advance.

Neg

---

### Post by Biggus on 2007-01-14
They'll probably want one of those instant messaging things, I have one installed called 'Gaim', but I've never used it, so I couldn't advise if its any good or not.

One of my friends who is a responsible parent type was overjoyed when he saw Stellarium, its a program which tells you where things are in the sky, for want of a better adjective. He reckons that its exactly the sort of fun, educational thing his kids go for.

Google Earth can be time consuming, although not neccessarily educational.

Celestia can be quite fun and educational too.

---

### Post by rabid9797 on 2007-01-14
well, first off, if any of your kids use the computer for gaming of any kind that isn't internet games, your in a bit of a sticky situation, as ubuntu wasn't designed(and basically every other *nix distro) for gaming.

BUT if they use it as just an average computer user, there are a couple things you should consider installing:

Automatix - [http://getautomatix.com](http://getautomatix.com) - all in one utility for installing basic programs that don't come with ubuntu initially(ex: audio/video/dvd codecs, multimedia software, firefox plugins, etc.)

Gaim - (in ubuntu repo) - alternative for trillian(AIM/MSN/Yahoo) etc.

Songbird/Amarok/Realplayer 10 -(if you need helping finding them ask) - some of the best multimedia programs(akin to windows media player). They play music, videos, you can keep your files in a library, etc.

Adobe Flash Player 9 - installs first time you find flash on firefox 2.0 - essential for surfing web with multimedia content.

Frostwire - [http://frostwire.com](http://frostwire.com) - P2P client(limewire without the viruses and DRM potential). if you don't have quams against downloading music for free, this is a must.

streamtuner - (in ubuntu repo's) - internet radio program, has tons of presets.

Armegetron - (in ubuntu repo) - Tron like game, very addicting.

Picasa - (automatix) - photo manager

Google Earth - (automatix) - who doesn't have fun with this =P

Myth TV - (in ubuntu repo) - internet tv, lots of channel and variety.

thats all i can really think of off the top of my head. xgl/compiz/beryl eyecandy would keep their attention(and their friends), i know its kept me occupied for hours:mrgreen: , but might be too far beyond your technical expertise. if you want more information, ask or search for "xgl beryl" in the howto forums.

---

### Post by Azakus on 2007-01-14
[Edubuntu]("http://www.edubuntu.org/") is an Ubuntu distro designed for children.
You might try that one for your younger children.

---

### Post by meng on 2007-01-14
Gaim is fairly straightforward to configure and use for those with hotmail accounts, just don't expect webcam conferencing to work.

As for drawing and kids, GIMP isn't really a drawing program as such, but it depends what you mean by drawing program. Tuxpaint is a drawing program, but it's pitched at a slightly younger age group. I've never used it, but I've heard it's good. [http://www.tuxpaint.org/](http://www.tuxpaint.org/)

---

### Post by peabody on 2007-01-14
> **Negative said:**
> Greetings and salutations.
...
I want the kids to have internet, open office, and drawing program capabilities.  So I have firefox and epiphany, openoffice and Gimp.  That much I know.  But I also want them to ENJOY being on their computer, and to learn from it as well as play with it.

So I reach out to you and ask what I should ensure is readily available to them when I have Ubuntu installed?


Well, GAIM for instant messaging (which I believe is installed by default).  GAIM's compatible with just about all versions of IM (MSN, AIM, etc).  Do they have MP3 players/cell phones and a Music Collection?  You probably want to install Banshee then.  Do they watch DVDs or download movies from the Internet?  You'll want to look into codecs and DVD playback (this can be a pain, there's legal issues).  Digital cameras are fairly well supported out of the box in Ubuntu, but they may want to look into different packages for managing their photos.  You probably want to make sure they can print, etc.

YouTube is popular with the kiddies these days, you probably want to make sure Flash is working.  Maybe the official Java plug-in as well.

Someone suggested this...

> 
Myth TV - internet tv, lots of channel and variety.


This is PVR software that's fairly complicated to setup.  Probably not what you want unless they have cable/satellite to their room.

Here's something to note about Ubuntu that are different from FC--Ubuntu is Debian based, so uses debian packages and the concept of repositories (which if you're familiar with yum in FC, it's basically analogous).  So, you don't look for RPMS[1] when finding obscure software, you look for debs, but hopefully you'll never have to do that as the Ubuntu repositories should have everything you need.

Good luck.

[1] admittedly there's a package called alien which tries its best to convert an RPM into something a debian based distro can use, but you probably don't want to have to resort to this unless you absolutely have to.

---

### Post by SuperMike on 2007-01-14
I think I concur with rabid9797, but I'll add some on to that:

* If they get an iPod, try gtkpod, jokosher, and amarok and see which one you like better. My experience, however, is that iPods don't work as well with Linux as much as other MP3 players do. My favorite MP3 player is Sandisk's Sansa, and I use ordinary File Browser (aka Nautilus) to upload songs to it.

* If they like games, install zsnes and download a bunch of SMC files.

* Try a desktop theme that they might like. If they seem cautious and don't want to use it because it doesn't look like windows, consider a theme like this:

[http://www.gnome-look.org/content/show.php?content=41095](http://www.gnome-look.org/content/show.php?content=41095)

* If you don't want to purchase separate computers, there's some projects I think out there that can help you take a new, fast computer and share it multiple times with separate keyboards, monitors, and OS logins. Another route is to purchase thin client PCs that connect back to a fast computer that's running something like NX or LTSP.

* You'll probably want to install Tinyproxy. See my signature line for how to get that going.

* My daughter and I use a technique to get stuff from YouTube for our MP3 players and this is listed in my signature below -- you might want that.

---

### Post by Negative on 2007-01-14
Wow!  Thanks for all the quick and full-of-information-posts!  That was fast!  I wasn't expecting such a quick answer!  

I have a list going now (I forgot GAIM, I use it on FC as well)

Yes they have their MP3 players, and digital cameras and what not.  Gimp is what they use know (just the Adobe version ;) ) I use Gimp, perhaps "drawing" wasn't the best word to use there.

Of course they will have Flash and Java, daddies websites require them both :D

Again, thank you for the ideas, I will look into each of them and if you think of any more, please let me know!

My linux days are spent behind ftp clients and emacs, LOL  I forgot about all the fun stuff out there for them!

---

### Post by meng on 2007-01-14
> **Negative said:**
> Wow!  Thanks for all the quick and full-of-information-posts!  That was fast!  I wasn't expecting such a quick answer!
That's the best feature of Ubuntu - I'll bet Fedora Forum is nowhere near as good. (I wouldn't have a clue what it's like, since I've never been there.)

---

### Post by Negative on 2007-01-14
> **SuperMike said:**
> I think I concur with rabid9797, but I'll add some on to that:

* If they get an iPod, try gtkpod, jokosher, and amarok and see which one you like better. My experience, however, is that iPods don't work as well with Linux as much as other MP3 players do. My favorite MP3 player is Sandisk's Sansa, and I use ordinary File Browser (aka Nautilus) to upload songs to it.


Mine have the samsung yp-z5.  I can't stand ipods, so therefore *they* can't stand ipods (they want to be just like me, LMAO)

> 
* You'll probably want to install Tinyproxy. See my signature line for how to get that going.

* My daughter and I use a technique to get stuff from YouTube for our MP3 players and this is listed in my signature below -- you might want that.

Great!  I will check those out for sure!

---

### Post by rabid9797 on 2007-01-14
glad we can help out. :D

you really shoudl seriously consider xgl/beryl, it makes the whole linux experience more fun(as long as the computer can handle the graphics load)

---

### Post by Negative on 2007-01-14
> **meng said:**
> That's the best feature of Ubuntu - I'll bet Fedora Forum is nowhere near as good. (I wouldn't have a clue what it's like, since I've never been there.)

I can't complain, nor compare the 2 forums.  I have never had a complaint about FC's forum, helpful as well over there. I haven't asked this type of question there, so I am not sure onthe quality of responses, all my other FC questions have been more hardware based, so I only needed one or 2 posts :D

I think it's the Linux community as a whole that is by far superior and helpful, not flavor based at all (although I have heard some horror stories from those Mandriva folk.

---

### Post by meng on 2007-01-14
Actually I was joking, but it wasn't very clear that I was joking (and it wasn't very funny anyway).

---

### Post by SuperMike on 2007-01-14
Oh, and one more thing. Right after I posted this note, my daughter came over to me and said she didn't save her Abiword document for her class, and it crashed. She thought she had lost everything. I asked if she saved it at least once because the program auto-saves every 5 mins. by default after that and she said she had not saved it at least once. She was in a panic. The first thing I did was tell her that in the future she's going to want to save her doc at least once. Second, I changed the auto-save to every 2 mins. in Abiword. Third, I did something **that you cannot do on Windows!** I went to her Ubuntu computer and did:

$ sudo strings /dev/mem | grep -i dinosaur > /home/family/C:/docs/saved.memory1.txt
$ sudo strings /dev/mem | grep -i temperature > /home/family/C:/docs/saved.memory2.txt

...because she was writing a paper on dinosaur eggs and had at least these two keywords in there. She then opened the text files, highlighted stuff she had previously typed, pasted it back into Abiword, and re-edited it. All was not completely lost.

Now if she had Windows Vista, she would be up the creek.

So as you try to convince your children that Linux is better, this is definitely one great example of it.

---

### Post by meng on 2007-01-14
Great story, except for the bit about Abiword crashing.
By the way, that's another bad joke.

---

