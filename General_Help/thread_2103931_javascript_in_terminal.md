---
title: "javascript in terminal"
date: 2013-01-11
forum: General Help
---

### Post by LLCoolJeff on 2013-01-11
Im learning some javascript at codeacademy.com and I wanted to write some of my own stuff and then run it in the terminal.

After searching, I decided I needed rhino in order to run javascript, but it doesn't seem to understand the same javascript I am learning.

for example:

```

jeff@ubuntu:~$ rhino
Rhino 1.7 release 3 2012 02 16
js> console.log("Hello World");
js: uncaught JavaScript runtime exception: ReferenceError: "console" is not defined.

js>

```How can I get this to work like I am learning it, is it trying to read a different version of javascript or something?

---

### Post by AlexDudko on 2013-01-11
> **LLCoolJeff said:**
> Im learning some javascript at codeacademy.com and I wanted to write some of my own stuff and then run it in the terminal.

After searching, I decided I needed rhino in order to run javascript, but it doesn't seem to understand the same javascript I am learning.

for example:

```

jeff@ubuntu:~$ rhino
Rhino 1.7 release 3 2012 02 16
js> console.log("Hello World");
js: uncaught JavaScript runtime exception: ReferenceError: "console" is not defined.

js>

```How can I get this to work like I am learning it, is it trying to read a different version of javascript or something?

JavaScript is rather a browser language, so the best way (and the most reasonable) to test your code is to do it in browser.

---

