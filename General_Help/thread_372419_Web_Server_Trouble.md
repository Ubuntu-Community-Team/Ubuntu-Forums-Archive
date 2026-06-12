---
title: "Web Server Trouble"
date: 2007-02-28
forum: General Help
---

### Post by Quillz on 2007-02-28
I installed the latest versions of Apache, MySQL, PHP and PHPMyAdmin to set up a web server. The installation worked fine, and everything is set up. However, when I try to log into PHPMyAdmin using the default user name of [FONT=Courier New]root[/FONT] with no password, I get error #2002. Do I need to edit some files beforehand? I read the included documentation, but didn't seem to answer my question.

---

### Post by scxtt on 2007-02-28
have you tried setting a password for the root user?  i can't imagine it would work w/o setting that, even if you can login to MySQL w/ no password ...
```
CHANGE ROOT P/W:
        % mysql -u root -p mysql
          mysql> UPDATE user SET password=PASSWORD('manager')
              -> WHERE user='root';
          mysql> FLUSH PRIVILEGES;
```change *manager* to whatever you want the p/w to be ...

---

### Post by Quillz on 2007-02-28
No, I didn't set a password, since all my prior experience with PHPMyAdmin is that by default, you only needed to type root. Lemme see if this works...

---

### Post by Quillz on 2007-03-10
> **scxtt said:**
> have you tried setting a password for the root user?  i can't imagine it would work w/o setting that, even if you can login to MySQL w/ no password ...
```
CHANGE ROOT P/W:
        % mysql -u root -p mysql
          mysql> UPDATE user SET password=PASSWORD('manager')
              -> WHERE user='root';
          mysql> FLUSH PRIVILEGES;
```change *manager* to whatever you want the p/w to be ...
This isn't working out for me. It says to enter a password, but my user password isn't working. Do I have to change some MySQL files to allow me to enter PHPMyAdmin?

---

