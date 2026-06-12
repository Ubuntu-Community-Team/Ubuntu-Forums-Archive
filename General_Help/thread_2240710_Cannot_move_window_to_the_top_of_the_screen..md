---
title: "Cannot move window to the top of the screen."
date: 2014-08-21
forum: General Help
---

### Post by nathanrussell-nrc02 on 2014-08-21
Hello,

I was wondering if you could help me with a problem I'm experiencing with UbuntuGNOME.

This problem only occurs with with applications that use (I believe) the new gtk header bar.

I cannot move the GNOME programme Files, or Web, or Documents, etc. to touch the topbar in the GNOME desktop environment.

When I try, it is as if there is something above the header bar in the way.

However, when I press the alt key (I believe this is called the window action key in tweak tool?) and drag the window it is possible to place it.

I understand this hardly threatens stability or usability, but it is rather frustrating!

I'd be really appreciative if anyone knew about the issue, has experienced it, or has fixed it at all.

I apologise for the lack of accurate terminology, or any particular details that you need? I have done my best, please be kind, I'm rather new at this.

Many thanks!

I am currently using Ubuntu GNOME 14.04 lts

Recording of regular click and drag:
 [https://www.youtube.com/watch?v=CFdllltkd98](https://www.youtube.com/watch?v=CFdllltkd98)

Recording of alt click and drag:
 [https://www.youtube.com/watch?v=UrxESaYue3s&list=UUD09xVuApghGZxDjOYX0I_Q](https://www.youtube.com/watch?v=UrxESaYue3s&list=UUD09xVuApghGZxDjOYX0I_Q)

Comparison of regular click and drag with titlebar and non-titlebar applications:
 [https://www.youtube.com/watch?v=F_SJJAGEz7Y&list=UUD09xVuApghGZxDjOYX0I_Q](https://www.youtube.com/watch?v=F_SJJAGEz7Y&list=UUD09xVuApghGZxDjOYX0I_Q)

---

### Post by nathanrussell-nrc02 on 2014-08-22
[COLOR=#000000]Hello,[/COLOR]

[COLOR=#000000]I was wondering if you could help me with a problem I'm experiencing with UbuntuGNOME.[/COLOR]

[COLOR=#000000]This problem only occurs with with applications that use (I believe) the new gtk header bar.[/COLOR]

[COLOR=#000000]I cannot move the GNOME programme Files, or Web, or Documents, etc. to touch the topbar in the GNOME desktop environment.[/COLOR]

[COLOR=#000000]When I try, it is as if there is something above the header bar in the way.[/COLOR]

[COLOR=#000000]However, when I press the alt key (I believe this is called the window action key in tweak tool?) and drag the window it is possible to place it.[/COLOR]

[COLOR=#000000]I understand this hardly threatens stability or usability, but it is rather frustrating![/COLOR]

[COLOR=#000000]I'd be really appreciative if anyone knew about the issue, has experienced it, or has fixed it at all.[/COLOR]

[COLOR=#000000]I apologise for the lack of accurate terminology, or any particular details that you need? I have done my best, please be kind, I'm rather new at this.[/COLOR]

[COLOR=#000000]Many thanks![/COLOR]

[COLOR=#000000]I am currently using Ubuntu GNOME 14.04 lts[/COLOR]

[COLOR=#000000]Recording of regular click and drag:[/COLOR]
[https://www.youtube.com/watch?v=CFdllltkd98](https://www.youtube.com/watch?v=CFdllltkd98)

[COLOR=#000000]Recording of alt click and drag:[/COLOR]
[https://www.youtube.com/watch?v=UrxE...ghGZxDjOYX0I_Q]("https://www.youtube.com/watch?v=UrxESaYue3s&list=UUD09xVuApghGZxDjOYX0I_Q")

[COLOR=#000000]Comparison of regular click and drag with titlebar and non-titlebar applications:[/COLOR]
[https://www.youtube.com/watch?v=F_SJ...ghGZxDjOYX0I_Q]("https://www.youtube.com/watch?v=F_SJJAGEz7Y&list=UUD09xVuApghGZxDjOYX0I_Q")

(I'm not too sure where to post this)

---

### Post by ajgreeny on 2014-08-22
It almost looks as if the titlebar is still there but completely transparent and invisible in the examples you show.  Is that possible in your setup of the gnome window-manager, which I don't know in any way?

---

### Post by nathanrussell-nrc02 on 2014-08-22
Well, I'm not sure. I installed Ubuntu GNOME via the live CD and haven't changed anything (so far as I know) since. I've had this problem on two different machines, using two different versions of Ubuntu GNOME. Considering I'm using a long term support release, I'm very surprised that this has happened (especially since I haven't seen anyone else reporting this problem).

---

### Post by sammiev on 2014-08-22
It almost seems like a bug. Same happens with 14.10

---

### Post by nathanrussell-nrc02 on 2014-08-22
I think its a specific GNOME issue, when using Debian on a different computer a long time ago I noticed the same problem.

Does anyone know if there's a way to report this, if it does need reporting, or a solution? I'd be very surprised if no one had noticed this before.

---

### Post by Jonor on 2014-08-23
Thanks for this post Nathan, i filed a [bug]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1310322") a few months ago about this and have now 
amended it with a workaround using the super key as the alt key does not fix it on my keyboard. 
There is a [hide top panel extension]("https://extensions.gnome.org/extension/740/hide-top-panel/") that might be useful at getting things to display better.

---

### Post by nathanrussell-nrc02 on 2014-08-23
Alas no, with the top panel removed there is still a gap between Nautilus (and the other applications) and the very top of the screen.

Oh wonderful, thanks for filing the bug. Do you also have the same problem when using the GNOME application Documents? If so, I think its a problem that goes beyond just Nautilus; its my thinking that its a problem with the gtk header bar, would this need to be updated on the bug page? could you update it for me?

Many thanks.

Someone has posted a bug here:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1310322](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1310322)

I'd be grateful if you could update it with any information you have.

Many thanks.

---

### Post by vasa1 on 2014-08-23
Hi Jonor & Nathan, you could also think of posting in [https://lists.ubuntu.com/mailman/listinfo/ubuntu-gnome](https://lists.ubuntu.com/mailman/listinfo/ubuntu-gnome) to get a few more eyes on your issue (in case you haven't already).

---

### Post by nathanrussell-nrc02 on 2014-08-23
Thank you, doing now!

Jonor, I believe the reason the key differs is because it is the Windows Action Key. You can change this setting in the Tweak Tool application in Ubuntu GNOME.

---

### Post by Jonor on 2014-08-23
Haven't seen the problem with anything other than directory windows. Gedit and all other apps are fine.
In your Youtube vids it looks like directory windows are disappearing behind the top panel too, which i had and why the hide top panel
extension was mentioned. Diffucult to get at the directory window top panel buttons in that situation if you use them.
Had these problems since the start of Gnome 3.5, about 3 years now so am delighted you have lead me to a workaround.

---

### Post by nathanrussell-nrc02 on 2014-08-23
[https://www.youtube.com/watch?v=WxWOo6ra9EA](https://www.youtube.com/watch?v=WxWOo6ra9EA)

Do you have this application here?

Notice how the magnifying glass and tick buttons are attached to the same line as the close button (the same as how the directory entry is on the same line in Nautilus.)

Well, I'm glad things are a little better but it is still infuriating meeting that resistance trying to move a window. I hope with more people acknowledging the bug gets us closer to finding the cause and a potential fix.

---

### Post by Jonor on 2014-08-23
I haven't seen that app with the magnifying glass before.
For reference [here]("http://ubuntuforums.org/showthread.php?t=2168019&p=12759109#post12759109") is a post from a year ago when maximized directory windows were getting cut off at the top.
In my next [post]("http://ubuntuforums.org/showthread.php?t=2168019&p=12759625#post12759625") in the thread  hiding the top panel did not help because they were not
just hidden by the hideable top panel, so things are slowly improving from that situation.

---

### Post by nathanrussell-nrc02 on 2014-08-23
Oh wow,  I didn't realise. With a change like that I'd imagine bugs are fairly common. Thanks for your help, Jonor.

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1310322](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1310322)

Does anyone know what the process would be from here?

Does anyone know what the process would be from here?

---

### Post by Frogs Hair on 2014-08-23
If the bug is confirmed by enough people and categorized as important a person will be assigned to investigate and fix if possible.

---

### Post by nathanrussell-nrc02 on 2014-08-23
oh thank you

although, admittedly, I think the very nature of the bug would cause it to affect everyone using Ubuntu GNOME in its present, or previous (post-introduction of the gtk header bar) state.

---

### Post by vasa1 on 2014-08-23
Well, it looks like you've got a few more "affects me too" possibly as a result of posting on the mailing list but you could have linked to this thread as well :)

---

### Post by nathanrussell-nrc02 on 2014-08-23
Ah, apologies, I didn't quite know what to write.

Is there an estimate number of "affects me too" before something happens? I'm really unfamiliar with the system.

Also, do you have any personal inclinations on where the problem comes from or how to fix it?

Thank you.

---

### Post by vasa1 on 2014-08-24
> **nathanrussell-nrc02 said:**
> Ah, apologies, I didn't quite know what to write.

Is there an estimate number of "affects me too" before something happens? I'm really unfamiliar with the system.

Also, do you have any personal inclinations on where the problem comes from or how to fix it?

Thank you.Whether some happens or not depends on the devs. I think more people marking it as "affects me too" could only help draw attention to it. I think you should make an effort to discuss it at length on the Ubuntu GNOME mailing list and point to your videos which illustrate the problem.

Sorry, not a clue. I use another flavor, Lubuntu.

---

### Post by nathanrussell-nrc02 on 2014-08-24
I've noticed that someone has updated the bug description such that it says Nautilus isn't effected by the bug when it is being run as root, or sudo. I'd just like to point out the reason; the version with root privileges does NOT use the gtk header bar, this further supports the idea that it is in fact that that is causing the problem.

I've noticed that someone has updated the bug description such that it  says Nautilus isn't effected by the bug when it is being run as root, or  sudo. I'd just like to point out the reason; the version with root  privileges does NOT use the gtk header bar, this further supports the  idea that it is in fact that that is causing the problem.

---

### Post by lisati on 2014-08-24
Threads merged by request of OP

---

### Post by nathanrussell-nrc02 on 2014-08-24
Relevant submission to the Ubuntu GNOME mailing list:

Subject: Ubuntu Bug - Update

Content: 

I'd like to first raise awareness of every piece of evidence or relevant data I'm aware of regarding the bug.


1) The Ubuntu Forum thread I first submitted to try and gain information on the validity of the bug: [http://ubuntuforums.org/showthread.php?t=2240710](http://ubuntuforums.org/showthread.php?t=2240710)


2) The bug I subscribed to and heavily edited, to address the  technical causes and effects of the bug, to the best of my ability: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1310322](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1310322)


I'd now like to mention my thoughts on the true severity of  this problem; due to the very nature of the bug itself, it is likely to  manifest itself automatically (regardless of differences between one  computer and another) in every single installation of Ubuntu GNOME  present, future, and (dependant on the usage of GTK+ header bars) past.


The practically infinite spread of Bug #1310322, in my  opinion, gives it heat enough to be tackled as soon as practically  plausible.


I apologise I can't offer any useful technical  advise on this bug, but I do hope this effort will eventually lead to  the bugs fix.

---

### Post by nathanrussell-nrc02 on 2014-08-24
Bug #1310322 "Unmaximized windows that use the gtk header bar have a barrier above them preventing them from touching the top panel" has a new Bug Heat point of 34 and a new subscriber/affectee.

Regarding the nature of the bug: if the problem does lie in the gtk widget, or GNOME's window manager, is the Ubuntu GNOME forum the right place to document the bug? Any information would be appreciated.

Any current users of Ubuntu GNOME who know of this problem are, as always, encouraged to follow the link to the bug page and confirm the bug affects them too.

Thank you.

---

### Post by nathanrussell-nrc02 on 2014-08-29
I've heard from one person who says they don't experience the same problem. My thoughts are perhaps people without a dedicated graphics card (and use an integrated one) experience the problem, and those with one do not. Is that a thing? Could it be?

Curiouser and curiouser...

---

### Post by vasa1 on 2014-08-29
By the way, [http://www.webupd8.org/2014/08/how-to-disable-gtk3-client-side.html](http://www.webupd8.org/2014/08/how-to-disable-gtk3-client-side.html)

---

### Post by nathanrussell-nrc02 on 2014-08-29
Ah thank you, I've posted it to the bug page.

I'm still looking for more people, are any information on the bug whatsoever.

Anything would be greatly appreciated.

---

### Post by Jonor on 2014-08-29
[Here]("http://ubuntuforums.org/showthread.php?t=2158397&p=12711240") is another Gnome top bar thread that might be of interest.
If i remember correctly, when Gnome 3 first came out, the top bar was 
thicker, possibly equivelent to where the current barrier is ?
Does anyone else remember if this was so ?
It might help locate when, where and by whom the bug originated.

---

### Post by nathanrussell-nrc02 on 2014-08-29
alas, the problem isnt with the topbar but with the header bar of the windows; try moving the Files window directly underneath another window (Firefox, for example) there is still the gap. Oh wait... no, there isn't...huh

This is increasingly strange...

---

### Post by nathanrussell-nrc02 on 2014-09-20
Does anyone know if this will be solved by the next installment of ubuntu GNOME?

---

### Post by nathanrussell-nrc02 on 2014-10-01
I do not have the same issue using the GNOME shell in Fedora 19...

Can anyone suggest a reason for this?

My thoughts had been it could be a hardware issue. This now appears to be wrong...

This really is rather strange.

Are we certain this wont be fixed in the next Ubuntu GNOME release?

---

### Post by Jonor on 2014-10-02
My guess is the fact that you very helpfully identified a workaroud 
will delay the bug being assigned to a bug fixer so don't hold your breath !
RedHat Gnome software won't be identical to Ubuntu Gnome software.
Last time i checked Fedora, Gnome was the default Desktop Environment, 
so is bound to be more polished than over here which of course has Unity as default.

---

### Post by nathanrussell-nrc02 on 2014-10-02
I've also tested the new Utopic Unicorn on my laptop, this handles the header bar perfectly as well.

This information may well be useful in the long term, any help from others would be fantastic.

Thanks,

---

### Post by nathanrussell-nrc02 on 2014-10-02
Whilst this is true, I experienced the same issue with Debian on another PC and it appears also to be fixed on 14.10 (some had previously said 14.10 offered no such fixes for them)

this really has peaked my interest

very curious indeed...

regards,

---

### Post by nathanrussell-nrc02 on 2014-10-05
fedora 20 worked fine also, but after one update it broke again with this issue.

As I say, the beta for Utopic is perfect. No problems here.

Nathan

---

### Post by nathanrussell-nrc02 on 2014-10-05
Just confirming that this was a mult-os problem.

---

