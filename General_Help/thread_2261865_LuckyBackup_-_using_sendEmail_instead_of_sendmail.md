---
title: "LuckyBackup - using sendEmail instead of sendmail"
date: 2015-01-21
forum: General Help
---

### Post by ecomer on 2015-01-21
I wanted luckybackup to use lightweight sendEmail instead of sendmail for mailing via Yahoo mail. I use sendEmail in some shell scripts so I know that it works on my 14.04 system but it failed with luckybackup. After much fiddling I solved the problem - the server line must contain NOTHING but the smtp servername. I have attached a screenshot of a working configuration.

---

