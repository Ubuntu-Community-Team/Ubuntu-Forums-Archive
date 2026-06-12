---
title: "compare files and delete the older ones"
date: 2018-01-05
forum: General Help
---

### Post by atux on 2018-01-05
I have a folder in my system(ubuntu server) that gets synchronized with work by using wget. Files are in the following format and once downloaded they  will be something like  A156.0.1.x, A156.0.y, A156.0.z, A156.0.a,  A156.0.b. All files are created at once in my office and all have the  same time and date. Rsync or any other connection to the office is not  permitted.  I am synchronizing 4 times a day and there is not a pattern of how often  the files will be created. There might not be a change in the folders  for a couple of weeks or it might be 10 times in a day. once the new  file created it will be something like A156.1.[a,b,x,y,z]. Each file is  huge (~500MB) So i am ending with the in my system having more than one set of files  (5) and i have in total 10 files*500MB=do the maths! is there any easy script that it will run by cron and check frequently  the folder and delete the older files? So i will end up only with the  latest set of 5 ones. i could run something like delete files that are  older than 5 days, but we are never sure when the next set of files will  get created. 
```
find /path/to/files* -mtime +5 -exec rm {} \;
```
So in general it will be compare all files and delete the older ones.

---

### Post by sisco311 on 2018-01-05
Hi, atux!

Check out BashFAQ #3 for some examples on how to find the `oldest/newest' file in a dir (link in my signature).

It would be good if you could share more details. Do you have control about how the files are named on the server? What command are you using to download them? Maybe we can find a better way to accomplish what you want to do.

---

### Post by atux on 2018-01-05
Hi. Thanks a lot for the replies.
On my home server i am issuing the following:
```
wget -nc -nd --no-check-certificate --user atux --password null -r -np "https://3.3.3.3/folderA" -A "*.tar.gz" 
```

At the moment i run manually this script and i delete the older files by hand. I would like to automate that and run by script every 1 hour. In case there are newer files, download them, delete the old files and keep only the newer files.
Regarding the naming all of them are in format A156.0.**1**.x. Where x is an extension of the file and then tar.gz.(eg doc.tar.gz), then the 1(in bold) is the sequence number that changes in every production. Each production could be once every 3 weeks or 5 in a day, it is based on the integration that is been done.
any ideas on how to script that please?

---

### Post by HermanAB on 2018-01-05
Logrotate can do that for you.  It is already installed and running.  Configure it in /etc/logrotate.conf.

---

### Post by atux on 2018-01-08
I am afraid i did not find how to make logrotate work for my situation.

---

### Post by HermanAB on 2018-01-08
Here is a tutorial:  [https://www.thegeekstuff.com/2010/07/logrotate-examples](https://www.thegeekstuff.com/2010/07/logrotate-examples)

Logrotate can periodically look at a folder and do something to files that are old, e.g. compress and/or delete them.  It is easy to use, and it works.  It is normally used to manage log files in /var/log, but it can work on any files in your system.

---

### Post by atux on 2018-01-09
```
hi. i did the following: 
cat /etc/logrotate.conf
weekly
rotate 4
create
include /var/www/html/A
{
hourly
    minsize 1M
    create 0664 root utmp
    rotate 1
}
```

but unfortunately i did not manage anything at all.  the folder is /var/www/html/A and it has files in the following ending to .tar.gz. I would like to keep only the latest by date and time and delete all the rest. Files size ranging from 1-2GB.

---

### Post by HermanAB on 2018-01-09
Hmm, you may need to restart logrotate to make it reread the configuration file.

It is several years since I last played with logrotate, so I cannot help much off the top of my head.  I would need to go and read the documentation again myself, but it certainly can do what you need.  After all, it is the tool that manages your system and keeps the disk from filling up with logs.  It may just need some gentle persuasion though...

---

### Post by atux on 2018-01-09
i did restart the system but i did not manage to make it work for me.

---

### Post by sisco311 on 2018-01-09
Hi, and sorry for the delay.

So if I understand it correctly, on the server side you have 5 type of (tar.gz) files: .x, .y, .z, .a and .b

Each has a uniform prefix *165.0* and an increasing sequence number *1,2,3...*.

And on the client side you would like to have a copy of each type with the highest sequence number. 

Is that right? If not please post more details and examples.

---

### Post by atux on 2018-01-10
> **sisco311 said:**
> Hi, and sorry for the delay.

So if I understand it correctly, on the server side you have 5 type of (tar.gz) files: .x, .y, .z, .a and .b

Each has a uniform prefix *165.0* and an increasing sequence number *1,2,3...*.

And on the client side you would like to have a copy of each type with the highest sequence number. 

Is that right? If not please post more details and examples.

Yes, i got this scenario.
Do you have any clues on how to achieve this? I need it to check frequently through cronjob, eg every hour.

---

### Post by untrustytahr on 2018-01-10
So if I understand you correctly, you have a directory with files such as:


```
A156.0.1.doc.tar.gz
A156.0.1.pdf.tar.gz
A156.0.1.xml.tar.gz
A156.0.1.xlc.tar.gz
A156.0.1.img.tar.gz
A156.0.2.doc.tar.gz
A156.0.2.pdf.tar.gz
A156.0.2.xml.tar.gz
A156.0.2.xlc.tar.gz
A156.0.2.img.tar.gz
A156.0.3.doc.tar.gz
A156.0.3.pdf.tar.gz
A156.0.3.xml.tar.gz
A156.0.3.xlc.tar.gz
A156.0.3.img.tar.gz

```

and at any given time, you only want the 5 most recent files?

If the incremental sets (i.e A156.0.1*, A156.0.2*, A156.0.3* etc.) have different creation times, how about something like:

```
 ls -t| tail -n+6|xargs rm -f
```

If you remove the "|xargs rm -f"  it will display the files that will be removed if you want to verify be doing.

You need to be careful parsing 'ls', but it might get you in the right direction if I understand the problem correctly.

---

### Post by sisco311 on 2018-01-10
But if you delete the old files, then wget will re-download them when you run it next time. Right?

Unfortunately I can't think of an easy/reliable way to get only the file names from the server and download only the files you want. 

The most optimal solution IMO would be to solve this on the server side. If it's possible, ask the server admin to create a "latest" directory for you with links to the latest versions of the files. In this way you could easily download them without generating unnecessary network trafic.

---

### Post by atux on 2018-01-11
The server has only the latest ones. So it is fine with my side since wget will download only the set of the files on the server.

---

### Post by atux on 2018-01-11
> **untrustytahr said:**
> ...

```
 ls -t| tail -n+6|xargs rm -f
```

If you remove the "|xargs rm -f"  it will display the files that will be removed if you want to verify be doing.
...

it works. thanks a lot :D

---

### Post by atux on 2018-01-11
OK, now the final bit to make it a script. 
at the moment i do manually download the files by ssh to folder /var/www/html/A by typing  ```
wget -nc -nd --no-check-certificate --user atux --password null -r -np "https://3.3.3.3/folderA" -A "*.tar.gz"
```  and to folder /var/www/html/B by typing  ```
wget -nc -nd --no-check-certificate  --user atux --password null -r -np "https://3.3.3.3/folderB" -A  "*.tar.gz"
```

how can i make it a nice bash script and call it through cron every hour, please? Compare the downloaded files and keep only the latest 5, while deleting all the rest from these 2 folders.

i thought of something like the following, but it does not work nice```
cd /var/www/html/A
wget -nc -nd --no-check-certificate --user atux --password null -r -np "https://3.3.3.3/folderA" -A "*.tar.gz"

ls -t|tail -n+6|xargs rm -f

```

---

