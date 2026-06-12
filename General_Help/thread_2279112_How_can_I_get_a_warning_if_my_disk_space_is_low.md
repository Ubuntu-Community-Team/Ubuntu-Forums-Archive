---
title: "How can I get a warning if my disk space is low?"
date: 2015-05-21
forum: General Help
---

### Post by rdh61 on 2015-05-21
Hi,

On two recent occasions I have had problems with computers becoming inoperable because the hard disks were full. Is there some way I can get a warning when disk space is running low?

Many thanks.

---

### Post by dino99 on 2015-05-21
System-monitor > File system show you the % used; but i'm not aware of a warning popup

---

### Post by v3.xx on 2015-05-21
You should get a warning.  Check to be sure housekeeping active.
[ATTACH=CONFIG]262104[/ATTACH]

Also check be sure its not something else filling up.
```
df -h
```

---

### Post by leunam12 on 2015-05-21
Why don't you just use conky or a screenlet?

---

### Post by Habitual on 2015-05-21
[http://aarvik.dk/simple-disk-usage-monitor-script-with-bash-and-mail/](http://aarvik.dk/simple-disk-usage-monitor-script-with-bash-and-mail/)

---

### Post by rdh61 on 2015-05-22
Thanks for that. I cannot find housekeeping in the directory tree of gconf-editor. Doesn't seem to be in Synaptic either. Where can I get it?

---

### Post by rdh61 on 2015-05-22
> **v3.xx said:**
> You should get a warning.  Check to be sure housekeeping active.
[ATTACH=CONFIG]262104[/ATTACH]



Thanks for that. I cannot find housekeeping in the directory tree of gconf-editor. Doesn't seem to be in Synaptic either. Where can I get it?

---

### Post by rdh61 on 2015-05-22
> **leunam12 said:**
> Why don't you just use conky or a screenlet?

Thanks for the suggestions. Screenlets seem too complicated/advanced for me. Conky seems annoying. It takes up the top left quarter of my screen and I can't find a way of moving or minimising it. When I click (right or left) it or any other part of the screen it disappears and I can't get it back again!

---

### Post by rdh61 on 2015-05-22
> **Habitual said:**
> [http://aarvik.dk/simple-disk-usage-monitor-script-with-bash-and-mail/](http://aarvik.dk/simple-disk-usage-monitor-script-with-bash-and-mail/)

Thanks, looks interesting. But I didn't get very far. I failed on this:

"Choose the partition your want to monitor and grep that value, and print out 5th row with awk: 

```
$ df -h | grep '/dev/simfs' | awk {'print $5'}


```

 This will return the percentage used on the chosen partition (in my case "/dev/simfs"): 
24%"

But what I got was:

```
robert@robert-P4i65GV:~$ dh -f | grep '/dev/sda5' | awk {'print $5'}
dh: No compatibility level specified in debian/compat
dh: This package will soon FTBFS; time to fix it!
dh: cannot read debian/control: No such file or directory
```

Which is as good as Greek to me!

---

### Post by vasa1 on 2015-05-22
> **rdh61 said:**
> ... Conky seems annoying. It takes up the top left quarter of my screen and I can't find a way of moving or minimising it. When I click (right or left) it or any other part of the screen it disappears and I can't get it back again!
A lot of people here can help you set up conky just the way you like it. I have my Conky sharing a single row with tint2 at the top of the screen.

Habitual's link to a cron job maybe suitable if you prefer a periodic on-screen notification.

---

### Post by vasa1 on 2015-05-22
> **rdh61 said:**
> 
```
robert@robert-P4i65GV:~$ dh -f | grep '/dev/sda5' | awk {'print $5'}
dh: No compatibility level specified in debian/compat
dh: This package will soon FTBFS; time to fix it!
dh: cannot read debian/control: No such file or directory
```

Which is as good as Greek to me!

You should have used **df -h**. Simple typo there.

---

### Post by Elfy on 2015-05-22
> **rdh61 said:**
> Thanks, looks interesting. But I didn't get very far. I failed on this:

"Choose the partition your want to monitor and grep that value, and print out 5th row with awk: 

```
$ df -h | grep '/dev/simfs' | awk {'print $5'}


```

 This will return the percentage used on the chosen partition (in my case "/dev/simfs"): 
24%"

But what I got was:

```
robert@robert-P4i65GV:~$ dh -f | grep '/dev/sda5' | awk {'print $5'}
dh: No compatibility level specified in debian/compat
dh: This package will soon FTBFS; time to fix it!
dh: cannot read debian/control: No such file or directory
```

Which is as good as Greek to me!
How often do you use a terminal - you could have the result echo there when you open it if you want.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=262120&d=1432292565[/IMG]

---

### Post by Mike_Walsh on 2015-05-22
You say Screenlets seem too hard to set up. I find them quite easy; mind you, it's the old saw about 'once you've done something'...you know how to do it next time. **Did** take a bit of figuring out the first time round...

I'm not using them currently, so can't give you a screenshot to demonstrate.....but the 'Disk Space' Screenlet can be reduced down to a small window about 1" high, by about 3" wide, and can sit unobtrusively in a corner of your screen where it won't get in the way.

You **can** reduce it further than this, but it gets a wee bit difficult to read (unless your eyesight is better than mine, which wouldn't be hard!)


Regards,

Mike. ;)

---

### Post by HermanAB on 2015-05-22
You can also use quota:
[https://www.howtoforge.com/tutorial/linux-quota-ubuntu-debian/](https://www.howtoforge.com/tutorial/linux-quota-ubuntu-debian/)

---

### Post by Habitual on 2015-05-22
> **rdh61 said:**
> Thanks, looks interesting. But I didn't get very far. I failed on this:
```
$ df -h | grep '/dev/simfs' | awk {'print $5'} That's just an example.
Yours is likely something like [CODE]df -h | grep/dev/sda***x*** | awk {'print $5'}
``` Where ***x*** would be one partition, (likely sda1). There can be > 1 on a disk, so 
open a terminal command and paste here the results of:
```
sudo df -hT
```

You said "disks", so let us know which in the ```
df -hT 
```output you are concerned about.

---

### Post by rdh61 on 2015-05-22
> **vasa1 said:**
> A lot of people here can help you set up conky just the way you like it. I have my Conky sharing a single row with tint2 at the top of the screen.


Thank you. Looks good. How can I achieve something similar with the Lubuntu task bar at the bottom of the screen?

---

### Post by Keith_Helms on 2015-05-22
What kind of warning were you looking for?  A screen message?   An email?  

If you just want a screen message that pops up every now and then to "nag" you, you could try the following script:

```
#!/bin/bash

WARNPCT=75
CHECKSECONDS=300
IFS=$'\n'
while [ true ]
do
    fsinfo=`df --output=pcent,target`
    skipfirst=y

    for fsline in $fsinfo
    do
        # Skip over header line
        if [ "$skipfirst" == "y" ]
        then
            skipfirst=n
            continue
        else
            fspct=${fsline:0:4}
            ckpct=${fspct:0:3}
            ckpct="${ckpct#"${ckpct%%[![:space:]]*}"}"
            fsystem=${fsline:5}
            if [ $ckpct -ge $WARNPCT ]
            then
                /usr/bin/notify-send "$fsystem is at $fspct"
            fi
        fi
    done
    sleep $CHECKSECONDS
done
```

Set the percentage threshold you want it to start warning you and the number of seconds you want it to wait between checking in the 2 variables at the top of the script.  Then you can add the script to your autostart applications and it will run in the background.

---

### Post by rdh61 on 2015-05-23
> **Habitual said:**
> That's just an example.
Yours is likely something like ```
df -h | grep/dev/sda***x*** | awk {'print $5'}
``` Where ***x*** would be one partition, (likely sda1). There can be > 1 on a disk, so 
open a terminal command and paste here the results of:
```
sudo df -hT
```

You said "disks", so let us know which in the ```
df -hT 
```output you are concerned about.

```

robert@robert-P4i65GV:~$ df -hT
Filesystem            Type      Size  Used Avail Use% Mounted on
/dev/sda5             ext4      151G   60G   84G  42% /
none                  tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev                  devtmpfs  738M  4.0K  738M   1% /dev
tmpfs                 tmpfs     151M  1.3M  149M   1% /run
none                  tmpfs     5.0M     0  5.0M   0% /run/lock
none                  tmpfs     751M  2.1M  749M   1% /run/shm
none                  tmpfs     100M   20K  100M   1% /run/user
/home/robert/.Private ecryptfs  151G   60G   84G  42% /home/robert
/dev/sdc1             vfat      7.4G  239M  7.1G   4% /media/robert/3B4A-426B
/dev/sdb1             vfat       75G   14G   62G  18% /media/robert/Backup Disk
```

I am concerned about sda5 (which, BTW, I have now emptied considerably).

```

robert@robert-P4i65GV:~$ df -h | grep/dev/sda5 | awk {'print $5'}
bash: grep/dev/sda5: No such file or directory
```

---

### Post by Elfy on 2015-05-23
> dh -h

this should be df -h

You were given the same info in post #11

---

### Post by rdh61 on 2015-05-23
Thanks Mike, I'll look into it.


> **Mike_Walsh said:**
> You say Screenlets seem too hard to set up. I find them quite easy; mind you, it's the old saw about 'once you've done something'...you know how to do it next time. **Did** take a bit of figuring out the first time round...

I'm not using them currently, so can't give you a screenshot to demonstrate.....but the 'Disk Space' Screenlet can be reduced down to a small window about 1" high, by about 3" wide, and can sit unobtrusively in a corner of your screen where it won't get in the way.

You **can** reduce it further than this, but it gets a wee bit difficult to read (unless your eyesight is better than mine, which wouldn't be hard!)


Regards,

Mike. ;)

---

### Post by rdh61 on 2015-05-23
> **Elfy said:**
> this should be df -h

You were given the same info in post #11

Sorry, I have been a little confused.

robert@robert-P4i65GV:~$ df -h | grep/dev/sda5 | awk {'print $5'}
bash: grep/dev/sda5: No such file or directory

---

### Post by Elfy on 2015-05-23
> **rdh61 said:**
> Sorry, I have been a little confused.

robert@robert-P4i65GV:~$ df -h | grep/dev/sda5 | awk {'print $5'}
bash: grep/dev/sda5: No such file or directory

```
df -h | grep/dev/sda5 | awk {'print $5'}
```

Try 

df -h | grep '/dev/sda5' | awk {'print $5'}

When there is an error - there is usually a pointer as to what's wrong. Here you missed out the space between grep and /dev/sda5

In this case it's telling you that there's not a file or directory called grep/dev/sda5 

Don't worry about confusion - we've all been there at some point ;)

---

### Post by rdh61 on 2015-05-23
Eureka...

```
robert@robert-P4i65GV:~$ df -h | grep '/dev/sda5' | awk {'print $5'}
42%
```

Thanks. I'll now get back to [http://aarvik.dk/simple-disk-usage-monitor-script-with-bash-and-mail/](http://aarvik.dk/simple-disk-usage-monitor-script-with-bash-and-mail/)

---

### Post by Elfy on 2015-05-23
> **rdh61 said:**
> Eureka...

```
robert@robert-P4i65GV:~$ df -h | grep '/dev/sda5' | awk {'print $5'}
42%
```

Thanks. I'll now get back to [http://aarvik.dk/simple-disk-usage-monitor-script-with-bash-and-mail/](http://aarvik.dk/simple-disk-usage-monitor-script-with-bash-and-mail/)

Excellent - good luck.

Bear in mind that spaces mean something and that uppercase and lowercase are different in linux. Both things I scratched my head over back when ...

---

### Post by rdh61 on 2015-05-23
Or, better, how can I achieve this?


> **Elfy said:**
> How often do you use a terminal - you could have the result echo there when you open it if you want.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=262120&d=1432292565[/IMG]

---

### Post by Elfy on 2015-05-23
> **rdh61 said:**
> Or, better, how can I achieve this?

Put it in .bashrc

Edit that file - then add the command at the end.

Then when you start a terminal it'll show you that. 

I assume you don't mean the kernel version ...

---

### Post by rdh61 on 2015-05-23
Thanks to everybody. In the end I've gone for Keith_Helms' script. It works, it's simple, unobtrusive and it's exactly what I wanted! But I've learned a lot from everybody else's replies, too.


> **Keith_Helms said:**
> What kind of warning were you looking for?  A screen message?   An email?  

If you just want a screen message that pops up every now and then to "nag" you, you could try the following script:

```
#!/bin/bash

WARNPCT=75
CHECKSECONDS=300
IFS=$'\n'
while [ true ]
do
    fsinfo=`df --output=pcent,target`
    skipfirst=y

    for fsline in $fsinfo
    do
        # Skip over header line
        if [ "$skipfirst" == "y" ]
        then
            skipfirst=n
            continue
        else
            fspct=${fsline:0:4}
            ckpct=${fspct:0:3}
            ckpct="${ckpct#"${ckpct%%[![:space:]]*}"}"
            fsystem=${fsline:5}
            if [ $ckpct -ge $WARNPCT ]
            then
                /usr/bin/notify-send "$fsystem is at $fspct"
            fi
        fi
    done
    sleep $CHECKSECONDS
done
```

Set the percentage threshold you want it to start warning you and the number of seconds you want it to wait between checking in the 2 variables at the top of the script.  Then you can add the script to your autostart applications and it will run in the background.

---

