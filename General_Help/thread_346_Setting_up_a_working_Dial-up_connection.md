---
title: "Setting up a working Dial-up connection"
date: 2004-10-12
forum: General Help
---

### Post by thebeast on 2004-10-12
Hi all.  Don't have Ubuntu yet, waiting for my pressed CD of 4.10 final.  When I get it i have one big concern.  I only have dial-up internet and I rely heavily on KPPP to connect.  Ubuntu doesn't come with KPPP.  

I hear that they allow you to set up a ppp connection in post-install config which is nice, but how do I dial?  Right now I use Slackware 10 and the Gnome Modem Lights applet has never worked for me.  Hopefully they'll work in Ubuntu....?

---

### Post by flygmaskin on 2004-10-12
I dont have dialup myself, so I'm not sure about this. But I think gnome has some sort of dialup tool. If it doesn't kppp is still included in Universe.

It would be best if someone who has a clue about dialup could answer this :)

---

### Post by Nikola on 2004-10-13
This how I did it:

1. pppconfig in Terminal to set up your connection.
2. pon name_of_the_connection to connect, maybe you'll have to "modprobe ppp_generic" if that module is not already loaded
3. poff name_of_the_connection to disconect.

Step between 2 and 3:
Start Synaptic, get wvdial and gnome-ppp, that's what I'm using.

---

### Post by thebeast on 2004-10-13
Thanks a lot Nikola.  I have gnomePPP now, and was wondering why the heck it wouldn't connect.  It's because I don't have wvdial.  Thx for the tip.  Looking forward to using ubuntu.

---

### Post by simbloke on 2004-10-15
Hmm, where did you find gnome-ppp? I've enabled the universe repositories and reloaded the list but I just can't find it!
Sim

---

### Post by Nikola on 2004-10-15
[quote=simbloke]Hmm, where did you find gnome-ppp? I've enabled the universe repositories and reloaded the list but I just can't find it!
Sim[/quote]

Download deb file from here:
[http://linux.org.by/debian/pool/main/g/gnome-ppp/](http://linux.org.by/debian/pool/main/g/gnome-ppp/)

Then, dpkg -i gnome-ppp_*something*.deb.

---

