---
title: "Output specific log entries to a file"
date: 2013-02-25
forum: General Help
---

### Post by oygle on 2013-02-25
I have a web server log file, and need to extract specific entries, either by IP address or by the string "POST".

I have looked at **find**, but can't seem to work out how to do this from bash.

---

### Post by Doug S on 2013-02-25
I would, and do, use grub for what you are wanting to do. Example:```
doug@s15:~/sguide-1304$ [COLOR=red]grep POST /var/log/apache2/access.log[/COLOR]
192.168.111.101 - - [24/Feb/2013:09:28:50 -0800] "POST /blog/wp-admin/install.php?step=2 HTTP/1.1" 200 1089 "http://s15.smythies.com/blog/wp-admin/install.php" "Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.0; Trident/5.0)"
127.0.0.1 - - [24/Feb/2013:09:29:54 -0800] "POST /blog/wp-cron.php?doing_wp_cron=1361726994 HTTP/1.0" 200 211 "-" "WordPress/3.3.1; http://s15.smythies.com/blog"
192.168.111.101 - - [24/Feb/2013:09:29:54 -0800] "POST /blog/wp-login.php HTTP/1.1" 302 1043 "http://s15.smythies.com/blog/wp-login.php" "Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.0; Trident/5.0)"

```

---

### Post by oygle on 2013-02-25
Thanks for that tip. For output to a file, I used

```

grep -c POST example.com-Feb-2013 >Feb_post.txt

```

and for a count of the number found, used

```

$ grep -c POST example.com-Feb-2013

```

---

