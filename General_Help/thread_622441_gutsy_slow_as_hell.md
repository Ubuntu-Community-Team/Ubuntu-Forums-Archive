---
title: "gutsy slow as hell"
date: 2007-11-24
forum: General Help
---

### Post by Chymera on 2007-11-24
I've posted similar threads before but this is IT, i can't believe that an os which has any ambition of not exasperating it's users can lock up DAILY.
For the past 4 days ubuntu has given me a lockup a day, following which I had to restart my machine unceremoniously. Mind what I'm saying: LOCK UP, not CRASH, I get 2-4 crashes a day, but I cant say I really mind that, its only about twice as bad as windows after all... 

I've had memory issues before, and some wise-guys tried to convince me that it's just a memory leak due to compiz, and due to exaile... which left me wondering if I ever had any such issues on windows or OSX....
Anyway, the situation is catastrophic; they say windows gets thrice as slow after 6 months of use, well my gutsy gets about 10 times as slow after 6 hours of use, by that time firefox takes about 10 seconds to decide to start up, exaile turns gray whenever loading a new playlist, nautilus cant seem to handle folders with more than 3000 files in them, compiz effects look as if they were engineered by the Lumière brothers themselves, even pidgin manages to crash occasionally, the icons in the panel menus appear 0.5 secs or more after the corresponding text,  open office just managed to break office 2007's record of sluggishness in word processing, the system monitor also takes some 5 seconds to decide whether or not to start up, even the terminal takes a couple of seconds to think about whether or not I pushed the right shortcut keys, and this is after all the 21st century...

Additionally, contrary to what some of you may think by now, I do not use a computer built last millennium (such as yours); I have a core2 quad processor at 2.4 GHz and 1066 MHz FSB, an Asus P5B Premium Motherboard with a matching 1066 MHz FSB, and 1066 MHz DDR2 RAM slots, sadly only 1 GB of ram at this point, but I doubt that's the source of my problems. My filesystem is on a serial ata drive; no, i don't have some crappy agp video card, and no, my computer doesn't work on hamster power. That being said, try to refrain from telling me its because I have a bad computer, and in addition refrein from telling me to just use OSX or windows if i can't seem to get along with ubuntu.... I have my own reasons for using linux, and have tried out quite a few distros before deciding to set camp here at Ubuntu.

Hopefully having deterred part of the flame-happy people reading this thread; do any of you share the same problem or have any idea on why Ubuntu is reducing my machines capacity to that of an atari console?

---

### Post by KIAaze on 2007-11-24
Disable tracker & beagle if you have them.
I heard they slow down a lot.

Did Feisty also run this slow on your PC?

---

### Post by skymera on 2007-11-24
ive found that after reinstaling serveral times ive loast quite a lot of performance, from distro hopping etc.
could be a reason? im gettin a new drive for ubuntu only, fresh install, fresh drive.

your specs are mighty fine, i dont understand the problem.
 reading through, my terminal sometimes takes a while, firefox does too.

i suggest new drive, if you do, tell me how it gos :)

---

### Post by technoidiot on 2007-11-24
Can't help with your speed issue but the crashing was (note: was) my problem. Am using KDE on an Nvidia card. enable 3d and mutliple windows. Result - constant freezes. Research and fiddling brought me to NO 3d and two desktops. Finally have updated Nvidia drivers installed and 3d working OK. BUT- can not go over 2 desktops or will freeze. No compiz - no cube none of the fancy stuff. Am currently running Kubuntu 7.04 on 2.6 Ghz HT with 2 GIG DDR. Not sure how to track down the issue to enable comiz, etc. but to avoid to freezes I live with want I know the machine will perform with.

---

### Post by daengbo on 2007-11-25
You don't need to fear flames, but you should calm yourself down a little.

First of all, that many lockups is a sign of something sriously wrong. Based on my experience, I'll guess that it's a hardware or driver issue.

Secondly, you're using Exaile, which is an Alpha program at 0.2. If you want a stable desktop, use stable apps like Amarok or Rhythmbox.

