---
title: "Call to undefined function mail()"
date: 2008-01-22
forum: General Help
---

### Post by YEforce on 2008-01-22
Hi there fellow peeps.  My problem is very simple, yet I haven't come up with any solution yet.  I installed Ubuntu 7.04 distribution onto my server.  I put php, mysql, apache, among other things onto my server due to the fact that I am trying to run a Wiki for our group at work.  Wiki works however when you try to create an account or do anything that uses the mail() function for php, it fails with an error message.  Now I did some investigation and found you need sendmail (yes I am a newbie), so I install that, find out it still doesn't work.  Then I read more, find out I need to recompile Php since I installed sendmail version 8.13.8 after compiiling php the first time.  I recompilie, still not working.  I'm lost for ideas on what to try now.  Below I will put in everything that corresponds to sendmail that I know of, hopefully someone has come across this.  

----

My configure command to recompile php:
./configure --with-mysql --with-apxs2=/usr/local/apache/bin/apxs --with-sendmail

The loaded configuration php.ini file has these fields in it:
Directive Local Value Master Value 
sendmail_from no value no value 
sendmail_path /usr/sbin/sendmail -t -i /usr/sbin/sendmail -t -i 

The sendmail program is there:
root@wiki:/usr/sbin# ls -lt sendmail*
lrwxrwxrwx 1 root root    26 2008-01-17 12:00 sendmail -> /etc/alternatives/sendmail
lrwxrwxrwx 1 root root    30 2008-01-17 12:00 sendmail-msp -> /etc/alternatives/sendmail-msp
lrwxrwxrwx 1 root root    30 2008-01-17 12:00 sendmail-mta -> /etc/alternatives/sendmail-mta
-rwxr-xr-x 1 root root 21675 2006-12-13 08:53 sendmailconfig
root@wiki:/usr/sbin# 

The sendmail program is running:
root@wiki:/# ps -ef | grep sendmail | grep -v grep
root     10372     1  0 09:42 ?        00:00:00 sendmail: MTA: accepting connections          
root@wiki:/# 

Yet, when I call any page with mail() it fails:
Fatal error: Call to undefined function mail()

---

### Post by YEforce on 2008-01-22
Does this need to go to a different Forum group?

---

### Post by YEforce on 2008-01-22
This thread can be closed...

I had to completely recompile php, and I was missing the step below.

'make clean'

---

