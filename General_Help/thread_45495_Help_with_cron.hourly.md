---
title: "Help with cron.hourly"
date: 2005-06-30
forum: General Help
---

### Post by crazeinc on 2005-06-30
Hey guys, I was under the impression that if you put a shell script under /etc/cron.hourly, it was supposed to be executed every hour, but mine appears not to be. I've chmod'd it a+x like the scripts in cron.daily. Here's all that the script is:

#!/bin/sh
ruby /usr/local/runweather.rb

That's it, so what am I missing?

---

### Post by intangible on 2005-07-01
That looks good to me.  Are you sure cron is running?  Are your daily scripts getting ran?

also, try it like this:

sudo crontab -e
```
@hourly /usr/bin/command-to-run
```

and see if that works.

---

### Post by Yotto on 2005-08-30
I stumbled across this thread because I was having this exact problem, and I (think I) figured out (at least for me) what's going wrong but (being a moderate newbie) have no idea how to fix it.

The problem is, root is the one running my script, and my script is trying to set the desktop background for user root. I am not running as user root, however, so it's not changing /my/ background.

I'm using gconftool to do it, but there's not --user option. Is there a way to "anti-sudo" to make root run as another user? Or am I totally off and don't know what's going on?

(For reference, here's the script I'm using, in full, in \etc\cron.hourly\ and when I run it as me, it changes my background no problem. I got the script from some webpage somewhere)
------
```
#!/usr/bin/perl

$dir = "/home/yotto/backgrounds/";

@files = `ls -t ${dir}*`;
my $base = 1.1;
$tmp = ($base ** rand(log(2)/log($base)) - 1);
#$filename = $files[rand(@files)];
$filename = $files[int($tmp*($#files+1))];
chomp($filename);
#print $filename . "\n";
system("gconftool-2", "--type", "string", "--set", "/desktop/gnome/background/picture_filename", $filename);
system("gconftool-2", "--type", "string", "--set", "/desktop/gnome/background/picture_options", "scaled");

```

---

### Post by byronsalty on 2005-09-04
To change users you just need to run the "su <user-name>" command. If you are root then you don't need to type a password.

You should just need to add the line near the top:
```
`su <your-user-name>`
```

---

### Post by vladuz976 on 2005-09-28
what time of the day do daily scripts get exectuted?
i have a system backup in cron.daily but i don't want it to run during the day or at midnight coz i am on the computer at that time.

---

### Post by BigHairyTroll on 2007-12-04
Hey guys,
If I am not mistaken, the entries in your cron.hourly should not contain a dot as in myproc.sh
Try renaming that.

---

### Post by pointone on 2007-12-04
cron stumbles sometimes on scripts or programs that produce a lot of output. What happens if you run your script manually as root? 

```
sudo ruby /usr/local/runweather.rb
```

Please post the output of the following command:

```
sudo cat /var/log/syslog | grep CRON
```

@ BigHairyTroll:

Dots shouldn't matter. I have *.sh scripts that run fine, and find.notslocate is included by default in cron.daily.

@ vladuz976:

Check /etc/crontab to find what time cron runs. On my system, "cat /etc/crontab" reveals the following about cron.daily:

```
**25 6**    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
```

... meaning scripts in cron.daily are run at 06:25 each day.

---

### Post by psusi on 2007-12-04
The files in /etc are for root jobs only.  Users register jobs to run as themselves by running crontab -e and supplying a proper time/job spec line.  man cron for more info.

Also writing a shell script to run a ruby script is kind of silly; just run the ruby script directly, which you can do as long as the script is +x and the first line is a shebang line pointing to the ruby interpreter.

---

