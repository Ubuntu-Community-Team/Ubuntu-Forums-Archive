---
title: "interpreting the syslog"
date: 2008-05-03
forum: General Help
---

### Post by prezbedard on 2008-05-03
The one thing I still can not get a grip on is interpreting the syslog. For the most part the m$ eventlog gives you an idea on what caused a problem that doesn't seem to be true with the Linux syslog. I believe google earth was the reson my system locked up a few minutes ago but I can not determine that from the syslog probably because I still don't know how to interpret it. Are there any guides or how-to's? Also this might be something that should be addressed  in making Linux more user friendly is to make the syslog less cryptic. I am an advanced computer user so if I find it cryptic then I can only imagine what a typical user sees.

Thanks!

---

### Post by p_quarles on 2008-05-03
Moved to General Help.

The equivalent of the event log in Linux would be dmesg. This is both a command and a log file in /var/log. Check that to see if you can find what you are looking for.

---

### Post by ibuclaw on 2008-05-03
No easy way, sorry. You just really need to know what you are looking for.

Though the structure from left to right is easy enough.

ie:
```
May  3  15:37:31  fredbuntu  dhclient: wifi0: unknown hardware address type 801
```
In order:
[LIST]
[*]Month (**May**)
[*]Day (**3**)
[*]Time in H:M:S (**15:37:31**)
[*]The Machine Name (**fredbuntu**)
[*]The Application (**dhclient**)
[*]The Process ID, if ran under one would show (**dhclient[1234]**) instead.
[*]The Module ran under that Application (**wifi0**)
[*]The Error Message or Debug Report (**Blah Blah**)
[/LIST]

As I said, you have to know what you are looking for in order to determine or breakdown anything. (Knowing the exact time helps too...)

In the command-line, I personally use **grep** to remove all the garbage that I don't want to read so I can focus on **ONE** single task and how that task progressed on loading.

ie:
```
:-$ cat /var/log/syslog | grep -i dhclient
May  3 15:37:42 fredbuntu dhclient: wifi0: unknown hardware address type 801
May  3 15:37:43 fredbuntu dhclient: wifi0: unknown hardware address type 801
May  3 15:37:43 fredbuntu dhclient: DHCPREQUEST of 192.168.1.3 on ath0 to 255.255.255.255 port 67
May  3 15:37:45 fredbuntu dhclient: DHCPACK of 192.168.1.3 from 192.168.1.1
May  3 15:37:45 fredbuntu dhclient: bound to 192.168.1.3 -- renewal in 38242 seconds.
```
All log files are found in the /var/log/ directory.

If you know the time of which the break or freeze happened. You could use this sort of seeking method too.

```
cat /var/log/* | grep 15:37 
```
That will show up all log files with messages from that time.
Although alot can happen in a minute, but it cuts down the work you have to do.

[EDIT]
If you prefer reading from a GUI text editor, then you can save the screen output to a file too.

To re-iterate the previous example:
```
cat /var/log/* | grep 15:37 > ~/syslog.output
```
That will save it to a file in your /home/username/ directory as "syslog.ouput"
The use of the "**>**" symbols means that the file will be overwritten each time you use that command.

If you'd rather want it to append a file (add text to) without removing the data already there use the "**>>**" symbol instead.

Regards
Iain

---

### Post by prshah on 2008-05-03
> **prezbedard said:**
> The one thing I still can not get a grip on is interpreting the syslog. For the most part the m$ eventlog gives you an idea on what caused a problem that doesn't seem to be true with the Linux syslog. 

I agree that the syslogs are cryptic at times, but I find them a lot more useful than Window's event log.

That said, I have found that using the System-Administration-System Logs option is much better for cases like you mention, but nothing beats old fashioned grep and tail when you need to do something else.

---

