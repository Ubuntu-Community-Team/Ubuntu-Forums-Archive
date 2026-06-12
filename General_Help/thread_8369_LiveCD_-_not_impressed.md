---
title: "LiveCD - not impressed"
date: 2004-12-16
forum: General Help
---

### Post by jobby on 2004-12-16
My experience with the LiveCD:

1st Boot: Hung on progress bar.
2nd Boot: Tried expert mode, entered 'yes' for the SCSI question, promptly hung. Aha!
3rd Boot: Answered 'no' to SCSI and managed to boot. Tried to access the net...and nothing. Then I tried the networking config app, which was decidedly unhelpful. When I entered all my settings and hit activate, the activate box became checked...and then promptly unchecked itself. No error messages or anything, it just didn't work. My USB ports don't seem to work either. Of course, the Device Manager thing just doesn't load, so no help there. I have a K8N Neo motherboard (Nforce3 Ultra), an Athlon64 2800+ 512MB of generic RAM and a vanilla 6800. Any ideas?

---

### Post by eldrich_rebello on 2004-12-17
hi have you tried the cd on another computer?

---

### Post by nemin on 2004-12-17
[QUOTE=jobby]My experience with the LiveCD:

1st Boot: Hung on progress bar.
2nd Boot: Tried expert mode, entered 'yes' for the SCSI question, promptly hung. Aha!
3rd Boot: Answered 'no' to SCSI and managed to boot.[/QUOTE]
Sadly, there are still computer configurations linux doesn't easily run on. This is not really ubuntu-specific, though other live cds like knoppix might give better results.
You maybe want to try another computer, or remove non standard hardware from you r pc.

> 
Then I tried the networking config app, which was decidedly unhelpful. When I entered all my settings and hit activate, the activate box became checked...and then promptly unchecked itself. No error messages or anything, it just didn't work.

What does 'ifconfig' sais? (You have to run that in a terminal)

---

### Post by rbrimhall on 2004-12-17
I wasn't impressed either... blank screen on my widescreen laptop... and a "squished" screen on my older desktop with i845 embedded graphics (800x600 res)...

---

### Post by nemin on 2004-12-17
Ubuntu is of course not a specific live distribution, like knoppix.  I see the live CD more as some sort of 'bonus' and it just works fine for me :)

---

### Post by jdong on 2004-12-17
Let's get something straight here...

The current Ubuntu LiveCD is actually a modified MORPHIX LiveCD -- with a mainmod containing Ubuntu packages.

So, the actual hardware detection and X configuration is done by **the morphix detection routines**, which are based off KNOPPIX.

Therefore, it's **NOT** Ubuntu's fault that the LiveCD can't detect certain types of hardware.

Since Ubuntu is working together with GNOPPIX, I anticipate the next LiveCD release will be better at this!

---

### Post by jobby on 2004-12-17
Thanks for all the replies:

eldrich_rebello - I don't have another computer to run it on.
nemin - Er, non-standard hardware? Sound, USB and ethernet is all integrated into my motherboard. ifconfig just gives me the loopback address and that's all. I'm not sure about seeing it as a bonus - I saw it as a way of checking Ubuntu's compatibility with my computer non-destructively.
jdong - I understand, but I expect more from a distro that bills itself as "Linux for Human Beings". Incidentally, I don't suppose you know of anywhere in the morphix world that would help with this? Googling for 'morphix scsi hang' and 'morphix nforce3 detection' were not particularly helpful.

Ah well. Incidentally, for any googlers led here: knoppix 3.7 works great with the K8N Neo mobo with 'knoppix26 noscsi' (although you may have to mount USB devices on your own).

---

### Post by jdong on 2004-12-17
[QUOTE=jobby]
jdong - I understand, but I expect more from a distro that bills itself as "Linux for Human Beings". Incidentally, I don't suppose you know of anywhere in the morphix world that would help with this? Googling for 'morphix scsi hang' and 'morphix nforce3 detection' were not particularly helpful.

Ah well. Incidentally, for any googlers led here: knoppix 3.7 works great with the K8N Neo mobo with 'knoppix26 noscsi' (although you may have to mount USB devices on your own).[/QUOTE]

It's a first release... You can't expect EVERYTHING from them!

It's probably caused by the old 2.6.7 kernel -- Have you tried Gnoppix? It's virtually a Warty Live CD, too, with newer Knoppix components.

---

### Post by nemin on 2004-12-18
> **jobby]
nemin - Er, non-standard hardware? Sound, USB and ethernet is all integrated into my motherboard. 
[/QUOTE]
Yeah, you're right: there's not a lot to remove then  said:**
> 
ifconfig just gives me the loopback address and that's all. 

Maybe you could try the 'ifconfig eth0 up'  command?

---

