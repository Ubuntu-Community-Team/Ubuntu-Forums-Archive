---
title: "Rubyripper and discid"
date: 2008-03-21
forum: General Help
---

### Post by jtreach on 2008-03-21
Heya after my failed attempts at running EAC under wine, I would like to install rubyripper. Problem is that if I use discid or cd-discid with it, then all the buttons grey out.

Can anybody help?

Thanks in advance.

---

### Post by logos34 on 2008-03-21
EAC works fine for me, but I can't get RubyRipper to recognize CDs, even though it sees the drive!

What's your problem with EAC?  Did you add it to Wine config? Maybe it doesn't see your cdrom (common problem)?

---

### Post by jtreach on 2008-03-21
My problem with EAC is that it doesn't delete the .wav files and all I get after the encoding is  the tempory mp3 files.

Any ideas?

---

### Post by logos34 on 2008-03-21
Here's the configuration guide you should be using:
[http://www.teqnilogik.com/tutorials/eac.shtml#CompressionOptionsMP3](http://www.teqnilogik.com/tutorials/eac.shtml#CompressionOptionsMP3)

(>'Delete WAV after compression')

Not sure what you mean by 'temporary mp3' though.  Maybe the path or command  line is wrong.

---

### Post by jtreach on 2008-03-21
Yeah i've got that option enabled, I get mp3's at the end of the process but there called things like "0tmp1!542.mp3@"

I'm using this commandline:

```
-V 0 --vbr-new --add-id3v2 --ignore-tag-errors --ta "%a" --tt "%t" --tg "%m" --tl "%g" --ty "%y" --tn "%n" %s %d@
```

---

### Post by jtreach on 2008-03-22
Anybody?

---

### Post by logos34 on 2008-03-22
I think the parts marked in red may be causing some mishief:

> -V 0 --vbr-new --add-id3v2 --ignore-tag-errors --ta "%a" --tt "%t" [COLOR="Red"]--tg "%m"[/COLOR] --tl "%g" --ty "%y" --tn "%n" %s %d[COLOR="Red"]@[/COLOR]

Try this line instead:

> -V 0 --vbr-new --add-id3v2 --pad-id3v2 --ta "%a" --tt "%t" --tl "%g" --ty "%y" --tn "%n" %s %d

Or the newer simplified version listed in the above guide.

---

### Post by jtreach on 2008-03-22
Just tried ripping with the flac encoder, it appears only the lame encoder is giving me this problem.

---

### Post by jtreach on 2008-03-23
> **logos34 said:**
> I think the parts marked in red may be causing some mishief:



Try this line instead:



Or the newer simplified version listed in the above guide.

Your a god!!!!! It works fine now, thing is I used the much used Jiggafellz guide to do this, do you think  this is a wine specific problem?

---

### Post by logos34 on 2008-03-23
I doubt it.  Comparing the guide you referred to with the authoritative [hydrogenaudio EAC-lame wiki]("http://wiki.hydrogenaudio.org/index.php?title=EAC_and_Lame"), I think the source of your problem was that final fateful "[COLOR="Red"]@[/COLOR]" that somehow crept in

---

