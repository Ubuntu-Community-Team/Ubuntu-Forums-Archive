---
title: "Java web start not working"
date: 2005-06-29
forum: General Help
---

### Post by duffman25 on 2005-06-29
Hi

I've installed java as the ubuntu guide points out: sun-jre1.5, but today I went to a web with java web start technology & firefox didn't load it.

[http://www.gentleware.org/webstart2/Poseidon.jnlp](http://www.gentleware.org/webstart2/Poseidon.jnlp)

Instead firefox ask me what to do with the jnlp file (download open it with firefox).

Any ideas on what do I have to do to enable jws?

Thanxs.

---

### Post by duffman25 on 2005-07-02
[QUOTE=duffman25]Hi

I've installed java as the ubuntu guide points out: sun-jre1.5, but today I went to a web with java web start technology & firefox didn't load it.

[http://www.gentleware.org/webstart2/Poseidon.jnlp](http://www.gentleware.org/webstart2/Poseidon.jnlp)

Instead firefox ask me what to do with the jnlp file (download open it with firefox).

Any ideas on what do I have to do to enable jws?

Thanxs.[/QUOTE]

no one uses java web start?

---

### Post by dulljeff on 2005-07-09
Yes, I do and I faced the same problem.
You just have to open the ".jnlp"-file with ```
/usr/java/javaws/javaws
``` and that's it.  :) 

Have fun,
dulljeff

---

### Post by duffman25 on 2005-07-11
[QUOTE=dulljeff]Yes, I do and I faced the same problem.
You just have to open the ".jnlp"-file with ```
/usr/java/javaws/javaws
``` and that's it.  :) 

Have fun,
dulljeff[/QUOTE]

Hi

Thanxs for answering, and sorry for my late response, but I can't find javaws on my pc.

```

$ whereis java
java: /usr/bin/java /usr/share/man/man1/java.1.gz
$ whereis javasw
javasw:

```

The java package I have installed is this: 

```

i   sun-j2re1.5  - Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)

```

which is the one recommended by the ubuntu guide.

---

### Post by jaranguren on 2005-07-11
On my machine, it is 
/usr/lib/j2sdk1.5-sun/jre/javaws
 
or 

try looking for javaws using
find /usr/lib -name javaws

---

### Post by duffman25 on 2005-07-11
[QUOTE=jaranguren]On my machine, it is 
/usr/lib/j2sdk1.5-sun/jre/javaws
 
or 

try looking for javaws using
find /usr/lib -name javaws[/QUOTE]


Thanxs!

---

