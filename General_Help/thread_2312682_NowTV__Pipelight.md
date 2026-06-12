---
title: "NowTV / Pipelight"
date: 2016-02-06
forum: General Help
---

### Post by jim_deadlock on 2016-02-06
I have Firefox + Pipelight + Silverlight plugin (version 5.0) + User Agent switcher (showing FF for Win).

After much googling and experimentation I've established the above optimum configuration and I've reached the point where the NowTV movies are going through the initialisation phase, but the movies then fail to start with the error "There's an error connecting, please try again in a few moments.". I did a screen recording and managed to see the previous error that flashes past, which says "Unable to issue a licence to play this protected video. Please try again.[c:1010]".

I've checked the Silverlight settings and they all seem to be in order - Application Storage -> enabled; Enable download and updates to components required for protected content playback -> enabled.

I have a Win10 dual boot and it plays without any problem there.

I know it's a long shot posting here but I feel like I'm close to a solution if I can make just one more final tweak...

---

### Post by ajgreeny on 2016-02-06
You may need to install hal using the ppa at [http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu](http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu) though I have no idea if that will work for Now-TV.

There are still, unfortunately, some sites that I am unable to get to work using Ubuntu, eg Channel-4 and Channel-5 catchup services, though ITV-Player works fine.

---

### Post by jim_deadlock on 2016-02-06
Yes I already have hal installed, forgot to mention.

I have the same as you re the catchup services. I had 4/5 working in the past but no longer.

---

### Post by ajgreeny on 2016-02-06
I know; annoying isn't it?  I also used to be able to get Ch4 & Ch5 catchup to work but it stopped some time ago and has never worked since then.

Luckily I also use NowTV (two older white boxes) connected to older non-smart TVs for those catchup services, and I dip in and out of their entertainment services..
I also have side-loaded Plex-mediaserver apps to both NowTV boxes so can stream any media on my desktop to them easily and simply.  You can also use emby-server if you prefer that to Plex.

PS:
It might be worth trying **google-chrome** as your browser as I am aware that it can do some things that no other Linux browser can manage.  I have not tried it on Ch4 or Ch5, never having installed google-chrome on my Ubuntu boxes.

---

### Post by jim_deadlock on 2016-02-06
Thanks, it's looking like a NowTV box is the answer to everything and I can put all this nonsense behind me :)

---

