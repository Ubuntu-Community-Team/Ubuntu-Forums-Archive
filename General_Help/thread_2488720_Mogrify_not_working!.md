---
title: "Mogrify not working!?"
date: 2023-07-13
forum: General Help
---

### Post by triplemaya on 2023-07-13
```
$ mogrify -crop 1291×732+1716+923 *.png
mogrify mogrify: Option '-crop' requires an argument or argument is malformed.

```

This is the format quoted everywhere I look. Man page is no help at all. Can someone please tell me what is going on!

---

### Post by Holger_Gehrke on 2023-07-13
I don't quite know how you managed to enter the character you have between width and height, but that should be just a normal lower case 'x' not '×' (for comparison the two side by side and enlarged:'[SIZE=5]x×[/SIZE]'; those are not the same ...).
Also mogrify works on one image at a time, you can't give it a list of images which is what the shell will make out of '*.png' (unless you only have one PNG-file in the current working directory). If you need to mogrify multiple images, you need to do a loop, something like
```

for i in *png ; do mogrify -crop 1291x732+1716+923 "$i"; done

```

Holger

---

