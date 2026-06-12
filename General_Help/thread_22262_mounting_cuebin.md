---
title: "mounting cue/bin"
date: 2005-03-26
forum: General Help
---

### Post by ubuntu_demon on 2005-03-26
Hi,

 I know how to mount an iso file. But what if I've got a cue and a bin ? How do I mount them ?

mounting iso is explained here :

[http://www.ubuntuguide.org/#mountunmountisofilewithoutburning](http://www.ubuntuguide.org/#mountunmountisofilewithoutburning)

---

### Post by jax2000 on 2005-03-27
not sure if it's possible to mount .cue/.bin, but you can convert .bin to .iso with [Bchunk](http://he.fi/bchunk/)

---

### Post by ubuntu_demon on 2005-03-27
[QUOTE=jax2000]not sure if it's possible to mount .cue/.bin, but you can convert .bin to .iso with [Bchunk](http://he.fi/bchunk/)[/QUOTE]
 thnx ... bchunk is in univserse

I just discovered gnomebaker doesn't support bin/cue. K3B does.

---

### Post by bobmitch on 2005-03-27
The new version of gnomebaker coming soon will support bin/cue files. :)

---

### Post by Darrena on 2005-03-27
cdemu will mount a bin/cue similar to daemon tools in windows

---

### Post by ubuntu_demon on 2005-03-27
[QUOTE=Darrena]cdemu will mount a bin/cue similar to daemon tools in windows[/QUOTE]
 The reason I want to mount bin/cue is that svcd's often are in this format.

from [http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/) :

"However, for watching an SVCD, we would recommend MPlayer which can play bin/cue images directly with the patch a friend and I made for it (more under History). The CDemu project is licensed under the GPL (v2 or later) !"

So where do I get this mplayer patch ?

---

### Post by dude2425 on 2005-03-27
According to the site, it's already included with mplayer.

> History

It all started like this: I got some movies from friends on a firewire disk which where bin/cue files. They told me I would need to burn them or use Daemon Tools under Windows in order to watch them. That was to much for me, booting Windows just to watch a movie? So a friend (Justus Schwartz) and I decided that we should make a patch for our favored video player (MPlayer). After one night we had a proof of concept; 2 weeks later we had a good patch and we submitted it. It was accepted by the MPlayer team and starting with 0.9rc3, our patch is included. The syntax is as follows:
$ mplayer cue://<cue file>[:track] [options] 

---

### Post by ubuntu_demon on 2005-03-27
[QUOTE=dude2425]According to the site, it's already included with mplayer.[/QUOTE]
 ow thnx I'll check it out.

too bad you have to do it from commandline.

---

### Post by Cal Paterson on 2005-06-13
Thanks guys, this was a big help.

---

### Post by johnmc on 2005-07-19
Great, that's what i've been searching for!
Mplayer plays the files without any hickup! :)

Thanks for the help!

---

### Post by Mikebgr on 2006-05-02
thx for all the info in this thread!

---

### Post by Dr. Cox on 2006-05-04
have you tried out VLC? it plays close to anything I've tried... good quality. usability is great as well and it's fast.

---

### Post by iluminate on 2006-05-07
[QUOTE=Dr. Cox]have you tried out VLC? it plays close to anything I've tried... good quality. usability is great as well and it's fast.[/QUOTE]
I first was on my way to say something bad, until I tested it out - to open up a bin/cue with VLC and it worked!!!!
Great and thank you very much for the tip and info!

---

### Post by jatilq on 2006-06-17
I love VLC but for some reason the audio is choppy for skvcd and cue/bin files. Mplayer plays the files without a hitch. Thank you for the info.

---

