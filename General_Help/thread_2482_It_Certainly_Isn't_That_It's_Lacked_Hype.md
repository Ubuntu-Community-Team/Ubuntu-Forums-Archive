---
title: "It Certainly Isn't That It's Lacked Hype"
date: 2004-10-28
forum: General Help
---

### Post by jlowell on 2004-10-28
One wonders what all the excitement is about. With all the hype your distro has gotten from Ladislav Bodnar at Distrowatch, I'd have thought Ubuntu's new livecd would have introduced me to a kind of linux nirvana, replete with developers transformed into ethereal, spiritual types of realities. Not so, sad to say.

In a far more concrete, down-to-earth environment I tried the Ubuntu livecd today and have the following observation to make:

(1) Trying to elicit boot options under current arrangements is far too difficult even for an experienced linux user. It seems to me that one ought to be given a clearer way to understand precisely how to edit these options from "help". What is easy to see is that there are any number of boot options available; what is very nearly mystery is how to get them entered. Getting into text mode remains something entirely arcane and it shouldn't be. Any number of livecd's using Knoppix type boot options make possible entering them on the introductory user interface and so should Ubuntu. Having to reach grub and make the entries via o and e is schlock in my opinion. Certainly with all the umph Distrowatch has mustered behind you one might expect more, eh? 

(2) Far too heavy a livecd for a machine in the PII 333 Mhz, 256 MB SDRAM category. It's slow as Moses.

(3) All the configuration tools for networking nothwithstanding, very little works. I got a static ip address configured together with subnet mask and gateway but entering DNS numbers was impossible, entirely grayed out. I couldn't even raise a terminal. Nothing seemed to work, programs, system tools, zilch. Not at all impressed with this offering, frankly.

Better luck with the next release.

jlowell

---

### Post by jdong on 2004-10-28
(1) Under normal circumstances it's unnecessary to insert any boot options. None of the other LiveCD's are much better at this. However, it's a good suggestion to keep in mind for future releases.

(2) That's not Ubuntu's problem. You're juggling a full-blown DESKTOP ENVIRONMENT, constant on-the-fly gunzipping from the LiveCD, all on limited RAM and on limited resources.

(3) Sorry about your networking experiences. Good LiveCD config tools are what I hope to get from the Gnoppix merger.

Again, this _IS_ a first release of a brand new distro. It's already a great effort and has a great future. I hope to see those annoyances fixed for you in the next release.

---

### Post by daniels on 2004-10-28
[QUOTE=jlowell]One wonders what all the excitement is about. With all the hype your distro has gotten from Ladislav Bodnar at Distrowatch, I'd have thought Ubuntu's new livecd would have introduced me to a kind of linux nirvana, replete with developers transformed into ethereal, spiritual types of realities. Not so, sad to say.[/QUOTE]

There are three things to bear in mind here:
  a) firstly, the entire live CD is compressed, since we are also fitting a whole bunch of Windows-based open source software on there, I believe.
  b) the live CD differs from the install in many, many ways.
  c) the install has received a lot more attention and polish than the live CD has; bear in mind that employee #3 was hired in mid-to-late March, and since then, we've had to bootstrap a company, infrastructure, and a distribution; and now a community.

I suggest you try the install rather than the live CD; you can't really judge how the install will be from the live CD.

---

### Post by bshea on 2004-11-26
[QUOTE=jlowell]One wonders what all the excitement is about. With all the hype your distro has gotten from Ladislav Bodnar at Distrowatch, I'd have thought Ubuntu's new livecd would have introduced me to a kind of linux nirvana,  
...
(2) Far too heavy a livecd for a machine in the PII 333 Mhz, 256 MB SDRAM category. It's slow as Moses.
(3) All the configuration tools for networking nothwithstanding, very little works. I got a static ip address configured together with subnet mask and gateway but entering DNS numbers was impossible, entirely grayed out. I couldn't even raise a terminal. Nothing seemed to work, programs, system tools, zilch. Not at all impressed with this offering, frankly.
Better luck with the next release.
jlowell[/QUOTE]

I have a couple of opinions in answer to this 'review' of sorts.
As for the DNS in (3) I have no idea what the hell he is talking about. Worked fine for me. YES it was greyed out. You have to type one or more in and then click ADD (!) Duh!
The bug he complains about in (3) is simply a hostname x server security related bug already covered in a previous post. Just simply make sure the hostname is 'ubundu' and not 'macaroni' or use the magic-cookie xauth commands supplied in a previous post to fix this. And as mentioned in the above msg, this is a LIVE cd not an install and a first release at that! WHat can you expect? (Obviously too much.) NOTHING WORKS because you failed to realize that you introduced a problem/bug into the distro by entering a diff hostname. (Which is the developers fault, granted... but...)

As for it being slow, I used it first on a P2-300mhz machine and I found it not unbearable.  (Later on a P4-3.4Ghz)  As they mentioned they released some other open source stuff (mozilla type stuff et al) for M$Windows also on the live cd. So stop bitch'n already! It worked and it is free and I got  it mailed free of charge. Awesome way to spread the distro around (I got more then one copy, and will be giving it to some ppl who have never tried Linux)
If nothing else it gives someone who has never even SEEN linux before a nice free look at a decent distro.  I have used Slackware/Debian-Knoppix/RedHat and many others, and this was one of the nicest 'clean' looking Debian/Gnome LIVE-CD creations I have seen in a long time. Well.. good job for what it is worth. 

Brady Shea

---

