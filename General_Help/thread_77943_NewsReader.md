---
title: "NewsReader"
date: 2005-10-17
forum: General Help
---

### Post by JediPottsy on 2005-10-17
Hi can someone suggest a good newsreader?
I normally use newsbin for windows, however whats a good one for linux?

---

### Post by Hikaru79 on 2005-10-17
Mozilla Thunderbird can, among other things, be a newsreader, and a very good one. Give that a try.

---

### Post by JediPottsy on 2005-10-17
no i dont like thunderbird for newsreader, just email

---

### Post by mcpish on 2005-10-17
[QUOTE=JediPottsy]Hi can someone suggest a good newsreader?
I normally use newsbin for windows, however whats a good one for linux?[/QUOTE]

2 suggestions:  
 1.  If you used newsbin for Windows which is basically for binary downloads I recommend "**klibido**", it's almost identical to newsbin and designed for major binary downloads

  2.  For general reading I recommend "**Pan**" which is very similar to Forte Agent.

Both are in the repositories, enable universe and multiverse

---

### Post by gpw797 on 2005-10-17
Pan works for me..

---

### Post by hunteramor on 2005-10-17
I use Straw and I'm pretty happy with it

---

### Post by dbott67 on 2005-10-17
[RSSOwl]("http://www.rssowl.org/") is my personal favourite.

[EDIT]
D'Oh!  It says "Newsreader" not "RSS Reader"  --- sorry, must learn to read before I post.
But I still like it! :)
[/EDIT]

-Dave

---

### Post by sizzam on 2005-10-17
[QUOTE=mcpish]2 suggestions:  
 1.  If you used newsbin for Windows which is basically for binary downloads I recommend "**klibido**", it's almost identical to newsbin and designed for major binary downloads

  2.  For general reading I recommend "**Pan**" which is very similar to Forte Agent.

Both are in the repositories, enable universe and multiverse[/QUOTE]

+1

I am a former Newsbin user.   Specifically for NZB use, I used to use [nzbperl]("http://noisybox.net/computers/nzbperl/").  It was pretty tricky for me to set up because I had to add a whole bunch of Perl modules.  I was not able to install klibido on Hoary, it was giving me some dependency errors.   However, it installs perfectly on Breezy using apt:

```
sudo apt-get install klibido
```

I now use klibido along with a program called 'alltray' (you can get it via apt) so that it starts up in my 'notification area', and stays running there when I close the program window during long downloads.

---

### Post by hwbj on 2005-10-17
[QUOTE=JediPottsy]Hi can someone suggest a good newsreader?
I normally use newsbin for windows, however whats a good one for linux?[/QUOTE]


Pan

it's worked well for me

---

### Post by tahuya_rat on 2005-10-17
You might try just running Newsbin in Wine.  I run Agent 3.x in Wine, and it works like a champ.

---

