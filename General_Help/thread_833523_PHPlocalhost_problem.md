---
title: "PHP/localhost problem"
date: 2008-06-18
forum: General Help
---

### Post by suicidejack on 2008-06-18
I am having a problem with my localhost.  It is the lamp setup with nothing modified running on Ubuntu Hardy.  Html files seem to work fine but when I try to get anything php related to run I get the following error message:

Parse error: syntax error, unexpected T_STRING, expecting ',' or ';' in /var/www/tester.php on line 2

I can not figure out why this error is occuring as my code appears fine to me.  Here is my code:

```

<?php 
echo “Hello World”;
?>

```

I am relatively new to apache and Ubuntu together but I have a decent amount of experience with Windows and apache so if there is any editing to the httdp.conf file that I should do please be precise!

---

### Post by suicidejack on 2008-06-26
to answer my own question...

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop)

---

