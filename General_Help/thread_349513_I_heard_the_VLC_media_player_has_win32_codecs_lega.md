---
title: "I heard the VLC media player has win32 codecs legally implemented in it??"
date: 2007-01-30
forum: General Help
---

### Post by presbp on 2007-01-30
I have heard that VLC media player contains legal implementations of the win32 codecs.. is this true?? (assuming you don't own a copy of Windows)

---

### Post by az on 2007-01-30
No.  It can play a lot of different media types, but that does not change the patent rights on those formats.

---

### Post by Gillingham on 2007-01-30
Apparently not, to quote the VLC [faqs]("http://www.videolan.org/doc/faq/en/index.html#id289618")

> 3.3.	

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

### Post by CSMatt on 2007-01-30
And just how are we supposed to pay these royalties?

---

