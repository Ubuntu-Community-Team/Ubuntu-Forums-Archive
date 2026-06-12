---
title: "Renaming JPEG file from Exif (but NOT date/time)"
date: 2022-11-19
forum: General Help
---

### Post by trenien2 on 2022-11-19
So here is my problem : I've had a major drive crash with a complete loss of its allocation table. I was lucky enough to recover the raw data, from which I've extracted the files according to their type (txt, odt, jpg and so on).
From this, I'd like to recover the (large) number of family pictures which are lost among a sea of various jpg (total number close to 500000. No way I can realistically do that manually).
I figured the best way would be to do an auto-renaming of files using the exif data, provided I don't extract the date and time (which all jpg have and so would be of limited help). Instead, I'd like to extract the camera type or brand so as to append at the start or the end of the file names. Most of the other random pictures will not have such data, and I'd be able to quickly differentiate.

Question is, how do I do that ? I guess some kind of script would do the trick, but that's far and beyond my abilities...

---

### Post by Holger_Gehrke on 2022-11-19
I'd use 'identify' from the ImageMagick suite of command line tools (package imagemagick). Using the '-format' option and '%' escapes it will output EXIF-tags to standard output. This
```

for i in *jpg ; do echo mv "$i" "$(identify -format '%[exif:Make]-%[exif:Model]' $i)$i"; done

```
executed in the directory where the *jpg files are, will output a long list of 'mv' commands to rename the files. Check that list carefully for problems. Once you are sure this is what you want to do, remove the 'echo' command and instead of showing the commands it will execute them.

Holger

---

### Post by trenien2 on 2022-11-19
Well, that does do the trick over a small sample.

Thanks

Time to run the real thing (and it's on to a few hours of the computer running it)...

---

