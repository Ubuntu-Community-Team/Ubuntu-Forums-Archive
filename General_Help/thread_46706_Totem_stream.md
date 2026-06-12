---
title: "Totem stream"
date: 2005-07-05
forum: General Help
---

### Post by greenwom on 2005-07-05
I'm currently streaming video in totem and I'm loving it but....

I can't fast forward or slide the time bar over to cue up video.

I can do it in Win Media player on the same stream.  Anyone have a clue as to how 
I can fix that?

I've had to watch the first 20 minutes of the smae video due to a bad connection and
I'd love to be able to cue up.

---

### Post by james957 on 2007-02-07
One workaround (although still not as good as Windows Media Player) is to use Mplayer (search for it in Synaptic).

To fast forward, you should call it from the command line to increase the cache:

> mplayer -cache 20000 [http://webaddresshere.com](http://webaddresshere.com)

You can then increase playback speed by pressing ], and decrease it with [. 
there are lots of commands available.. for a list type:

> info mplayer

If it exceeds the cache, either by jumping too far forward, or by fast-forwarding too fast, then  Mplayer will crash... so still not as bombproof as Media player, but it works ok.

- James

---

