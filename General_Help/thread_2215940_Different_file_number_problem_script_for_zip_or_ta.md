---
title: "Different file number problem script for zip or tar.bz2"
date: 2014-04-09
forum: General Help
---

### Post by secoonder on 2014-04-09
Hello.
i wrote the script.
I want to backup files daily ,but different file numbers.
for example:
abc.tar.bz2.1
abc.tar.bz2.2
abc.tar.bz2.3

or

abc.zip1
abc.zip2
abc.zip3

i created zip script. " zip -r abc.zip /home/abcd/*  "
But i can't know different file number 
For example .. Today,the file name must be abc.zip.1.
But next Day the file name must be abc.zip.2

or  i created tar script.
tar cvzf  abc.tar.bz2 /home/abcd/*
But i can't know different file number 
For example .. Today,the file name must be abc.tar.bz2.1
But next Day the file name must be abc.tar.bz2.2

**What should I add a line in this script.** ?
Help me please
Regards.

---

### Post by Impavidus on 2014-04-09
Instead of numbers you could use the current date:```
tar cvzf  abc.tar.bz2.$(date +%Y-%m-%d) /home/abcd/*
```will give file name abc.tar.bz2.2014-04-09 today and abc.tar.bz2.2014-04-10 tomorrow. Use whatever date format you want. This one has the nice property of also sorting chronologically whenever you sort alphabetically.

---

### Post by sudodus on 2014-04-09
For example, you can add the current date (yy-mm-dd) into the file name

```

mydate=$(date '+%Y-%m-%d')
echo $mydate

```
so you can add **$mydate** where you want it in the file name

---

### Post by secoonder on 2014-04-11
Hello
Impavidus and Sudodus thank you for your answer.My problem is solved.
my script is :
cd /_USERF&#304;LES/
tar cvzf /_abc/papua$(date +%k_%M--%d_%m_%Y).tar.bz2 files/
But it was a new problem.When &#305; am running script,start backup.
But,after it is zipped end file, it was an error
"tar : exiting with failure status due to previous errors"
What can i do .
Regards

---

### Post by Lars Noodén on 2014-04-11
tar z goes with the extension tar.gz or tgz.  bz2 or tar.bz2 is made and extracted with j.  

```

tar cv**j**f  abc.tar.bz2.$(date +%Y-%m-%d) /home/abcd/*

```

Also the files will sort more easily if you put the year first then month, day and time.

---

### Post by secoonder on 2014-04-11
Lars Nooden Thank you for reply.
it is not error now.Thank you.
with  cvzf  directory sizes are 490 Mb
with  cv**j**f  directory sizes are 440 Mb now.is this situation normal?
on the other and,is  cvjf command more compress than cvzf ???

---

### Post by Lars Noodén on 2014-04-11
Yes, gzip and bzip2 are different compression algorithms so the results will be different.  And the results will vary greatly depending on what is being compressed.  Some data, like JPEG and PNG and ODF, are already compressed and won't change much.  Others, like plain UTF-8 or ASCII text, will compress quite a lot.  If I recall correctly, gzip is faster but bzip2 is usually smaller.  The decompression time for both is less than the compression time.  If you search around for comparisons of the two algorithms, you can find a lot.

---

### Post by secoonder on 2014-04-12
Lars Nooden Thank you ver much for your reply.

But ,the problem is occured now.Just now,&#305; checked backup files.
The compressed file name is "abc"...
Not" abc.12_04_2014.tar.bz2".
yesterday ,i am running script.And then it occured abc.11_04_2014.tar.bz2. (4
But now ,file name is abc .Sizes 413 Mb.how can i check abc files?
What am I doing wrong?
why is not compreesed file name is abc.12_04_2014.tar.bz2

Regards

---

### Post by Lars Noodén on 2014-04-12
Can you post the exact line from your script that you are using to make the tarball?

---

### Post by secoonder on 2014-04-12
Script
"cd /_USER_FILES/
tar cv**j**f  /DB/abc$(date +%k-%M--%d%m%Y).tar.bz2 attachmens/   "
 
When i runned script manual yesterday,it was no problem as follows.And No errors "tar : exiting with failure status due to previous errors"
DB # ls -l abc*
-rw-r--r-- root root 441100165 Apr 11 15:16 abc15_14--11_04_2014.tar.bz2

i setted the script at crontab
02 50 * * * /root/scripts/dodi.sh

this morning, &#305; looked server.
DB # ls -l abc*
**-rw-r--r-- root root 439230734 Apr 11 02:51 abc**
-rw-r--r-- root root 441100165 Apr 11 15:16 abc15_14--11_04_2014.tar.bz2
--------------------------------------------------------------------------------------
1) i entered command "tar xvjf abc" .
The files succesfully decompressed.But i did not entered "tar xvjf abc.tar.bz2.Because Compress file name is abc.
This situation,is it accurate true conclusion.On the other hand,is it data loss?
2)i think,the file name must be "abc02_50--12_04_2014.tar.bz2" ? why is the file name abc ?
3)before 5 minutes,&#305; run script.it is succesfully compressed.But after it is zipped end file, it was an error
"tar : exiting with failure status due to previous errors".
What can i do ?
thank you very much for your help
Regards

---

### Post by Lars Noodén on 2014-04-12
It could possibly be due to a misspelled pathname .  Was "attachmens" meant to be "attachments" ?

---

### Post by Impavidus on 2014-04-12
> ```

cd /_USER_FILES/
tar cv**j**f  /DB/abc$(date +%k-%M--%d%m%Y).tar.bz2 attachmens/
```
Very simple, but you have to pay attention. The %k in the date command gives the hours padded with spaces. So the tar command becomes```
tar cvjf /DB/abc 2-50--12042014.tar.bz2 attachments/
```Mind the space between abc and 2. Now the tar command thinks that you want to name the archive /DB/abc and that you want to put into the archive both the attachments directory and the file 2-50--120414.tar.bz2, which doesn't exist and therefore gives an error. When you tried manually it was past 10 o'clock, leading to the disappearance of the space and with that of the problem.

Best to replace the %k with %H, which will give a 0-padded output.

---

### Post by secoonder on 2014-04-13
Lars Nooden and &#304;mpavidus thank you very much for your reply.
Lars nooden,i m so sorry.&#305; wrote wrong this area.My script is
"cd /_USER_FILES/
tar cv**j**f  /DB/abc$(date +%k-%M--%d%m%Y).tar.bz2 attachmen**t**s/"
So,my script is not misspelled pathname.it is not a problem here.

&#304;mpavidus
i edited my script.
"cd /_USER_FILES/
tar cv**j**f  /DB/abc$(date +%Y-%m-%d--%**H**%M).tar.bz2 attachments/"

i replaced also Y,m,d   with H,M.....
firstly ; Y,m,d ... .And then H,M..
i runned script manualy.the compressed is succesfully.
And then i edited my cron hour.(from 02:50 to 10:30).And the compressed is succesfully.
i took again from 10:30 to 02:50.i will check this night.And then,i will inform last situation.
Thank you for your reply again.
Regards

---

### Post by secoonder on 2014-04-18
Hello
Impavidus thank you. My problem is solved.

My script finally ;
"cd /_USER_FILES/
tar cv**j**f  /DB/abc$(date +%Y-%m-%d--%**H**%M).tar.bz2 attachments/"

i replace the %k with %H.And it was no errors. :D..

the problem is solved.
Thank you very much for your helps

Regards

---

