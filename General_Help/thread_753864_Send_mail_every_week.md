---
title: "Send mail every week"
date: 2008-04-13
forum: General Help
---

### Post by ajitam on 2008-04-13
hi I'm looking for I way to send mail automatically every week. I was looking around the forum but all I can found was some pieces. I don't have any mail server install. All I have is Ubuntu an lampp.

thx

---

### Post by tams on 2008-04-13
So you have PHP. That's nice.

Here's how you can do this:

Create a php script somewhere, like /home/ajitam/weekly_mail.php. And code it like this:

```
<?php

mail('email@example.com', 'subject of mail', "Hi!\n\nI'm the message body.");
```

Execute it with "php /home/ajitam/weekly_mail.php". If the script syntax and your mail configuration is correct you should get no errors and and you'll promptly get an email at the address specified.

Now create a script in /etc/cron.weekly with the contents below and name it weekly_mail.sh. /etc/cron.weekly normally isn't writable by your user so do this as root. Be sure to pass the full path to the script to php. Do a chmod +x /etc/cron.weekly/weekly_mail.sh so it will be executable.

```
#!/bin/bash

php /home/ajitam/weekly_mail.php
```

Note that cron expects your machine to run 24/7 so it's a good idea to put this on an always-on server.

That's it. :KS From now on you'll get an email once a week.

---

### Post by ajitam on 2008-04-13
great

Only thing I dont understand is how do you set cron to perform at exact time lest say 14th May at 3pm. It's that with cron.weekly ?

---

### Post by marcusfurius on 2008-04-13
An easy way to set scheduled tasks is to use gnome-schedule. This is a GUI to cron. It also can be run as an applet.
Download it with:
```
sudo apt-get install gnome-schedule
```
Find the program under SYSTEM TOOLS - SCHEDULE.

---