### Post by nemin on 2004-12-18
[QUOTE=jdong]Let's get something straight here...

The current Ubuntu LiveCD is actually a modified MORPHIX LiveCD -- with a mainmod containing Ubuntu packages.

So, the actual hardware detection and X configuration is done by **the morphix detection routines**, which are based off KNOPPIX.

Therefore, it's **NOT** Ubuntu's fault that the LiveCD can't detect certain types of hardware.

Since Ubuntu is working together with GNOPPIX, I anticipate the next LiveCD release will be better at this![/QUOTE]
Didn't know Ubuntu LiveCD is based on MORPHIX LiveCD. Does that mean that the hardware detection of the LiveCD isn't the same as the normal Ubuntu distribution? So you can't use the LiveCD to check Ubuntu's compatibility with your computer?

---

### Post by jdong on 2004-12-18
[QUOTE=nemin]Didn't know Ubuntu LiveCD is based on MORPHIX LiveCD. Does that mean that the hardware detection of the LiveCD isn't the same as the normal Ubuntu distribution? So you can't use the LiveCD to check Ubuntu's compatibility with your computer?[/QUOTE]

Not really... Linux universally detects the same amount of hardware -- as the kernel (and XWindows) contains all the "drivers".

The morphix livecd contains a fairly recent 2.6 kernel, and it contains Warty's exact version of X.

---

### Post by eBopBob on 2004-12-18
> Let's get something straight here...

The current Ubuntu Live CD is actually a modified MORPHIX Live CD -- with a mainmod containing Ubuntu packages.

So, the actual hardware detection and X configuration is done by the morphix detection routines, which are based off KNOPPIX.

Therefore, it's NOT Ubuntu's fault that the Live CD can't detect certain types of hardware.

Since Ubuntu is working together with GNOPPIX, I anticipate the next Live CD release will be better at this!
Hmm... That just does not sound right. Sorry, however why say it's an Ubuntu Live CD when it's obviously not?? :confused:

That kind of thing will just cause problems - Taking something possibly inferior, saying it's your own and then freely distributing it so people will try it out and then download the proper version which is yours.

---

### Post by jdong on 2004-12-18
It **IS** a Ubuntu LiveCD.

All the programs-- X, GNOME, Openoffice, Firefox, etc is made by Ubuntu.

---

### Post by nemin on 2004-12-18
[QUOTE=eBopBob]Hmm... That just does not sound right. Sorry, however why say it's an Ubuntu Live CD when it's obviously not?? :confused:[/QUOTE]
I don't agree with you. As jdong said, the LiveCD is Ubuntu. That it's (partly) based on something else doesn't matter.
> 
That kind of thing will just cause problems - Taking something possibly inferior, saying it's your own and then freely distributing it so people will try it out and then download the proper version which is yours.
The LiveCD gives you a preview on the real distribution and I think that's what it is meant for.  In my opion, every distribution has some sort of "feeling" and the LiveCD is an easy way  to get the "Ubuntu feeling".

---

### Post by eBopBob on 2004-12-19
> It IS a Ubuntu Live CD.

All the programs-- X, GNOME, Openoffice, Firefox, etc is made by Ubuntu.
Sorry... I am a bit confused. You said "*The current Ubuntu Live CD is actually a modified MORPHIX Live CD -- with a mainmod containing Ubuntu packages. So, the actual hardware detection and X configuration is done by the morphix detection routines, which are based off KNOPPIX. Therefore, it's NOT Ubuntu's fault that the Live CD can't detect certain types of hardware.*"

Correct me if I am wrong, however from that I understand that Ubuntu took another Live CD and modified it slightly to give the feeling of Ubuntu when at its core it isn't really?



> The Live CD gives you a preview on the real distribution and I think that's what it is meant for. In my opinion, every distribution has some sort of "feeling" and the Live CD is an easy way to get the "Ubuntu feeling".
But does it give you a 100% preview of the real distro?
That is what I mean when I say it can cause problems - If that in fact certain things are different on the Live CD and the real distro (IE: Hardware detec, speed, etc. etc.).

---

### Post by nemin on 2004-12-19
[QUOTE=eBopBob]Sorry... I am a bit confused. You said "*The current Ubuntu Live CD is actually a modified MORPHIX Live CD -- with a mainmod containing Ubuntu packages. So, the actual hardware detection and X configuration is done by the morphix detection routines, which are based off KNOPPIX. Therefore, it's NOT Ubuntu's fault that the Live CD can't detect certain types of hardware.*"

