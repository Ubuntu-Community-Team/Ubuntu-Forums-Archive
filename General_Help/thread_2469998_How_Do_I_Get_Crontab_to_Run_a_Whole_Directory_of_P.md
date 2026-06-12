---
title: "How Do I Get Crontab to Run a Whole Directory of PHP Files?"
date: 2021-12-16
forum: General Help
---

### Post by aaronesteban on 2021-12-16
I've created a little program that will generate php files and place them into a '/crons' folder to allow cron jobs to execute the files. These php files will be generated and named dynamically based on user input. So I was wondering how I could get Crontab to execute ALL of the php scripts that are in that '/crons' directory, simultaneously. Is it some kind of regular expression (regEx) with a wildcard to run the entire directory, as shown below (something similar to it)?


```
*/1 * * * * php /var/www/mywebsite.com/path-to-my-awesome-php-scripts/crons/*

```

What exactly would I need to do? Does this require a bash or shell script? (I have no experience with bash or shell). Thanks.

---

### Post by HermanAB on 2021-12-16
Use find with exec.

---

### Post by KBar on 2021-12-16
Particularly with this primary:```
-exec command {} +
```

---

