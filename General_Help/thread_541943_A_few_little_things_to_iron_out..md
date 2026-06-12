---
title: "A few little things to iron out."
date: 2007-09-03
forum: General Help
---

### Post by davebrazier on 2007-09-03
Hi,

I'm new here so first I'll introduce myself, otherwise it's just plain rude!  My name's Dave and I'm a 21 year old music student from Canterbury, Kent, UK (the little island off the coast of Europe!).  I've been using Windows all my life and consider myself a fairly advanced user.  I regularly find myself fixing things and I'm getting fairly fluent in web-development (mainly in PHP).  I've finally taken the plunge into Linux for the simple reason that I have now tried Vista.  Nuf said!!

I've been running UbuntuStudio for about a month now and I'm liking it a lot.  Still got a few things I'm not sure about though.  I'm gonna try and describe my system, and PLEASE correct anything that I say wrong!

Like I said I'm running UbuntuStudio which is a Gnome interface, right?  I'm also running a kind of dual login (or whatever it should be called) with Kubuntu which is the KDE version.  KDE, as I understand it, has more stuff but is slower.  Right?  It also obviously looks quite different.  Is it also newer?

I have a few programs which claim to be to do with Jack (Jack Control, Jack EQ, Jack Rack, Jack Timemachine) but I haven't set that up yet.  But that's to do with MIDI, right?

I'm in the process of trying to get VMware sorted out so I can run my specialist musical score editer (Sibelius) which isn't available for linux.  I found this forum by searching for an article about VMware, and the one I found is brilliant.  That's why I registered.  I also tried Wine but it didn't run properly.  What's the difference between Wine and VMware?  Do they just do the same thing in different ways?

Hmmmm, thats a lot.  Sorry!  I think the main thing I want to get my head around is the differences between KDE and Gnome.  Also, I keep reading references to "Edgy" and "Feisty" and other things like that.  What are they?  Are they types of distributions?  Or can a single distribution be several?  At once or is it a case of one or the other?  Whats the difference?  Which am I likely to be running?

Thank you very much to anyone who can correct, confirm or elaborate on anything I have written.  Maybe one day I'LL be able to answer noobie questions!

Cheers guys.  Hope you're all having a great day.

Dave.

---

### Post by wolfen69 on 2007-09-03
i can answer this: what you are doing is called "dual boot".
kubuntu is not neccesarily slower, although it might be on your setup.
kubuntu is not newer, it is just an alternative to regular ubuntu,(gnome)
edgy is a previous release of ubuntu. feisty is the current release.
if you downloaded ubuntu studio in the last several months, you are likely using feisty 7.04. if before april, you have edgy ubuntu. i can't answer the MIDI question. cheers.

p.s. here is some great info on ubuntu- [http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution](http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution))

---

### Post by Happy_Man on 2007-09-03
Hey there, and welcome to Ubuntu! 

Yes, UbuntuStudio does run GNOME, same as the default Ubuntu. Kubuntu runs KDE, which is actually older than GNOME. KDE has more applications included in a default install than GNOME does, which is great for some people (like me), not so great for others. It's not really *slower*, per se, only in comparision to GNOME, because GNOME was made to be simple and fast, whereas KDE was made for the power user. For more info, see here: [http://psychocats.net/ubuntu/kdegnome](http://psychocats.net/ubuntu/kdegnome)

WINE, which stands for WINE Is Not an Emulator, is a program that emulates (a fancy word for imitates) certain essential Windows files. This allows Windows programs to install and run under the illusion that they are running ona Windows box, even though they're really not. It works well for some programs, not so well for bigger and more complicated ones. VMWare, on the other hand, is virtualization software. That means that it can run a full Windows install from within Ubuntu. It's like running two OS's at once! The full Windows experience is right there, such that you can have Windows in a window :lolflag: in Ubuntu. 

"Edgy" and "Feisty" are nicknames for versions of Ubuntu. Edgy, or Edgy Eft, is version 6.10. Feisty, or Feisty Fawn, is version 7.04 (the current version, and the one you are most likely running). Gutsy, or Gutsy Gibbon, is version 7.10. That is the next version, due to be released in October. 

Wow, that is a looong answer. Hope some of it makes sense!

---

### Post by swisscow on 2007-09-03
Hi Dave, Canterbury is a nice town.

OK, can help with a few things.

KDE and Gnome are just different desktops that you can see - you can have both installed at the same time but not running at the same time.Saying that you can run the kde applications under gnome and vice versa. Which is slower - well thats open for debate. Personally I find kde better, but that's just a personal opinion. Have a look at [HTML]http://www.psychocats.net/ubuntu/[/HTML] which will give you loads more info.

Edgy, Feisty, Gutsy etc are just release names of versions of Ubuntu. The current is feisty or 7.04 (from 2007, April). The next is Gutsy (due 2007, October) hence called 7.10

Difference between VMWare and wine. I believe VMWare is like a pc within a pc so windows thinks its running on a clean pc. Wine interacts between linux and windows to make it work. Personally I use virtualbox instead of vmware, but again, that's just my choice.

Can't help you with jack - I knpw jack sh*t about it. 

Hope this helps

---

### Post by rfcompte on 2007-09-10
> **davebrazier said:**
> I have a few programs which claim to be to do with Jack (Jack Control, Jack EQ, Jack Rack, Jack Timemachine) but I haven't set that up yet.  But that's to do with MIDI, right?

I'm in the process of trying to get VMware sorted out so I can run my specialist musical score editer (Sibelius) which isn't available for linux.

Jack runs as a server so it manages the connections between apps. For instance you want the output from a programm to go to the input of another one so the can connect in real time... It's very powerful... Once you you understand how it works, the sky is the limit. Jack Control is the main frontend for Jack, the other do as the name says: an EQ, a rack for managing plugins mostly, etc. Jack Timemachine if is activated is recording a few seconds before you press the record button. Just what you read... :lolflag:  Very useful in a studio I guess... They interact with MIDI of course as well as with audio.
I run Sibelius inside Virtual Box 1.5 I highly recommend it. Works for me better that Vmware Server... But you'd better try both to see which works for you and your machine..

Welcome to the Ubuntu Community

Rafael

---

