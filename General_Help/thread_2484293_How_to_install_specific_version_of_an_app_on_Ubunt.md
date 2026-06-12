---
title: "How to install specific version of an app on Ubuntu server 22.04"
date: 2023-02-22
forum: General Help
---

### Post by bostjan-cadej on 2023-02-22
At the time of writing the ***apt install mysql*** command installs you MySQL 8.0.32. I would like to have MySQL 8.0.30.

How to get MySQL 8.0.30?
How to prevent that ***apt update && apt upgrade*** will NOT upgrade MySQL to 8.0.32?
How to later update to a more uptodate version?

---

### Post by TheFu on 2023-02-22
Check out **apt-mark hold** for the last 2 questions.

---

