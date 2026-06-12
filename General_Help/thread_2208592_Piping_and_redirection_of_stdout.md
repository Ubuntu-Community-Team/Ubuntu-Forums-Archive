---
title: "Piping and redirection of stdout"
date: 2014-03-01
forum: General Help
---

### Post by Valpskott on 2014-03-01
I'm piping ffmpeg into sox, which works great. But I want to also redirection stdout to /dev/null. 

```
ffmpeg -i input.mp3 -f mp3 - | sox -t mp3 - output.mp3 &>/dev/null

```

The command above still outputs text from ffmpeg.

While the command below tells me that ffmpeg has failed to pipe the mp3 file to sox.
```
ffmpeg -i input.mp3 &>/dev/null - | sox -t mp3 - output.mp3

```

---

### Post by jeanjd63 on 2014-03-01
Hello 
You can try something like :

ffmpeg -i input.mp3 >/dev/null 2>&1 - | sox -t mp3 - output.mp3

---

### Post by Valpskott on 2014-03-01
> **jeanjd63 said:**
> Hello 
You can try something like :

ffmpeg -i input.mp3 >/dev/null 2>&1 - | sox -t mp3 - output.mp3

Thanks for the suggestion, didn't work and here is the output.

```
ffmpeg -i input.mp3 >/dev/null 2>&1 - | sox -t mp3 - output.mp3
sox FAIL formats: can't open input  `-':
```

Adding back the "-f mp3" (that you left out) made no difference.

---

### Post by Valpskott on 2014-03-01
Hurray, I tried only the 2>&1 thingie and it worked.

like this:
<code>ffmpeg -i input.mp3 -f mp3 2>&1 - | sox -t mp3 - output.mp3</code>

---

### Post by jeanjd63 on 2014-03-01
You can try :
**ffmpeg -i input.mp3 -f mp3 - 2>/dev/null | sox -t mp3 - output.mp3 **

---

### Post by andrew.46 on 2014-04-15
I am a little curious as to what you are accomplishing with this? It looks like you are piping andmp3 file into sox and outputting an mp3 file :)

---

