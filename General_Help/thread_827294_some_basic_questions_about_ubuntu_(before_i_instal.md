---
title: "some basic questions about ubuntu (before i install it)"
date: 2008-06-12
forum: General Help
---

### Post by dinbrca on 2008-06-12
1) Can ubuntu run games? - I am not so sure I think yes..
2) Is ubuntu faster then windows XP?
3) Is ubuntu security is better then windows XP?
4) If I have a software that work on windows XP will fully work in ubuntu?
5) I understood from another forum that if you install ubuntu then it is harder to format the PC because of the GRUB Boot. Is it true? and if yes then how do I format it?
6) I want an English theme of the ubuntu OS but I want it support Hebrew language with my keyboard how do I add Hebrew support? if i added a Hebrew support then how do I toggle the right to left language pointer? to write from right to left..?

---

### Post by aysiu on 2008-06-12
> **dinbrca said:**
> 1) Can ubuntu run games? - I am not so sure I think yes.. Yes. Gnometris, Tux-Racer. Lots of games. Or did you mean games designed for Windows? > 2) Is ubuntu faster then windows XP? Sometimes. It seems depend on the computer, strangely. > 3) Is ubuntu security is better then windows XP? Yes. > 4) If I have a software that work on windows XP will fully work in ubuntu? If it's cross-platform, yes. If it's Windows-only software, no. > 5) I understood from another forum that if you install ubuntu then it is harder to format the PC because of the GRUB Boot. Is it true? and if yes then how do I format it? It's not harder to format. I don't know what you're talking about. You can use Wubi, though, to install Ubuntu without repartitioning or installing Grub. > 6) I want an English theme of the ubuntu OS but I want it support Hebrew language with my keyboard how do I add Hebrew support? if i added a Hebrew support then how do I toggle the right to left language pointer? to write from right to left..? No idea.

By the way, from your questions, it seems as if you have the impression that Ubuntu is a faster, safer, free version of Windows. It isn't Windows. It's something completely different. If you have a lot of Windows-only software you need to run, then you should run Windows.

---

### Post by MaxNorris on 2008-06-12
1)  Yes.  There's some good quality native Linux games.  Or, for Windows stuff, it's a definite "Maybe".  Install a copy of Wine and check out their Application Database.. it's a crapshoot.  Some games run, some don't.  Some games actually run better than Windows (World of Warcraft for me for example runs faster), some run slower.   If gaming is a must, you can always set up a dual-boot system for the games that don't play nicely in Wine.

2) Yes and no.  Personally, I find that in raw horsepower, Linux stomps all over XP/Vista.  *But*, there's a few places that Windows has the edge.  SuperFetch for example in Vista is amazing.

3) Yes, with caveats.  By design, you're more secure because you don't run as a root/administrator, so you're already limited in the damage you can cause.  Plus, almost every application you install will come from one central repository, vs downloading "willy nilly" off of random web sites.  No system is 100% secure though.  There are the occasional bugs for example; the SSH key thing for instance.  You can pop into root mode and hose your system pretty quickly.  Wine and Spyware?  Not sure how that plays out, I suppose its possible. 

4) Yes and no, see gaming.  Wine or Crossover are pretty amazing, but not 100% foolproof.

5) If you mean if you decide to get rid of Ubuntu and go back to XP at a later time, no it doesn't make a bit of difference.  The intaller will rewrite its own boot record and off you go.  The only time it's tricky is if you want to dual boot.  In that case, install XP **first**, then Ubuntu second.  Save you a lot of hassle.

6) Not sure how that works as I've never been inclined to check out multilanguage support, but I do recall it throwing me a bunch of languages that I can pick from during the installation.

---

### Post by MaxNorris on 2008-06-12
> **aysiu said:**
> By the way, from your questions, it seems as if you have the impression that Ubuntu is a faster, safer, free version of Windows. It isn't Windows. It's something completely different. If you have a lot of Windows-only software you need to run, then you should run Windows.

That's an excellent point too.. a lot of people expect it to work exactly like Windows, and at the first sign of trouble or not able to figure something out immediately, they jump to the quick "Linux sucks" conclusion and reformat.  

Windows was designed with the lowest common denominator in mind.  Shoot I think it was Steve Ballmer who equated a Windows user with a spider monkey. (Seriously.)  

Linux is a bajillion percent more flexible, but can be complicated at times.  The guys from Gnome and KDE have made great strides at removing the need to get into a terminal, but it still comes up.  (And after getting used to it, I actually prefer it) Be ready to Google certain things, as it *will* come up, but if you approach it with an open mind, you'll pick it up and fall in love with it.  It's not for everyone.

---

