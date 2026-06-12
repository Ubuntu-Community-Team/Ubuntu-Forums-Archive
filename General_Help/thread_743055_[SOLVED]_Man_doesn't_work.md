---
title: "[SOLVED] Man doesn't work"
date: 2008-04-02
forum: General Help
---

### Post by odrium on 2008-04-02
I know this is a newbie question, but I am desperate and I use man often. I don't remember when but I have time with my man down </reallybadjoke>. When I try to run man this is what happens:

bash: man: command not found (with any user)

I tried sudo mandb and mandb did its work but man is still not working.

I searched for my man in /usr/bin/man but nothing just the hatefuls man1 and man5.

Please help I need my man.

---

### Post by justleen on 2008-04-02
weird.. 
How about sudo apt-get install man ?

---

### Post by odrium on 2008-04-02
I also tried that, it only says:

Nota, seleccionando man-db en lugar de man
man-db ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 3 no actualizados.

In english that means its selecting man-db instead of man and because man-db is already in the latest version it won't install anything.

---

### Post by cdenley on 2008-04-02
```

sudo apt-get --reinstall install man-db

```

---

### Post by odrium on 2008-04-03
That didn't work neither. I'm considering the idea of installing again the whole system just to have my man.

---

### Post by odrium on 2008-04-03
Problem solved. I saw that the symbolic link at /usr/bin/man was broken: it was pointing to /usr/bin/lib/man-db/man and I changed it to /usr/lib/man-db/man. I also had to add /usr/bin/man (this man is a directory) to my PATH variable

---

### Post by erginemr on 2008-04-04
Glad that you have solved your problem.

In my system "/usr/bin/man" is just a link pointing to "/usr/lib/man-db/man". And I don't have it in my $PATH variable. So, I believe you don't need to apply the latest step.
```
**echo $PATH**

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

---

### Post by odrium on 2008-04-04
Yes I have to. My man is not /usr/bin/man it's /usr/bin/man/man, the first man is a directory the second is the command itself. That's weird, maybe it's specific to my distro (Linux Mint 4.0). I was thinking in moving the man to /usr/bin but I maintained the link in that directory because there are some weird configs archives in there,

---

