---
title: "ripping dvds"
date: 2007-06-08
forum: General Help
---

### Post by cessna_89702 on 2007-06-08
how do i rip a dvd onto my computer????

if i use k3b it says it cant because its encrypted . it plays fine in xine move player though

---

### Post by cessna_89702 on 2007-06-08
actually xine doesnt lol it plays teh first second or so then says it doesnt have encrypted support

---

### Post by balance07 on 2007-06-08
[http://ubuntuforums.org/showthread.php?t=273635](http://ubuntuforums.org/showthread.php?t=273635)

---

### Post by ramjet_1953 on 2007-06-08
You need to install[COLOR="Blue"] libdvdcss2[/COLOR] and [COLOR="Blue"]libdvdread3[/COLOR]

However, a much better idea is to follow this link:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Look under section 1.7.6

Regards,
Roger :cool:

---

### Post by cessna_89702 on 2007-06-08
```
Invalid NAVI packet! lba=0x452A  navi=0x44DF  
Invalid NAVI packet! lba=0x452B  navi=0x44DF  
Invalid NAVI packet! lba=0x452C  navi=0x44DF  
Invalid NAVI packet! lba=0x452D  navi=0x44DF  
Invalid NAVI packet! lba=0x452E  navi=0x44DF  
Invalid NAVI packet! lba=0x452F  navi=0x44DF  
```


thats what I get with a lot more of those lines when i run ```
mplayer dvd://1 -v -dumpstream -dumpfile title.vob
```

xine says something about nav error

---

### Post by cessna_89702 on 2007-06-09
nevermind i fixed t

---

### Post by DasCrushinator on 2007-12-19
> **cessna_89702 said:**
> nevermind i fixed t

Mind sharing how?

---

### Post by weblordpepe on 2007-12-19
me too.

---

### Post by DasCrushinator on 2007-12-19
> **videolovely said:**
> About rip dvds to other video formats,i usually use nidesoft dvd ripper, it works well for me,maybe you can try it go to [their site]("http://www.nidesoft.com").

Personally, I am looking for the solution to the "Invalid NAVI Packet!" error.

---

### Post by pholden on 2007-12-19
Here's a pretty good article: [http://lifehacker.com/software/linux/rip-dvds-in-linux-the-semi+easy-way-330983.php](http://lifehacker.com/software/linux/rip-dvds-in-linux-the-semi+easy-way-330983.php)

---

