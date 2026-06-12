---
title: "Kubuntu: just too much like Windows [Resolved]"
date: 2007-05-20
forum: General Help
---

### Post by BLTicklemonster on 2007-05-20
Okay kids, want some fun? Take your gnome ubuntu, and install kubuntu desktop on it, then check it out, then try removing it. Then reboot. 

Nice Kubuntu splash screen huh?

Kubuntu kinda takes over don't it?


Question:

How can I be rid of the kubuntu splash screen, and why is it even still there?

---

### Post by sdide on 2007-05-20
As root or with sudo, do:

~# apt-get install --reinstall usplash usplash-theme-ubuntu

---

### Post by Bachstelze on 2007-05-20
You're being stupid.

Just because KDE has the taskbar at the bottom doesn't mean it's like Windows !! When Windows will do a tenth of the things KDE can do, hell will freeze...

---

### Post by BLTicklemonster on 2007-05-20
Thank you for the command to remove the splash screen. That was all I was asking for, I have no idea where that other remark came from. Kde and Kubuntu are okay, I just prefer gnome, and wanted to remove the kubuntu splash screen. 

And I'll leave the gut reaction to calling anyone stupid for not understanding my request out of this, thank you.


No wait, Slackware, because it works?

Sheesh.

---

### Post by Bachstelze on 2007-05-20
Your request was answered, wasn't it ? And sorry to disappoint you but bashing something you don't like by saying it's "like Windows" is not a proof of high intelligence. And not being able to see beyond the colour of the desktop is not, either...


Oh, wait.

And not being able to run Slackware is not, *either*.

---

### Post by BLTicklemonster on 2007-05-20
Dude, chill out. I'm in kde right now, so get off me you troll.

[[IMG]http://img204.imageshack.us/img204/2770/200705200330361400x1050zn3.th.png[/IMG]](http://img204.imageshack.us/my.php?image=200705200330361400x1050zn3.png)

---

### Post by HereInOz on 2007-05-20
I understand now what you meant by "too much like Windows" in that it took over your machine and did what it wanted, with no apparent way to change it, however, I, too, initially read it and understood it the same way that HymnToLife did.  It was only after a re-read that I realised that you were referring specifically to the splash screen behaviour.

There are many people on this forum for whom English is not their first language, and we have to be mindful of that, and be gentle with the inevitable misunderstandings.  I sometimes run foul of people in the US when I use Australian expressions and common Australian syntax, and the Americans don't get the meaning, and therefore respond inappropriately.

---

### Post by Bachstelze on 2007-05-20
I understood what he meant very well, thanks. And it definitely is nonsense. Kubuntu installs it's splash screen when you install it, you think it's a bad thing and you're perfectly right. But Ubuntu does the very same thing ! Doesn't it install it's splash screen without asking you anything about it when you install it ? Yes it does. So blaming Kubuntu on that is just stupid. As if there were'nt enought things to blame it for as it is...

Oh, and with more than 3000 messages, I guess I can say that I am no troll...

---

### Post by Tomosaur on 2007-05-20
> **HymnToLife said:**
> I understood what he meant very well, thanks. And it definitely is nonsense. Kubuntu installs it's splash screen when you install it, you think it's a bad thing and you're perfectly right. But Ubuntu does the very same thing ! Doesn't it install it's splash screen without asking you anything about it when you install it ? Yes it does. So blaming Kubuntu on that is just stupid. As if there were'nt enought things to blame it for as it is...

Oh, and with more than 3000 messages, I guess I can say that I am no troll...

If you have nothing nice to say, then say nothing at all. He only asked for help, not a lesson in semantics.

---

### Post by nphx on 2007-05-20
Don't worry he'll change his mind when KDE 4 comes out.

---

### Post by mikewhatever on 2007-05-20
> **BLTicklemonster said:**
> Okay kids, want some fun? Take your gnome ubuntu, and install kubuntu desktop on it, then check it out, then try removing it. Then reboot. 

Nice Kubuntu splash screen huh?

Kubuntu kinda takes over don't it?


Question:

How can I be rid of the kubuntu splash screen, and why is it even still there?

I had the very same issue with 6.10. In fact, if you search for kde (locate kde) on your system, there are lots of left overs you might also want to get rid off.
I am not going to take part in the scramble, but just express my opinion. Kubuntu looks nothing like Windows and in no way did it take over my machine. The issue with the splash screen was purely cosmetic and easily fixable.
HymnToLife, I think BLTicklemonster has an opinion and should not be flamed at for it.

---

### Post by g8m on 2007-05-20
Yep, forum title is a bit confusing. I opened it because of the flaming. I like flaming.

Usplash and KDE are in not connected. Usplash can be themed. It's just a setting

Have a look in /usr/lib/usplash

If installed as alternative: sudo update-alternatives --config usplash-artwork.so

My current theme:  [http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468](http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468)

---

### Post by mitko_ on 2007-05-20
When I showed KDE (Kubuntu) to my roommates, they said exactly the same thing: this looks too much like Windows. They don't have any experience with computers (except playing games) , so the probably made a judgment solely by the looks of it. 

I don't want to make a judgment either - I know that the looks are very customizable, and they are not the one thing to judge on. And, even, so what if it looks too much like Windows - it not a bad look :o. 

Personally, I think that GNOME has a better usability and thats why I like it. ;)

---

### Post by BLTicklemonster on 2007-05-20
I personally don't mind anything about Kubuntu or Kd3 at all. I just prefer Gnome. But as stated, the fact that it kept the splash screen instead of removing it when I was under the impression that I was removing Kubuntu bothered me. Oh, and I normally use either icewm or fluxbox.

And a high post count is not a bellweather of "non-trollular entities" thank you.

---

### Post by Sunflower1970 on 2007-05-20
> **BLTicklemonster said:**
> Okay kids, want some fun? Take your gnome ubuntu, and install kubuntu desktop on it, then check it out, then try removing it. Then reboot. 

Nice Kubuntu splash screen huh?

Kubuntu kinda takes over don't it?


Question:

How can I be rid of the kubuntu splash screen, and why is it even still there?

I have a similar problem with Xubuntu. I installed Xubuntu, uninstalled Ubuntu, yet the Ubuntu splashscreen still shows up....It's a bit weird, but nothing I'm too upset over. I'll fix it some day. :D

---

### Post by Nythain on 2007-05-20
yeah, correct me if im wrong, but when you install any of the *buntu desktops dont they replace the splash screen with thiers... i've even heard that they will replace the DM (eg GDM and KDM)... its not just kde

---

### Post by aysiu on 2007-05-20
The support question has been answered.

As has been pointed out, the Usplash "taking over" has nothing to do with Kubuntu. The same thing happens when you add Ubuntu to Kubuntu or Xubuntu to Ubuntu.

Any further discussion should be directed to [this thread](http://ubuntuforums.org/showthread.php?t=427232).

---

