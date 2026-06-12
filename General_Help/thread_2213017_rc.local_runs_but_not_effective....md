---
title: "rc.local runs but not effective..."
date: 2014-03-24
forum: General Help
---

### Post by diyhouse on 2014-03-24
I run the following rc.local file

------------------------------
#!/bin/sh -e


#
SNIP out comments
#
PATH=/sbin:/usr/sbin:/bin:/usr/bin


ir-keytable -c -p JVC,LIRC -w /etc/rc_keymaps/logitech650.map > /var/log/ir-table.txt 2>&1


exit 0
------------------------------
Now, I know the script runs from the log file output.... but if I run irw when system has finished booting,.. the key table is not recognised... 

I assume I am missing something about the "environment" but my knowledge runs out here, is anyone able to spread in further light/ideas on the subject pls,.. and hopefully a fix.

Many thanks

---

### Post by Irihapeti on 2014-03-26
*Thread moved to **General Help**.*

Not an Ubuntu One question.

---

### Post by varunendra on 2014-03-26
> **diyhouse said:**
> ir-keytable -c -p JVC,LIRC -w /etc/rc_keymaps/logitech650.map > /var/log/ir-table.txt 2>&1

Does this code work if you run it manually?

Some things may require to be run AFTER a particular stage in boot sequence. In that case, you may need to give it some time to let the system get ready to accept it.

Now adding a 'sleep' time to rc.local file is not such a good idea. So if this works, you may try adding your code to a script (with added 'sleep' time), then add a line in rc.local file to run that script as a 'Background' process by adding [s]"&&"[/s] **&** after it.

For example, something like this -
```
[s]/home/**[COLOR="#B22222"]diyhouse[/COLOR]/[COLOR="#0000CD"]myscript.sh[/COLOR]** **[COLOR="#FF0000"]&&[/COLOR]**[/s] *[COLOR="#0000CD"]# should be single '&' as below[/COLOR]*
/home/**[COLOR="#B22222"]diyhouse[/COLOR]/[COLOR="#0000CD"]myscript.sh[/COLOR]** &
```
..where the script **[COLOR="#0000CD"]myscript.sh[/COLOR]** is located in the home directory of user **[COLOR="#B22222"]diyhouse[/COLOR]**.

And where the contents of script **[COLOR="#0000CD"]myscript.sh[/COLOR]** would be -
```
#!/bin/bash

sleep 20
ir-keytable -c -p JVC,LIRC -w /etc/rc_keymaps/logitech650.map > /var/log/ir-table.txt 2>&1
```
Of course make the script executable, and adjust the timeout (20) as required. On slow systems, it may need to be increased, on superfast ones where it takes only seconds to load, it may well be stepped down to just 2-3 seconds.

Try that, and let us know if it works.

---

### Post by diyhouse on 2014-03-27
Sorted,.. placed main command into separate script file,.. including sleep, changed rc.local to point to new script.

And all works fine,..   many thanks,....
sleep set to 5Seconds
one little question,... why double ampersand ie && at line end in rc.local,.. I understand a single & tells the script to process the command as a background task,.. and to not halt main program execution,... so why double &&

again many thanks for help
Rgds

---

### Post by Dave_L on 2014-03-27
I think the double ampersand in that post is a typo, and it should be a single ampersand.

---

### Post by varunendra on 2014-03-27
> **Dave_L said:**
> I think the double ampersand in that post is a typo, and it should be a single ampersand.

Umm.. you are right that it should be a single ampersand, but I have to admit that it was not a typo in my post. I had **_wrongfully_** thought that it has to be a double ampersand while overlooking the fact that it simply translates into a logical 'and'.

Thanks for questioning it **diyhouse**, and thanks for correcting me **Dave**! :)

---

