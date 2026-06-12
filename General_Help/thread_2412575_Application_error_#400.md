---
title: "Application error #400"
date: 2019-02-14
forum: General Help
---

### Post by cedrickzepp on 2019-02-14
After updating (through -apt update and apt upgrade) access to the installation of MantisBT has become useless. The databases and users are intact.


Access to the server (VPS) through SSH is available and intact.


```
The connection to the database has failed. The error returned by the database was # 2054: The server requested authentication method unknown to the client
Use the «Back» button in your web browser to return to the previous page. There you can correct the problems that have been identified in this error notification or select another action. You can also click on an option in the menu bar to go directly to a new section.

```

Error in phpmyadmin:


```
#2054 - The server requested authentication method unknown to the client


mysqli_real_connect(): The server requested authentication method unknown to the client [caching_sha2_password]


mysqli_real_connect(): (HY000/2054): The server requested authentication method unknown to the client


```
**Description: Ubuntu 18.04.2 LTS**
**Release: 18.04**
**PHP 7.2.15-0ubuntu0.18.04.1 (cli) (built: Feb 8 2019 14:54:22) ( NTS )**
**mysql Ver 8.0.15 for Linux on x86_64 (MySQL Community Server - GPL)**
**Server version: Apache/2.4.29 (Ubuntu)**

[ATTACH=CONFIG]282519[/ATTACH][ATTACH=CONFIG]282518[/ATTACH]

---