Finally, we need to know what graphics card you're using and what driver. If you are using the closed source driver from NVidia or ATI, then disable it and see if you stop having freezes.

The best way to have a good experience with Ubuntu is to use default apps.

---

### Post by Chymera on 2007-11-25
@danegbo: I started using Exaile because rythmbox is a piece of shirt and amarok was too unstable....
I have an nvidia geeforce 7300 gfx card, and that new driver that comes with gutsy 100.14.19 i think....

@skymera: what's distro hopping?

@Klaaze: how do i disable them?
Fiesty did run slower than my old windows xp, but not remotely as slow as gutsy is now...

---

### Post by Chymera on 2007-11-25
Oh and I forgot to add in my initial post, Add/Remove takes for ever to search, and everything gets twice as slow as hell while installing a program... reminds me of how I played w3 while installing corel in the background 1 year ago on my old pentium4 @ 2.4 GHz machine with 512 ram and an agp video card, which also had a broken motherboard (broken as in: with a fissure in it)....

---

### Post by KIAaze on 2007-11-25
I don't know if this could be the cause or not, but did you install the correct version for your architecture? (32-bit or 64-bit)
You can find out the architecture by typing "uname -a" in a console. (altough I don't know if that gives the installed version or the hardware info)

To disable beagle and tracker, go to "System->Preferences->Session" and uncheck all services containing beagle or tracker.

To remove (uninstall) them, run:
```
sudo apt-get remove beagle tracker tracker-search-tool tracker-utils
```

---

### Post by Chymera on 2007-11-25
yes, well, I have no idea at what point I could have left the impression of being a complete idiot, but yes, i managed to click the right link in the download window, and thus have the right architecture installed... incredible, is it?

now about beagle and tracker.... will i loose the ability to do certain tasks without them?

---

### Post by dips_xe on 2007-11-25
> **Chymera said:**
> yes, well, I have no idea at what point I could have left the impression of being a complete idiot, but yes, i managed to click the right link in the download window, and thus have the right architecture installed... incredible, is it?

now about beagle and tracker.... will i loose the ability to do certain tasks without them?

it wouldn't even install if it was the wrong architecture, but he wasn't implying you were an idiot, and you know that, so stop being smart, that MAKES you look like an idiot.

anyway, something's wrong with a driver, probably. it's not exaile (which i use and works fine), or beagle or tracker (and you can remove these, it doesn't matter)... and the other guy that said "distro-hopping" or whatever, he was referring to trying a bunch of different distros, and in the process wiping and writing to your hard drive a lot. he was implying it slows down your drive, but i don't think so

using another distro will probably fix the problem, reinstalling ubuntu might.

---

### Post by ekravche on 2007-11-25
Have you tried installing the 686 kernel, you can add it through the repositories... It will increase performance by taking advantage of your dual cores. I think yours will be the smp one I could be wrong. Google it and see which kernel people with your processor spec use

---

### Post by Chymera on 2007-11-25
> **dips_xe said:**
> it wouldn't even install if it was the wrong architecture, but he wasn't implying you were an idiot, and you know that, so stop being smart, that MAKES you look like an idiot.

anyway, something's wrong with a driver, probably. it's not exaile (which i use and works fine),

using another distro will probably fix the problem, reinstalling ubuntu might.

Really? asking someone if he installed a wrong architecture doesn't imply believing he is some sort of idiot who probably doesn't even know what a computer architecture is, and probably has to run some command to find out what he's got? You must be coming from a very jolly place then... Now, if I would REALLY want to look like an idiot, I'd state that you can't run operating systems built for a different architecture than that of your comp... 
having pointed that out, if you spent any resonable amount of time (3 weeks or more) amongst linux users you'd probably know that the fact that it worked well for you doesn't mean it has to work well for everyone else, which applies to all sort of apps, yes, including exaile... and that, of course, also works the other way around.
And yes, I know it's not exaile, or else i wouldn't call it a general problem...

Now, your suggestion is incredibly intuitive... I stated in my initial post that i have used quite a few distro's before deciding on ubuntu, and have good reason to not use most of the rest.... however, if i had the intention to change my distro would i still hang aroung to see what's wrong with my current install? lets see..... NO. Oh and it may be just me who's trying to be smart, but "use another distro!" sounds something like "buzz off" in a very euphemistic way, and considering how you started your reply, my interpretation doesn't seem that far fetched...

Thank you for your kindness and constructive commenting ;)

---

### Post by Chymera on 2007-11-25
> **ekravche said:**
> Have you tried installing the 686 kernel, you can add it through the repositories... It will increase performance by taking advantage of your dual cores. I think yours will be the smp one I could be wrong. Google it and see which kernel people with your processor spec use

Ive tried to look it up on google, but i have no idea where i could find something like that.... isn't there a site on which i can look it up?
Another thing.... where can i find that 686 kernel? searched add/remove and synaptic and it returned nothin'....
uname -r returns 2.6.22-14-generic 
and I havn't got dual cores but quad cores

---

### Post by KIAaze on 2007-11-25
> **Chymera said:**
> Really? asking someone if he installed a wrong architecture doesn't imply believing he is some sort of idiot who probably doesn't even know what a computer architecture is, and probably has to run some command to find out what he's got?

No, it just means that I can't know your level of computer knowledge just because you stated you have a super-computer with quad core, etc.
Sorry if I have offended you. That wasn't my goal.

My main suggestion was removing tracker and beagle, which are just some daemons that do file indexing so you can locate files faster.
If that didn't work, I can't help you further. My knowledge about kernel versions and compilation is pretty limited.

I suppose you already found the [http://www.kernel.org/](http://www.kernel.org/) page.
In the "What is Linux?" section there seems to be a list of links to kernels for other architectures.

And no, I am not implying that you are an idiot by telling you about this. It's just that since I'm posting here to excuse myself, I thought I might as well point that out to you in case you missed it.

---

### Post by Chymera on 2007-11-25
no problem, I didn't mean my reply as an enraged offense either, it's dips who had to make a tragedy out of it....

Now, i must admit i haven't checked that page, but I will as soon as i get over my present, more urgent issue, if any of you would want to help, here it is: [http://ubuntuforums.org/showthread.php?t=622404](http://ubuntuforums.org/showthread.php?t=622404)

---

### Post by pete.dawgg on 2007-11-26
the 2.6.22-14-generic is **** for smp-capable machines as it only uses the first processor;
do a > cat /proc/cpuinfo and the super-dooper-hyper-monster intel-quad MUST show you at least processors 0-3 if you got the right kernel.
find which kernel to install:
> apt-cache search i686 if you can't find it do some variations on the search expression (i686, kernel, smp, tralala)

i have to remind you that it is a very real possibility that your computer does not run well because it is TOO young (or too new). such grossly overpowered and wasteful hardware is developed mainly for windoze in its beginning stages, and that's why driver development for linux is (often considerably) slower. strange as it may sound: you'll most likely get faster running apps with "slower" hardware (in the later hardware generations) (not that you as a human would notice anything - but it can be measured ;)  and as a bargain you might get fewer freeze-ups and crashes )

setting your bios to conservative and "slow" settings might help here, too.
but still - your prob seems like some misconfig.


AND YES, you can install software for different architectures on the same computer (unless you consider x86 and x86_64 as SAME archs). it all depends on your compiler settings. and there's still the possibility of chroot, emulation-layers etc etc etc ;)

if you want to take advantage of your  powerful beast you should compile a kernel that really and exactly fits it and only it, compile it with decent, but optimized compiler settings and maybe recompile some sys-libs and the compiler itself, too. (there's MUCH MUCH room there  for esoteric tweaking, if you're into that ;)  )the prebuilt binaries you get from apt are compiled in a pretty generic way
BIG FAT WARNING: THIS CAN (AND WILL)  BREAK STUFF.  DO IT IN A TESTING ENVIRONMENT.


