---
title: "Bash script fails in /etc/cron.hourly but not as hourly scheduled crontab task"
date: 2018-10-30
forum: General Help
---

### Post by silverspr on 2018-10-30
Hello, I did search the forum for a solution but was not successful finding my scenario. 
I created a bash script pieced together of snippets from the internet and named the script tomcat_status.  The script behaves differently when run in cron.hourly than it does as an hourly scheduled crontab task or when run manually. 
The script under /etc/cron.hourly fails the first part of the if statement when tomcat is running.  Then tries to start tomcat and fails due to the already existing PID (which is supposed to happen I'm guessing). When the script is run as a crontab hourly scheduled task or run "manually" it works as expected.  What am I doing wrong, at first I thought it was due to the outputs, but that doesn't explain why the first part of the if statement fails under cron.hourly only?  Your help is appreciated.

#!/bin/bash
#check for tomcat PID
mypid=$(ps x | grep <full path to tomcat> | grep -v grep | awk '{ print $1 }')

if [ ! -z $mypid ]

then

    echo "Tomcat Running"

else

    echo "Tomcat Stopped"

    /bin/sh <full path to tomcat>/bin/startup.sh

fi

---

### Post by HermanAB on 2018-10-31
You have a grep piped into another grep - I'm sure that can be simplified.

Also, you have "print $1" which means you need to pass in a variable to the script somehow - rather make that a constant.

So, that first line is all suspect to me.  Simplify it and check every piece - break it into multiple lines and use variables that you can print and inspect.

---

### Post by spjackson on 2018-10-31
> **silverspr said:**
> 
```

mypid=$(ps x | grep <full path to tomcat> | grep -v grep | awk '{ print $1 }')

if [ ! -z $mypid ]

```

If there is more than 1 process that matches, then your if will fail with
```

[: too many arguments

```
and proceed to execute the else branch. Therefore it is safer to quote the variable:
```

if [ ! -z "$mypid" ]

```

However, that doesn't explain why the behaviour is different when run in different contexts. I can't think why that would be.

---

### Post by spjackson on 2018-10-31
> **HermanAB said:**
> 
Also, you have "print $1" which means you need to pass in a variable to the script somehow - rather make that a constant.

That's incorrect. When $1 appears inside a single-quoted string as used by the OP, it is not expanded by the shell. It is passed as is to awk where it has specific meaning and this usage is perfectly valid.

---

### Post by Doug S on 2018-10-31
> **spjackson said:**
> However, that doesn't explain why the behaviour is different when run in different contexts. I can't think why that would be.Neither can I. I made a similar version of the script and ran it manually and under /etc/cron.hourly, and it ran fine.

```
doug@s15:~$ [COLOR="#FF0000"]ls -l /etc/cron.hourly[/COLOR]
total 4
-rwxrwxrwx 1 root root 307 Oct 30 23:39 bla
doug@s15:~$
doug@s15:~$ [COLOR="#FF0000"]cat /etc/cron.hourly/bla[/COLOR]
#!/bin/bash
#check for tomcat PID
date >> /home/doug/temp_logrotate/zzzzz
mypid=$(ps x | grep /usr/sbin/dnsmasq | grep -v grep | awk '{ print $1 }')

if [ ! -z $mypid ]

then

echo "dnsmasq Running" >> /home/doug/temp_logrotate/zzzzz

else

echo "dnsmasq not running" >> /home/doug/temp_logrotate/zzzzz

fi

doug@s15:~$ [COLOR="#FF0000"]tail -20 /home/doug/temp_logrotate/zzzzz[/COLOR]
Tue Oct 30 23:47:29 PDT 2018  [COLOR="#FF0000"]<<< run manually as root[/COLOR]
dnsmasq Running
Tue Oct 30 23:47:50 PDT 2018  [COLOR="#FF0000"]<<< run manually as root[/COLOR]
dnsmasq Running
Wed Oct 31 00:17:01 PDT 2018
dnsmasq Running
Wed Oct 31 01:17:01 PDT 2018
dnsmasq Running
Wed Oct 31 02:17:01 PDT 2018
dnsmasq Running
Wed Oct 31 03:17:01 PDT 2018
dnsmasq Running
Wed Oct 31 04:17:01 PDT 2018
dnsmasq Running
Wed Oct 31 05:17:01 PDT 2018
dnsmasq Running
Wed Oct 31 06:17:01 PDT 2018
dnsmasq Running
Wed Oct 31 07:17:01 PDT 2018
dnsmasq Running

```

---

### Post by HermanAB on 2018-10-31
I think you should use the full search path for all spawned programs, including "/usr/bin/grep" and "/usr/bin/awk".

---

### Post by silverspr on 2018-11-01
Thank you everyone for all the excellent suggestions and help.  I've been debugging this as best I can...it is very odd how the script behaves so differently whether manually executed or from /etc/cron.hourly.  I've tried all your suggestions and nothing has made a difference.  I've mostly given up trying to capture the running pid of the tomcat instance I'm using.  I tried simplifying the code and thought for sure I had it licked: mypid=$(ps x | grep -m 1 tomcat | awk '{ print $1 }').   This worked manually and returned the same pid each time it was run, however installed to /etc/cron.hourly the script gave a different pid every hour it ran??  So I'm perplexed with trying to capture the running pid.  Instead I have resorted to capturing the pid from the catalina.pid file spawned when tomcat starts.  I had it in my head this method wouldn't be as foolproof, but in thinking it through, it should work as well as capturing the running pid.

Once again thank you all for your help, it gave me food for thought. @spjackson, I've wrapped the variable in quotes.

---

### Post by silverspr on 2018-11-02
Ironically, after one more attempt I've been able to get the running tomcat process by using a much simplified call: mypid=$(pgrep -f tomcat/conf).  Even more astonishing: the script works loaded to /etc/cron.hourly.  yayyy!!
Thanks again to everyone who helped with this.

---

