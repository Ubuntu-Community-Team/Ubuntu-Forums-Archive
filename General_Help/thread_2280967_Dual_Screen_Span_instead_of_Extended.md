---
title: "Dual Screen: Span instead of Extended"
date: 2015-06-03
forum: General Help
---

### Post by Ryan_Fleming on 2015-06-03
I am trying to create a VNC or RDP connection to a virtual machine with dual monitor display.  However when I choose full screen on the Unbuntu/Kubuntu client connection it only fills one display. (I've tried both Ubuntu 14.04 and, Kubuntu 15.04 with different VNC/RDP clients like Reminna, [COLOR=#333333][FONT=Ubuntu]xvnc4viewer, [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]x11vnc, and for [/FONT][/COLOR]Kubuntu [SIZE=2]KRDC).  Manually re-sizing the window is not an option because the user can not see one of the two displays as it is mounted from the ceiling pointed away from the user.  Any suggestions would be greatly appreciated.  The PC is a latest Xenarc PC using intel video driver with one VGA cable and one DVI output, both displays set at 1024x768.  The subject title of span is what I think is my best solution, meaning instead of two 1024x768 displays could I just somehow create a 2048x768 and span it across both displays?

Best Regards

Ryan[/SIZE]

---

### Post by TheFu on 2015-06-03
x2go.

---

### Post by QDR06VV9 on 2015-06-03
> **TheFu said:**
> x2go.

Nice Find!;)
Of some Importance though.
> **Always Compatible and no Workarounds Required**

  
[LIST=1]
[*] LXDE (not LXQt) 
[*] XFCE 
[*] MATE 
[/LIST]
MATE (the fork of GNOME2) is not included with certain distros, such as  Ubuntu 12.04 _**and Ubuntu 14.04**_. You can however install it from [http://mate-desktop.org/](http://mate-desktop.org/) on those 2 versions of Ubuntu and on other distros.
[http://wiki.x2go.org/doku.php/doc:newtox2go](http://wiki.x2go.org/doku.php/doc:newtox2go)
Kind Regards

---

### Post by TheFu on 2015-06-03
*Not included* simply means nobody has bothered with keyboard mapping.
You can customize that, but most keys should work already. I always need to map the ctl-bckspc to Delete, for example. Chromebooks dont have a delete key.
Also, there is always the ability to run a custom command if you need some other DE ... within limitations of no-HW accelerated DEs/compositers will ever be supported, for obvious reasons.

I use plain openbox or decked out fvwm-crystal happily, but understand why some folks might prefer LXDE.

The great thing about x2go - feels 2-3x faster than VNC/RDP AND the NX protocol uses ssh tunnels by default. That means if you have ssh setup and secured already, no other ports need to be touched.  The bad of NX (and x2go) is they run with old X/Windows code and clients only exist for the main 3 OSes - not android, not Apple's iOS (or Cisco's iOS either).

For normal "productivity" applications, the slight difference between running remote and native (local) isn't bothersome.  I've used x2go and freeNX before that from 5 continents. For 12.04 and earlier, FreeNX works well. For 14.04 (I only run LTS), x2go is great.

My daily-use desktop is running inside a KVM VM on a headless server. I connect from a stripped down Chromebook running openbox or from a Win7 laptop. I forget the desktop is "remote."  It is THAT good for normal work stuff. The convenience of a netbook/laptop (8+ hrs of battery, portable, etc), but the full power of a Core i7 with unlimited storage, fast CPUs, 16G of RAM, and GigE network connection to the LAN.  All available from anywhere in the world, secured by ssh-keys.

No remote desktop will be great for audio or video. That is a limitation of the network - well - unless the stream is transmitted to the client directly and the client does the decoding. Commercial solutions do this with specific limitations. None of the free remote desktops are doing it ... yet ... to my knowledge.

---

### Post by QDR06VV9 on 2015-06-03
Yep I agree, Their Information should be updated though due the Fact I'm running Ubuntu Mate 14.04.
I see there is link to all the Distros that provide Mate DE. Just trying to keep facts in order.
Thanks for the find though I will check it out for sure.:)

---

### Post by TheFu on 2015-06-03
Don't confuse the local desktop with the remote desktop requirements.  All my mapping is done on the remote system.

---

### Post by QDR06VV9 on 2015-06-03
> **TheFu said:**
> Don't confuse the local desktop with the remote desktop requirements.  All my mapping is done on the remote system.

Nope won't confuse that and thanks for the mapping tip, Noted
Thanks for the additional info Probably saved me some time and frustration.
Kind Regards

---

