---
title: "Display corrupted / unusable after change in resolutioin"
date: 2008-03-25
forum: General Help
---

### Post by Benarden on 2008-03-25
Hi There..

Poking around,  - Trying to change the resolution, I believe in administrator mode;

 I made it 800 x 600..

However,  - now it's total colorful gibberish, which is pretty but useless

I can log in (it acepts keyboard input but does not echo it back in any meaningful way.

( In command /rescue  mode, )

On the Ubuntu side of this PC

, in the /etc/X11 directory, there are two files:


5253 ( date / time ) xorg.conf
- and
2324 ( date / time ) xorg.conf.1

Found neiter on the install disc..

- Any ideas? 

which should I poke at, and what should I look for?

what can I comment ouot in VI ( or whatever)

- any way of changing it back to 1024 x 768, or whatever, so I can
 use the ubuntu side of this  machine again

 -with , or without doing a reinstall..
 ?

 Any help would be appreciated

( Msg. Sent from the XP Side of this dual boot machine)



PS: - Sent away for a 600 page UbuntuBook to be on the safe side

Thanks

Ben

Dell 2400

 1 Gig ram
 Diamond 256 Meg Video card; probably NVDIA chips






> > Click on the KDE button in the bottom left-hand corner of the
> screen then on "System Settings" then on "Monitor & Display" at
which
> point you should click on the Administrator button in the bottom
> right-hand corner of the window (the password is the your password
to
> log into your account) which will then allow you to change your
> resolution.
> >
> > Happy new year one and all :)
> >
> > A.
> >
> > ----- Original Message ----
> > From: John Luckey <jluckey@>
> > To: [email]ubuntulinux@yahoogroups.com[/email]

---

### Post by Benarden on 2008-03-25
All:


Found a post which ( - and I summarize here ) 

indicated copying 

/etc/X11 xorg.conf.1 to xorg.conf

- which worked like a charm 

Here is the link below 

[http://absolutebeginner.wordpress.com/2006/09/15/restoring-your-previous-xorgconf-file/](http://absolutebeginner.wordpress.com/2006/09/15/restoring-your-previous-xorgconf-file/)


Thanks !

Ben

---

