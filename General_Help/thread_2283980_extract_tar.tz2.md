---
title: "extract tar.tz2"
date: 2015-06-26
forum: General Help
---

### Post by Miykel on 2015-06-26
G'Day; After extracting files I run ./configure but there is no make file, according to the install note and the read me file there should be, is there anything I can do about this ???

---

### Post by steeldriver on 2015-06-26
If ./configure ran but didn't produce a makefile, then you need to examine its output for errors - usually missing build dependencies

---

### Post by Miykel on 2015-06-26
Thank you steedriver for the reply, how would I find the output, is there a log or something and also how would I check for dependencies, I notice there was a couple of files makefile.so or some thing like that, is that relevant ???

---

### Post by steeldriver on 2015-06-26
./configure scripts usually produce output direct to the terminal, with rather verbose output going to a file called config.log

Just scrolling up through the last few lines of the terminal output is usually enough to see what state it exited in

---

### Post by Miykel on 2015-06-26
Thank you so much for your help, will have another play and see what eventuates, I find Linux very enjoyable, even if it is frustrating because of my ignorance of the system, fiddle tll I get it..

---

