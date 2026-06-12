---
title: "Renaming mp3 files extension"
date: 2012-11-05
forum: General Help
---

### Post by Herbon on 2012-11-05
Simple questions to for you pros.

I moved  200 mp3 file to a folder on my NAS.

via the CLI, somehow the files were all moved without the .mp3 extension 

How do I add the extension back to the files.

---

### Post by pbrane on 2012-11-05
> **Mr_Imhotep said:**
> Simple questions to for you pros.

I moved  200 mp3 file to a folder on my NAS.

via the CLI, somehow the files were all moved without the .mp3 extension 

How do I add the extension back to the files.

did you list the files in a terminal? Make sure before running the command below. Run this command from the directory containing the files to be renamed.
```

find . -type f -exec mv '{}' '{}'.mp3 \;

```

---

### Post by Lars Noodén on 2012-11-05
You can also use *rename*

```

rename -n 's/$/.mp3/' *

```

When you have the substitution the way you like it, take out the -n.

---

### Post by Vaphell on 2012-11-05
you can also do this with pure shell
```
for f in *; do mv "$f" "$f".mp3; done
```
or
```
rename 's/.*/$&.mp3/' *
```

---

### Post by nothingspecial on 2012-11-05
> **pbrane said:**
> did you list the files in a terminal? Make sure before running the command below. Run this command from the directory containing the files to be renamed.
```

find . -type f -exec mv '{}' '{}'.mp3 \;

```

No need to use find if you know where the files are, especially since you can make a right mess of stuff if you get the command slightly wrong.

---

### Post by pbrane on 2012-11-05
> **nothingspecial said:**
> No need to use find if you know where the files are, especially since you can make a right mess of stuff if you get the command slightly wrong.

point taken.

---

### Post by Herbon on 2012-11-05
All thanks for the assist, I created a folder and tested out commands suggestion.

They all worked!!:P

Thanks again

PS, do guys have notepads full of commands, or do you just "know" from doing it over and over again?:confused:

---

