---
title: "Lubuntu: reboot-log-entries don´t seem to be correct"
date: 2018-08-28
forum: General Help
---

### Post by rosika on 2018-08-28
I´ve recently taken a look at my reboot-logs with  ```
last -x | grep reboot
``` :


    ```

    reboot   system boot  4.4.0-134-generi Tue Aug 28 12:20   still running
    reboot   system boot  4.4.0-134-generi Mon Aug 27 14:57   still running
    reboot   system boot  4.4.0-134-generi Mon Aug 27 12:36   still running
    reboot   system boot  4.4.0-134-generi Sun Aug 26 12:18   still running
    reboot   system boot  4.4.0-134-generi Sat Aug 25 13:22   still running
    reboot   system boot  4.4.0-133-generi Sat Aug 25 12:56 - 13:21  (00:25)
    reboot   system boot  4.4.0-133-generi Thu Aug 23 12:40 - 13:21 (2+00:41)
    reboot   system boot  4.4.0-133-generi Wed Aug 22 12:46 - 19:04  (06:17)
    reboot   system boot  4.4.0-133-generi Tue Aug 21 11:37 - 18:48  (07:11)

```

Here it occurred to me that the first entry is correct. Well, my system is running right now, so that´s o.k.


Yet the following two entries make no sense at all.


Mon Aug 27 up to Sat Aug 25: I shut down my computer as I always do.
A normal clean shutdown. Despite that fact there´s the entry "still running".
But not so with all the other preceding entries.


What strikes me as odd is the fact that this phenomenon can be seen since the point in time when I updated the system from kernel 4.4.0-133 to 4.4.0-134 .....


And  ```
last -x | grep shutdown
```  shows me the following:


    ```

    shutdown system down  4.4.0-133-generi Sat Aug 25 13:21 - 13:22  (00:00)
    shutdown system down  4.4.0-133-generi Wed Aug 22 19:04 - 12:40  (17:35)
    shutdown system down  4.4.0-133-generi Tue Aug 21 18:48 - 12:46  (17:57)
    shutdown system down  4.4.0-133-generi Sat Aug 18 19:02 - 12:02  (16:59)
    shutdown system down  4.4.0-133-generi Fri Aug 17 18:35 - 11:54  (17:18)

```

no new entry since the new kernel


Does anybody know what´s going on here?


Tnx a lot in advance.

Rosika


P.S.:


my system: Linux/Lubuntu 16.04.5 LTS, 64 bit

---

### Post by rosika on 2018-08-30
[COLOR=#242729][FONT=Arial]*****UPDATE*****
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Hi again.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I´m glad to tell that I somehow could get things straight again. But I really don´t know how exactly it worked out.

[/FONT][/COLOR](Background: Dual-boot installation: WIN 8.1 and Lubuntu)

[COLOR=#242729][FONT=Arial]What I did the day before yesterday was the following:
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]1.) I booted up WIN. I had a vague feeling that it could have something to do with it...... I realized that the boot process look longer that ususal.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]2.) It seemed that a reboot was pending as I got a message from avira (third party software, antivirus) which told me to reboot. That I did.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]3.) After a reboot I used WIN for a while and in the evening I performed a normal shutdown.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]4.) The next day (yesterday) I booted up Lubuntu and saw with last ```
-x | grep -E '(reboot)|(shutdown)'
```[/FONT][/COLOR] that nothing has changed. Well, I thought, that was to be expected.

5.) So I performed a normal shutdown and the booted up Lubuntu again.
Here are the results:```


last -x | grep -E '(reboot)|(shutdown)'
    reboot   system boot  4.4.0-134-generi Wed Aug 29 14:34   still running
    shutdown system down  4.4.0-134-generi Wed Aug 29 12:33 - 14:34  (02:01)
    reboot   system boot  4.4.0-134-generi Wed Aug 29 14:25 - 12:33  (-1:-51)
    reboot   system boot  4.4.0-134-generi Tue Aug 28 13:56 - 12:33  (22:37)
    reboot   system boot  4.4.0-134-generi Tue Aug 28 13:12 - 12:33  (23:21)
    reboot   system boot  4.4.0-134-generi Tue Aug 28 12:20 - 12:33 (1+00:13)
    reboot   system boot  4.4.0-134-generi Mon Aug 27 14:57 - 12:33 (1+21:36)
    reboot   system boot  4.4.0-134-generi Mon Aug 27 12:36 - 12:33 (1+23:57)
    reboot   system boot  4.4.0-134-generi Sun Aug 26 12:18 - 12:33 (3+00:15)
    reboot   system boot  4.4.0-134-generi Sat Aug 25 13:22 - 12:33 (3+23:11)
    shutdown system down  4.4.0-133-generi Sat Aug 25 13:21 - 13:22  (00:00)
    reboot   system boot  4.4.0-133-generi Sat Aug 25 12:56 - 13:21  (00:25)
    reboot   system boot  4.4.0-133-generi Thu Aug 23 12:40 - 13:21 (2+00:41)
    shutdown system down  4.4.0-133-generi Wed Aug 22 19:04 - 12:40  (17:35)
    reboot   system boot  4.4.0-133-generi Wed Aug 22 12:46 - 19:04  (06:17)
    shutdown system down  4.4.0-133-generi Tue Aug 21 18:48 - 12:46  (17:57)
    reboot   system boot  4.4.0-133-generi Tue Aug 21 11:37 - 18:48  (07:11)
    [...]

```


As can be seen there is a shutdown entry this time and only one still running entry. 


I really don´t know whether all this really had something to do with WIN and the fact that there was a reboot pending. After all it was just a wild guess. 
But somehow it worked out and the Lubuntu logs display the entries as would be expected.

Greetings
Rosika

---

