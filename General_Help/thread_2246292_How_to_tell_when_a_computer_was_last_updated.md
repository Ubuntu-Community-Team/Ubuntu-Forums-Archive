---
title: "How to tell when a computer was last updated?"
date: 2014-09-29
forum: General Help
---

### Post by ogp on 2014-09-29
Hello, 

This may turn out to be a more complex question than I think, but is there an easy way to tell when a Ubuntu machine was last updated? I am guessing this will mean finding out the last time *sudo apt-get upgrade* was run, probably from bring typed in a terminal. 

Thanks, 


Oli.

---

### Post by Bashing-om on 2014-09-29
ogp; Guess what ?

That is an oft asked thing. And guess what ? The system does take that into consideration and provides a log !
What do you see:
```

less /var/log/dpkg.log

```
Press 'q' to 'quit' from 'less'

[INDENT]even after 50+ years
[INDENT][INDENT][INDENT]linux still doing it right
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ogp on 2014-09-29
Bashing-om, 

Thanks - I should probably have had more of a look around to see if the question had already been answered. I guess I'm just a lazy hound (it's been said before!) 

Thank you. That looks like the answer I have been looking for. Out of curiosity, how far does that log go back? The machine I am typing this on doesn't get used much but seems to go back a couple of weeks. Does it store everything from the current month or something like that? 

Thanks again. 


Oli.

---

### Post by Habitual on 2014-09-29
They seem to be rotated.
Check out 
```
 ll /var/log/dpkg.log*
```

and use 
```
zcat /path/to/one_of_those.gz | less
```

---

### Post by Bashing-om on 2014-09-30
ogp; Great !

Pleased to be of some small help.
Even more so that we can point ya in the right direction.

[INDENT][INDENT]Happy Trails to You[/INDENT][/INDENT]

---

