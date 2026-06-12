---
title: "Picture Conversion Script"
date: 2006-10-01
forum: General Help
---

### Post by bkanuka on 2006-10-01
I need help with making a script.  I have a very organized music folder that goes /Documents/Music/{artist}/{album}/{song}.mp3 and in every album folder there's a picture of the album cover in .png format but the name of the picture is different in every album folder.
I need a command or script that will name and format every *.png to "cover.jpg" and leave the .png there.
Any help?

---

### Post by IYY on 2006-10-01
```
for x in */*/*.png
do
    base=`echo $x | cut -d/ -f0-2`
    convert "$x" "$base/cover.jpg"
    echo $base/cover.jpg
done
```

Run this in your music directory.

---

### Post by bkanuka on 2006-10-02
Perfect. Thank you.
What is "cut -d/ -f0-2'" though? I think I understand the rest.

---

### Post by IYY on 2006-10-02
```
cut -d**/** -f**0-2**
```

Is to cut a string (read from standard input) with the delimiter **/** by taking fields **0 to 2** of it.

For example, if we had the string

```
Some/Random/String
```

This cut command would return

```
Some/Random

```

---

