---
title: "How to export in a file with festival"
date: 2015-05-02
forum: General Help
---

### Post by CkDGTAT on 2015-05-02
How can I create output.mp3 with festival:

```
echo "This is a test." | festival --tts > output.mp3


```

Thank you

---

### Post by CantankRus on 2015-05-02
You can use **text2wave** ,which is installed with festival, to save as a wav file.
eg
```
echo "This is a test." | text2wave -o output.wav
```

Then if you want in mp3 format, you would have to convert it.
I have lame installed here and can convert with...
```
lame output.wav output.mp3
```

---

