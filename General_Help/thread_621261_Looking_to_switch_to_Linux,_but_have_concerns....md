---
title: "Looking to switch to Linux, but have concerns..."
date: 2007-11-23
forum: General Help
---

### Post by Fev on 2007-11-23
Today, I will be discarding Vista. Between the 100 misc processes and not being able to run things without the OS freaking out, I’m done with it. I am either going to be switching back to XP or try Linux for the first time.

Though… I have some concerns… Here they are:

1) I want to be able to run World of Warcraft still. It’s one of the things I do daily and is a must for whatever OS I goto. That spawns a few concerns.
a) Will my ATI card work with Linux? It’s a x1800.
b) I don’t think there is a Linux install for World of Warcraft…?

2) I have an old copy of photoshop I use (version 7 I think). Is it possible to get that installed or is there a Linux like app for graphic design?

3) I have a Netgear wireless card, WN311T. Worked great in XP, barely works in Vista. I still have the XP drivers, would it be possible to get those to work under Linux? Whole house is WiFi.

4) File sharing. How well does Linux and Windows XP/Vista play with each other when it comes to sharing files over the network?

I think that’s all I have for now =). Or at least to get myself started.

---

### Post by GavinZac on 2007-11-23
> **Fev said:**
> 1) I want to be able to run World of Warcraft still. It’s one of the things I do daily and is a must for whatever OS I goto. That spawns a few concerns.
a) Will my ATI card work with Linux? It’s a x1800.ATI isnt the very best with ubuntu/linux, but unless you're unlucky, you should be ok.
> b) I don’t think there is a Linux install for World of Warcraft…?

2) I have an old copy of photoshop I use (version 7 I think). Is it possible to get that installed
 there isnt, but there is a great program called WINE that lets you run a lot of windows applications. given WoW and photoshop's popularity, id imagine they will work.
>  or is there a Linux like app for graphic design?Ubuntu comes with GIMP installed. I use it for all my graphic design work.

> 4) File sharing. How well does Linux and Windows XP/Vista play with each other when it comes to sharing files over the network?You can use Samba. there are many guides on how to use it, here on this forum :)

---

### Post by sirdilznik on 2007-11-23
Addressing your questions:

1) You are correct in assuming that there is no native Linux client for WoW, but you should be able to play it through wine or cedega (a commercial fork of wine).  I haven't played the game for a long time myself, but it ran about as well as it did in Windows using cedega back when I did.  As far as the graphics card goes, I know there are Linux drivers and they are not as far along as their Nvidia counterparts, but it should work.  I can't say for sure for that specific card though.

2) You will probably be able to run photoshop through wine (like you would WoW).  Also there are native apps.  There is gimp which you can try on Windows before you switch.  It doesn't have 100% of the functionality of Photoshop, but it comes pretty close and suits my needs fine.  There is also krita and inkscape for svg graphics.

3) The Netgear NIC uses an Atheros chipset I think which would mean that it's most likely supported by the drivers at [madwifi.rog](http://madwifi.org/).  Beyond that I know little about wireless :oops:

4) File Sharing should be no problem.  You have all kinds of options here including NFS and Samba.

Edit: Beat me to it...

---

### Post by Fev on 2007-11-23
I really appreciate the input =). I am going to repartition my drive and give Ubuntu a try!

---

### Post by diction on 2007-11-23
> **Fev said:**
> I really appreciate the input =). I am going to repartition my drive and give Ubuntu a try!

You can just pop the CD in and it'll boot into Ubuntu automatically.
You can then try it out for a bit before you even begin installing it.
Installing Ubuntu is a joy, very quick and painless, you can even keep using the Live CD while it partitions your hd and install Ubuntu.

---

### Post by AlanRogers on 2007-11-23
You can try it Live first; it might be safer. Just allow the computer to boot from the CD/DVD and Ubuntu will load into RAM, without touching your hard drive. You'll then know whether you have compatiility issues without partitioning your hard drive.
 
EDIT: Great minds think alike ...

---

### Post by diction on 2007-11-25
> **AlanRogers said:**
> You can try it Live first; it might be safer. Just allow the computer to boot from the CD/DVD and Ubuntu will load into RAM, without touching your hard drive. You'll then know whether you have compatiility issues without partitioning your hard drive.
 
EDIT: Great minds think alike ...

:)

---

### Post by #Reistlehr- on 2007-11-25
Hey, atleast linux is free. Doesn't hurt [the wallet] to try.

:D

Photoshop has a lot of known bugs when running with WINE, so i wouldn't advise it. I've have troubles getting it to run, but atleast it somewhat ran. I've always been a Photoshop user, so, GIMP was hard to switch to. With WoW in Wine, it will work, a million how-tos. Only thing is, some people noticed a drop in FPS. [Just telling how it is]

---

