---
title: "Run a php file using URL in crontab?"
date: 2013-02-10
forum: General Help
---

### Post by ArfanHaider on 2013-02-10
I want to run a php file from a url using cron tab.
I am using a webhosting and i give a command like that
9 11 9 2 * wget -O /dev/null [http://www.domainname.com/cronfile.php](http://www.domainname.com/cronfile.php)
but it does not work please tell me why this not work.
I think this command must run a "cronfile.php" and i do not want to recive any email from cron.

---

### Post by pqwoerituytrueiwoq on 2013-02-10
have you verified there are no errors in your php script?

that is set to run on the 9th minute of 11th hour of the 9th day of the  2ed month

---

### Post by ArfanHaider on 2013-02-10
I cn check my php code it is working.
and i know the time when it is activated.please tell me can this is a right command or something wrong with my hosting if it is a valid command it means there is something wrong with my hosting.

---

### Post by pqwoerituytrueiwoq on 2013-02-10
you can try using curl instead of wget

---

### Post by Bufeu on 2013-02-10
Googled?
Worked for me: [http://www.thegeekstuff.com/2011/07/php-cron-job/](http://www.thegeekstuff.com/2011/07/php-cron-job/)

---

### Post by SeijiSensei on 2013-02-10
Usually you just need to run the command-line php binary:

```
1 1 * * * /usr/bin/php -q /path/to/script.php
```

If the script produces output either direct it to a writable location in the script, or redirect it to a file with a pipe

```
1 1 * * * /usr/bin/php -q /path/to/script.php > /path/to/somefile
```

If you need to pass a parameter like a URL to the script, append it after the script.php entry and retrieve its value in the script from the built-in [$argv]("http://php.net/manual/en/reserved.variables.argv.php") array.  In your example, the URL will appear as $argv[0].

If you are running a script on a remote site, then wget or curl should work.  You can suppress errors via email by piping as I show above.  Also are you sure that the user that is running the script has sufficient privileges?

What do you see in /var/log/syslog when the script is run?

---

