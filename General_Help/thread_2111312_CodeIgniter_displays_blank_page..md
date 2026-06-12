---
title: "CodeIgniter displays blank page."
date: 2013-02-01
forum: General Help
---

### Post by srekcahrai on 2013-02-01
I am trying to install code igniter in my Ubuntu 12.10. I downloaded a zip file(CodeIgniter_2.1.3.zip) from the Code Igniter official website. I extracted the zip in my /var/www directory.

I opened the application/config/config.php file with a text editor and set my base URL.

I know I have done everything well. My apache server is running. But as I open localhost, blank is displayed. I tried

localhost/index.php
[http://localhost/](http://localhost/)
[http://localhost/index.php](http://localhost/index.php)

but same result.
Navigating to localhost/user_guide/ works as I open it. But the main index page doesn't appear. Any help will be accepted.

---

### Post by srekcahrai on 2013-02-01
```

sudo apt-get install php5 libapache2-mod-php5 php5-mysql php5-cli mysql-server

```
It did the job!

---