(nontechnical aside:
> if you spent any resonable amount of time (3 weeks or more) amongst linux users 
that is REALLY, REALLY cute.
i have read two books on linux and those ignorants at kernel.org will still NOT accept me as a new developer. maybe i should give it 3 more weeks ;)  )

GOOD LUCK WITH YOUR  MACHINE.

---

### Post by dips_xe on 2007-11-27
> **Chymera said:**
> Really? asking someone if he installed a wrong architecture doesn't imply believing he is some sort of idiot who probably doesn't even know what a computer architecture is, and probably has to run some command to find out what he's got? You must be coming from a very jolly place then... Now, if I would REALLY want to look like an idiot, I'd state that you can't run operating systems built for a different architecture than that of your comp... 
having pointed that out, if you spent any resonable amount of time (3 weeks or more) amongst linux users you'd probably know that the fact that it worked well for you doesn't mean it has to work well for everyone else, which applies to all sort of apps, yes, including exaile... and that, of course, also works the other way around.
And yes, I know it's not exaile, or else i wouldn't call it a general problem...

Now, your suggestion is incredibly intuitive... I stated in my initial post that i have used quite a few distro's before deciding on ubuntu, and have good reason to not use most of the rest.... however, if i had the intention to change my distro would i still hang aroung to see what's wrong with my current install? lets see..... NO. Oh and it may be just me who's trying to be smart, but "use another distro!" sounds something like "buzz off" in a very euphemistic way, and considering how you started your reply, my interpretation doesn't seem that far fetched...