### Post by flyingbrass on 2005-10-17
For large binaries, [BNR2](http://www.bnr2.org/) is also an option.  It worked fine for me in Hoary.  I haven't tried it yet in Breezy.

---

### Post by marties on 2005-10-18
You can use wine + grabit 
just don't apt get wine from ubuntu's source-list but follow the recomendations
[http://www.winehq.com/site/download-deb]("http://www.winehq.com/site/download-deb")

in short you have to do this :

**add to source-list :**

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

Then, you can run 'apt-get update' to update APT's package information. Finally, to install Wine, do 'apt-get install wine'.

**If you want to make sure that apt-get will install the WineHQ wine package instead of the Debian wine package** (which usually has the same version), then add something like the following entry to /etc/apt/preferences:

Package: wine
Pin: release l=WineHQ APT Repository
Pin-Priority: 1000

Hope that helps

---

### Post by Jingo on 2005-11-03
[QUOTE=flyingbrass]For large binaries, [BNR2](http://www.bnr2.org/) is also an option.  It worked fine for me in Hoary.  I haven't tried it yet in Breezy.[/QUOTE]

Did you get it to work in Breezy?
What about those libqtinf libraries?

---

### Post by poptones on 2005-11-03
I've not had any problems with pan since I got it properly configured. If you are downloading very large files you will want to change the cache size to something much larger, like 300MB for example. I had lots of problems trying to fetch large files on pan before I did this - with the default cache size it deletes the first parts of large posts before it's finished downloading the last.

You cannot post binaries with pan, but newspost works better than agent or those others anyway.

---

### Post by Cupido on 2005-11-12
I'm a new Ubuntu user, just downloaded, installed and configured the newest ubuntu version. That machine is running as a web/file/mail server and I also want to use it to download during the nightly hours.

I installed Pan and it's working allright (except for nzbs), BUT.
As soon as I want to download headers from groups like a.b.boneless or a.b.dvd,  it downloads all the way.. untill the last aprox 40 headers and just stops there. I can leave it on for days, but it won't get the last headers and get everything right.

So I can't really do a thing with Pan atm. Any help is mostly appreciated.
Thanks in advance.

---

### Post by Cupido on 2005-11-12
[QUOTE=mcpish]2 suggestions:  
 1.  If you used newsbin for Windows which is basically for binary downloads I recommend "**klibido**", it's almost identical to newsbin and designed for major binary downloads

  2.  For general reading I recommend "**Pan**" which is very similar to Forte Agent.

Both are in the repositories, enable universe and multiverse[/QUOTE]

I am now installing Klibido.. let's give that a try.

Marties said something about using grabit. Under linux?? I used grabit on my windows machine and I liked it. If i can get that working well under my ubuntu installation, I'll be very happy. Also, I used to use FTD for just knowing what will be on the newsgroups and where to find it. If anybody knows a program to replace that or get something similar working in ubuntu, I'm gonna be really happy.

---

### Post by Cupido on 2005-11-17
Anyone?

---

### Post by robgue on 2005-11-18
klibido. use that. it even supports nzb's. and you don't have to miss with it to install as it's in the repositories. it's the easiest

---

### Post by Cupido on 2005-11-18
Isn't Klibido for KDE? I'm using GNOME atm.:rolleyes:

---

### Post by robgue on 2005-11-18
well i don't have kde installed. apt-get will of course get any dependencies  needed. before klibido was included in breezy i had a hard time trying to configure a binary newsreader that supported nzb's. im glad they did though, one step closer to getting rid of the dual boot. now we need a gui for .rar files and .par2. not that it's difficult from the command line but of course i prefer slick gui's ;)

---

### Post by Cupido on 2005-11-24
I got Klibido working.
Now I just need something to work with the rars and par2s.

---

### Post by marties on 2005-11-25
apt-get install par2 unrar
or 
apt-get install par2 unrar-nonfree

---

### Post by spartas on 2005-11-25
My personal favorite is Liferea.  It's in universe.  Try out all the ones that were suggested and pick one is the best suggestion for you.

---

### Post by Dustin Wyatt on 2005-11-26
Liferea is a RSS aggregator.  Not a newsreader in the traditional sense of the word.

---

### Post by Cupido on 2005-11-27
Dustin, thanks for telling.

I tried apt-get install par2 unrar, which didn't work.
I tried apt-get install par2, which worked.
And I tried apt-get install unrar, which didn't work.

---

### Post by BlueGhost on 2005-12-16
try sudo app-get install rar

or better, just use synaptic and search for rar.  I know it's there.

---

### Post by gookie on 2006-01-07
Hi, I'm a former Newsleecher user (windows) and now I'm trying **klibido** for ubuntu, and I must say it's pretty neat, gets the job done flawlessly. One thing though, it seems that it has no Speed monitor? I have to fire up my system monitor everytime I have to check my bandwidth speed. Am I missing something here? Is there a fix for this?

Thanks!

:p 
(1st post, hi 2 all!!!)

---

### Post by Zerocool10482 on 2006-01-24
I don't know about all of you but I use Blam. And that works fine for me. I like it because it's simple. And I don't have that may feeds to categorize.

---

