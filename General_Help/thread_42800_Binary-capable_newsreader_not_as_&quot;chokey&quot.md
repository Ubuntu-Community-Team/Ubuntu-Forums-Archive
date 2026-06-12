---
title: "Binary-capable newsreader not as &quot;chokey&quot; as Pan?"
date: 2005-06-19
forum: General Help
---

### Post by tahuya_rat on 2005-06-19
Hi.

I've been using pan for a week or so now, and I like it, in many ways, better than Agent.

One problem I've noticed, though, is that when loading a group that has alot of headers, such as alt.binaries.dvd (3,000,000+), it will download them, and then just hang when trying to populate the headers in the GUI.  The same problem doesn't happen in Agent, either in XP or WINE, so I know it's not just a RAM/CPU math problem (1gig RAM / AMD Athlon 64 3200+), but Pan's download speed comes in handy particularly in groups like that.

In Agent, even with 4 instances open, downloading different parts of a large binary post, I get ca. 350kb/s, whereas with Pan, using all 4 connections my news server will allow, I get 500kb/s+ consistently..  That adds up to a huge difference over, say, a 14gb file from alt.binaries.hdtv.

Sorry for the ramble, I'm not fully coffeed yet.

The upshot is, does anyone know of a fix/alternative for Pan that can work around this problem?

TIA
tahuya_rat

---

### Post by betrayed on 2005-06-19
klibido.  I use it all the time in major groups such as a.b.dvdr with no problems and this machine has no where near the power your machine has

---

### Post by tahuya_rat on 2005-06-19
Thanks for the quick reply!  I can't seem to find klibido anywhere, though.

It's not in synaptic, and I tried apt-get, using the procedure described at [http://klibido.sourceforge.net/#_download](http://klibido.sourceforge.net/#_download)  ... Still no luck.  Anyone have any ideas?

---

### Post by betrayed on 2005-06-19
[QUOTE=tahuya_rat]Thanks for the quick reply!  I can't seem to find klibido anywhere, though.

It's not in synaptic, and I tried apt-get, using the procedure described at [http://klibido.sourceforge.net/#_download](http://klibido.sourceforge.net/#_download)  ... Still no luck.  Anyone have any ideas?[/QUOTE]
 Well I no longer use unbuntu but I remember that when I used it I noticed it the build part was trying the wrong folder.  so I just went to the folder and build it by hand and installed it with checkinstall

---

### Post by tahuya_rat on 2005-06-19
Ok, thanks.

I downloaded, extracted, and ran:

```
./configure
```

and got the error:

```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
```

Is this the error you were talking about?  If so, I'm not sure what the fix you described entails, you'll have to forgive, I'm still pretty new at all this.

Thanks again.
tahuya_rat

---

### Post by alphazero on 2005-06-25
I can vouch for Klibido. It is really stable. What you need to do is go to the Klibido homepage -> downloads section. It has instructions specifically for hoary in which you have to build the package from source. I sucessfully built it and It runs like a dream.

---

### Post by fishfork on 2005-07-02
Have you tried the [CVS version](http://pan.rebelbase.com/download/#cvs) of Pan? It massively reduces the amount of memory used when downloading headers. As it's a development version it'll be a bit buggy, but it works for me and will probably solve your problem. Someone's put up a guide [here](http://www.ubuntuforums.org/showthread.php?t=23434&highlight=pan+cvs) that might help.

Cheers,

Ben

---

