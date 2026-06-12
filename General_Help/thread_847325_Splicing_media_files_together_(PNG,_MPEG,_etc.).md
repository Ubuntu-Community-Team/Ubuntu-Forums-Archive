---
title: "Splicing media files together (PNG, MPEG, etc.)"
date: 2008-07-02
forum: General Help
---

### Post by tom66 on 2008-07-02
I would like to know if it is possible to splice media together, that is, append a PNG to a MPEG and possibly after that append another MPEG, etc. 

Also, is it possible to insert a PNG at a certain point in a media file (lets say at 10 seconds) and then have the rest of the file shifted appropriately.

Thanks,
Tom

---

### Post by soccerboy on 2008-07-02
yes that is very much possible in a decent video editing tool.

---

### Post by tom66 on 2008-07-02
Yeah, but I'm looking for an FFMPEG or Mencoder solution. 

Thanks anyways.

---

### Post by soccerboy on 2008-07-02
just out of curiosity, what are you trying to do with the splicing thing?  maybe there is a different solution?

---

### Post by tom66 on 2008-07-02
I was considering to make a PHP script for personal use, a simple tool to edit videos (I'm not great at C++). The reason is I want to develop numerous features into it that I have not seen in other editors, but it would need a backend.

---

### Post by soccerboy on 2008-07-02
maybe use gdk-pixbuf to import pictures.  That is how kino accomplishes it.  Not sure if it has a commandline interface though.
EDIT: Actually strike that.  Not sure how kino exactly accomplishes it.

---

### Post by adewale on 2008-07-02
This should be possible by using the terminal and entering the code below. You can take a look at this [http://lifehacker.com/software/privacy/geek-to-live--hide-data-in-files-with-easy-steganography-tools-230915.php](http://lifehacker.com/software/privacy/geek-to-live--hide-data-in-files-with-easy-steganography-tools-230915.php)

```
cat somefile.mp3 >> somefile.gif
```

---

### Post by tom66 on 2008-07-08
Splicing a gif and mp3 works, how? They are two different file formats!

---

### Post by DJYoshaBYD on 2008-07-08
I am a music/video producer.. Have been for 10 years.. You need a multi-format multi-track program, such as Sony Vegas.. Alot of music multi track programs can do this as well... like Sonar Pro...

Sont vegas has hella plugin effects, and you can pretty much encode it anyway you want..

---

### Post by tom66 on 2008-07-08
I'm guessing Sony doesn't just give Vegas away for free? I found ffmpeg-php but unfortunately I can't see how to add frames. Ah well, no worries. 

Thanks anyways!
Tom

---

### Post by JOshea on 2008-12-08
You can use a combination of Blenders Video Sequence editor 

The manual is located @ Blender.org at the bottom of the page.

you can pick up single frames and then do Sequence in the editor and choose your output format. 

you can tweak bit rate and everything else as long as you have codec installed for that particular kind of video. 

It does have a high learning curve but they do provide a lot of reading to 

understand how things work from several sites. 

Avidemux and VLC player are also good to use hand in hand with this one.

I have managed to put the output into Windows Movie Maker on another 

machine.....why you would want to is another question but it works.

---

### Post by jessebean on 2010-01-28
**Awesome!** So simple and elegant. :KS

> **adewale said:**
> This should be possible by using the terminal and entering the code below. You can take a look at this [http://lifehacker.com/software/privacy/geek-to-live--hide-data-in-files-with-easy-steganography-tools-230915.php](http://lifehacker.com/software/privacy/geek-to-live--hide-data-in-files-with-easy-steganography-tools-230915.php)

```
cat somefile.mp3 >> somefile.gif
```

```
cat somesong.mp3 >> anothersong.mp3
```

Mixing tracks is that easy!:KS

---

