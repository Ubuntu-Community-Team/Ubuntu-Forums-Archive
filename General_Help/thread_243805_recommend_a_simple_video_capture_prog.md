---
title: "recommend a simple video capture prog"
date: 2006-08-25
forum: General Help
---

### Post by beerorkid on 2006-08-25
basically I have a HAUPPAUGE pvr 250.  i have used it in the past in a windows environment with beyond TV.

I do not need the complexity of mythtv I am guessing.
I am looking to capture shows I have on my DVR (cable co one, wife wanted it, yadda yadda) so I can burn them to DVD.
gonna just split the coaxial out on my cable box with one going to the PVR 250.
Just need a program to capture it.  Something I can start and stop manualy.

I have not attempted anything yet.  Figguring kino or maybe pitivi.  I could install mythtv prob, would that be better?

any suggestions?

Thanks

---

### Post by jazzgossen on 2006-08-25
xawtv is allright (though it has a rather spartan interface, it has worked well for me). I don't think Kino is going to help you. As far as I remember, it only imports video through firewire. I never tried Myth or pitivi myself.

---

### Post by beerorkid on 2006-08-25
thanks
will look into it

edit:

so I got what I wanted working.

basiaclly i tried the mythtv install here: [http://www.ubuntuforums.org/showthread.php?t=186747&highlight=HAUPPAUGE](http://www.ubuntuforums.org/showthread.php?t=186747&highlight=HAUPPAUGE)

where it links you to here: [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

got the ivtv thing working and by using the commands to test if it is working, I have everything I need.

```
cat /dev/video0 > /tmp/test.mpg
 (hit Ctrl+C to stop the capturing)
```

me happy now.

---

