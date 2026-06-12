---
title: "Gespeak - mbrola - Path of voices"
date: 2013-11-06
forum: General Help
---

### Post by subcoolent on 2013-11-06
I have just installed gespeak and mbrola. 
I have followed a few guides, as simple as this it, the program refuses to accept the path to the location of voices, or detect them. 
Im a bit lost on what to do. There arent many resources for assistance given how simple this is supposed to be. 
Someone please help.

---

### Post by sudodus on 2013-11-07
I suggest that you start the the simple espeak program

```
sudo apt-get install espeak
```

and try for example

```

espeak -v en action
espeak -v fr action
espeak -v sv action

```
You should get fairly good voices in the different languages even with the basic espeak.

Read ```
man espeak
``` and then go on to gespeaker and mbrola. I think you can browse the internet for more detailed tutorials and tips.

---

