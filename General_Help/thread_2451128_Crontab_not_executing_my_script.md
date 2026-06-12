---
title: "Crontab not executing my script"
date: 2020-09-27
forum: General Help
---

### Post by ryuuxx on 2020-09-27
I dont know what im doing wrong :

The crontab config : (last line)

[https://ibb.co/m0HsGxs](https://ibb.co/m0HsGxs)

The script :

[https://ibb.co/7gkQggx](https://ibb.co/7gkQggx)

---

### Post by spjackson on 2020-09-27
Welcome to the forums. Pasting output between CODE tags is preferred to external links to images.

"/5" is not a valid format for the minute field. If you want the job to run at 5 past the hour then you want "5" for the minute field (without the quotes). If you want it to run every 5 minutes then you want "*/5" (again without the quotes).

---

