---
title: "Best video format to convert to"
date: 2006-08-08
forum: General Help
---

### Post by Bou on 2006-08-08
Hi, I've got a buch of videos and I'd like to use avidemux to convert them to a free format (it would be perfect if an Ubuntu fresh install could play them out of the box) with the same quality as the original but taking up less space.

What would be my format of choice?

Thanks guys!

---

### Post by The Noble on 2006-08-08
I know .mp4 is not bad (if that is even a free format...), otherwise I only know of the ogm....

---

### Post by OrganicPanda on 2006-08-08
do them to xvid avi's because xvid rules all (in terms of compression and uber coolness at least) it's open source, i think, but i don't think ubuntu can play them out of the box, i've no idea why

---

### Post by FISHERMAN on 2006-08-10
There is only one good working free video format, ogg Theora(others snow, dirac,... aren't mature enough). Same Quality with less space will unfortunately be impossible.
I don't think you can use AviDemux to convert them.

But ffmpeg2theora(command line only) can convert most(but not all) video formats to theora.
just open a terminal
Just install it via the repo's, and type ffmpeg2theora in a terminal to see the available options.

The downside is that the Quality/compression ratio of Theora isn't as good as Xvid(but it's certainly not as bad as some people claim it to be)+AFAIK there are no DVD-Players that support Theora. But it's a free format so I don't care about these minor disadvantages.

PS: Xvid isn't entirly free, because it is based on the MPEG-4 standard(same problem like Lame-MP3). An even if Xvid would be a free format, the AVI-container and MP3-Audio are not free. So a AVI/Xvid/MP3(the most used Xvid-combination) is not a free format.

---

