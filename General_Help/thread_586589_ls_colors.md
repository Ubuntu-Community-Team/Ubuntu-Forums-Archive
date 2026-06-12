---
title: "ls colors"
date: 2007-10-22
forum: General Help
---

### Post by oldcpu on 2007-10-22
Some file extensions do not print with colors.  How do I add colors to the files when I ls?

---

### Post by mali2297 on 2007-10-22
The colors are governed by the environment variable LS_COLORS, check
```

echo $LS_COLORS

```
Then you will see how the files are colored according to their extensions, eg *.mp3=01;35. This means that .mp3 files are shown in **bolded** [COLOR="Magenta"]magenta colored[/COLOR] fonts. The codes used are

Attribute codes:
00=none 01=bold 04=underscore 05=blink 07=reverse 08=concealed
Text color codes:
30=black 31=red 32=green 33=yellow 34=blue 35=magenta 36=cyan 37=white
Background color codes:
40=black 41=red 42=green 43=yellow 44=blue 45=magenta 46=cyan 47=white

If you want to color .wma and .m4a files in the same way, you can add the following line to your **.bashrc** file:
```

export LS_COLORS=$LS_COLORS:"*.wma=01;35":"*.m4a=01;35"

```

Hopefully you understand how to add additional color definitions to that line.

---

