---
title: "Digikam MPEG Encoder Problem"
date: 2005-07-28
forum: General Help
---

### Post by alec on 2005-07-28
Hi,

I am trying to use the MPEG encoder Kipi plugin in Digikam.

I keep getting two error messages:

1. I cannot find MP2ENG I can live with because it is to do with audio. However

2. IMAGES2MPG script has reported an error. Is terminal to the whole problem.

Does anyone know a fix for this problem?

Or do you know another way of making DVD slide shows that will show on a TV?

---

### Post by pestilence4hr on 2005-07-29
[QUOTE=alec]
Or do you know another way of making DVD slide shows that will show on a TV?[/QUOTE]

Some DVD players will "play" discs that have pictures in the root directory, you could try that.  I have done this, numbering the pictures so that any reasonable player would order them correctly (i.e. 000000001.jpg, 000000002.jpg, etc).

---

### Post by alec on 2005-07-29
Do you mean burn the pictures directly onto the dvd, no folders, each picture in numenrical order?

---

### Post by pestilence4hr on 2005-07-29
[QUOTE=alec]Do you mean burn the pictures directly onto the dvd, no folders, each picture in numenrical order?[/QUOTE]

Yup.

---

### Post by regeya on 2005-09-20
[QUOTE=alec]Hi,

I am trying to use the MPEG encoder Kipi plugin in Digikam.

I keep getting two error messages:

1. I cannot find MP2ENG I can live with because it is to do with audio. However

2. IMAGES2MPG script has reported an error. Is terminal to the whole problem.

Does anyone know a fix for this problem?

Or do you know another way of making DVD slide shows that will show on a TV?[/QUOTE]

You're probably getting an error because you don't have mjpegtools installed.  both mpeg2enc and mp2enc are in this package.  and iirc you have to have an audio stream on DVD video (though I could be wrong about that one.)  most programs I've run into just pad video with a silent mp2 track.

---

