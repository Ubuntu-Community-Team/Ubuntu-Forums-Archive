---
title: "ISPConfig help"
date: 2007-01-11
forum: General Help
---

### Post by Aberrix on 2007-01-11
So I've following [this guide]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06") to setup my new server. I had some bumps along the way but I believe that I got everything completed in the guide. Well after the install of ISPConfig I was able to pull up the config login ([https://192.162.100:81](https://192.162.100:81)) however I was unable to login using the default login (u:admin p:admin). During my install of ISPConfig I ended up having to reset my mysql password which took me a little while but I got it all done and the install appeared to complete just fine. however, like I said I was unable to log in. I figured it had something to do with my little mysql bump. So... I decided to just try and re-install ISPConfig... everything appeared to go fine up until the end when I receive this:

```

All prerequisites are fulfilled.
Here we go...

Connected successfully to db db_ispconfig

Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /home/aberrix/install_ispconfig/install.php on line 692

Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /home/aberrix/install_ispconfig/install.php on line 717
mysqldump: Got error: 1045: Access denied for user 'root'@'localhost' (using password: YES) when trying to connect

Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /home/aberrix/install_ispconfig/install.php on line 806

Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /home/aberrix/install_ispconfig/install.php on line 811

Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /home/aberrix/install_ispconfig/install.php on line 821

Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /home/aberrix/install_ispconfig/install.php on line 838

Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /home/aberrix/install_ispconfig/install.php on line 1144
Restarting some services...
./setup2: line 1115: [: ==: unary operator expected
Shutting down ISPConfig system...
/root/ispconfig/httpd/bin/apachectl stop: httpd (no pid file) not running
ISPConfig system stopped!
Starting ISPConfig system...
Syntax error on line 1072 of /root/ispconfig/httpd/conf/httpd.conf:
ServerName takes one argument, The hostname of the server
/root/ispconfig/httpd/bin/apachectl startssl: httpd could not be started

Warning: mysql_fetch_array(): supplied argument is not a valid MySQL result resource in /root/ispconfig/scripts/lib/config.inc.php on line 47
No results found!ISPConfig system is now up and running!
Congratulations! Your ISPConfig system is now installed. If you had to install quota, please take the steps described in the installation manual. Otherwise your system is now available without reboot.
```

but when I go to the ISPConfig login ([https://192.168.0.100:81](https://192.168.0.100:81)) the page no longer comes up. I fear I've done something to completely bork the system... Can someone please provide me some insight as to what I've done wrong and what I can do to correct this? Thanks in advance.

---

