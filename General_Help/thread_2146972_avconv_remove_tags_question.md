---
title: "avconv remove tags question"
date: 2013-05-20
forum: General Help
---

### Post by AgentZ86 on 2013-05-20
Hi

I want to remove the metadata on the audio files and I read about this method
[http://manpages.ubuntu.com/manpages/precise/man1/avconv.1.html](http://manpages.ubuntu.com/manpages/precise/man1/avconv.1.html)

For example
-metadate key="value"

So for example:
avconv -i filename.wmv -metadata title= -b 128k filename.wav
Leaving the title= (blank) means metadata deleted for that value

But what if I want to remove ALL metadate not just title ?

I can make it work like this with individual blank values (ouch)
avconv -i filename.wmv -metadata title= -metadata artist= -b 128k filename.wav

But what a pain to create a line for each metadata value. 

Isn't there one simple option that can remove ALL the metadata ?

Please advise
Thanks

---

### Post by andrew.46 on 2013-05-20
I believe that you need to investigate this option:

```

-map_metadata -1

```

but I have not tested this...

---

### Post by AgentZ86 on 2013-05-26
I think your right, but I can't seem to get it working without syntax errors

Currently I can just add multiple lines using -metadata object=(leave blank) literally blank

It's just a lot of lines and if there are comments and things I didn't account for then it's not complete, but I'll look into the map some more
Thanks

---

