---
title: "wma to ogg"
date: 2006-07-16
forum: General Help
---

### Post by music_man on 2006-07-16
I live in New Zealand and the only music download service that I can use is Coketunes (can't be bothered with digirama). The coketunes website sucks - you have top download all this activex rubbish, so I have to do this on my friend's laptop computer and then transfer the files onto my Ubuntu computer.

Now I have the problem that they are wma (with I think some sort of protection on them). Now I have bought these tracks and I want to be able to use them.

I went to Synapic package manager and downloaded: nautilus-script-audio-convert

But I can't find out how to get that to launch.

Any other ways I can get these wma files ot work?

---

### Post by bluecherry on 2006-07-16
This site is in french but presents a script that does what you want it to do (scroll down for english):
[http://www.tux-planet.fr/blog/?2006/05/12/78-convert-wma-files-to-mp3-or-ogg-format](http://www.tux-planet.fr/blog/?2006/05/12/78-convert-wma-files-to-mp3-or-ogg-format)

Make sure you've got the wma codec. An easy way to get it is by using Automatix (search forum).

---

### Post by music_man on 2006-07-16
Thanks for your reply.

Downloaded mplayer. Now I have three media players.

This seems an exteremly complicated process for getting it to work. I really  dislike this command line stuff.

mplayer wont launch either.

So this Automatix is like Synaptic Package Manager?

---

### Post by bluecherry on 2006-07-16
Automatix is a GUI that lets you install things that are normally very hard to install (like SUN java, firefox plugins... and a lot of non-free multimedia codecs like wma).

It's basically a list and you select what you would like to see installed and it installs it...

---

### Post by music_man on 2006-07-16
But how does it work together (the codec and media player)? Why can't these media players just have a function where they look up the codec and download it!? Do I have to do this command line stuff?

---

### Post by music_man on 2006-07-16
mplayer doesn't work so are there any other ideas please?

---

### Post by bforbes on 2006-07-17
How does mplayer not work? What error do you get?

---

### Post by slimdog360 on 2006-07-17
I think if you convert from one lossy format(wma) to another(ogg) you will lose sound quality in the song. So I wouldnt recommend it.

---

### Post by stimpsonjcat on 2006-07-17
uprotected .wma files can be played on ubuntu if you install the w32codecs package. see [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")  for instructions.

if the .wma files are protected with [DRM]("http://en.wikipedia.org/wiki/Digital_Rights_Management") you won't be able to play them even with the w32codecs package.

In the second link I gave you there are some hints on how to remove the DRM. I don't know if that would be legal where you live though.

---

### Post by music_man on 2006-07-17
Argh. I think I have legally bought these tracks twice now. I am (as I type) listening to them on my friend's laptop as I have conducting today.

So it would be illegal for me to remove the DRM even though I have repeatedly bought the tracks?

---

### Post by bforbes on 2006-07-17
Unfortunately yes. It's also illegal to decrypt DVDs using programs like DVD Decrypter.

---

### Post by music_man on 2006-07-17
So given that I live in New Zealand and there are no legal music download websites for Linux, nor can any of the legally downloaded music be played on my computer... What am I supposed to do?

---

### Post by bforbes on 2006-07-18
I've heard rumours of these things called p2p programs, but at the risk of incriminating myself I won't say anything further.

---

### Post by stimpsonjcat on 2006-07-18
> **music_man said:**
> So given that I live in New Zealand and there are no legal music download websites for Linux, nor can any of the legally downloaded music be played on my computer... What am I supposed to do?
Are you sure you can't remove the DRM? Or was that a rhetorical question?

---

### Post by erniewinner on 2006-09-14
now i hope this will end postings like "why do you hate ms." :twisted: :twisted: :twisted: could ms do their market research elsewhere please! ;)

---

### Post by Lunar_Lamp on 2006-09-14
I am not a lawyer, but it's probably a good idea to check the law in NZ.  Different countries vary in their laws, and often quoted are the American laws, which are seen to be some of the most strict.  It may be legal to remove the DRM in your country, though I wouldn't get your hopes up.

---

### Post by darrenm on 2006-09-14
> **music_man said:**
> So given that I live in New Zealand and there are no legal music download websites for Linux, nor can any of the legally downloaded music be played on my computer... What am I supposed to do?

Yes. What a ridiculous state of affairs the world is in. Why do you have to use only a NZ download site? 

If the only site you can use to download music is forcing you to use DRM that is only supported in Windows Media Player then that is very unfair and governing bodies in NZ need to be made aware.

If I want to download songs I will only use a site that doesnt use DRM and uses open formats such as ogg.

Does such a site exist?

---

### Post by toasterofirony on 2006-09-14
Yeah, DRM is a funny thing like that. And by funny thing, I mean a %£"#*! thing most of the time.

Politics aside, if they are DRM protected you won't be able to play them in Linux with a bit of fiddling(to the best of my knowledge). You can however get rid of it, though the legality of it is something I don't know about either, so if you want to find out you'll have to do the leg work yourself ;)

On the note of Mplayer not working, is this just with your possibly DRM'd files or all media files?

---

### Post by moore.bryan on 2006-09-14
[http://svn.mplayerhq.hu/*checkout*/mplayer/trunk/TOOLS/wma2ogg.pl](http://svn.mplayerhq.hu/*checkout*/mplayer/trunk/TOOLS/wma2ogg.pl)

---

### Post by toasterofirony on 2006-09-14
> **darrenm said:**
> Yes. What a ridiculous state of affairs the world is in. Why do you have to use only a NZ download site? 

If the only site you can use to download music is forcing you to use DRM that is only supported in Windows Media Player then that is very unfair and governing bodies in NZ need to be made aware.

If I want to download songs I will only use a site that doesnt use DRM and uses open formats such as ogg.

Does such a site exist?

:\

.ogg is not all that popular, trust me as a Linux user in a sea of friends who Windows and Mac users. Try giving a Mac user a .ogg file and watch them weep. If I were to pimp a music download site I'd whore out [eMusic]("www.emusic.com"). It's a little niche but it does offer 25 free downloads when you sign up.

---

### Post by psycosmyth on 2006-09-14
not too many .ogg sites, shame. I use occasionaly Jamendo(French) for music. I have found many new artists there and that's the main reason it's free. You're not going to find top-o-the-charts stuff but the point in having that exposure is to make money. Try using XMMS or another player, there are dozens.I once broke down and used a tape recorder in the headphone jack and recorded it back as .wav, OK it was awful but it worked:lol:

---

### Post by allix on 2006-09-14
> **music_man said:**
> So given that I live in New Zealand and there are no legal music download websites for Linux, nor can any of the legally downloaded music be played on my computer... What am I supposed to do?

Looks like you need some help from the [worlds largest Bittorrent tracker]("http://www.google.com/search?hs=cJa&hl=sv&client=opera&rls=sv&q=worlds+largest+bittorrent+tracker&btnG=S%C3%B6k&lr=")... ;) 
Seriously, you tried the legal way but they obviously don't want your money. If you still want to support your favorite bands and artists buy concert-tickets, t-shirts, stickers or whatever. F this DRM crap.

---

### Post by moore.bryan on 2006-09-14
*have you tried the wma2ogg script i suggested before?*

---

### Post by user1397 on 2006-09-14
@ music_man

okay, let's clear some things up. Ahemm:

Automatix is a third-party project that allows you to automatically (hence the name) download and install software packages that would normally be difficult to install, things like sun's java, audio codecs, flash player, etc.  it is not command-line based, it is an entirely graphical program, all you have to do is tick the packages that you want, and the rest is done for you.  for people that want to do things the easy way, or they're tried the hard way before and now they just want it to get done fast and easy, then they should use automatix. **[here]("http://getautomatix.com/")**'s their official website.

automatix may indeed solve a lot of your problems.  if the music you download is not DRM protected, then a simple package that automatix will install for you, lets you play audio formats like wma.  the package is called the **w32codecs**, but automatix calls it "multimedia codecs"

another option would be to install a sound-converting program.  if you look in synaptic package manager, you can search for a package that i believe is called **soundconverter**, with no spaces.  pretty straight forward.  with that program, you can convert files to ogg from other formats, and vice versa.  i don't know if it works with wma, but i would think so.

that's my 10 cents

---

