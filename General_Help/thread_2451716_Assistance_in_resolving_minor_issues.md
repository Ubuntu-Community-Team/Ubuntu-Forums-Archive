---
title: "Assistance in resolving minor issues"
date: 2020-10-09
forum: General Help
---

### Post by dtpr0xy on 2020-10-09
Hello there!

[B]Long time Windows user here - now looking to migrate to Linux over time, the choice of entry distro fell on Ubuntu.
[/B]
The installation worked after I had to work around some problems (probably display driver related (bug?) that caused artifacts when I tried to finish the Ubuntu Installation, turned black screen and frozen/"artifacted" images when i tried to boot it up.) In the GNU menu i had a option to boot Ubuntu in "safe mode", which worked, then I installed the latest Nvidia repository drivers, which solved the problem (I could now boot into Ubuntu without crashing).

I would appreciate if someone would take their time to address the issues that I'm unable to solve on my own now.I have searched for solutions on the Internet but I can't fully comprehend everything so please ELI5. :redface:[INDENT=2]

[/INDENT]
[INDENT][COLOR=#b22222][B][COLOR=#b22222][B]GRUB Boot option display
[/B][/COLOR][/B][/COLOR][/INDENT]
[INDENT=2]Everytime I boot up Ubuntu I'm prompted by the Grub boot menu e.g "Boot Ubuntu" normal or few other options.
I would like Ubuntu just to boot up and not get prompted and have to make a choice every time (30S timer for it to automatically boot).
[/INDENT]
[INDENT=2][COLOR=#000000]

[/COLOR][/INDENT]
[INDENT]**KDE Plasma problems**[/INDENT]
[INDENT=2][COLOR=#000000][B]I know this is not a forum for desktop environments (hopefully It's okay for me to ask anyway as I think there's probably a lot of Plasma users here?)
[/B]
I have two minor issues here:
1. On startup there is a big virtual keyboard blocking half of the screen (I have to type someting and press enter to make it dissapear to access the login screen)
2. On startup I get prompted that a application wishes to access KDE Wallet and asks for the password which I have to enter every time I log in, quite annoying.

From what I understand KDE Wallet helps me to login on the application. From a security standpoint I can understand this but it's only one application that I use that needs to access it.
[/COLOR]

[/INDENT]
Thank you for your time reading this and I appreciate any help i get here.
Have a nice weekend :popcorn:


[SIZE=1]Linux>Windows,
Why didn't anyone tell me earlier?[/SIZE]

---

### Post by Autodave on 2020-10-09
Let's start by getting some important information:
Tell us about your equipment, especially video card.
What version of Ubuntu did you install?
If you installed a video driver, what one did you install and where did you get it from?

---

### Post by QIII on 2020-10-09
Hello.

I have restored the contents of your post.  Please do not delete text like that.  We consider it forum vandalism.

Rather than taking your ball and going home, how about explaining what the solution was in case someone else can be helped by it?

---

### Post by helen314 on 2020-10-09
> **QIII said:**
> Hello.

I have restored the contents of your post.  Please do not delete text like that.  We consider it forum vandalism.

Rather than taking your ball and going home, how about explaining what the solution was in case someone else can be helped by it?

"Vandalism " ?   " We..." ? 
 
Instead of choosing the "we superiority complex " and  "it is users fault" - direct you post to **actually help the user**.

The user is not obligated to rate or share HIS own resolution in such controlling environment.
Same goes for the another and usual "RTFM" , "this may  be over your head". 

And if I get banned for  posting this - what else is new ?

---

### Post by QIII on 2020-10-09
I suggest you read the [Ubuntu Forums Rules]("https://ubuntuforums.org/misc.php?do=showrules") and the [Posting Guidelines ]("https://ubuntuforums.org/showthread.php?t=2158945").

"We" being the forums community, the Staff and the Admins.  "Vandalism" being what "we" call it.  The posts here are not the property of the individual.  The content belongs to the community.

And no, the poster is under no obligation other than being considerate of the forum community and the next person who might find an answer they are looking for.  This is not an individual help forum.  It is a community forum for everyone to find answers and we have an expectation that good citizenship includes leaving breadcrumbs for others to follow in seeking solutions.  See my signature: 

"A thing discovered and kept to oneself must be discovered time and again by others. A thing discovered and shared with others need be discovered only the once."

RTFM?  We remove those posts.

As for posting something to help the user ... the user deleted to post contents and is not logged in right now. 

I acted in the capacity of a Forum Admin.  That is what I am charged with.  If you don't like the fact that this is a *moderated* forum, you are welcome to spend your time elsewhere.

---

### Post by grahammechanical on 2020-10-09
I learnt a lot from this forum before I felt confident enough to join the forum community. So, in the interests of both the forum community and those forum readers who are not yet members I will try to give some answers.

> Everytime I boot up Ubuntu I'm prompted by the Grub boot menu e.g "Boot Ubuntu" normal or few other options.

This is the default when there are two or more operating systems on the machine. If this machine has only one operating system then I have next to no idea why the Grub boot menu is appearing. I suspect this behaviour can be obtained by editing a Grub configuration file.

> I would like Ubuntu just to boot up and  not get prompted and have to make a choice every time (30S timer for it  to automatically boot).[COLOR=#000000]
[/COLOR]

The default is usually 10 seconds. I am sure it is 10 seconds. The clock can be stopped by pressing a key. I use an arrow key. I suspect that the length of the timeout can be adjusted by editing the Grub configuration file.

The default operating system is usually at the top of the list and highlighted. I simply press enter and the default operating system loads. 

For those technically inclined there is a manual

[https://www.gnu.org/software/grub/manual/grub/grub.html](https://www.gnu.org/software/grub/manual/grub/grub.html)

Check out &#8216;GRUB_TIMEOUT&#8217;

Regards

---

