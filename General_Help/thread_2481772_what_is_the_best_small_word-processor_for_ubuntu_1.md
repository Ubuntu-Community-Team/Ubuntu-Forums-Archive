---
title: "what is the best small word-processor for ubuntu 14.04?"
date: 2022-12-08
forum: General Help
---

### Post by lanzcc on 2022-12-08
Hello, Thank you Ubuntu Forums for all your help! I use a word-processor only for very basic stuff (if I need more features, I devolve to my MacBook) and I am asking for recommendations from the community so I don't do something ignorant. I would love to order my decision according to "ease of installation". "Ted" is an example of something that might be appropriate for me, and it worked for (even) earlier versions of Ubuntu. Thanks for your advice.

---

### Post by VMC on 2022-12-08
I use **Abiword** to replace Libreoffice, as a word processor. Works for me. [word-processor and not text editor]

---

### Post by Autodave on 2022-12-08
Ubuntu 14.04????  Seriously?  You need to upgrade to something newer....that reached its end of life (EOL) quite awhile ago!

---

### Post by TheFu on 2022-12-08
Support for 14.04 ended years ago.  If this machine isn't connected to any network, fine.  OTOH, if it is connected to **any** network, what you have is an attack machine with remote control, since the kernels for it have remote control security issues with root takeover.  Basically, it isn't your machine when someone else takes it over.

I'd concur that AbiWord is probably the best, lightest, word processor to be considered.
'ted' isn't a word processor, it is an editor.  Editor selection is about taste, knowledge, and history. There are 30+ popular editors.  Do you need a GUI?  If not, nano is the current minimal that average people use for quick edits.  If you want a little more with a GUI, there are Kate, Gnome-Edit, and Geany.

All of these are installed using apt-get/APT, but since the repos for 14.04 are all gone, the only way you'll get them is to use a local CDROM ISO, probably from a 8 yr old disc.  No updates. No patches. No fixes.  I'd think almost all of these packages would be on that CDROM, waiting to be installed.

Of course, there's also 'vim', which is what Unix nerds use, but if you don't already use it, I have doubts that you'd want to spend the time learning it.  It is an editor like no other and does take some effort to learn.  But once you have learned a big, there is always more to know, to be even more efficient.  Vim is like learning a foreign language, but so it Linux/Unix.  The main reason to learn vim is that every router, computer, server, and many network switches have a copy. It runs on everything - EVERYTHING.  It doesn't need a GUI. It works over remote text-only network connections, and has 10K+ addons to accomplish anything.  I run an addon called vimwiki as a personal knowledge organization tool.  Most of my normal vim knowledge transfers to vimwiki.  There are outline mode addons and other organization addons too. I've heard that creating your own addon isn't THAT hard, but I've always found that someone else already solved the problem I had.

But if you don't know 'vim', some other editor would likely be the choice.
OTOH, if you want a real word processor, adiword. Definitely.

---

### Post by Holger_Gehrke on 2022-12-08
@TheFu: I think lanzcc is talking about [this ted]("https://nllgg.nl/Ted/"), which is indeed a simple word processor that saves in rtf by default. It's about comparable to Windows Wordpad in features. There are .deb packages available for download on that page but they can't be installed on modern Ubuntu versions because of dependencies (libtiff4 and libpng12) that are not part of modern Ubuntus. Might be possible to make it compile with libtiff5 and libpng version 1.6 but I haven't tried ...

Holger

---

### Post by MAFoElffen on 2022-12-08
I remember "ted"... And 'sublime text'...

---

### Post by TheFu on 2022-12-08
> **MAFoElffen said:**
> I remember "ted"... And 'sublime text'...

I remember ted from the 1990s. It was very similar to nano, except useful, unlike nano. ;)

---

### Post by Impavidus on 2022-12-08
That Ted website hasn't been updated since 2013. Looks like a dead project to me. It was in the Ubuntu repos up to 8.04 LTS.

For older computers, abiword would be best, I think. It's still in the official repositories and used to be the default on Xubuntu (and Lubuntu, I think). Abiword is supposed to be lighter than libreoffice. I prefer text editors though, normally vim. Text editors are a lot lighter than even light word processors. I use word processors only to exchange files with other people.

But really, 14.04 is from the stone age.

---

### Post by dragonfly41 on 2022-12-08
Theoretically (I don't use 14.04)  CherryTree on Ubuntu 14.04 might work, but I agree that AbiWord is a good choice.

[https://sourcedigit.com/14048-install-cherrytree-text-editor-ubuntu-14-04-debian-derivatives/](https://sourcedigit.com/14048-install-cherrytree-text-editor-ubuntu-14-04-debian-derivatives/)

---