### Post by Zipster90 on 2007-11-25
> **Fev said:**
> 
I want to be able to run World of Warcraft still. It’s one of the things I do daily and is a must for whatever OS I goto. That spawns a few concerns.


On WINE's website they have WoW listed on their gold list, which means that with some special configuration, it will work fine. I'm not sure what the configurations are, but it's probably nothing big.

---

### Post by foxholeunder on 2007-11-25
Just remember to have patience and really  give Ubuntu a good chance to warm your heart! 

You will run into little things like terminology differences that will at first throw you off-track but just need a little time for them to be added to your speech. Probably the first and most noticeable terminology difference you may notice is programs are referred to as packages in *nix.

For every program that is available in other OS's there is almost assuredly a replacement within *nix. Ubuntu has virtually unlimited packages to offer and just like the first time you use a program on Windows you will require yourself some teaching time to understand the full potential of how that program works.

WOW works wonderfully in WINE, I have had very few complaints and in fact from my own experience will dare say that WOW under WINE on Ubuntu is more stable than anywhere else. It is true that there is a lower FPS but you truly do not notice anything. The most notable lag is when the WOW servers are over-loaded... but then it will not matter what OS you are running WOW under in these instances.

As far as graphic design the Gimp is hands down my favorite. I use to be a big photoshop user when I ran WIndows, but once you figure out how the Gimp works you will find that the Gimp is every bit as powerful as anything out there. As a dabbler in graphic design I can only equate the Gimp as equaling the most expensive version of photoshop. If you spend a day or so just messing with every possible setting within the Gimp you ought to find it meets your needs and then some. With more experimentation you may find that are asking yourself what you ever saw in Photoshop. Obviously this is personal opinion, but I use to run the $1200 pro version of photoshop when I ran windows... and after the Gimp I have no desire to waste money on inferior products.

Wireless.... I will not venture to answer here, except that I understand wireless is fairly well supported and improves daily... I have an estimated 1.3 miles of ethernet cable strung throughout my house offering up some 100+ ethernet jacks... you know... for those just in case I have a huge LAN party....

As far as network sharing goes, Samba will more than cover your needs... Samba offers up more refined configuration than Windows sharing, IF you will have or expect to have Windows machines on your LAN then Samba will be required to share, Else there is also as has been mentioned NFS. And my personal favorite SSHFS Both NFS and SSHFS can run on-top-of Samba allowing highly secured sharing between any/all *nix boxes and more standard sharing with non *nix boxes. With SSHFS you can even mount and share your drive(s) securely over the wildlands of the Internet... say at your work or from a hotel while you are traveling... Run SSHFS through VPN and you double your encryption tunnel.

Otherwise, take it slow and ask for help in the forums as needed, you will almost assuredly receive one good response within a day of your posting.

Again, remember you are venturing into the unknown and there will be many things that will require your continued efforts to learn how things work... once you spend a good six months behind the wheel of Ubuntu I think you will find much satisfaction in your choice to venture this way! I have run a combo of *nix/Windows for about 11years now and been totally Windows free for close to 2years now... Since finding Ubuntu I would not honestly go back to Windows now if Bill Gates himself came to me personally with a briefcase full of half of his fortune... I really have found the ultimate replacement for Windows with Ubuntu... Not to mention I no longer spend hours combing my file system in search of virus,trojans,worms,etc... Nor do I feel separated from the world.. The community of Ubuntu users has linked me to the world. Virtually every one of the Opensource project forums I am apart of have given me this world-united-ness feeling. 

Best of luck on your venture... the learning curve is not as large as it may seem at first, so just venture slowly at first and before you know it you will be responding to others much the same as I am responding to you!

---

### Post by ubukool on 2007-11-25
You always have the option to run Windows under Virtualbox or VMWare.  I use Gutsy, but I've got XP as a guest machine running under Virtualbox.  If you did that you could use photoshop and WoW, no problem! :):) check it out!

---

### Post by Subban on 2007-11-25
> **ubukool said:**
> You always have the option to run Windows under Virtualbox or VMWare.  I use Gutsy, but I've got XP as a guest machine running under Virtualbox.  If you did that you could use photoshop and WoW, no problem! :):) check it out!

As far as I know WoW isn't really going to be pleasant in virtualbox, the graphics card VB emulates is pretty low spec, I haven't tried it myself so I hope to stand corrected.

However, I have been playing WoW on Ubuntu via Cedega for the last 2 years or so now very nicely in Cedega, there are some issues at the moment but Transgaming seem to be getting back on top of them, performance wise it runs a little slower than it did on windows but is 100% fine to go raiding with etc (I see around 30fps on average). WoW in Wine seemed to work pretty well too as I tried that recently, wasn't quite so good for me as in Cedega but in its defense  I didn't spend too long configuring it.

---

