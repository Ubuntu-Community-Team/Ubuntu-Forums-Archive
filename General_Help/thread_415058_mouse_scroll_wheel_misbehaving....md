---
title: "mouse scroll wheel misbehaving..."
date: 2007-04-20
forum: General Help
---

### Post by gokwyjibo on 2007-04-20
Hello,

I just install Ubuntu 7.04 last and have run into a problem with my mouse.  When I use the mouse scroll wheel to scroll up it behaves as if I have pressed the right mouse button.  It will actually scroll up but when I stop the wheel the right-click context menu for whichever application I am using will pop up.  It's a relatively standard Logitech optical mouse (I can get the model number if necessary) and is connected through an Avocent SwitchView KVM (Keyboard Video Mouse) switchbox.  I did have Ubuntu 6 installed about a month ago and did not experience this problem.   Any thoughts/advice on how to resolve this?

Thanks,

Greg

---

### Post by bwitherell on 2007-04-20
Out of curiosity. Does it still have the problem if you use it without the KVM?

---

### Post by scottuts on 2007-04-20
I have the same problem.  Does seem to be the KVM.  I have a 4 port iogear miniview.  If I plug the mouse right into the computer without the KVM the problem goes away.

---

### Post by gokwyjibo on 2007-04-20
Thanks for the reply!  I tried a direct mouse connection to the computer and it does behave normally.  As soon as I plug it back into the KVM the problem returns.  The KVM has built-in "drivers" for MS and Logitech and toggling between the two makes no difference.

---

### Post by bwitherell on 2007-04-21
You might want to try looking for a KVM that is recomeded for use with linux.

---

### Post by muralpennies on 2007-04-22
I was having exactly the same problem in 7.04 and I'm using a Raritan switchman with an Intellimouse (ver 1.1A, PS/2).  Debian etch had the problem as well.  I checked the Debian website and they suggest using "ExplorerPS/2" as the mouse protocol (mine was set to "ImPS/2") in /etc/X11/xorg.conf.  I made the change, rebooted, and that seems to have fixed the issue in 7.04.  I had already uninstalled etch, so I'm not sure if that would have worked in Debian.

---

### Post by abovett on 2007-04-23
I've encountered the same problem since upgrading one of my machines to 7.04, but I'm already using the ExplorerPS/2 option. I'm using a 4 port Dakota Scout KVM.

Can anyone advise a KVM which does not exhibit this problem?

Andy B

---

### Post by gokwyjibo on 2007-04-23
> **muralpennies said:**
> I was having exactly the same problem in 7.04 and I'm using a Raritan switchman with an Intellimouse (ver 1.1A, PS/2).  Debian etch had the problem as well.  I checked the Debian website and they suggest using "ExplorerPS/2" as the mouse protocol (mine was set to "ImPS/2") in /etc/X11/xorg.conf.  I made the change, rebooted, and that seems to have fixed the issue in 7.04.  I had already uninstalled etch, so I'm not sure if that would have worked in Debian.

I made the change as you suggested and it worked.  Thanks!!   Is there an easy way to modify files such as that (xorg.conf)?  I had to log in as root to do it (also had to hunt down how to do that too as the account is "disabled" by default).  I realize it's locked down for good reason but it appears the standard user account has elevated permissions so it would seem likely there is some way to modify system files such as this.

Thanks again.

Greg

---

### Post by muralpennies on 2007-04-24
I'm glad it helped.  I'm not sure if that's the real fix for the issue, but it seems to be working okay.

In Ubuntu you should "sudo" instead of switching to the root user.
```
sudo gedit /etc/X11/xorg.conf
```

You can change "gedit" to whatever editor (vi, etc) you normally use.  I'm a Slackware user normally, so not having root was odd for me as well.

---

### Post by gokwyjibo on 2007-04-24
Thanks again Muralpennies for your assistance, it's greatly appreciated.   It's nice to see a forum so willing to help us newbies.  :)


Cheers,

Greg

---

