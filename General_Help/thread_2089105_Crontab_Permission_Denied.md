---
title: "Crontab Permission Denied"
date: 2012-11-28
forum: General Help
---

### Post by KentAgent on 2012-11-28
I'm having problem with crontab when I'm running a script.
  My *sudo crontab -e* looks like this:
  ```

 05 00 * * * /opt/mcserver/backup.sh
 10 00 * * * /opt/mcserver/suspend.sh
 05 08 * * * /sbin/shutdown -r +1
 11 11 * * * /opt/mcserver/start.sh  <--- This isn't working 

``` And the *start.sh* looks like this: 

```
  
#!/bin/sh
screen java -d64 -Xincgc -Xmx2048M -jar craftbukkit.jar nogui   
```and have these permissions (ls -l output)
```
  -rwxr-xr-x 1 eve eve  72 Nov 24 14:17 start.sh   
```I can run the command from the terminal, either using sudo or not
  
```
./start.sh
```   But it wont start with crontab. If i do 

```
  grep -iR "start.sh" /var/log   
```I get the following output
```
  
/var/log/syslog:Nov 27 11:11:01 eve-desk CRON[5204]: (root) CMD (eve /opt/mcserver/start.sh)
 grep: /var/log/btmp: Permission denied
 grep: /var/log/lightdm/x-0-greeter.log: Permission denied
 grep: /var/log/lightdm/lightdm.log: Permission denied
 grep: /var/log/lightdm/x-0.log: Permission denied
   
```So my question is, why isn't it working?  And since my script run without using sudo, I don't necessarily need to put it in sudo crontab, am I right?
  [I]( and I'm using Ubuntu 12.10 )

[/I]Thanks in advance,
KentAgent

**Solved!**

Screen in my start script needed proper flags, so this worked:
```
screen -d -m java -d64 -Xincgc -Xmx2048M -jar craftbukkit.jar nogui
```

---

