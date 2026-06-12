---
title: "non free woes..."
date: 2005-04-03
forum: General Help
---

### Post by uberlinux on 2005-04-03
I'm trying to figure out why in a distro tailored to new users of Linux, packages are being left without support for mainstream, but proprietary, formats, such as mp3 wma.  I understand that Debian is all about truley free software, but this is alienating prospective adopters of linux, and I find myself having to hand out SuSE 9.2 disks because I bont have the time to dpkg -r --force debs and rebuild them.
Mplayer needs attention, still dosent play some wma's and Divx's
Ark won't make use of UNRAR, I've got to do some digging to see why
K3b had to be totally removed and rebuilt, took longer than the average doze user would put up with
I'm sure that there are more fun things awaiting me, but its 3:30am and I've had enough for one night/morning.
P.S. Kbear is broken...try copying to a local dir and you too can have your own easilly replicateable sig11 crash :p 
But it's a great start for a distro other than that, I love it and have used it exclusively for longer than any one other distro, so thanks and if I ever hit the lotto, y'all will get half!

---

### Post by ankitmalik on 2005-04-03
I would love to see and use an 'Ubuntu Non free edition'

---

### Post by Buffalo Soldier on 2005-04-03
[QUOTE=uberlinux]I understand that Debian is all about truley free software, but this is alienating prospective adopters of linux...[/QUOTE]Adopters of GNU/Linux should also be adopters of the FOSS (Free / Open Source Software) philosophy behind it.

To adopt GNU/Linux solely for the reason it's free (as in free drinks) and not because of it's also free (as in freedom) is uncool.

---

### Post by uberlinux on 2005-04-03
I'm all for free software and the principals and ethics behind it but the reality is that I download mp3's not ogg's, they arent out there unless you are into jam-band hippie music, tons of websites encode their video content into wma, I e-mail them and plead them to encode in something else, but most places dont care.  Half of the things I bittorrent are rarchived, not gzipped, these things wont change right away, we need to focus on  end-user useability, just as much as shiny ideals. This is something that makes people turn away from computing in linux...

---

### Post by Buffalo Soldier on 2005-04-03
I agree. I guess we have to find a middle road somewhere. It's becoming like a chicken-egg scenerio. Artist won't distribute their work under open standard unless there is enough deman from consumer. And consumer won't be using open standard unless artist start distributing using it.

But I think we (people who have some knowledge about FOSS) should be making the first move.

Of course the journey won't be easy. There will be a lof of handholding, repeating the same answer to the same question, explaining over and over again to newbies about FOSS.

But then again, the road to freedom has never been easy.

*"they can take my MP3, but they will never take my freedom" * ...Buffalo Soldier.

EDIT:[list]
[*] [xiph.org](http://www.xiph.org/about.html) - for those who care.
[*] [Tired of RIAA and propriety codec](http://ubuntuforums.org/showthread.php?t=21564)
[*] [Someone from Europe, tell me... WTF????](http://ubuntuforums.org/showthread.php?t=22469)[/list]

---

### Post by az on 2005-04-03
"This is something that makes people turn away from computing in linux..."

On the other hand, there are a few MP3 players that play ogg.  I would only buy one of those.

---

### Post by mw13068 on 2005-08-04
I can't speak for the motives of the Ubuntu folks, but people involved in Free Software movement value software freedom over popularity and convenience.

After all, Microsoft Windows is very popular and convenient in most ways, is it not? Why do we not choose to keep using Windows?  Is it simply because we want our software to be available to us at no cost?

If an organization creates a "Linux" distribution that is packed with popular and "convenient" non-free software packages, like Macromedia's Flash Player, patented mp3 encoders and decoders, etc., then where does it stop?  Suppose Microsoft was to offer some groovy full-featured, but non-free mp3 player, dvd player, etc. for "Linux"? Would you think that this "convenient" software should be packaged in every "Linux" distro? Why or why not?

Is it a benefit to new "Linux" users if half of the software in their "Linux" distro could be taken away from them, or become unsupported, be illegal to copy and give to a friend, or at some point require payments to the companies that created it?

Is it the aim of the "Linux" user to simply get all of his or her software at no cost, or with complete software freedom?

Personally I choose not to use mp3s (I only use .ogg), not to view Flash animations (with Macromedia's non-free product anyway) and I choose not to do quite a few other computer activities because there is simply no way to do them and retain my freedom to use, copy, modify and redistribute all of the software on my computer.

This may seem quite stupid to those who prioritize convenience and popularity over freedom, but I don't care about being popular, I just care about having freedom.
 
I encourage anyone interested in reading more about software freedom to read the essays on the GNU project's Web site:
[http://www.gnu.org/philosophy/philosophy.html](http://www.gnu.org/philosophy/philosophy.html)

---

### Post by ubuntp on 2005-08-04
[QUOTE=uberlinux]I understand that Debian is all about truley free software, but this is alienating prospective adopters of linux, and I find myself having to hand out SuSE 9.2 disks because I bont have the time to dpkg -r --force debs and rebuild them.[/QUOTE]
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

---

### Post by uberlinux on 2005-08-10
[QUOTE=ubuntp][http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)[/QUOTE]
gstreamer is wack, I'd rather have things work

---

### Post by Stormy Eyes on 2005-08-10
> **uberlinux]I'm trying to figure out why in a distro tailored to new users of Linux, packages are being left without support for mainstream, but proprietary, formats, such as mp3 wma.[/quote]

They're not included by default because Canonical Ltd. doesn't want to deal with the legal issues surrounding the inclusion of proprietary codecs. Don't blame Ubuntu said:**
> I understand that Debian is all about truley free software, but this is alienating prospective adopters of linux, and I find myself having to hand out SuSE 9.2 disks because I bont have the time to dpkg -r --force debs and rebuild them.

The [Ubuntu Guide](http://www.ubuntuguide.org) has HOWTOs for installing proprietary codecs. Why are you wasting your time rebuilding packages?

> **uberlinux]Mplayer needs attention, still dosent play some wma's and Divx's[/quote]

Try vlc. I doubt that the Mplayer developers will listen said:**
> But it's a great start for a distro other than that, I love it and have used it exclusively for longer than any one other distro, so thanks and if I ever hit the lotto, y'all will get half!

I sympathise, but there isn't much Ubuntu can officially do when it comes to proprietary codecs other than play it safe and not include them by default. You don't want to see Ubuntu die because Canonical got sued into the ground, do you?

---

### Post by Stormy Eyes on 2005-08-10
[QUOTE=uberlinux]gstreamer is wack, I'd rather have things work[/QUOTE]

Amen. If I was writing a music player, I'd just wrap a pretty GUI around command line tools like mpg321 (for mp3) and ogg123 (for ogg vorbis), instead of buggering about with a complicated framework. Old-school Unix, baby.

---