### Post by inan on 2007-05-02
I have similar behaviour with a Cybex Switchview, except in my case it does a left click after scrolling.  This seems to be limited to gtk widgets (doesn't happen in firefox), but I have not tested very much.

---

### Post by GnuSense on 2007-05-04
Yes, thanks Muralpennies.  The "ExplorerPS/2" replacing IMPS/2 did the trick for me, as well.  And yes, I do have a KVM switch.  The annoying behavior happened both in Gnome and KDE.

---

### Post by stevux on 2007-10-24
ha! I had this issue for a long long time, and almost accepted it. the mouse protocol change in xorg.conf did not help me much, nor did anything else, and I really *need* my KVM.

in my google-istic approach, i finally encountered an entry that I had not tried before, it was about parameters for the 'psmouse' module.

maybe my case is special, but this worked for me; you can test it by typing at the console;

[INDENT][FONT="Fixedsys"]  sudo rmmod psmouse
  sudo modprobe psmouse rate=100 proto=imps[/FONT]
[/INDENT]
I played around with the speed a bit, and found 100 was ok-ish, and looking at some source code it also seemed in range. experiment as you wish.

when you find a setting that suits you, you may save the parameters in /etc/modprobe.d/psmouse file.

hth,

---

### Post by TechnoSwiss on 2007-10-30
I also have an Avocent KVM switch, and a MS Intellimouse on it.

It's a 4 position switch, and between it I have a Windows 2K box, XP, Fedora, and Ubuntu.

The mouse works great on the 2 Windows boxes, it worked on Fedora Core 4, but stopped working when I upgraded to Fedora 7. Gusty is the first version of Ubuntu I've had installed at home on a system on the KVM.

If I remove the KVM from the equation F7 and Gusty work great.

With the KVM in place, F7 and Gusty have the same problem.

(using xev on both to see what events the mouse is sending)
(letting F7 or Gusty auto detect the mouse)

Left -> button 1
Middle -> button 2
Right -> button 3
Scroll Down -> button 5
Scroll Up -> (if previous event wasn't Scroll Up) button 3, an event I don't recognize, button 4
(if previous event was Scroll Up) just button 4
Right Side -> nothing
Left Side -> nothing

If I edit xorg.conf on F7 to force the protocol to IMPS or use the method stevux describes above, I get the following.

Left -> button 1
Middle -> button 2
Right -> button 3
Scroll Down -> button 5
Scroll Up -> button 4
Right Side -> nothing
Left Side -> nothing

Which is a little better since scrolling up doesn't cause that extra button press event, but I don't get my back/forward buttons.

If I force to Explorer/PS2 or exps I get the following.
Left -> button 1
Middle -> button 2
Right -> button 3
Scroll Down -> button 5
Scroll Up -> (if previous event wasn't Scroll Up) button 3, an event I don't recognize, button 4
(if previous event was Scroll Up) just button 4
Right Side -> (if previous event was Scroll Up) button 2
(if previous event wasn't Scroll Up) nothing
Left Side -> nothing

Not sure why going through the KVM is causing the problem, or why it stopped working on the Fedora side (changes to the mouse made in xorg7?)

The problem was driving me up the wall on Fedora and I couldn't find a fix so I thought I'd try Ubuntu on this box (currently using it on my server) but found the same problem exists here.

---

### Post by TechnoSwiss on 2007-11-03
I found a fix to this problem, although I'm not sure I'd call it "ideal".

On a whim I borrowed the PS/2 to USB converter my wife uses with her Laptop. Plugging the PS/2 mouse from the KVM into this, then into my PC fixes the problem. (still have to go through the "normal" multi-button mouse setup). I have my mouse fully functional at this point now, going to have to go pick up some more converters...

---

### Post by Gordy on 2007-11-04
> **muralpennies said:**
> I was having exactly the same problem in 7.04 and I'm using a Raritan switchman with an Intellimouse (ver 1.1A, PS/2).  Debian etch had the problem as well.  I checked the Debian website and they suggest using "ExplorerPS/2" as the mouse protocol (mine was set to "ImPS/2") in /etc/X11/xorg.conf.  I made the change, rebooted, and that seems to have fixed the issue in 7.04.  I had already uninstalled etch, so I'm not sure if that would have worked in Debian.

This worked for me as well and I use the DLink DKVM-4k. All I did was just replace the 
"mouse" with  "ExplorerPS/2"  and rebooted a few times and it is working.

---

### Post by jzerocsk on 2008-04-10
It's a very bizarre issue.  I am having the same problems as TechnoSwiss using a 2-port Cybex Switchview and Intellimouse Explorer.  If I watch in xev, extra events are fired.  I've tried a variety of modifications to xorg.conf without success.  Oddly, it worked fine under CentOS 4.4 with just a minor tweak to xorg.conf

Fortunately I don't use the KVM all that often (just when I need to work on someone else's computer so I don't have to completely unplug/untangle all the wires) so I just plugged the mouse directly into the PC and that's that.

I was also having some random freezes which I previously thought had something to do with my nVidia driver but now I'm thinking it may have been related to the KVM switch...it froze again while I was typing this message...now I have the KVM completely disabled and I'll see what happens.

---

### Post by stucky on 2008-04-20
> **stevux said:**
> 


```
[INDENT][FONT="Fixedsys"]  sudo rmmod psmouse
  sudo modprobe psmouse rate=100 proto=imps[/FONT]
[/INDENT]
```

when you find a setting that suits you, you may save the parameters in /etc/modprobe.d/psmouse file.

hth,

This worked brilliant for my problem on a Tripp-Lite 4 port \\:D/=D>

---

