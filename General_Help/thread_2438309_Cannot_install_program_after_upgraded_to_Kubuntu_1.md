---
title: "Cannot install program after upgraded to Kubuntu 19.10"
date: 2020-03-09
forum: General Help
---

### Post by yoramdavid on 2020-03-09
Hi all,
I recently upgraded to Kubuntu 19.10 and one of the programs I used regularly is now having dependencies issues:
kfilereplace.
I get the following dependencies not met:
[HTML]A preparar para desempacotar kfilereplace_16.04.3-1+b2_amd64.deb ...
A descompactar kfilereplace (4:16.04.3-1+b2) ...
dpkg: problemas com dependências impedem a configuração de kfilereplace:
 kfilereplace depende de kde-runtime (>> 4:4.10); no entanto:
  O pacote kde-runtime não está instalado.
 kfilereplace depende de libkde3support4 (>= 4:4.3.4); no entanto:
  O pacote libkde3support4 não está instalado.
 kfilereplace depende de libkdecore5 (>= 4:4.4.0); no entanto:
  O pacote libkdecore5 não está instalado.
 kfilereplace depende de libkdeui5 (>= 4:4.3.4); no entanto:
  O pacote libkdeui5 não está instalado.
 kfilereplace depende de libkio5 (>= 4:4.3.4); no entanto:
  O pacote libkio5 não está instalado.
 kfilereplace depende de libkparts4 (>= 4:4.5.85); no entanto:
  O pacote libkparts4 não está instalado.
[/HTML]
When I try to install those dependencies, they cannot be found, it says it is not available.

Is there a way to go around this? Or anyone knows a package with similar functions?
Thank you all.
Yoram

---

### Post by mörgæs on 2020-03-10
It looks like your Kubuntu was installed ages ago. I recommend that you back up your important files and do a fresh install of 19.10.

---

### Post by yoramdavid on 2020-03-11
> **mörgæs said:**
> It looks like your Kubuntu was installed ages ago. I recommend that you back up your important files and do a fresh install of 19.10.


Hi, actually it is a fresh install. I just installed it 5 days ago.
What makes you say so?

Thank you for your help.
Yoram

---

### Post by SeijiSensei on 2020-03-12
"This app is unmaintained and no longer released by the KDE community."

[https://kde.org/applications/unmaintained/org.kde.kfilereplace](https://kde.org/applications/unmaintained/org.kde.kfilereplace)

It's not in the repositories for 20.04 either.

---

### Post by mörgæs on 2020-03-12
> **yoramdavid said:**
> Hi, actually it is a fresh install. I just installed it 5 days ago.
What makes you say so?


A blunder. I noticed ```
libkde3support4 (>= 4:4.3.4)
``` in your output and compared to [https://answers.launchpad.net/ubuntu/trusty/+package/libkde3support4](https://answers.launchpad.net/ubuntu/trusty/+package/libkde3support4)
but now I see that it doesn't prove anything.

---

### Post by yoramdavid on 2020-03-12
Oh, that is so sad, such a good program.
If I install Ubuntu Mate 16.04, which is what I had before, will I be able to install it?
I could dual boot.

---

