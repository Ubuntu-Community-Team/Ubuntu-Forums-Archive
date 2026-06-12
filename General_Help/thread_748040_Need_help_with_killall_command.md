---
title: "Need help with killall command"
date: 2008-04-07
forum: General Help
---

### Post by JSpaceCadet on 2008-04-07
Hello all,
I am working on a new program and playing with different ways to run it.  (some work, some don't ;-) ).
I need to find a quick way to kill off all of the processes left over even though many are in different forms.  It seems like the "killall" command is ideal for this but I'm having a lot of trouble with it not accepting my names either as exact or as regular expressions.

Can someone please take a look at these variants and make some concrete suggestions about how to go about this?

Here is the output of ps for the processes that are left:

[FONT="Courier New"][SIZE="1"]_***talker@talker:~$ ps -elf|grep "timetalk"|grep -v "grep"***_

0 S talker    5384     1  0  78   0 -  3559 -      Apr06 ?        00:00:00 php /var/www/timetalk.php
0 S talker    5835     1  0  78   0 -  3560 -      Apr06 ?        00:00:00 php /var/www/timetalk.php
0 S talker    5872     1  0  78   0 -  3559 -      Apr06 ?        00:00:00 /usr/bin/php /var/www/timetalk.php
0 S talker    5902     1  0  78   0 -  3559 -      Apr06 ?        00:00:00 /usr/bin/php /var/www/timetalk.php >timetalk.log
0 S talker    6241  5437  0  75   0 -   707 -      Apr06 pts/0    00:00:00 tail -f timetalk.log
0 S talker    6400     1  0  78   0 -  3559 -      Apr06 ?        00:00:00 php timetalk.php
talker@talker:~$ 
[/SIZE][/FONT]

Thank you for your help coming up with some ideas.  I'm trying to use this KISS principle here bug getting further away by the minute.

Joe

---

### Post by justleen on 2008-04-07
```

echo `ps -ef|grep "timetalk"|grep -v "grep"  | awk 'NR != 1 {print $2}'`

```

something like that? (replace echo will kill when your sure of the output)

---

### Post by JSpaceCadet on 2008-04-07
Hi justleen,
For some reason that command is missing the top process - #5384.  It is in the process list if I take off all of the "awkable" ;-) parts.  I don't know enough (read "anything") about awk to know what is making this happen.  Can you help?

Joe

---

### Post by JSpaceCadet on 2008-04-07
Hi again,
Well, I decided to give something a try.  Here is your original suggestion:

[FONT="Courier New"]echo `ps -ef|grep "timetalk"|grep -v "grep"  | awk 'NR != 1 {print $2}'`[/FONT]

I wondered if the "1" after 'NR!=1..." was an "array"/line index and if maybe 1 should be valid but 0 be invalid.  So I changed this to:

[FONT="Courier New"]echo `ps -ef|grep "timetalk"|grep -v "grep"  | awk 'NR != 0 {print $2}'`[/FONT]

and joila, it worked and gave me the correct first and last PIDs.

Please take a look and see if I made a valid change.

Thanks a bunch!

Joe

---

### Post by ghostdog74 on 2008-04-07
don't have to use that many greps. Use awk instead. 
```

ps -eo pid,args | awk '$2 ~ /timetalk/{ cmd="kill -9 "$1; system(cmd)}'

```

---

