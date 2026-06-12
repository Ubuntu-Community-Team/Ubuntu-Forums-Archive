---
title: "Can I copy SecuROM protected CDs?"
date: 2008-01-28
forum: General Help
---

### Post by 47_MasoN_47 on 2008-01-28
Hello,

I've searched around and can't seem to find a solid answer.  My boss's wife wants me to make a backup copy of a crapload of Video Professor and other computer tutorials so she can teach the office's errand boy how to use Word, Excel, teh interwebs, etc. but she doesn't want him to take the originals home because he has a nasty habit of losing/breaking things.  I can't copy them with my desktop (Windoze) because the boss won't let me buy a copy of Alcohol.  I have a Ubuntu based laptop here (I use Ubuntu at home as well) so are there any programs I can use to copy these CDs with Ubuntu?  I have tried Brasero and Gnome CD Master with no avail.

Thanks.

---

### Post by PeterJS on 2008-01-28
I don't know the exact mechanics of secuROM so I don't know where/how it keeps it's protected data. But for you want a very dumb tool that knows nothing about protection schemes of any sort (and there for can't respect them even if it wanted to, but it doesn't yay open source) look at dd. It copys bytes from stream A to stream B, no questions asked, and if stream A happens to be a device node for a cdrom, and device B happens to be a file, the result is a prefect reproduction to the byte level of the readable portion of the cdrom, about the best iso image you can get.
```

dd if=/dev/cdrom of=/home/user/somefile.iso

```
dd doesn't give any textual feedback until it completes, don't worry if it doesn't look like it's not doing anything just let it do it's thing. If it fails you'll know all about it, in the form of error messages.

---

### Post by 47_MasoN_47 on 2008-01-28
Awesome!  I'll definitely have to remember that command.  I just tried it with of=/home/mason/Desktop/word1.iso and as soon as I pressed enter the iso file appeared on the desktop and the CD started spinning up.  Sounds like it's working!  Thanks a lot for the fast reply and great advice!

---

### Post by gyrfalcon on 2008-01-28
> **47_MasoN_47 said:**
> I can't copy them with my desktop (Windoze) because the boss won't let me buy a copy of Alcohol.

SecureROM and other protection formats work by creating corrupt info on the CD that can not be read.  I don't know of a way to copy this data in a RAW type mode in Linux and replicate it on burned CD's.

That being said, I would just blow your boss off and tell him/her that you need to buy Alcohol 120% to be able to circumvent and use this software on a different machine.

You may also be able to order replacement CD's from the company you purchased them from.

---

### Post by gyrfalcon on 2008-01-28
> **47_MasoN_47 said:**
> Awesome!  I'll definitely have to remember that command.  I just tried it with of=/home/mason/Desktop/word1.iso and as soon as I pressed enter the iso file appeared on the desktop and the CD started spinning up.  Sounds like it's working!  Thanks a lot for the fast reply and great advice!

Doubt it'll work... let us know.

---

### Post by 47_MasoN_47 on 2008-01-28
Yep Falcon you were right.  I put it in and the "SecuROM copy protection loading" screen thing came up, then a few minutes afterwards a message came up saying the disc failed authentication.

I'd really like to do this stuff at work if possible, where I'm getting paid to do it.  I can take the things home and use Alcohol, CloneCD, or whatever will work to copy em but I don't get paid for that stuff because I'm not really supposed to do it.

Any advice?

---

### Post by gyrfalcon on 2008-01-29
> **47_MasoN_47 said:**
> I'd really like to do this stuff at work if possible, where I'm getting paid to do it.  I can take the things home and use Alcohol, CloneCD, or whatever will work to copy em but I don't get paid for that stuff because I'm not really supposed to do it...Any advice?

**This is way off topic for this forum unless someone wants to chime in about software that can copy SecuROM CDs on Linux (I don't know of anything)**

Basically you need to either charge you employer for your time working at home, or get them to buy you the proper tools to do it at work

To make working copies of SecuROM CD's is not very easy.  You need to create a  D.P.M. "Data Position Measurement" reading of the errors using software like Alcohol 120.  Then you need burn the CD's with that and hope for the best.

If you have further questions checkout the Alcohol, or cdfreaks.com forums.

---

### Post by 47_MasoN_47 on 2008-01-29
I use Alcohol at home and am pretty good with copying PC games with it so I think I should be able to do these.  If I can fix the charger port on my Windoze based laptop I can use it (it has alcohol) at work to copy the CDs.

What forum should this go in specifically?  I didn't know so I figured general would be the best place.

---

