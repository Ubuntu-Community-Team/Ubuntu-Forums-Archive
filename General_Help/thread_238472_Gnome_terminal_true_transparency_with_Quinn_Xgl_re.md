---
title: "Gnome terminal true transparency with Quinn Xgl repo"
date: 2006-08-17
forum: General Help
---

### Post by panurge77 on 2006-08-17
Just for those not reading compiz forums, after latest updates on Quinn's repo we can have true transparency in gnome-terminal using xgl/compiz on dapper. That's a pretty nice spoiler from edgy, he!

---

### Post by Rotarychainsaw on 2006-08-17
Is this from quinns repo? I got it somehow haha. Looks good too.

---

### Post by magicrobotmonkey on 2006-08-17
nice, glad to see this. apt-get upgrading now

edit: done, that sure is nice! nice job devs! now if java would opensource so we could add it to jedit, i'd be a happy developer.

---

### Post by ccheaton on 2006-08-22
I have the latest updates from Quinn... How do you make the terminal window transparent?

---

### Post by mostwanted on 2006-08-22
> **ccheaton said:**
> I have the latest updates from Quinn... How do you make the terminal window transparent?

In Gnome Terminal:

Edit &#8594; Current Profile

Find the "Effects" tab and enable it. I'm using a non-English Ubuntu so the path might be different for you.

---

### Post by ccheaton on 2006-08-22
Hmm...  Maybe I don't have all of the latest stuff, then, because the transparency setting there is not the 'true' transparency (I cannot see the apps behind it, only the desktop).  

How can I make sure that I have all of the latest stuff from Quinn's repository?

---

### Post by mostwanted on 2006-08-22
Here's a sexy screenshot:

[IMG]http://monkeyblog.org/img/screens/Truly_transparent_terminal.png[/IMG]

---

### Post by mostwanted on 2006-08-22
> **ccheaton said:**
> Hmm...  Maybe I don't have all of the latest stuff, then, because the transparency setting there is not the 'true' transparency (I cannot see the apps behind it, only the desktop).  

How can I make sure that I have all of the latest stuff from Quinn's repository?

Make sure it's enabled and do a system update/upgrade.

---

### Post by ccheaton on 2006-08-22
OK, I need some help then.  What I have listed as installed packages when I search for 'compiz' are the following:

compiz (installed version 0.0.13.35-oubuntu1)
compiz-core (installed version 0.0.13.35-oubuntu1)
compiz-gnome (installed version 0.0.13.35-oubuntu1)
compiz-plugins (0.1-oubuntu1)

Both compiz and compiz-gnome have version 0.0.2-4ubuntu2 listed, but for some reason, my computer thinks that the 0.0.13 version is newer than the 0.0.2 version.

I also have:

xserver-xgl (installed verion 7.0.0+CVS20060625)

How can I either purge all of these and re-get the correct ones or get rid of the ones that I don't need here?  When I initially installed, I had 2 compiz repositories listed, one of which I came to understand should not have been included.  Now, the only compiz repository I have listed is the beerorkid one.  

I tried to do a 'downgrade' on compiz, but it didn't work.  Thoughts?

Thanks,
Clay

---

### Post by Rotarychainsaw on 2006-08-22
Just pointing out that compiz 0.0.13 is newer that 0.0.2 because 13 > 2. Version numbers aren't decimals. 

I'd say if you have the old compiz installed and a compiz repo added, just do a dist upgrade, or smart upgrade in synaptic. A regular update broke the compiz packages for me, but doing it in synaptic fixed it all up.

Im using the xgl.compiz.info repo.

---

### Post by ccheaton on 2006-08-24
Thank you.  I was confused by that, thinking that ... well, you know what I was thinking.  

Hey, how do you get the background when you're spinning the cube around to be anything other than black?

---

### Post by ricesteam on 2006-08-29
Hi,

Can you guys please give me a link to a guide or instructions on how to get this true transparency working?

