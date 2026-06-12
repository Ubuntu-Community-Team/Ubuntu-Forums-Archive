---
title: "Alltray not cooperating in Hardy"
date: 2008-04-24
forum: General Help
---

### Post by LogicalDash on 2008-04-24
In Gutsy I used the GNOME session manager to run "alltray thunderbird -na" at the start of every session. This had the effect of starting Thunderbird iconified in the system tray, so that it would let me know about new mail while keeping out of the way.

In Hardy, this still kinda works, but now I always see the Thunderbird window open at startup and have to get rid of it manually. Further, I cannot get rid of it by clicking on the Close Window button, because that causes Thunderbird to *quit*, whereas in Gutsy it would disappear into the systray as I wanted it to. Instead, I have to click on the icon in the systray.

This is annoying. Why is it happening? What can I do to fix it? Alltray has an option "-show" to let me specify that I *do* want to see the window at program start, but no equivalent option to say that I *don't*; that seems to be the intended default behavior.

---

### Post by ibuclaw on 2008-04-24
Have you tried typing it in the terminal?

Hit **Alt+F2**, then type in:
```
alltray thunderbird -na
```
Wait for the app to start, then quit it.

Copy and post up any error messages or feedback the program gives you when you run it.

Regards
Iain

---

### Post by LogicalDash on 2008-04-24
When I run it that way, it behaves the same way as described above. There are no error messages.

**However**, when I run it in a terminal window, Alltray correctly starts Thunderbird hidden in the systray. I still have the problem where closing the window kills the program, though.

Weird. Maybe there's something wrong with the way GNOME passes the command to the terminal?

---

### Post by xand on 2008-04-26
same here...very annoying :/

---

### Post by Shampyon on 2008-04-26
I've noticed this too. I used to have a couple of apps set to run at startup under Alltray. It's a bit of an annoyance.

---

### Post by SpaceTeddy on 2008-04-27
yep - same problem here. Alltray application will not minimize to the systray anymore when clicked on the close button

a fix would be great :)

---

### Post by vordan on 2008-04-29
The problem occurs when compiz is enabled. If you disable the visual effects, alltray works as expected. 
So, because my productivity is more important to me than some windows dancing around, the visual effects got the axe!
All good again in the land of Ubuntu!:cool:

---

### Post by SpaceTeddy on 2008-04-29
wobbly windows and desktop cubes are no real deal - they're just eyecandy. 
What is important is the widget layer. Is there a way to enable it without using compiz ?

I really need widgets ! I use SSHManage and terminal widgets to get my daily work done...

---

### Post by xand on 2008-04-29
Unfortunately, here, even turning compiz off choosing metacity over it in fusion-icon, all-tray insists in closing the application...:/

---

### Post by akoro on 2008-04-29
Same problem here, I hope someone finds a workaround soon!

---

### Post by SpaceTeddy on 2008-04-29
i am using kdocker at the moment. That one does NOT overwrite the close button (so using that will still close your application), but at least it can minimize any application to the system tray. For that, you must click on the icon in the system tray itself... not minimize and not close. 

It's ugly, and it also produces pop-ups that i really don't like - but at least it sort of works...

---

### Post by akoro on 2008-04-29
I found a working version in [https://bugs.launchpad.net/ubuntu/+source/alltray/+bug/106583](https://bugs.launchpad.net/ubuntu/+source/alltray/+bug/106583)

For i386:
[http://ppa.launchpad.net/mtrausch/ubuntu/pool/main/a/alltray/alltray_0.69-1ubuntu2~ppa1_i386.deb](http://ppa.launchpad.net/mtrausch/ubuntu/pool/main/a/alltray/alltray_0.69-1ubuntu2~ppa1_i386.deb)

For amd64:
[http://ppa.launchpad.net/mtrausch/ubuntu/pool/main/a/alltray/alltray_0.69-1ubuntu2~ppa1_amd64.deb](http://ppa.launchpad.net/mtrausch/ubuntu/pool/main/a/alltray/alltray_0.69-1ubuntu2~ppa1_amd64.deb)

It's working fine for me.
Cheers,
koro

---

### Post by SpaceTeddy on 2008-04-29
works for me in metacity (normal gnome). 

But as soon as compiz is running, the close button still closes the application instead of minimizing it. 
But also the click on the icon in the system-tray works again, so i do not have to use kdocker anymore, and thus not get the pop-ups... 

so it is an improvement :)
thanks a lot !

---

### Post by simon_w on 2008-04-30
I've been experiencing more-or-less the same problems, which are solved when Compiz is disabled.  However, just for the record, when Compiz *is* enabled, the command 'alltray thunderbird -na' simply loads thunderbird without alltray at all.  In fact, when desktop-effects are on, the only way to invoke alltray for, e.g., thunderbird is to start thunderbird first, and then dock it using the alltray gui.

I too hope a way can be found to allow alltray and compiz to live happily together!

:):)

---

### Post by mowgli81 on 2008-05-02
[http://ppa.launchpad.net/mtrausch/ubuntu/pool/main/a/alltray/alltray_0.69-1ubuntu2~ppa1_i386.deb](http://ppa.launchpad.net/mtrausch/ubuntu/pool/main/a/alltray/alltray_0.69-1ubuntu2~ppa1_i386.deb) ... this worked for me

---

### Post by SpaceTeddy on 2008-05-02
that's the same version as posted before. It works on metacity, it does not work properly when compiz is enabled...

at least for me

---

### Post by volanin on 2008-05-12
This PPA version works perfectly here, minimizing thunderbird at startup.
I am using the 32-bit version and compiz is enabled.
Thank you a lot!
:)

---

### Post by hihihi on 2008-05-13
hehehe
thanks a lot people!!
alltray_0.69-1ubuntu2~ppa1_amd64.deb WORKS with all compiz enabled!! on hardy... i am happy. :)
(i let alltray start sunbird, my callendar)

---

### Post by darthpenguin on 2008-05-31
Thanks a Million!
alltray_0.69-1ubuntu2~ppa1_amd64.deb works perfectly in Hardy with compiz-fusion enabled. For me any way. Have to uninstall alltray first before you install this package. Ubuntu Rocks:guitar::guitar::guitar:

---

### Post by Plasma_NZ on 2008-05-31
> **simon_w said:**
> I've been experiencing more-or-less the same problems, which are solved when Compiz is disabled.  However, just for the record, when Compiz *is* enabled, the command 'alltray thunderbird -na' simply loads thunderbird without alltray at all.  In fact, when desktop-effects are on, the only way to invoke alltray for, e.g., thunderbird is to start thunderbird first, and then dock it using the alltray gui.

I too hope a way can be found to allow alltray and compiz to live happily together!

:):)

try 

```
alltray "thunderbird -na"
```
I used the patch a while ago - works mint.. 64bit hardy with compiz.. :)

---

### Post by Pastito on 2008-07-13
For this issue I have to click on the tray icon of evolution (the same that on thunderbird) instead of the exit button, this way the app minimize to tray without any problem. To make appear the app again I click the tray icon again.
Saludos.
Pasto.

---

