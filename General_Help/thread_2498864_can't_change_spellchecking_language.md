---
title: "can't change spellchecking language"
date: 2024-07-01
forum: General Help
---

### Post by lroy0 on 2024-07-01
Hello friends, 
I have changed my language from English to French in the system preferences but when I type in french, all my words are underlined in red : The spellchecker is not functioning in French but still in English. 
Do you have any solution to allow me to correct my spelling in French and not in English by default ? 
Thanks in advance. 
BR

---

### Post by Rubi1200 on 2024-07-02
Are you talking about writing in LibreOffice or also other applications?

Is the French spellchecking package installed?

```
dpkg -l | grep aspell-fr

```

---

### Post by lroy0 on 2024-07-02
> **Rubi1200 said:**
> Are you talking about writing in LibreOffice or also other applications?

Is the French spellchecking package installed?

```
dpkg -l | grep aspell-fr

```

dpkg -l | grep aspell-fr
ii  aspell-fr                                               0.50-3-8.1                           all          French dictionary for aspell

I would like to have the french package running for all applications. and if it is possible french and English combined. 
Thanks for your quick reply.

---

### Post by lroy0 on 2024-07-02
Also other applications...

---

### Post by #&amp;thj^% on 2024-07-02
You never showed what Rubi1200 asked.
```
sudo apt-get install aspell-fr

```
Just comes down to setting it in your applications you use.

Or  CLI:
```
aspell --mode=fr check file.txt
```

---

### Post by #&amp;thj^% on 2024-07-03
> **lroy0 said:**
> 
I would like to have the french package running for all applications. and if it is possible french and English combined. 
.

That's a bit more complicated and can become messy.

---

### Post by lroy0 on 2024-07-04
> **1fallen said:**
> You never showed what Rubi1200 asked. ```
Reading package lists... Done Building dependency tree... Done Reading state information... Done aspell-fr is already the newest version (0.50-3-8.1). The following packages were automatically installed and are no longer required:   hunspell-gl-es hunspell-sv-se libdbus-glib-1-2 Use 'sudo apt autoremove' to remove them. 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```  I'm sorry I'm on Debian I'm asking help in their forum. I've hope to find help somewhere but I think I'm not in the right place... but if you have a solution, I'll take it.  B.R.

---

