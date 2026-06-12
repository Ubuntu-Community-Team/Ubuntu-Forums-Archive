---
title: "RipIt4Me + Wine = Crash?!"
date: 2006-07-27
forum: General Help
---

### Post by ubu-for on 2006-07-27
Does anybody use RipIt4Me successfully with wine?

[http://www.ripit4me.org/](http://www.ripit4me.org/)
[http://www.ripit4me.org/guide.html](http://www.ripit4me.org/guide.html)

---

### Post by GuitarHero on 2006-07-27
Why not use a native linux dvd ripper?

---

### Post by ubu-for on 2006-07-27
> **GuitarHero said:**
> Why not use a native linux dvd ripper?

Because they (k9copy, dvddecrypter, dvdshrink) can't do the job!

---

### Post by JimS on 2006-07-27
To get RipIt4Me to work in Wine ([COLOR="Red"]and I don't think we can[/COLOR])
IMHO and following the steps in the RipIt4Me Guide,
you must first be able to create a PSL file.
How to do this?
I don't know, but I'm sure you can find the answer.
Then you need to attach it to DVD Decrypter so that
DVD Decrypter can rip protected media.
After DVD Decrypter has ripped, run FixVTS to clean up.
Clear as mud???

What RipIt4Me does in MS Windows is automate several processes.
What I think we need to do in Linux is manually excute each
individual program/process seperately.
I don't think RipIt4Me will work in Linux unless it can
find each element/program ii uses.

Bottom Line:  I think we need to use RipIt4Me only as
guide to how to rip in wine.

I am fairly new to Linux and don't fully understand how wine works.
So the above is only a guess.

---

### Post by ubu-for on 2006-07-27
> **JimS said:**
> To get RipIt4Me to work in Wine ([COLOR="Red"]and I don't think we can[/COLOR])
IMHO and following the steps in the RipIt4Me Guide,
you must first be able to create a PSL file.
How to do this?
I don't know, but I'm sure you can find the answer.
Then you need to attach it to DVD Decrypter so that
DVD Decrypter can rip protected media.
After DVD Decrypter has ripped, you are home free.
Clear as mud???

What RipIt4Me does in MS Windows is automate several processes.
What I think we need to do in Linux is manually excute each
individual program/process seperately.
I don't think RipIt4Me will work in Linux unless it can
find each element/program ii uses.

Bottom Line:  I think we need to use RipIt4Me only as
guide to how to rip in wine.

I am fairly new to Linux and don't fully understand how wine works.
So the above is only a guess.

RipIt4Me crashes everytime it tries to open FixVTS from its directory. But FixVTS works manually with Wine. So ... maybe I should do it separately.

---

### Post by JimS on 2006-07-27
An alternate to RipIt4Me is to install the following in Wine:
DVD Fab free version with either VobBlanker or FixVTS for cleanup.
Has anyone done this?

---

### Post by ubu-for on 2006-07-27
> **JimS said:**
> An alternate to RipIt4Me is to install the following in Wine:
DVD Fab free version with either VobBlanker or FixVTS for cleanup.
Has anyone done this?

After the installation of DVDFab Free 2.9.8.1 I always get an error message with no content!

---

### Post by sha_man on 2006-09-19
[This Guide]("http://forum.digital-digest.com/showthread.php?t=56831") should really help you! It's what RipIt4Me does - only manually. All the programs listed there should work in Wine - afaik.

---

