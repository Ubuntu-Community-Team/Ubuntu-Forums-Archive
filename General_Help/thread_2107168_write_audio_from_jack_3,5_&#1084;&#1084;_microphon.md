---
title: "write audio from jack 3,5 &#1084;&#1084; microphone in console"
date: 2013-01-21
forum: General Help
---

### Post by marchelloUA on 2013-01-21
Hi all, 

how do I write audio from jack 3,5 &#1084;&#1084; microphone in console?

Upd: Write only when "something is going on".

---

### Post by Bucky Ball on 2013-01-21
Don't quite follow. What do you mean by 'write audio'? Do you mean record audio from a microphone plugged into your machine? You might try using Audacity. It is in the repositories.

---

### Post by marchelloUA on 2013-01-21
Bucky Ball, 

Yes, I mean record audio from a microphone plugged into my machine. 
Does Audacity work in console? 
Is it possible to write only when "something is going on" ?

---

### Post by Bucky Ball on 2013-01-21
Ah, sorry. In a console. No. Audacity is standalone GUI.

---

### Post by Cheesemill on 2013-01-21
Take a look at sox.

You can record audio from the command line, and also configure it to automatically record if a certain volume threshold is reached.

```
sudo apt-get install sox
man sox
```

---