Correct me if I am wrong, however from that I understand that Ubuntu took another Live CD and modified it slightly to give the feeling of Ubuntu when at its core it isn't really?[/QUOTE]
What do you mean here with core? I'm not sure, but I think Ubuntu took the specific 'live' code of Morphix and built the distro based on that. Ubuntu is not a specific live distro, so what's wrong with taking that part from another?
[QUOTE=eBopBob]
But does it give you a 100% preview of the real distro?
That is what I mean when I say it can cause problems - If that in fact certain things are different on the Live CD and the real distro (IE: Hardware detec, speed, etc. etc.).[/QUOTE]
Of course it doesn't give you a 100% preview of the real distro, a LiveCD is something different than a normal installation. But in my option, the LiveCD gives you an excellent preview on the most important things of a distribution.

---

### Post by Nomad on 2004-12-21
Very bad marketing idea!

I have been using Ubuntu for awhile, but I can't give out
this Live CD,  I just keep handing out Knoppix 3.7

---

### Post by snitgaard on 2004-12-22
Hmmm... feeling versus technology!
 
What is the purpose of having an Ubuntu Live CD? It is my impression that the purpose is to have a tool for convincing ordinary users ("humans", Windows users) that Linux, specifically Ubuntu, is a viable alternative to Windows. This is a matter of demonstrating daily usage and not a technology showoff - it&#8217;s all about selling the idea, and you may refer to this as marketing.
 
Why do you hand out Live CD&#8217;s? Clearly you like Ubuntu, but you see an ethical/techical issue in handing out a very convincing demonstration of Ubuntu Linux capabilities and consequently you prefer to hand out Knoppix (which is not that bad [img]http://www.ubuntuforums.org/images/smilies/icon_wink.gif[/img] ).
 
I guess you see this (choosing Knoppix and d[font=Times New Roman][font=Verdana][size=2]isqualifying Ubuntu Live CD)[/size][/font] [/font]as being more technically true, than the minor twist (Morphix) that has been used to create the Ubuntu Live CD. I was also I bit surprised when I heard that the internals of the Ubuntu Live CD is in fact derived from another distribution, but having seen the effect of the Live CD on real humans/users, I can easily forgive this.
 
[font=Times New Roman][font=Verdana][size=2]I hope that everybody in this community agree, that the Ubuntu Live CD is a great way of demonstrating Linux to our surroundings and will continue to distribute the CD&#8217;s. [img]http://www.ubuntuforums.org/images/smilies/icon_razz.gif[/img] [/size][/font][/font]

---

### Post by jakeslife on 2004-12-22
I for one will definitely continue to give out the Ubuntu CD's that I have ordered, and even made myself for those who want them badly enough. Live CDs gave me a testing ground for the little bit of linux that I already knew, without compromising the data on my Windows partitions, and many people use them not only for exploration, but also technology forensics, diagnostic, etc. I would be lying if I said that a Live CD didn't help me rescue a friend's computer when they messed something up in Windows.

Another thing for me is that Ubuntu, while the Live CDs capabilities are somewhat limited, it worked great for me! I have tried many linux distros and Live CD's (mostly KDE-based--while pretty, I find them somewhat bloated), and Ubuntu was the one that recognized most of my hardware installed, and needed only minor tweaking in order to get working functionally. 

I know that many companies and community-based distributions are trying to get more Windows people (read: non-power users) to discover linux and OS, and I think that Live CDs are a great way to do that. They can play around all they want without panicking when something goes wrong, being able to wave their Windows flag just by rebooting if they don't like it. 

Right now the current state of linux--including Ubuntu--is not ready for those regular computer users at home who want things easy and simple for them, but it's definitely getting there, and I see Ubuntu as a huge step in the right direction. When I first started becoming interested in OS, I did as much research as I could about the various distros and software available, known issues, etc., and realized that I was going to have to learn something new. Right now, if people choose to switch from Windows to linux, they will have to learn something new: they will have to learn how the command line functions, they will have to get used to a new file directory structure, and they will have to get used to new software. But that's the exact same thing they had to get used to when they started using Windows as well. 

The command line scares most people. I have to admit, I can be fairly intimidated by it at times, but I research everything I do before I do it, but I realize everyone is not open to that kind of research and learning. This is why I don't think linux is yet ready for those average desktop users who have to call their second cousin over whenever something goes wrong. While apt-get is so functional, and Ubuntu's non-GUI installer is simple, streamlined, and in my opinion extremely functional, that takes a bit to warm up to when you're used to doing things through a standard GUI. 

I think that when linux and OS goes mainstream (*cringes at the looks I'm getting*) that Ubuntu will be at the forefront--it has a strong community, it has impressive backing, and it is not just a product that has been made to generate revenue, it helps generate knowledge and community. Before I found Ubuntu, I have never been so involved with a forum online, and frankly it's one of those little things that I find fulfilling, knowing that by learning what I learn about Ubuntu, I can show someone else to get them out of the rut they're in. 

So yes, in short, I will still be handing out my CDs!

---

