---
title: "In case anybody has problems; here's how to install and setup logwatch"
date: 2016-01-30
forum: General Help
---

### Post by MechaMechanism on 2016-01-30
I installed the program logwatch.  A little confusing at first.  This is mostly so I don't forget.  I thought it could help others.

```
sudo apt-get install exim4
```I prefer EXIM4, however some people like Postfix.  Setting up EXIM4 and Postfix is beyond the scope of this logwatch thread.

```
sudo apt-get install logwatch
```

```
sudo nano -w -W /usr/share/logwatch/default.conf/logwatch.conf
```

Use nano to change the following settings.

```
#To make Html the default formatting Format = html
Format = html
```

```
# Default person to mail reports to.  Can be a local account or a
# complete email address.  Variable Output should be set to mail, or
# --output mail should be passed on command line to enable mail feature.
MailTo = user@example.org
```

```
# Default person to mail reports from.  Can be a local account or a
# complete email address.
MailFrom = user@ubuntu.org
```

```
sudo logwatch --html_wrap 80 > logwatch.html
```

When done, open logwatch.html in your home dir.  Example /home/nate/logwatch.html, should open in your web browser.  Everything should work.  Now you will need to wait 12 to 24 hours for an email from logwatch.  Check your spam box too if you missed it.  Be sure to add logwatch to your email address contact list.

---

