---
title: "Java app works on 19.04 but not 19.10"
date: 2020-03-30
forum: General Help
---

### Post by ChrisOfBristol on 2020-03-30
This was because I had java-jre version 8. What is the default version on 19.10?

---

### Post by spjackson on 2020-04-01
The default jre in both 19.04 and 19.10 is openjdk-11-jre, i.e. java 11. See [https://packages.ubuntu.com/disco/default-jre](https://packages.ubuntu.com/disco/default-jre) and [https://packages.ubuntu.com/eoan/default-jre](https://packages.ubuntu.com/eoan/default-jre)

---

### Post by ChrisOfBristol on 2020-04-01
> **spjackson said:**
> openjdk-11-jre
Thanks, I got some information from another site and upgraded to 11. It was a bit of a puzzle why I had V8 as Java is not installed by default and I hadn't installed it. I assume that it must have been installed as a dependency of one of the packages I installed. The link you included will be useful for answering such questions in future.

Not meaning to be cast aspersions on this site, but why are answers usually so slow in forthcoming compared with other sites? Is it not the official and most important Ubuntu forum?

[EDIT] To answer my own question, I think most people use                   [https://askubuntu.com/](https://askubuntu.com/)

---