Thank you for your kindness and constructive commenting ;)

if he was calling you an idiot, then why should you care? you don't know him and you know you're not an idiot... right? i personally think he was just trying to eliminate a possibility that would've solved a lot of time. even though you might be a linux expert, you could've clicked the wrong architecture or something, who knows?

and, yeah, you really can't run a different architecture than what the cpu was built to support. you can run a x86_64 AND i386 on a core 2 duo, but you can't run x86_64 on a pentium 1 or something.

and i think you should use another distro because the time it takes to solve the problem probably isn't worth it. it's unlikely that this is going to get solved.

---

### Post by dolphinsonar on 2007-11-28
[COLOR=Black]KIAaze, thank you!  I got that same feeling that I do popping a huge zit when I uninstalled beagle and tracker:

Errrghhh--OH, yeah...

Running much smoother now.

[/COLOR]
> **KIAaze said:**
> I don't know if this could be the cause or not, but did you install the correct version for your architecture? (32-bit or 64-bit)
You can find out the architecture by typing "uname -a" in a console. (altough I don't know if that gives the installed version or the hardware info)

To disable beagle and tracker, go to "System->Preferences->Session" and uncheck all services containing beagle or tracker.

To remove (uninstall) them, run:
```
sudo apt-get remove beagle tracker tracker-search-tool tracker-utils
```

---

### Post by Chymera on 2007-12-01
@ pete.dawgg:
10x, very much for you comment, and I will give it a try.... as for the do-it-yourself kernel part.... I've already given Gentoo some attempts, and one day would like to switch to it, at least temporarily; however, my rather superficial knowledge of linux systems is somewhat detrimental here :)

For now, I have a lot of work to do and will try to get along with this snail here, just so I won't risk any major data loss or long-term interruptions. Still, I am considering giving gentoo another try around new-year....

On the other hand, i am a little skeptical about your appreciation of the generic kernel.... you say it only uses the first core? well, on the system monitor I get 4 processors (cores) showing up...

oh yes, and the 3 weeks part was intended to be somewhat ironic, I've been around Ubuntu for 4 months and around linux for 2 years, and still don't consider myself anything remotely close to a wiz.... I just ment that by that time it usually dawns on ppl that under linux one installation differs a lot more from the next than under windows....

---

### Post by dolphinsonar on 2007-12-02
My uname output is 
  
2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

Should I install 64 Bit Kernels?

I think I used those words right...

---

### Post by KIAaze on 2007-12-02
i686 means it's 32-bit I think.

---

