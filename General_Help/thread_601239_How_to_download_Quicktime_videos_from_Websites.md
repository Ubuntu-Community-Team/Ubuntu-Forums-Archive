---
title: "How to download Quicktime videos from Websites ?"
date: 2007-11-03
forum: General Help
---

### Post by agitator1 on 2007-11-03
Please suggest how to download and save quicktime videos from websites like [www.apple.com/trailers.com]("www.apple.com/trailers")

i m new to Ubuntu and i dont know my way thru...


thanks

Raj

---

### Post by ecschiel on 2007-11-03
This is a hot issue. Actually, you cannot download that videos for legal reasons, but i'm not going to explain this because is not what you ask :lolflag:

The only programs I know for downloading streamed media are really outdated or not feature rich, one of them is mmsclient, the other is mimms. The second one is based in the first but are really different right now. I'm working in other right now, is an alpha version and i'll publish something when get things the way I want.

The only problem (for you) with this apps is that only works with mms streams (micro$oft formats) and not with Quicktime.

I find a way to download the videos from the page u post (actually, it takes me just five minutes :lolflag:). I'll put this step by step so u can understand this:

1 - Open the page u post
2 - Choose a movie (i'll choose 27 dresses for tellin you how to do this)
3 - Click on trailer in the new page
4 - Here u can watch the movie but instead you will look at the HTML code (here it depends what is your navigator, in Firefox you can do Ctrl+U)
5 - Now in the source code look for this "QT_WriteOBJECT_XHTML" (without the quotes). There will be a link that is a reference to the real trailer (in this case is [http://movies.apple.com/movies/fox/27_dresses/27_dresses-h.ref.mov](http://movies.apple.com/movies/fox/27_dresses/27_dresses-h.ref.mov))
6 - In a console put ```

wget http://movies.apple.com/movies/fox/27_dresses/27_dresses-h.ref.mov

```
7 - And then ```
 cat 27_dresses-h.ref.mov
```
8 - This is a binary file so there will be weird char is the screen and maybe your speaker will beep sometime. At this point you will have dumped the file in the console showin you the real files
```

ir3ul@magi:~$ cat 27_dresses-h.ref.mov
&#65533;moov&#65533;rmrafrmda(rdrfurl 27_dresses_h320.movrmdr
&#65533;
 rmqurmvcqtimfrmda(rdrfurl 27_dresses_h480.movrmdrd
                                                       rmqurmvcqtim

```
9 - If you look carefully you will see 2 filenames similar to the one we download with wget steps earlier: 27_dresses_h320.mov and 27_dresses_h480.mov. The one with the higher number it's the better resolution (480x204) so it's the best choice. now do
```

wget http://movies.apple.com/movies/fox/27_dresses/27_dresses_h480.mov

```
and in a few seconds you will have the trailer downloaded.

I'm sorry if i give too many details, u tell u were new to ubuntu, and i tought "new to linux too", so, don't blame me. If it's not too clear just PM me and give you a better explanation

---

### Post by disturbedite on 2007-11-03
simple with firefox:  install the mediaplayerconnectivity extension.

---

