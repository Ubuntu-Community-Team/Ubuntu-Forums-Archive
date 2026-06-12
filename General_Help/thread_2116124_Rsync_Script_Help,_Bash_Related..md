---
title: "Rsync Script Help, Bash Related."
date: 2013-02-14
forum: General Help
---

### Post by Roasted on 2013-02-14
Hello! I'm trying to write a script to run an rsync command. I've used an rsync script for backing up my stuff to a file server many times before, but it's been a super simple script. Now I want to change it a bit by adding some kdialog/zenity GUI info boxes. The curve ball is I want to ensure that it's working accurately. I will be setting up the script to either use kdialog or zenity depending whether it's Unity or KDE (quite an even split here). 

Here's what I have so far:

```
#!/bin/bash
rsync -a /home/jason/ jason@192.168.1.100:/media/storage/jason/
if [ $? -eq 0 ]; then
kdialog --msgbox "Backup Complete"
else
kdialog --msgbox "Backup Failed"
fi
exit
```

Is this right? I want to make sure that if rsync reports 0, aka a success, it reports Backup Complete, whereas a failure (1) would be Backup Failed...

---

### Post by lordievader on 2013-02-15
You can make use of "&&".
For example:
```
#!/bin/bash
rsync -a /home/jason/ jason@192.168.1.100:/media/storage/jason/&& Completed=1
if [ $Completed == 1 ]; then
    kdialog --msgbox "Backup Complete"
else
    kdialog --msgbox "Backup Failed"
fi

```

The command after the "&&" is only run when the previous command completed successfully.

Hope this helps,
-lordievader.

---

### Post by schragge on 2013-02-15
I'd even rewrite it like this
```

#!/bin/bash
rsync -a /home/jason/ jason@192.168.1.100:/media/storage/jason/ &&
  Status=Complete || Status=Failed
kdialog --msgbox "Backup $Status"

```

---

### Post by papibe on 2013-02-15
Hi Roasted.

Here are my thoughts

rsync is very reliable, specially over a LAN (as this seems ). In case of a problem, almost always, it can be resolve by running the same rsync command again.

With that in mind, I would use this skeleton:
```
#!/bin/bash 
...
rsync -av ...
while [  $? -ne 0 ]; do
    ...
    rsync -av ...
done
```
Now, that goes to the extreme by assuming that rsync eventually will get it right. That wouldn't be right. I think a good compromise would be to give rsync a predetermined number of trials:
```
#!/bin/bash 
[COLOR="Blue"]# Initializing[/COLOR]
count=1      [COLOR="Blue"]# counter[/COLOR].
NTRIALS=3    [COLOR="Blue"]# number of trials[/COLOR].

[COLOR="Blue"]# Try rsync until successful or number of trials reached.[/COLOR]
rsync -av ...
while [  $? -ne 0 &&  $count -lt $NTRIALS ]; do
    ...
    count=$((count+1))
    rsync -av ...
done

[COLOR="Blue"]# Check if the cycle ended because of rsync's success or number of trials reached.[/COLOR]
if [ $? -eq 0 ]; then
    kdialog --msgbox "Backup Completed."
else
    kdialog --msgbox "Backup Failed."
fi

```
Another consideration: since you are bringing to your attention the case of a failed rsync using kdialog, you may want to the log rsync activities with log option:
```
rsync -a --log-file=/path/to/log  ...
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by schragge on 2013-02-16
@**papibe**. There are two typos in your code. [highlight]Edit[/highlight]: corrected.

But since it's bash, I guess we can use some [color=green]bashisms[/color], too ;). 
```

#!/bin/bash 
[color=blue]# Initializing[/color]
count=3      [color=blue]# counter.[/color]
status=Failed

[color=blue]# Try rsync until successful or number of trials reached.[/color]
while [color=green]let count--[/color]; do
    ...
    rsync -av ... && status=Completed && break
done

kdialog --msgbox "Backup $status"

```

---

### Post by papibe on 2013-02-16
Thanks schragge :D

---

