---
title: "are these following codecs legal in the US?"
date: 2007-01-29
forum: General Help
---

### Post by presbp on 2007-01-29
gstreamer0.10-ffmpeg 
gstreamer0.10-gl 
gstreamer0.10-plugins-base 
gstreamer0.10-plugins-good 
gstreamer0.10-plugins-bad 
gstreamer0.10-plugins-bad-multiverse 
gstreamer0.10-plugins-ugly 
gstreamer0.10-plugins-ugly-multiverse 
libxine-extracodecs

I live in the US and I want the most multimedia functionality that is legal in the US.  Are all of those codecs legal in the Eastern United States?

---

### Post by machoo02 on 2007-01-29
gstreamer0.10-gl isn't a codec, it just lets your media player do those cool OpenGL visualizations.  As for the rest, I'm not sure...

---

### Post by llamakc on 2007-01-29
> **presbp said:**
> gstreamer0.10-ffmpeg 
gstreamer0.10-gl 
gstreamer0.10-plugins-base 
gstreamer0.10-plugins-good 
gstreamer0.10-plugins-bad 
gstreamer0.10-plugins-bad-multiverse 
gstreamer0.10-plugins-ugly 
gstreamer0.10-plugins-ugly-multiverse 
libxine-extracodecs

I live in the US and I want the most multimedia functionality that is legal in the US.  Are all of those codecs legal in the Eastern United States?

Are they from a repository based in the US? Have you checked yourself yet?

---

### Post by KaeseEs on 2007-01-30
The only codecs you have to worry about in the States are w32codecs and DeCSS.  Everything you have listed there should be clear.

As an aside, if you install the VLC media player, it has its own (legal) implementation of the w32 and other codecs - it plays about any media file you throw at it.  It's in the repos, too.

---

### Post by user2037 on 2007-09-04
Actually the fact that those implementations are free may indicate there is a problem. Formats and codecs like MP3 and AAC are patented and royalties must be paid to develop encoders and decoders.

Anyone know if Gstreamer or VLC has paid the licensing fees for the all formats and codecs they support? It is doubtful.

One advantage of commercial software like Windvd, Windows Media Player and Itunes is that they paid the fees.

---

### Post by rsambuca on 2007-09-04
From the Videolan.org's FAQ:

3.3.	

Is libdvdcss legal?
	

The use and distribution of the libdvdcss library is controversial in a few countries such as the United States because of a law called the DMCA (Digital Millennium Copyright Act). If you are unsure about the legality of using and distributing this library in your country, please consult your lawyer.
Note

Beware: VLC media player binaries are distributed with the libdvdcss library included.
3.4.	

What about personal/commercial usage?
	

Some of the codecs distributed with VLC are patented and require you to pay royalties to their licensors. These are mostly the MPEG style codecs.

With many products the producer pays the license body (in this case MPEG LA) so the user (commercial or personal) does not have to take care of this. VLC (and ffmpeg and libmpeg2 which it uses in most of these cases) cannot do this because they are Free and Open Source implementations of these codecs. The software is not sold and therefore the end-user becomes responsible for complying to the licensing and royalty requirements. You will need to contact the licensor on how to comply to these licenses.

This goes for playing a DVD with VLC for your personal joy ($2.50 one time payment to MPEG LA) as well as for using VLC for streaming a live event in MPEG-4 over the Internet.

---

### Post by Bablefish on 2007-09-04
Yes and no, yes because on the DMA and no because no one is going to arrest you for downloading them

---

### Post by rsambuca on 2007-09-04
The fact that no one is going to arrest you has absolutely no bearing on the legality of its use.

---

