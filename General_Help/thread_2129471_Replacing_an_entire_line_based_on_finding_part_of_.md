---
title: "Replacing an entire line based on finding part of it"
date: 2013-03-26
forum: General Help
---

### Post by cbillson on 2013-03-26
In a shell script i can directly replace text using:

sed -i "s/texta/textb/g" /home/me/myfile

I there any way i can replace an entire line, by only looking for part of it?

ie, say myfile contained [INDENT]"the quick red fox"
"the quick brown fox"
"the quick blue fox"
[/INDENT]

and i wanted to replace the line with brown in its entirety for "the lazy dog" - the only bit i could search for would be a line containing "brown" but i also want to replace "the quick" and "fox"

any help gratefully appreciated.

---

### Post by schragge on 2013-03-26
Sure
```

[COLOR=green]$[/COLOR] for color in red brown blue;do echo the quick $color fox;done
[COLOR=#008000]the quick red fox
the quick brown fox
the quick blue fox[/COLOR]

```
```

[COLOR=green]$[/COLOR] for color in red brown blue;do echo the quick $color fox;done | sed '/brown/s/.*/the lazy dog/'
[COLOR=#008000]the quick red fox
the lazy dog
the quick blue fox[/COLOR]

```

---

### Post by cbillson on 2013-03-26
> **schragge said:**
> Sure
```

[COLOR=green]$[/COLOR] for color in red brown blue;do echo the quick $color fox;done
[COLOR=#008000]the quick red fox
the quick brown fox
the quick blue fox[/COLOR]

```
```

[COLOR=green]$[/COLOR] for color in red brown blue;do echo the quick $color fox;done | sed '/brown/s/.*/the lazy dog/'
[COLOR=#008000]the quick red fox
the lazy dog
the quick blue fox[/COLOR]

```

you sir are a star, thank-you very much :)

---

