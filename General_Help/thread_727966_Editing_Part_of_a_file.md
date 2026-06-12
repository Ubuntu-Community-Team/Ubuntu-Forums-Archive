---
title: "Editing Part of a file??"
date: 2008-03-18
forum: General Help
---

### Post by IainAdams on 2008-03-18
Hello,

I am trying to edit the top few lines of a massive file. The file is 6GB, however I only need to edit the first 10 lines. Does anyone know of a way to do this without having to load the whole file into an editor.

WIth Thanks

Iain

---

### Post by Oldsoldier2003 on 2008-03-18
> **IainAdams said:**
> Hello,

I am trying to edit the top few lines of a massive file. The file is 6GB, however I only need to edit the first 10 lines. Does anyone know of a way to do this without having to load the whole file into an editor.

WIth Thanks

Iain

```
man sed
```

---

### Post by gobbles414 on 2008-03-18
> **IainAdams said:**
> Hello,

I am trying to edit the top few lines of a massive file. The file is 6GB, however I only need to edit the first 10 lines. Does anyone know of a way to do this without having to load the whole file into an editor.

WIth Thanks

Iain

That's a BIG file if it's just text! What kind of file are you trying to edit? Are you attempting to modify the tags of a video file or something? Anyway, I don't know of a way for a text editor to load just part of a file. You might try the "get a cup of coffee and a sandwich while the computer loads the file" approach.

I'd also be interested to learn if what you're asking is possible.

---

### Post by gobbles414 on 2008-03-18
> **Oldsoldier2003 said:**
> ```
man sed
```

Interesting... There's a Wikipedia page regarding sed [here]("http://en.wikipedia.org/wiki/Sed").

EDIT: Perhaps someone has made a GUI frontend for sed...?

---

### Post by IainAdams on 2008-03-18
I am editing a very large SQL file and need to adjust the table creation section at the beginning.

sed sounds perfect... 

Thanks Alot for your help

Iain

---

### Post by gobbles414 on 2008-03-18
> **IainAdams said:**
> I am editing a very large SQL file and need to adjust the table creation section at the beginning.

sed sounds perfect... 

Thanks Alot for your help

Iain

Yes, thank you Oldsoldier2003. I learned something valuable too.

---

