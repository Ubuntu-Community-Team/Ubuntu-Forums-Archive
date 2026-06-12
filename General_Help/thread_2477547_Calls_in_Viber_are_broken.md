---
title: "Calls in Viber are broken"
date: 2022-07-29
forum: General Help
---

### Post by mitakvd on 2022-07-29
Hello! I'm new here but I'm using Ubuntu since 2020. 


I upgraded to 22.04 two weeks ago and I had this problem with Viber - [https://ubuntuforums.org/showthread.php?t=2477283&highlight=viber](https://ubuntuforums.org/showthread.php?t=2477283&highlight=viber). I solved it but I have another problem now. I can't call anybody via Viber. I speak about Viber to Viber calls (video or audio).
I use the last version of appimage from Viber's site. Does anybody have the same problem?

---

### Post by Claus7 on 2022-08-15
Hello and welcome to the forums,

yes, this happens also with the deb new version, (edit: even the) new AppImage edit (isn't) working.
edit: I checked this in two different places. In the first one both (deb and Appimage) were working. On the second both were not working.
I created a new user and viber was working, so I narrowed down the problem to the folder ~.local/share/mime. By removing the contents of this folder viber was working both as deb and Appimage. I do not understand why this folder creates conflicts in one place and not on the other.

Regards!

---

