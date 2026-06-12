---
title: "Need suggestions for .iso create/burn software"
date: 2005-08-31
forum: General Help
---

### Post by greenstar on 2005-08-31
I have been trying to figure out what software to use to create & burn .iso images of my CDs & DVDs. I just need to straight copy and burn.

I love the command line for package installation & update amongst other things (apt-get is awesome), but I hate it for this purpose. It's too easy for me to screw up a perfectly good, innocent disc from the command line with all those switches and syntax and stuff (I have CRS syndrome: I Cant Remember Sh!t). I couldn't even get an .iso made while looking at the instructions on [ubuntuguide.org](http://www.ubuntuguide.org) . I'm not normally this inept with the command prompt, but this is killing me. I **can** make an .iso image from a directory structure with mkisofs, but that's as close as I've gotten.

Anyway, I'd like to do this through a GUI. For me, it preserves sanity & cash wasted on overpriced coasters.

I have no idea what software to use for this. I'd really appreciate a few suggestions. If possible I'd like to stay away from KDE based software such as K3B since Ubuntu uses Gnome. No reason to bloat my computer with KDE too (I don't like KDE.)

Thanks,
greenstar

---

### Post by frodon on 2005-08-31
K3B allow you to burn any common image files (.iso, .bin, .cue , ...).

---

### Post by casperl on 2005-08-31
I have tried them all and k3b (though not cashproof) does the job better than any other! \\:D/ 

Tips:
1) - sometimes (mostly actually) it works better when copying to a CD image first and then burning that image onto CD as a second step
2) - if you use k3b, make sure that nautilus does not pop up a new create CD window somewhere when the blank media for k3b to burn is inserted - I cannot prove that this interferes with k3b but I feel better when only 1 app has control over the burning process!

HTH

---

### Post by greenstar on 2005-08-31
I can get .iso images burned easy enough with gnomebaker or nautilus. What I'd really love to have is an nice GUI for copying  a CD or DVD to an .iso image. In windows I used DVD Decrypter because it works great for data DVDs too, and is faster and more reliable than anything else for data DVDs in Windows (based on personal experience). It's what I used to burn my SuSE, Debian & Fedora Core DVDs when I tried each of those distros. For CDs in windows I used CD Burner XP Pro. 

Thanks for your time.
greenstar

---

### Post by Perfect Storm on 2005-08-31
You could try Nerolinux. It's similiar to K3b, but without installing all these KDE libaries.


got a screenshot of it: [http://thilockdominus.freehomepage.com/images/Screenshots/Screenshot.jpg](http://thilockdominus.freehomepage.com/images/Screenshots/Screenshot.jpg)

---

### Post by darkmatter on 2005-08-31
GnomeBaker and Graveman! haven't given me any problems. I've actually found GnomeBaker to be more reliable than K3B.

Plus, it's gtk+native. looks good and no bloating your sys with all those nasty KDE libs... :razz:

---

### Post by greenstar on 2005-08-31
[QUOTE=casperl]I have tried them all and k3b (though not cashproof) does the job better than any other! \\:D/ [/QUOTE]

I've tried K3B, and though it looks promising, it crashed far too often for me to allow it to muck up my wonderfully stable Ubuntu box. :grin:  Also, I developed an aversion to KDE during my stint with SuSE 9.1/9.2.


[QUOTE=casperl]1) - sometimes (mostly actually) it works better when copying to a CD image first and then burning that image onto CD as a second step[/QUOTE]

I agree completely, copying on the fly is ridiculously unreliable.

[QUOTE=casperl]2) - if you use k3b, make sure that nautilus does not pop up a new create CD window somewhere when the blank media for k3b to burn is inserted - I cannot prove that this interferes with k3b but I feel better when only 1 app has control over the burning process![/QUOTE]

I've noticed this to be true with other burning apps too. I beleive it is an issue of control of the burner, as most burning apps will lock the drive while burning so as to have exclusive access to the drive. You can't even eject the media with the push button on the drive while burning.

greenstar

---

### Post by frodon on 2005-08-31
greenstar both K3B and Nerolinux have a really nice GUI, use one of these 2 software and you will easily (as easy as under windows) burn iso images. You can use synaptic to install them (I'm not sure for nerolinux).

---

### Post by greenstar on 2005-08-31
Darkmatter:  I'm installing Graveman now. I'll be giving it a look in a minute. Thanks

greenstar

---

### Post by Perfect Storm on 2005-08-31
[QUOTE=frodon]greenstar both K3B and Nerolinux have a really nice GUI, use one of these 2 software and you will easily (as easy as under windows) burn iso images. You can use synaptic to install them (I'm not sure for nerolinux).[/QUOTE]

No, Nerolinux is not avaible in the synaptic. It's not a GPL or freeware, but if you have a license to nero 6.x to windows you can use your code to it, other than that the trial is 30 days. It cost 19,95. [http://www.nero.com/en/NeroLINUX.html](http://www.nero.com/en/NeroLINUX.html)

---

### Post by greenstar on 2005-08-31
Darkmatter: I just finished copying my Beatrix CD with Graveman. Looks like just the tool for the job. Thanks for your help.

Thanks to everyone who took time to read and/or reply to this thread.

greenstar

---

