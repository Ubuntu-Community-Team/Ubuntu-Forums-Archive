---
title: "question about crontab and bashscript"
date: 2008-03-11
forum: General Help
---

### Post by paulus4605 on 2008-03-11
hi 
I would like to achieve this
1. a mail which is send every hour between 7 am and 10 pm with all the succesfull and failed logons to my server (ubuntu 7.10).
2. every logon that is registered between 10 pm and 7 am needs to be kept behind and sent in 1 mail to the specified email address.
3. with mailx I achieved to get the mail in html format however I can't seem to get every entry on a new line how do I solve this?
4.The script below is works only between 7 and 9 at manual request however I get the following error at that point  
line 5: let: 08: value too great for base (error token is "08")
due to the fact that the value is the one from 9pm the previous day. after 10 am the script runs like clockwork and no modifications need to be made.

the mail is comming into my mailbox like this :
Accepted password for root from 192.168.x.x port xxxxx ssh2 Mar 9 20:26:53 server sshd[xxxx]: Failed password for root from 192.168.x.x port xxxx ssh2 Mar 9 20:27:00 server sshd[xxxx]: Accepted password for root from 192.168.x.x port xxxxx ssh2

and I would like to have it like this 
Mar 9 20:01:12 server sshd[xxxx]: Accepted password for root from 192.168.x.x port xxxxx ssh2
Mar 9 20:26:53 server sshd[xxxx]: Failed password for root from 192.168.x.x port xxxxx ssh2
Mar 9 20:27:00 server sshd[xxxx]: Accepted password for root from 192.168.x.x port xxxxx ssh2 

this is the script 
```

#!/bin/bash

datum=`date '+%b %e'`
since=`date '+%H'`
let since=since-1


grep "$datum $since" /var/log/auth.log | egrep "Accepted password for|Failed password for"\n> /tmp/mysshparser

mailx -e -a "Content-type: text/html;" -s "connectie report" -c xxxxx@xxxxxx xxx@telenet.be < /tmp/mysshparser
```

can anyone help me out with this problem?
Paul

---

### Post by justleen on 2008-03-11
so you need want to run it from cron?


for the formatting i would include a sed at the and of the line to replace the end of line. now you just have an odd char there?
```

yourbithere | sed 's|$|\n|' > /tmp/mysshparser

```

im not sure why the let is not working, how do you mean "the value is the one from 9pm the previous day" ?

---

### Post by paulus4605 on 2008-03-11
I mean that on the line let since=since-1 is to my opinion not reset to the value of 7am -1h

---

### Post by koenn on 2008-03-11
for the let statement, try
```
let since=**$**since -1 
```
Alternative without 'let'
```
since=$((since -1))
##or
since=$[since-1]
```

---

### Post by koenn on 2008-03-11
you should have a look at tmp/mysshparser. I think you'll see the newlines are still there. My guess is you loose the line breaks by sending your mail as html but without html line break tags 
[HTML]<br>[/HTML]

---

### Post by paulus4605 on 2008-03-11
so you mean that I have to put my linebreak like this 
grep "$datum $since" /var/log/auth.log | egrep "Accepted password for|Failed password for<br>"> /tmp/mysshparser
or in the second one?

---

### Post by koenn on 2008-03-11
I mean : I think you get tekst without line ends because it's send as html without break tags.

Your sollution might work, although you migt have to "escape" the > and < because they might work as redirectors or have a special meaning to egrep. 

why don't you just try it ?

---

### Post by justleen on 2008-03-11
> 
grep "$datum $since" /var/log/auth.log | egrep "Accepted password for|Failed password for<br>"> /tmp/mysshparser


no that would not work, since you are now grepping for <br> 
you want to add the <br> at each line, not look in your log wether "Failed password for<br>" is present

