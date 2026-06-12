---
title: "scroll wheel in firefox keeps giving gright click menu"
date: 2007-12-08
forum: General Help
---

### Post by milliamp on 2007-12-08
So I am reading through some web pages on Ubuntu 7. 10/Firefox 2.0.0.8,  using the scroll wheel of my Intellimouse to scroll up and down the pages.

I am sure I am not pressing the wheel, but for some reason I am able to scroll down OK, but when I go to scroll up it scrolls about 2 lines then displays the standard right click menu.

I really hope this is a bug with a known work around and someone didn't make it that way by design. 

When I am using the scroll wheel, the goal is to...well scroll.
When I need to right click on a web page (not very often), there is a right click button to do just that.

PS. In what ever font I happen to be using to type into this box a , barely looks different than a .

---

### Post by milliamp on 2007-12-08
This is not just in firefox. I can reproduce in abiword with the right click context menu poping up when I scroll up.

Can anyone else reproduce this, or is it a driver issue or something with my mouse?

---

### Post by mnemosyne on 2007-12-31
I also have this issue with an Intellimouse, but I'm using Xubuntu 7.10, it only *just* started happening as of about 3 seconds ago.

EDIT: A simple restart solved the problem, still not sure what the problem was though. It only started happening after I killed the firefox-bin process because Firefox was not responding.

---

### Post by quinnten83 on 2008-01-16
I have this problem too. Not just in firefox but in everything, including when I am on the desktop.
This is not new, I was running ubuntu server 7.04 with an ubuntu desktop installed on this machine and I had the same problem. After that i wiped the disk clean and installed Xubuntu 7.10 and I still have the same problem.
My mouse is connected to a sitecom 2port KVM switch, but I don't have this problem on the windows machine also connected to the KVM switch. The KVM switch connects a PS2 to the computer, but the mouse and keyboard are themselves USB, but the since the ports on the KVM switch are also PS2 I have on of those thingies that changes your USB to a PS2.
I use a logitech wireless desktop mouse, it connects through infrared(?).
The system is a Xubuntu 7.10 HP Vectra VL.
If someone knows a fix for this, It would be much appreciated.

---

### Post by croperz on 2008-02-11
Same problem here, have had it on two separate computers. One using Xubuntu and another using Ubuntu 7.10.

---

### Post by scape279 on 2008-02-23
I'm getting the same problem aswell.

/all: how is your mouse connected? Is it wireless? Lets put down some more details.

Perhaps this is a common bug... I've been using ubuntu for a couple of years now, but whats the bug-reporting procedure?

System: i386, AMD
OS: Ubuntu 7.10 (Gutsy Gibbon)
Mouse: Logitech wireless mouse (and keyboard)
Connection: PS2 via KVM

/quinnten86: Maybe connecting via a KVM gives the same problem. I'm about to move my machine and wont be connected via KVM, I'll report if the scroll bug still occurs.

---

### Post by louieb on 2008-02-23
I connect 3 computers via a cheep 4 port KVM switch. After switching from one computer to the other.  My mouse goes wild every now and then . In my case I think it just the KVM switch getting lost.  

Anyway to check on/ report bugs you can go here: [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu")

---

### Post by SnowflakeRV7 on 2008-06-29
For what it's worth I have the same problem.  My Logitech MX1000 laser mouse works fine, and i've even had most of the buttons working properly, when connected through USB directly to the computer.  But if I connect it to a USB to PS/2 converter, then to my KVM (PS2 only, no USB) and try it, I'm in nowhereland.

The pointer works, the buttons work (left, right, middle) and scrolling down works.  Scrolling up gives me scrolling up on the screen until I stop scrolling, at which point the mouse throws a middle followed by a right click event, as shown by xev.

I'd like to get this going so I don't need a spare mouse sitting on my desk for when I connect my laptop to the KVM.

---

