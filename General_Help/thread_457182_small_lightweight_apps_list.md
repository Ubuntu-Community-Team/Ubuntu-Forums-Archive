---
title: "small lightweight apps list"
date: 2007-05-28
forum: General Help
---

### Post by Lutherian on 2007-05-28
# Blah Blah Start (Rambling on bit - can skip...)

Through all the years of Windows I was always a bit nostlagic for the DOS machines I had when I was a kid.
As small as the memory was - it worked and it was fast too. Lotus 1-2-3 was a few kb and could work as fast
as M$-Excell does today.

I thought switching to Linux would be like DOS-ON-STERIODS, reading that the Unix philosophy is to use a lot of small programs rather than one huge bloated program that tries to do everything. It sounded good at the time BUT those linux programs were damn difficult. Anyway ... time passes and you begin to realise that Linux is whatever you want it to be - it just takes time - you make it into what *you* want it to be and while you're changing the machine - the machine changes you too - because you learn to think differently.
A bit like growing Bonsai tree - Ne?

#Blah Blah End (===> The issue at hand)

I want my Unix to be super fast - super simple - Minimilism is the ultimate goal.
Criteria: Low memory consumption | Fast | Easy to use | Clean Uncluttered Interface | Pseudo GUI (Ncurses)

The programs that I've stumbled on so far are these:

