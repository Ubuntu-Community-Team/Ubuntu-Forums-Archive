---
title: "Firefox forcing text input color"
date: 2014-05-04
forum: General Help
---

### Post by Yellow Pasque on 2014-05-04
I use a dark theme with light text and some pages have white/light text input boxes where the text is white/light as well (making it invisible). I am a horrible typist, so it's important for me to see what I'm typing.

I know I fixed this issue before by making a userContent.css (or was it userChrome.css?) file with a few lines changed, but I can't find the code snippet I used (and css is not my thing).

Any ideas?

---

### Post by vasa1 on 2014-05-04
Try
INPUT, TEXTAREA {color: black !important; background: #aaaaaa !important; }
in userContent.css

---

### Post by Yellow Pasque on 2014-05-04
I changed it to:
```
INPUT, TEXTAREA {color: white !important; background: black !important; }
```

It seems to be working so far. Thanks.
(Will mark solved after more testing).

---

### Post by vasa1 on 2014-05-05
> **Temüjin said:**
> I changed it to:
```
INPUT, TEXTAREA {color: white !important; background: black !important; }
```

It seems to be working so far. Thanks.
(Will mark solved after more testing).

No problem, dark themes can produce a variety of surprises!

---

