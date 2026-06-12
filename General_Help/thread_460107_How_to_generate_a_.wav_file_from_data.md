---
title: "How to generate a .wav file from data?"
date: 2007-05-31
forum: General Help
---

### Post by richard7788 on 2007-05-31
Provided there is a .txt file containing some values (data), how to generate a .wav file which contain the data?  That is, making a sound file which sounds the data.
The problem is similar to the thread here : [http://www.programmersheaven.com/mb/sound/181870/181870/readmessage.aspx](http://www.programmersheaven.com/mb/sound/181870/181870/readmessage.aspx)
Is there any tools for this?  
If programming is necessary, which one is convenient ?

---

### Post by Rhubarb on 2007-05-31
You can listen to a file, say hello.txt by:
```
cat hello.txt > /dev/dsp
```
But that's probably not what you're wanting to do.

---

### Post by drakazz on 2007-05-31
what does your file look like, by te way?

---

### Post by drakazz on 2007-05-31
> **Rhubarb said:**
> You can listen to a file, say hello.txt by:
```
cat hello.txt > /dev/dsp
```
But that's probably not what you're wanting to do.
sounds nice :)

---

### Post by richard7788 on 2007-05-31
not what I want, but thanks.
the data is numerial values which is going to represent the wave.

I guess it is getting close here, 
[http://linux-sound.org/snded.html](http://linux-sound.org/snded.html) , or
[http://www.ibiblio.org/pub/Linux/apps/sound/editors/!INDEX.html](http://www.ibiblio.org/pub/Linux/apps/sound/editors/!INDEX.html) ,
but not sure which may help.

I know the .wav format, but I'm not quite sure where to start programming.

---

### Post by richard7788 on 2007-05-31
> **drakazz said:**
> what does your file look like, by te way?

I have used the data to generate a  .txt file which is input to GNUplot for generating a graphic file, or a plot.
Now I wish to generate a .wav file to hear it.
It would be convenient to use the same .txt file, but not necessary.

The .txt file looks like:
```

1   20
2   45
3   23
4   60
5   12
.
.
.
```

---

### Post by richard7788 on 2007-06-01
This is the reverse.
[http://en.allexperts.com/q/C-1040/read-wav-file-write.htm](http://en.allexperts.com/q/C-1040/read-wav-file-write.htm)

---

