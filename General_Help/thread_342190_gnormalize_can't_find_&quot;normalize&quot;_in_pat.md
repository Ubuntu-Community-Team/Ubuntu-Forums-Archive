---
title: "gnormalize can't find &quot;normalize&quot; in path?"
date: 2007-01-19
forum: General Help
---

### Post by wilberfan on 2007-01-19
Can anyone help me with this error?   (see attached)

I DO have normalize-audio installed from the repos...

---

### Post by po0f on 2007-01-20
wilberfan,

It looks like instead of installing one `normalize` command, it installs three separate commands: normalize-audio, normalize-mp3, and normalize-ogg.  Are you trying to normalize the WAV or the mp3?  Symlink the relevant one to "normalize":
```
[FONT="Courier New"]$ sudo ln -s /usr/bin/normalize-audio /usr/bin/normalize  # for wav
$ sudo ln -s /usr/bin/normalize-mp3 /usr/bin/normalize    # for mp3[/FONT]
```

HTH.

---

### Post by wilberfan on 2007-01-20
> **po0f said:**
> wilberfan,

It looks like instead of installing one `normalize` command, it installs three separate commands: normalize-audio, normalize-mp3, and normalize-ogg.  Are you trying to normalize the WAV or the mp3?  Symlink the relevant one to "normalize":
```
[FONT="Courier New"]$ sudo ln -s /usr/bin/normalize-audio /usr/bin/normalize  # for wav
$ sudo ln -s /usr/bin/normalize-mp3 /usr/bin/normalize    # for mp3[/FONT]
```

HTH.

It looks like gnormalize rips everything to wav, and then normalizes and outputs to either mp3 OR ogg?      How would I enable BOTH possibilites?

---

### Post by wilberfan on 2007-01-20
> **wilberfan said:**
> It looks like gnormalize rips everything to wav, and then normalizes and outputs to either mp3 OR ogg?      How would I enable BOTH possibilites?

No, wait, I think that question is invalid...    Since gnormalize rips everything into WAV first, THAT'S what needs the link...  It then ENCODES it to either mp3 or ogg, as I choose...

Gee, that was neat!   I rarely get to ANSWER my own questions!  =D>

---

