---
title: "Pipe to /dev/dsp"
date: 2006-11-18
forum: General Help
---

### Post by Chua-Chua on 2006-11-18
Hello,

I would like to know how to pipe something into /dev/dsp so that the bytes will be outputed to the sound card.

A friend of mine piped his kernel to the dsp so he can show me a trick.

I haven't been able to ask him how he did it and I was wondering if there are commands for that.

I think he piped like this:
$ echo kernelx.xx.x | /dev/dsp

I don't know. heh. 
Anybody have a clue?

---

### Post by reclusivemonkey on 2006-11-18
> **Chua-Chua said:**
> Hello,

I would like to know how to pipe something into /dev/dsp so that the bytes will be outputed to the sound card.

A friend of mine piped his kernel to the dsp so he can show me a trick.

I haven't been able to ask him how he did it and I was wondering if there are commands for that.

I think he piped like this:
$ echo kernelx.xx.x | /dev/dsp

I don't know. heh. 
Anybody have a clue?

Try 

```

cat *filename* > /dev/dsp

```

Or better still, try 

```

sudo apt-get install festival

```

then

```

echo "My festival is better than your kernel cat" | festival --tts

```

;-)

---

### Post by Chua-Chua on 2006-11-18
Cool.
Thanks a lot.

---

### Post by po0f on 2006-11-18
Chua-Chua,

```
$ cat /dev/urandom > /dev/dsp
```

---