```

leen@just-ux:/var/log$ egrep "FAILED" /var/log/auth.log|sed 's/$/<br>/'

Mar 11 20:29:17 just-ux login[5087]: FAILED LOGIN (1) on 'tty2' FOR `UNKNOWN', User not known to the underlying authentication module<br>
Mar 11 20:29:21 just-ux login[5087]: FAILED LOGIN (2) on 'tty2' FOR `UNKNOWN', User not known to the underlying authentication module<br>



leen@just-ux:/var/log$ egrep "FAILED<br>" /var/log/auth.log
leen@just-ux:/var/log$ 

```

---

### Post by koenn on 2008-03-11
> **justleen said:**
> 
```

leen@just-ux:/var/log$ egrep "FAILED" /var/log/auth.log|sed 's/$/<br>/'

Mar 11 20:29:17 just-ux login[5087]: FAILED LOGIN (1) on 'tty2' FOR `UNKNOWN', User not known to the underlying authentication module<br>
Mar 11 20:29:21 just-ux login[5087]: FAILED LOGIN (2) on 'tty2' FOR `UNKNOWN', User not known to the underlying authentication module<br>

```

yep, something along those lines  :)

---

### Post by ghostdog74 on 2008-03-11
> **paulus4605 said:**
> hi 
I would like to achieve this
1. a mail which is send every hour between 7 am and 10 pm with all the succesfull and failed logons to my server (ubuntu 7.10).
2. every logon that is registered between 10 pm and 7 am needs to be kept behind and sent in 1 mail to the specified email address.
3. with mailx I achieved to get the mail in html format however I can't seem to get every entry on a new line how do I solve this?
4.The script below is works only between 7 and 9 at manual request however I get the following error at that point  
line 5: let: 08: value too great for base (error token is "08")
due to the fact that the value is the one from 9pm the previous day. after 10 am the script runs like clockwork and no modifications need to be made.

the mail is comming into my mailbox like this :
Accepted password for root from 192.168.x.x port xxxxx ssh2 Mar 9 20:26:53 server sshd[xxxx]: Failed password for root from 192.168.x.x port xxxx ssh2 Mar 9 20:27:00 server sshd[xxxx]: Accepted password for root from 192.168.x.x port xxxxx ssh2

and I would like to have it like this 
Mar 9 20:01:12 server sshd[xxxx]: Accepted password for root from 192.168.x.x port xxxxx ssh2
Mar 9 20:26:53 server sshd[xxxx]: Failed password for root from 192.168.x.x port xxxxx ssh2
Mar 9 20:27:00 server sshd[xxxx]: Accepted password for root from 192.168.x.x port xxxxx ssh2 

this is the script 
```

#!/bin/bash

datum=`date '+%b %e'`
since=`date '+%H'`
let since=since-1


grep "$datum $since" /var/log/auth.log | egrep "Accepted password for|Failed password for"\n> /tmp/mysshparser

mailx -e -a "Content-type: text/html;" -s "connectie report" -c xxxxx@xxxxxx xxx@telenet.be < /tmp/mysshparser
```

can anyone help me out with this problem?
Paul

take note that %e in date is space padded, so if you do a grep, you may have to take note of that extra space is the date is 1 digit. 
For minus 1 hour, if you are using GNU date, it might be easier to do
```

date '+%H' -d "1 hour ago"

```
then using arithmetic.

here's a sample awk code
```

awk 'BEGIN{ 
 mth=strftime("%b")
 day=strftime("%e")
 if (day < 10) da=mth day
 else da=mth" "day  
}
{
  gsub(da,"\n"da)
  if ( $0 ~ da ) print $0
}' file

```
output:
```

# ./testnew.sh
Accepted password for root from 192.168.x.x port xxxxx ssh2
Mar 9 20:26:53 server sshd[xxxx]: Failed password for root from 192.168.x.x port xxxx ssh2
Mar 9 20:27:00 server sshd[xxxx]: Accepted password for root from 192.168.x.x port xxxxx ssh2


```

---

### Post by paulus4605 on 2008-03-12
@ghostdog

forgive me for my bad knowledge of linux but what would the final scriptfile look like 

thanks again for your help
Paul

---