I have XGL/Compiz up and running and I believe I have the latest versions running as I did an apt-get update and dist-upgrade.

I still cannot get true transparency.

---

### Post by Anduu on 2006-08-29
> **ricesteam said:**
> Hi,

Can you guys please give me a link to a guide or instructions on how to get this true transparency working?

I have XGL/Compiz up and running and I believe I have the latest versions running as I did an apt-get update and dist-upgrade.

I still cannot get true transparency.

No true transparency here either...

---

### Post by ~LoKe on 2006-08-29
Small issue here.  The transparency is working great, however, in the normal terminal there's that ugly titlebar.  So, I use alltray to remove the title bar and all that stuff.  The problem I'm having is that when I use alltray + XGL/Compiz + true transparency, my terminal turns black. o_O

---

### Post by mapage on 2006-08-30
I don't know if this helps, but if I hold down the alt key and scroll my mouse wheel inside of a window, it goes 'true' transparent.  It's not quite the same thing as setting the option in Gnome Terminal, but it does work for me.  (I don't get true transparency with the gnome-terminal setting.)

---

### Post by Ramses de Norre on 2006-08-30
What's the difference between the true transparency now and the one you get when using alt+scrollwheel?

---

### Post by mapage on 2006-08-30
Both methods are 'true' transparency, but with the gnome-terminal method just the contents of the window (not including title bar, menu bar, edges etc) are transparent.  Using Alt-scrollwheel, the ENTIRE window becomes transparent.

Also, modifying gnome-terminal settings means that the transparency will affect all gnome-terminal windows.  The alt-scrollwheel only affects one window.

---

### Post by ~LoKe on 2006-08-30
Alt+scroll wheel also makes the text transparent.  That's not fun.

---

### Post by mapage on 2006-08-30
Yeah...  Somewhat less than useful...

It would be nice to figure out why the terminal transparency isn't working for those of us for whom it is not working...

---

### Post by cbudden on 2006-08-30
Is the new gnome-terminal still there because I don't see it.

---

### Post by Tobba25 on 2006-08-30
> **mapage said:**
> Yeah...  Somewhat less than useful...

It would be nice to figure out why the terminal transparency isn't working for those of us for whom it is not working...

Yeah, it has something to do with something they call Quinns reposetories? You know, like the ones we added to our sources-list to get compiz working in the first place?

Well, I followed some HOWTO-guide that told me to install these two:

```
deb http://www.beerorkid.com/compiz dapper main
deb http://ubuntu.compiz.net/ dapper main
```

Can I replace any of these with the Quinn-ting? Or can I just add the Quinn-thing?

---

### Post by Anduu on 2006-08-30
Ok I looked through the Compiz forums and I think i know why some get true transparency and some don't.

For a brief time Quinn put up a patched version of Gnome Terminal that enabled true transparency but then took it down because it had issues.

So some got it and others did not.

---

### Post by ~LoKe on 2006-08-31
> **Anduu said:**
> Ok I looked through the Compiz forums and I think i know why some get true transparency and some don't.

For a brief time Quinn put up a patched version of Gnome Terminal that enabled true transparency but then took it down because it had issues.

So some got it and others did not.

How would one rid themselves of this patched version if they have it?

---

### Post by phido on 2006-08-31
>  How would one rid themselves of this patched version if they have it?

Downgrade
Start Synaptic and find the "gnome-terminal" package, in the menu choose "Package" - "Force Version" and choose the one out of the ubuntu repos.

---

### Post by mapage on 2006-09-06
Wouldn't somebody WANT the patched version so that they CAN do true transparency?

What I am hearing is that we are mostly SOL if we didn't download the patched version when it was available?

---

### Post by Anduu on 2006-09-06
> **mapage said:**
> Wouldn't somebody WANT the patched version so that they CAN do true transparency?

What I am hearing is that we are mostly SOL if we didn't download the patched version when it was available?

If you are running Dapper no...it is not supported and could cause stability issues.

If you really want it you can always upgrade to Edgy...

---

