---
title: "Loosing internet connection everytime I boot to other OS - dual booting."
date: 2007-07-11
forum: General Help
---

### Post by xl_cheese on 2007-07-11
I booted to ubuntu and did not have an internet connection.  I went to network and had to jump through some hoops to reconnect.  Everything was fine until I booted to my vista install.

I then had to jump through hoops to make that internet connection work.

I came back to ubuntu just now and had to reconnect again.

Any ideas?

this just started recently.  May of had something to do with connecting my old pc via wireless to my router?  I made a 2nd machine to stash behind the sofa in the living room.  wireless keyboard and mouse reside under the sofa and lcd monitor outta site till I want to use them.

At anyrate I'm not sure what I could have done.  I don't want to have to do this everytime I restart to the other OS.

---

### Post by Buggin on 2007-07-11
I know on my dualboot XP Ubuntu I had to enable Wake on LAN support in XP for my network card to work in Ubuntu. Something about XP turning the card off and the driver in Ubuntu not knowing how to turn it back on. Could be something similiar in Vista. Worth a shot anyway.

---

### Post by xl_cheese on 2007-07-12
> **Buggin said:**
> I know on my dualboot XP Ubuntu I had to enable Wake on LAN support in XP for my network card to work in Ubuntu. Something about XP turning the card off and the driver in Ubuntu not knowing how to turn it back on. Could be something similiar in Vista. Worth a shot anyway.

Are you sure this fixed your problem?  

```
What are "Wake on LAN" capabilities?
 Applies to all editions of Windows Vista. 
Which edition of Windows Vista am I using? 

Sometimes called Remote Wake-up, Wake on LAN is technology that allows someone to turn on a network computer remotely by sending a special data packet (called a Magic Packet). Even if the computer is turned off, the network adapter is still "listening" on the network, so when the special packet arrives, the network adapter can turn on the computer.

Wake on LAN is mainly used by system administrators to perform computer maintenance tasks remotely. The computer receiving the Magic Packet must have a motherboard, network adapter, adapter driver, and computer basic input/output system (BIOS) that work with Wake on LAN.

Network adapter__elbasuer__Network adapterA device that connects your computer to a network. Sometimes called a network interface card (NIC). Driver__elbasuer__DriverSoftware that enables hardware or devices (such as a printer, mouse, or keyboard) to work with your computer. Every device needs a driver in order for it to work. Packet__elbasuer__PacketA unit of information transmitted from one computer or device to another on a network. 
```

I was able to connect fine from a linux mint live CD and then when I boot back to ubuntu I had to click enable roaming.  then reselect wired connection and change then go in and uncheck enable roaming to fix it.

Now I just came back to vista and had no connection.

annoying and it's late.

---

### Post by davidjmayo on 2007-07-12
Not sure if the wireless is the problem

I have dual boot with rarely used W2K on a wired cable modem (only one PC) If I change OS then the connection goes. Only full power off (removing sockets) will restore the connection to either OS.
Seems that the modem gets confused. Don't know what kind of packets each OS sends to it (that's my feeling but beyond my knowledge)

---

### Post by ElEdwards on 2007-07-12
I dual boot WinXP and Mint 3.0 on my laptop.  My wireless card is a Linksys WPC54G.

I have to do differrent things for each OS, simple but easy to forget.....

When I boot Windows XP, I have to do so with the card UNPLUGGED!  AFter Windows has finished booting, I plug the card in, it is found, acquires the address and everything is fine.

When I boot Mint 3.0, I have to have the card PLUGGED IN from the beginning (as in: before I select the Kernel in Grub).  Even before the desktop completes, I get a message that I'm connected to my network.

If I have the card plugged in and boot Windows, the card is never seen.
If I don't have the card plugged in and boot Mint, the card is never seen if I plug it in later.

Simply put:
- I have to plug the card in BEFORE I boot Linux but AFTER I boot Windows.

:)  I hope that helps in some way.

---

### Post by dannyboy79 on 2007-07-12
I have heard that sometimes the ethernet card doesn't release somethign when closing Winxp and then booting into Ubuntu so then your card won't work in Ubuntu, I would try what the person said worked for them, unplug power to your computer for at least 1 minute prior to plugging it back in, then booting to the other os. I know it sucks but that's life. I beleive it was with the nvidia nforce ethernet chipset.

---

### Post by jimbob on 2007-07-12
You might consider running something like Virtualbox instead of dual booting.   Then once up your connection would remain that way when flipping OS's.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by xl_cheese on 2007-07-12
I figured it out. 

In vista I went to network and sharing center and had to uncheck some things.  I turned off network discovery.  I had turned it on when trying to connect this computer and the one running only ubuntu in my living room.

I actually have a vmware vista installed, but the screen is fuzzy and it lags a lil bit.

---

### Post by jimbob on 2007-07-12
I'm not surprised - Vista is a huge memory hog.  Try increasing your swap size if possible and see if that helps.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by xl_cheese on 2007-07-12
> **jimbob said:**
> I'm not surprised - Vista is a huge memory hog.  Try increasing your swap size if possible and see if that helps.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]


I have a 4G swap.  More you think?

---

### Post by jimbob on 2007-07-12
That should be enough I would think.  If you are using Gdesklets there is one for memory usage that includes swap usage also and you wouldn't believe how swap usage peaks when even XP (I don't have Vista) starts up in Virtualbox.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by dannyboy79 on 2007-07-12
no, swap isn't gonna like main memory does. I can tell you that virtualbox is better with os's than vmware in the little experiement I ran. WinXP in Ubuntu using both and virtualbox was faster. That was with 1.5gb of ram so needless to say, you need a lot of ram to run a virtual os as fast as a native os!

---

