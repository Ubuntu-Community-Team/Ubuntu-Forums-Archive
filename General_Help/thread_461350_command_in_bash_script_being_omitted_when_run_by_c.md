---
title: "command in bash script being omitted when run by cron"
date: 2007-06-01
forum: General Help
---

### Post by lhomme on 2007-06-01
I have made a very simple bash script that adds the output of 3 commands to a file.  When I run the script from a terminal it does exactly what it's supposed to, when I have cron run the script periodically (every 5 min for testing purposes) the 2nd command is omitted from my output file.

the bash script:
```
#!/bin/bash
# Jared McGee

DATE=$(date +"%T   %A %B %d, %Y")
echo $DATE >> $HOME/.davfs2/ifconfig.txt
ifconfig >> $HOME/.davfs2/ifconfig.txt
uptime >> $HOME/.davfs2/ifconfig.txt
cp $HOME/.davfs2/ifconfig.txt /mnt/OUwebdav/public_html/ifconfig.txt
cp $HOME/.davfs2/ifconfig.txt $HOME/Desktop/ifconfig.txt
rm $HOME/.davfs2/ifconfig.txt

exit
```


the output file when run from a terminal:
```
15:48:32 Friday June 01, 2007
eth0      Link encap:Ethernet  HWaddr 00:07:E9:60:FD:EF  
******stuff deleted for the sake of space********
          Interrupt:201 Base address:0xc000 

 15:48:32 up 134 days, 16:28,  3 users,  load average: 0.42, 0.25, 0.24
```


the output file when run by cron:
```
15:45:01 Friday June 01, 2007
 15:45:01 up 134 days, 16:24,  3 users,  load average: 0.40, 0.29, 0.25
```


I added the job to crontab from my normal user account

```
~$ crontab -l
01,05,10,15,20,25,30,35,40,45,50,55 * * * * /home/jmcgee/.davfs2/upload-ifconfig.sh
```


I really don't know a lot about what I'm doing and have only got this far by reading lots of tutorials etc. so be gentle.
I'm still using Ubuntu 6.06 (and don't want to deal with upgrading until school is over) and v3 of cron

---

### Post by hillbilly on 2007-06-01
Try specifying the full path for the date executable. ie. /usr/bin/date e.g.
> DATE=$(/usr/bin/date +"%T   %A %B %d, %Y")

if absolute path doesn't work with $() then try
> DATE=`/usr/bin/date +"%T   %A %B %d, %Y"`

---

### Post by lhomme on 2007-06-01
The problem isn't with the date command, it's with the ifconfig command.
When cron runs the script there is not output from ifconfig.

I'm wondering now if my problem is that cron or crontab isn't allowed to run the command ifconfig.  I'm looking into this and will post back what I figure out, but someone who knows more about cron may just be able to see the problem.

---

### Post by lhomme on 2007-06-01
Oh, ok I got it.  using the same idea hillbilly said about using the full path for date, but it wasn't date, it was the full path for ifconfig (/sbin/ifconfig).
I just changed my script to this:
```
#!/bin/bash
# Jared McGee

DATE=$(date +"%T   %A %B %d, %Y")
echo $DATE >> $HOME/.davfs2/ifconfig.txt
/sbin/ifconfig >> $HOME/.davfs2/ifconfig.txt
uptime >> $HOME/.davfs2/ifconfig.txt
cp $HOME/.davfs2/ifconfig.txt /mnt/OUwebdav/public_html/ifconfig.txt
cp $HOME/.davfs2/ifconfig.txt $HOME/Desktop/ifconfig.txt
rm $HOME/.davfs2/ifconfig.txt

exit
```

Thanks for the help

---

