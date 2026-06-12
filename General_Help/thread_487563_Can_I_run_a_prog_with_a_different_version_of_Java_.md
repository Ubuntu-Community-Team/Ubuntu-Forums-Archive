---
title: "Can I run a prog with a different version of Java than the default?"
date: 2007-06-29
forum: General Help
---

### Post by Nameless_one on 2007-06-29
I want to run PCGen which is only compatible with java 1.4/1.5, but I am also running Azureus which runs well only with java 1.6 (I am on an amd64 machine). Can I specify that PCGen be run by a 1.5 java VM?

---

### Post by tbresson on 2007-06-29
In Azereus you can tell the program where the path to the java bin's are so it will use that version. 
If you want PCGen to run on a specific java version I think you'll need to look at the application and not the OS.

---

### Post by Nameless_one on 2007-06-29
Hm. I see. I was wondering if there was a sort of wrapper, something I could do. I think I can change azureus to use the latest java while the system default is the other one, but I'd like to keep the latest as the default. 

What do you think I could do with the application, so that it runs as I want it to?

SOLVED: PCGen runs through a bash script, which detects java and then exec's a jar using "exec java etc.". I simply switched java for the full path to a 1.5 java installation, and it worked.

---