**ELINKS** for Webbrowsing (TABBED Browsing too :D Just press "t" or "T")
**wget** - File Downloading (A console type Pseudo GUI would've been nice)
**vi** - file editing (I wish someone told me about the :Ex command!!!)
**cplay** - music (I wish someone told me to press the "h" key!!!)
**streamripper **(*cough* *Cough*)
**mc **- ~File Commander kinda


If anyone is crazy like me and also likes these kind on minimalist programs - let me know what you use, there must be a lot  that still needs to be discoverd (eg bittorent client etc)

---

### Post by reclusivemonkey on 2007-05-28
mutt - Email
remind - calendaring system (my HOWTO on remind is here: [http://ubuntuforums.org/showthread.php?t=401502&highlight=remind](http://ubuntuforums.org/showthread.php?t=401502&highlight=remind))
wyrd - "GUI" for remind (ncurses)
workbone - CD player
btdownloadcurses - bittorent

If you search the forums, there are quite a few posts like this with many recommended apps.

---

### Post by kerry_s on 2007-05-28
I kinda follow DSL's choice of apps they really are good choices.-> [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by andrew.46 on 2007-07-02
Hi,

 Mutt:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

         Andrew

---

### Post by Nythain on 2007-07-02
centericq is a great ncurses command line instant messager client
rtorrent rocks my world as far as command line torrent clients go
ncmpc & mpd for music goodness
vi or nano for text editing
lftp (i hope thats right) is a pretty groovy ftp client
smbc (samba commander) is a nifty ncurses samba client ala commander style
i hear snownews is a good command line rss reader
lets not forget that aptitude run without any arguments or options will open up an interactive ncurses interface

---

### Post by Lutherian on 2007-08-31
So far the list is a follows:

[FONT="Courier New"]
centericq 	| is a great ncurses command line instant messager client
		| I really enjoy this one!
rtorrent  	| rocks my world as far as command line torrent clients go
ncmpc & mpd 	| for music goodness (A bit difficult for me to setup)
vi or nano 	|for text editing 
lftp 		|(i hope thats right) is a pretty groovy ftp client
smbc 		|(samba commander) is a nifty ncurses samba client ala commander style
snownews 	|is a good command line rss reader ( Nice)
aptitude 	|run without any arguments or options will open up an interactive ncurses interface
mutt 		|Email (Veeery difficult (hassel) to setup
remind + wyrd	|calendaring system (my HOWTO on remind is here: [http://ubuntuforums.org/showthread.p...ghlight=remind](http://ubuntuforums.org/showthread.p...ghlight=remind))
workbone 	|CD player
btdownloadcurses|bittorent (Works well)
ELINKS 		|for Webbrowsing (TABBED Browsing too  Just press "t" or "T")
wget 		|- File Downloading (A console type Pseudo GUI would've been nice) -wget rulez
cplay 		|music (I wish someone told me to press the "h" key!!!) 
streamripper 	|(*cough* *Cough*)
mc 		|- ~File Commander kinda (naaa - so so Gnome Commader is better still)[/FONT][/FONT][/FONT][/FONT]


In addition to this, the use of **[SIZE="5"]Fluxbox[/SIZE]** from the ubuntu distro make the system even more lightweight.
i.e Fluxbuntu is the way to go for laptops etc.

---

### Post by RedSquirrel on 2007-08-31
I like 'crip' for ripping CDs on the command line.

With regard to window managers, I prefer Fluxbox myself but there are other candidates, such as IceWM and Openbox.

... and don't forget that one can do a minimal install to make sure the system *itself* is light. :)

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by s26c.sayan on 2007-08-31
Maybe one would like to take a look at  [The Best Light and Fast Applications - 2006 LnF Awards ]("http://bbs.archlinux.org/viewtopic.php?id=18880"), a similar thread at the Arch Linux forums!
I've designed my March Linux to include apps mostly from this thread!

---

### Post by bodhi.zazen on 2007-08-31
This is a nice listing : [http://users.skynet.be/six/gpure/tech/linux/apps.html](http://users.skynet.be/six/gpure/tech/linux/apps.html)

If you like vi , try vim or gvim : ```
sudo apt-get install vim-full
```

---

### Post by RedSquirrel on 2007-08-31
> **bodhi.zazen said:**
> If you like vi , try vim or gvim : ```
sudo apt-get install vim-full
```

or...

```
sudo apt-get install vim-gtk
```vim-full pulls in a lot of GNOME stuff, which one may or may not want. ;)

---

### Post by Gremlinzzz on 2007-08-31
[http://www.linuxfromscratch.org/lfs/view/6.3/](http://www.linuxfromscratch.org/lfs/view/6.3/)
:guitar:

---

### Post by bodhi.zazen on 2007-08-31
> **RedSquirrel said:**
> or...

```
sudo apt-get install vim-gtk
```vim-full pulls in a lot of GNOME stuff, which one may or may not want. ;)

As always, thank you for the information ...

---

### Post by RedSquirrel on 2007-08-31
> **bodhi.zazen said:**
> As always, thank you for the information ...

My pleasure.

> **bodhi.zazen said:**
> This is a nice listing : [http://users.skynet.be/six/gpure/tech/linux/apps.html](http://users.skynet.be/six/gpure/tech/linux/apps.html)

I was just skimming through this link and read:

> fluxbox, popular, [COLOR=Red]**messed up**[/COLOR], dockapps:?

(Mind you, maybe it *was* at one time or another... :))

EDIT: ... and even if it wasn't, everyone's entitled to their opinion.

---

### Post by bodhi.zazen on 2007-08-31
> **RedSquirrel said:**
> 

(Mind you, maybe it *was* at one time or another... :))

EDIT: ... and even if it wasn't, everyone's entitled to their opinion.

As one fluxhead to another, don't you think one needs to be a little messed up to run fluxbox :twisted: ?

---

### Post by RedSquirrel on 2007-09-02
> **bodhi.zazen said:**
> As one fluxhead to another, don't you think one needs to be a little messed up to run fluxbox :twisted: ?

I don't think I've ever thought of it that way, but you may be right. :grin:

PS - Nice avatar.

---

### Post by Lutherian on 2007-09-03
Thanks for the listing, so as follows:

[Office]

AbiWord - Most of the features, none of the bloat
Excel Compatible Spreadsheet:  gnumeric. Excellent compatibility, very fast
Powerpoint Compatible Chartware: OO Impress. Neither fast nor light, but no alternatives!
PDF Viewer: acroread. Not so light, not so fast, but it is the golden standard
Runner Up: XPDF - amazingly useful after all this time, and very fast


[Graphics]

Image Viewer - feh. Very capable, very flexible, very fast
Runner Up 1: qiv. Not as many functions as feh, but an excellent and fast viewer
Runner Up 2: xv. Venerable image editor/viewer/manager still runs rings around many competitors
Honorable Mention: gqview. Very fast thumbnail oriented image viewer

Image Editor - GIMP. Not really very fast or very light, but absolutely alone in its class
Runner Up: xv. Not in the same league, but a surprising array of very useful editing functions

[Multimedia]

Audio Mixer: qamix. It does it all with style and speed
Runner Up: aumix. Both console and GUI versions available

Music Player: xmms. Does it all, takes only minimal screen space. No play lists though
Runner Up 1: wxMusik. An iTunes look-a-like that provides a lot of functionality
Runner Up 2: gtkpod. Play music from (and manages) your iPod
What about cplay - ncurses using 123mpg 123ogg etc, I wish there was a 123aac !!!

Video Player: MPlayer. The king of linux video players. (Yea, but user interface is so/so)
Runner Up: gxine.

CD Burner: xcdroast - quirky interface but it does the trick. Who needs K3B anyway? :-)

CD Ripper: grip. An excellent, excellent package. You're probably using it now
Runner Up: ripperX


Web, Email, IM

Firefox. Not really LnF, but  today's web demands complex browsers

e-mail : Sylpheed. Streamlined, very fast and quite capable
Console Email Agent: pine. An amazing email agent that still packs a punch
Runner Up: mutt.

IM Client: gaim - wonderful multi-protocol IM agent. 
(What about gaim-text, does it use less resources, does it use the plugins, same applies to Pidgeon/Finch)


VoIP Client: gnomemeeting. OK, its gnome, but like GIMP, its alone in its class

---

### Post by RedSquirrel on 2007-09-03
> **Lutherian said:**
> 
[Multimedia]

Audio Mixer: qamix. It does it all with style and speed
Runner Up: aumix. Both console and GUI versions available

There is no real need for these. alsamixer does the job very nicely.


> **Lutherian said:**
>  CD Ripper: grip. An excellent, excellent package. You're probably using it now
Runner Up: ripperX

grip has too many GNOME dependencies for my taste. crip or abcde are my suggestions.

---

### Post by andrew.46 on 2007-09-20
Hi,

 I see someone has got in before me with the greatest script in the world: abcde. Using a collection of CLI programsa this will rip music from cd, convert it to flac and/or mp3 and/or ogg and then tag the files and place them in a directory for you. Enormously configurable from a single configuration file: ~/.abcde.conf.

 Concerning mplayer: it does have a lousy gui as you have mentioned. The trick is to use it from the command line. The source package and svn versions are actually set up _not_ to have the gui by default.

                         Andrew

---

