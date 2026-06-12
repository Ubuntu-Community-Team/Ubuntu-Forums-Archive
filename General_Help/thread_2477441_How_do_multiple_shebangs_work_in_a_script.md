---
title: "How do multiple shebangs work in a script?"
date: 2022-07-25
forum: General Help
---

### Post by Paddy Landau on 2022-07-25
**EDIT:** This is due to a [misreading on my part]("https://ubuntuforums.org/showthread.php?t=2477441&p=14105582&viewfull=1#post14105582")! Multiple shebangs aren't allowed.

[HR][/HR]
I had always thought that a shebang had to be the first line in a script, and that only one was allowed.

Today, I realised that this isn't true. For example, dkms uses three shebangs, one at the top and the other two further down.

I have been searching about this, and all results that I've found claim that this is invalid and mustn't be used. Clearly, that is incorrect.

I have some questions about this.


[LIST]
[*]How specifically are multiple shebangs interpreted — when the script is loaded, or while it runs? The former makes the best sense, because the latter would lead to some strange and counterintuitive results, and make it horribly hard to debug.
[*]What would happen if you put a shebang inside a Bash function?
[*]What are the upsides and downsides of using multiple shebangs? I don't understand why dkms would use this (it mixes Bash and Sh).
[*]What gotchas should one be aware of when doing this?
[/LIST]
Or, if you know where the relevant documentation is, please point me to it!

Thank you

---

### Post by dragonfly41 on 2022-07-25
I just found this link amongst many if you search "multiple shebang"

[https://rosettacode.org/wiki/Multiline_shebang](https://rosettacode.org/wiki/Multiline_shebang)

My only experience with multiple shells is using Jupyter Notebooks where you can freely mix run time engines such as Python, R, Bash etc in one document

---

### Post by Paddy Landau on 2022-07-25
> **dragonfly41 said:**
> I just found this link…
I saw that, but that is about a multiline shebang, not about multiple shebangs. I admit that I didn't fully understand the page.

---

### Post by Holger_Gehrke on 2022-07-25
A careful reading of the context might pay off ...

dkms is basically creating additional shellscripts from HERE-documents
```

(cat << EOF
#!/bin/sh
... ... ...
EOF
) > $dstfile

```

So there are actually no multiple shebangs here, the second (and third) shebang are data that gets written to a file (which is then marked executable and executed ...)

Holger

---

### Post by Paddy Landau on 2022-07-25
> **Holger_Gehrke said:**
> dkms is basically creating additional shellscripts from HERE-documents…
Ah, thank you!

I've looked at the other scripts that do this (I found 20). They all seem to do the same thing, with one exception: libtoolize. I can't quite figure this one out; I think that the two extra shebangs are meant to be comments.

---

### Post by Holger_Gehrke on 2022-07-25
From reading the comments in libtoolize I believe the parts of the script after the additional shebangs started out as separate function libraries. Instead of including them with '. /path/and/name/of/library.sh' they were simply loaded into the script as they were to save a bit of (run-)time and to avoid loading a possibly different version.

Holger

---

### Post by Paddy Landau on 2022-07-25
> **Holger_Gehrke said:**
> … they were simply loaded into the script as they were to save a bit of (run-)time and to avoid loading a possibly different version.
And, presumably, to reduce maintenance by having just one script instead of several.

Thank you

---

