---
title: "Iowait 100% when apt update"
date: 2014-06-27
forum: General Help
---

### Post by navez_julien on 2014-06-27
Hello

I have webmin setup on my ubuntu 14.10 LTS

But when ubuntu or webmin check if update is available, i have always iowait at 100%

iotop

```
[COLOR=#29F914][FONT=Andale Mono] 4059 be/4 root        0.00 B/s  107.18 K/s  0.00 % 99.99 % perl -w /usr/bin/apt-show-versions -i[/FONT][/COLOR][COLOR=#29F914][FONT=Andale Mono]19404 be/7 root        0.00 B/s  107.18 K/s  0.00 % 99.99 % python3 /usr/lib/update-notifier/apt-check --human-readable[/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono]22471 be/4 root        0.00 B/s  107.18 K/s  0.00 % 99.75 % perl -w /etc/webmin/sysstats/sysstats.pl[/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono] 5702 be/4 root        0.00 B/s  103.35 K/s  0.00 % 97.92 % perl -w /usr/bin/apt-show-versions -i[/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono]20293 be/4 root        0.00 B/s  103.35 K/s  0.00 % 97.54 % python3 /usr/lib/ubuntu-release-upgrader/check-new-release -q[/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono]28413 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/u16:0][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono] 8192 be/4 fennec      0.00 B/s    0.00 B/s  0.00 %  0.00 % unity-panel-service --lockscreen-mode [gdbus][/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono]    1 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % init[/FONT][/COLOR]
[COLOR=#29F914][FONT=Andale Mono]    2 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthreadd][/FONT][/COLOR]



```

Can you see the problem thanks

---

### Post by rusia2 on 2014-08-01
I encountered exactly the same problem. also webmin setup on ubuntu 14.10 LTS
python3 /usr/lib/update-notifier/apt-check was eating up all my system resources and never stopped
I tried to google but with no success
So what I did just chmod /usr/bin/python3 0640
and then reboot

generally I must say that webmin sets up a lot of scheduled jobs eating up lots of system resources (and not all of them directly in cron)
so you can't disable it by simply switching off corresponding cronjobs

What I chose is just chmod /usr/bin/perl 0640 and then reboot to prevent webmin running its scripts
When I need webmin/virtualmin (which is very rarely) I chmod /usr/bin/perl 0755 then reboot and use webmin. then chmod perl 0640 and reboot again.
Now I realised that I have to chmod python 0640 as well

---