### Post by louieb on 2008-06-12
[LIST=1]
[*] games? - Not a gamer. I'm sure others will chip in
[*] faster  XP? about the same
[*] security? By far Linux and Ubuntu is more secure.
[*] software on windows XP work in ubuntu? Not natively.   [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm")
[*]harder to format the PC? Not true. More complex if you play to run more that 1 OS. (Dual Boot).
[*]Hebrew support? :confused: Have a hard enough time talking to my Hispanic buddies.
[/LIST]

---

### Post by dinbrca on 2008-06-12
So I will summarize it in this way:
if i want to play windows is better but i can use the wine software to run windows programs, linux is a lot more secured then windows xp, it isn't very support the languages, so you cant use alt+shift to change between diffrent languages, i can dual boot my pc so i can use a lot of softwares (that's what i was intended to do- but if i do it then install xp first), linux was programmed to more support itself and not other platforms, so if i want full support for everything i should dual-boot..
everything i sayed is ok?
is there any OS that allows you to play anygame?
If i am dual-booting (that's what i will do) then is the following GB per HD is good?:
C:/50GB - Ubuntu OS
D:/20GB - Softwares
E:/200GB - Games & Installs
G:/THE OTHER - Windows XP OS
Or:
C:/70GB - Ubuntu OS & Softwares
D:/200GB - Games & Installs
E:/THE OTHER - Windows XP OS

---

### Post by Pjotr123 on 2008-06-12
Shalom!
Here's a collection of tips and how-to's for beginners that will probably be of good use to you: [http://ubuntutip.googlepages.com/](http://ubuntutip.googlepages.com/)

---

### Post by MaxNorris on 2008-06-12
> **dinbrca said:**
> So I will summarize it in this way:
if i want to play windows is better but i can use the wine software to run windows programs, linux is a lot more secured then windows xp, it isn't very support the languages, so you cant use alt+shift to change between diffrent languages, i can dual boot my pc so i can use a lot of softwares (that's what i was intended to do- but if i do it then install xp first), linux was programmed to more support itself and not other platforms, so if i want full support for everything i should dual-boot..
everything i sayed is ok?
is there any OS that allows you to play anygame?
If i am dual-booting (that's what i will do) then is the following GB per HD is good?:
C:/50GB - Ubuntu OS
D:/20GB - Softwares
E:/200GB - Games & Installs
G:/THE OTHER - Windows XP OS
Or:
C:/70GB - Ubuntu OS & Softwares
D:/200GB - Games & Installs
E:/THE OTHER - Windows XP OS

Lets see.

As far as *Windows* gaming goes, yes it's iffy.  Some games run amazingly well.  Some are slow or buggy.  Some just refuse to even start.  (Check appdb.winehq.com to check on the status of something in particular)  Keep in mind that this is not Windows.  No OS will run a program that wasn't designed for it; Wine is a compatibility layer of sorts.  This only applies to Windows games of course.. Linux native games will of course run.  For games that *do* work properly with Wine, great.  Those that don't, that's what the disposable XP partition is for.

There is no OS that will perfectly run *every* game no.  

As far as the partition sizes go, that really depends on your needs. 

For me, I have two drives.  The first one is a 120GB that's purely Winders XP.  All it does is games that won't play in Wine.  Nothing else. Ever.

My other drive is a 500GB.  That's my Linux drive, partitioned into separate root, swap and home partitions, with home taking the majority of the space.  99% of the time I'm in Linux.  Home holds all my movies, music, a fair amount of games, blah blah it's pretty loaded up.

Whatever you pick, keep in mind the easiest way to set it up is to do XP first.  Ubuntu's installer is pretty good about picking up on another OS being installed and set up Grub appropriately.  XP on the other hand.... not so much.  It'll happily trash anything it finds as you can't possibly be using anything besides XP right?

---

### Post by markharding557 on 2008-06-13
there are some quite good native linux games,nexuiz,Sauerbraten(cube2)and openarena are good ones also the quake games run natively and quite a few opengl based games will work in wine.
directx however is much more patchy.
one thing not mentioned is you can run windows inside linux in a vm if you need it.

---

### Post by holiday on 2008-06-13
Security:
The security problems of Linux are different from those of Windows, but they are not necessarily small problems. I've known a number of Linux systems which have been seriously compromised by rootkits. 

You should run a firewall: firestarter is good, and you will help yourself a lot by putting your machine behind a router. Any old wireless router will do even if you're not going wireless. 

If you want to open your box to outside access via ssh, disable root access and avoid using standard usernames.

---

### Post by Camilia on 2008-09-07
To be certain that you could still use your games you could do a dual bootup.  Just click the option to use free space.

---

### Post by hyper_ch on 2008-09-07
> **holiday said:**
> I've known a number of Linux systems which have been seriously compromised by rootkits. 

You should run a firewall: firestarter is good, and you will help yourself a lot by putting your machine behind a router.

How will a firewall helping agains rootkits?

---

### Post by sloggerkhan on 2008-09-07
So far as language support, what you need to do is install the language pack for hebrew (search synaptic for hebrew, it will come up as a gnome language pack) and install.

You can then use language support to change to hebrew.
Please note that things may not be 100% translated depending on a large variety of variables, though you can get a rough idea by looking up translation > hebrew on launchpad. Also, I know that using arabic switches screen orientation of text and more from left to right to right to left, so I'd expect the same from other languages that follow the same pattern.

---

### Post by sudhakar on 2008-09-07
Yes , I am sure, this is faster than Windows Xp

---

### Post by MaxIBoy on 2008-09-07
Correction: Once you get all your drivers working, it'll be faster. For example, until you get graphics card drivers working, you won't be able to do 3d gaming and you will have worse performance. Just google linux plus the name of your graphics card, you'll find howtos.

---

