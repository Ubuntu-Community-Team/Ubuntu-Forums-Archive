---
title: "Script help"
date: 2007-05-26
forum: General Help
---

### Post by ahaslam on 2007-05-26
I would like to repeat a command either a given number of times or until a time limit is reached. Currently my script simply has the command listed a few dozen times. Surely there's a better way to do this?

The purpose of this is to run a graphics benchmark (that creates a log) repeatedly to test the stability of an overclocked vga. Your suggestions would be appreciated.

---

### Post by Bachstelze on 2007-05-26
```
i=0; while [ $i -lt 3 ]; do echo $i; i=$((i+1)); done
```

of course replace 3 with the number of times ou want to run the command and echo $i with something a bit more useful ;)

---

### Post by ahaslam on 2007-05-26
It only runs a single bench. I tried it both before & after the comand to the same effect. I am sure that I'm using your suggestion incorrectly, script n00b needs hand holding.

---

### Post by Bachstelze on 2007-05-26
In a clearer syntax, it gives :

```
i=0
while [ $i -lt 3 ]; do
    echo $i;
    i=$((i + 1))
done
```

---

### Post by ahaslam on 2007-05-26
I can't get this going. Where would my command go?

Thank you.

---

### Post by Bachstelze on 2007-05-26
Instead of echo $i.

---

### Post by ahaslam on 2007-05-26
Thank you, works perfectly ;)

> replace 3 with the number of times ou want to run the command and **echo $i** with something a bit more useful
:-\"

---

