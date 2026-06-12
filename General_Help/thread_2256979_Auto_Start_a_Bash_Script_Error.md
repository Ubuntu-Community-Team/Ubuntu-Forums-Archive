---
title: "Auto Start a Bash Script Error"
date: 2014-12-16
forum: General Help
---

### Post by chiques on 2014-12-16
I wrote a script which sends me an email whenever my server meets a certain criteria. The script runs fine when I'm in my user login (terminal) and I run ./myscript.sh.

Problem is when I save it in **/etc/init **or add the path to **crontab -e**  I get this weird error that is non-existent when I run it manually. 

>  unknown or illegal alias:...

Any ideas?

```

Dec 16 00:05:55 falcon sSMTP[2005]: RCPT TO:<mineon@skypatrol.net> (550 5.1.1 unknown or illegal alias: mineon@skypatrol.net)

```

---

### Post by ajgreeny on 2014-12-16
So please let us see the full content of this script, with any personal info edited out, otherwise we can not even start to guess what is going wrong.

---

### Post by chiques on 2014-12-16
> **ajgreeny said:**
> So please let us see the full content of this script, with any personal info edited out, otherwise we can not even start to guess what is going wrong.


Sure. I am using the code from [here]("https://ariandy1.wordpress.com/2014/04/08/linux-send-email-when-ip-address-changes/") with a while loop and sleep function added..

```

#!/bin/bash
# check and send ip address to email

while true; do

sleep 5 

MYIP=`ifconfig eth0 | grep 'inet addr'| awk '{print $2}' | cut -d ':' -f 2`;
TIME=`date`;
 
LASTIPFILE='/home/yourUserName/.last_ip_addr';
LASTIP=`cat ${LASTIPFILE}`;
 
if [[ ${MYIP} != ${LASTIP} ]]
then
        echo "New IP = ${MYIP}"
        echo "sending email.."
        echo -e "Hello\n\nTimestamp = ${TIME}\nIP = ${MYIP}\n\nBye" | \
                /usr/bin/mail -s "[INFO] New IP" yourothermail@gmail.com;
        echo ${MYIP} > ${LASTIPFILE};
else
        echo "no IP change!"
fi
done


```

---

### Post by nerdtron on 2014-12-16
> Problem is when I save it in **/etc/init **or add the path to **crontab -e**  I get this weird error that is non-existent when I run it manually.

Since the script is running fine on the terminal, we need to troubleshoot how the init or the crontab executes this script.
What is your crontab entry for this?

---

### Post by chiques on 2014-12-18
> **ajgreeny said:**
> So please let us see the full content of this script, with any personal info edited out, otherwise we can not even start to guess what is going wrong.

Here's the script:


```


#!/bin/bash
# check and send ip address to email


while true; do

#sleep 12h
#sleep 1

#MYIP=`ifconfig.me | grep 'inet addr'| awk '{print $2}' | cut -d ':' -f 2`;
MYIP=`curl ifconfig.me`;
TIME=`date`;

LASTIPFILE='/home/mineon/.last_ip_addr';
LASTIP=`cat ${LASTIPFILE}`;

if [[ ${MYIP} != ${LASTIP} ]]
then
        echo "New IP = ${MYIP}"
        echo "sending email.."
        echo -e "Hello\n\nTimestamp = ${TIME}\nIP = ${MYIP}\n\nBye" | \
                ssmtp mineon@skypatrol.net;
        echo ${MYIP} > ${LASTIPFILE};
else
#       echo "no IP change!"
        echo   "Nothing has changed\n\nTimeStamp = ${TIME}\n" | \
                ssmtp mineon@skypatrol.net;
fi
done


```


If I run it using ./sendip.sh it works and I see this:

> 
mineon@skypatrol:~/Scripts$ ./sendip.sh
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    13    0    13    0     0      3      0 --:--:--  0:00:03 --:--:--     3
New IP = 8.6.7.5.309
sending email..
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    13    0    13    0     0      1      0 --:--:--  0:00:07 --:--:--     3
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:09 --:--:--     0^Z


Running it manually displays this in the system log:

> 

Dec 17 23:21:27 [email]mineon@skypatrol.net[/email] sSMTP[15407]: Creating SSL connection to host
Dec 17 23:21:28 [email]mineon@skypatrol.net[/email] sSMTP[15407]: SSL connection using RSA_AES_128_CBC_SHA1
Dec 17 23:21:29 [email]mineon@skypatrol.net[/email] sSMTP[15407]: Sent mail for [email]mineon@skypatrol.net[/email] (221 2.3.0 Bye received. Goodbye.) uid=1000 username=mineon outbytes=421
Dec 17 23:21:37 [email]mineon@skypatrol.net[/email] sSMTP[15443]: Creating SSL connection to host
Dec 17 23:21:37 [email]mineon@skypatrol.net[/email] sSMTP[15443]: SSL connection using RSA_AES_128_CBC_SHA1
Dec 17 23:21:38 [email]mineon@skypatrol.net[/email] sSMTP[15443]: Sent mail for [email]mineon@skypatrol.net[/email] (221 2.3.0 Bye received. Goodbye.) uid=1000 username=mineon outbytes=413
Dec 17 23:22:01 [email]mineon@skypatrol.net[/email] CRON[15575]: (mineon) CMD (/home/mineon/Scripts/sendip.sh)






The line I added to the crontab -e file is:

```

#Run my ip checking script every minute
*/1 * * * * /home/mineon/Scripts/sendip.sh

```


When I monitor the system log using the crontab -e option I see:

> 
Dec 17 23:35:01 [email]mineon@skypatrol.net[/email] CRON[21104]: (mineon) CMD (/home/mineon/Scripts/sendip.sh)



The problem with the crontab -e option is I do not receive the email. 


The manual way works fine.

---

### Post by nerdtron on 2014-12-18
HHmmm let's see.

First, from what I understand this script, when you run it, runs continuously right? It will loop itself over and over again.
If so, you need to disable this looping first before you put in cron. The if,else statements are fine. The while true loop is what you need to remove so that it just runs once when you run it on the terminal.

Then cron will run the script every every minute. You should also explicitly tell cron which shell to use since environment variables on cron is different from your current environment.
```
 * * * * * /bin/bash /home/mineon/Scripts/sendip.sh 
```

---

### Post by chiques on 2014-12-23
> **nerdtron said:**
> HHmmm let's see.

First, from what I understand this script, when you run it, runs continuously right? It will loop itself over and over again.
If so, you need to disable this looping first before you put in cron. The if,else statements are fine. The while true loop is what you need to remove so that it just runs once when you run it on the terminal.

Then cron will run the script every every minute. You should also explicitly tell cron which shell to use since environment variables on cron is different from your current environment.
```
 * * * * * /bin/bash /home/mineon/Scripts/sendip.sh 
```

I removed the loop but the log is still showing that Crontab -e is using a different username other then what I have set in ssmtp.conf and in the script.

> 
Dec 22 23:27:09 minion sSMTP[1169]: Creating SSL connection to host
Dec 22 23:27:09 minion sSMTP[1169]: SSL connection using RSA_AES_128_CBC_SHA1
Dec 22 23:27:09 minion SMTP[1169]: RCPT TO:<Gru@skypatrol.net> (550 5.1.1 unknown or illegal alias: [email]Gru@skypatrol.net[/email])
Dec 22 23:27:09 minion CRON[1160]: (Gru) MAIL (mailed 1 byte of output; but got status 0x0001, #012)



So in my case the correct email address is > minion@skypatrol.net but for some reason Crontab -e uses my login > Gru@skypatrol.net. I have Crontab -e running the script every minute and it errors out.


Any ideal where I can tell Crontab -e to user a different username?

---

### Post by nerdtron on 2014-12-23
> Any ideal where I can tell Crontab -e to user a different username?

Sure. I use the mailx command with the -r option to send emails with specific "FROM" address. Sample syntax:

```
echo "Body of the Email Here" | mailx -r FromMe@email.com -s "Subject Of Email" ToYou@email.com 
```

---

### Post by steeldriver on 2014-12-23
is the confusion here perhaps because your cron **job** tries to send a mail to [email]minion@skypatrol.net[/email], whereas what you're seeing in the log relates to a **failure message from cron** which will (by default) be sent to the invoking user (i.e. the username whose crontab you placed the job in)

---

### Post by chiques on 2014-12-31
> **nerdtron said:**
> Sure. I use the mailx command with the -r option to send emails with specific "FROM" address. Sample syntax:

```
echo "Body of the Email Here" | mailx -r FromMe@email.com -s "Subject Of Email" ToYou@email.com 
```

This worked. Thanks!

---

### Post by chiques on 2014-12-31
> **steeldriver said:**
> is the confusion here perhaps because your cron **job** tries to send a mail to [email]minion@skypatrol.net[/email], whereas what you're seeing in the log relates to a **failure message from cron** which will (by default) be sent to the invoking user (i.e. the username whose crontab you placed the job in)

Yes. For some reason the cron application wants to send an email to [email]gru@skypatrol.net[/email]. 


Modifying my script as nerdtron recommended works flawlessly when I manually run the script. The first run it write so the .last_ip_address. The second and consecutive runs it simply prints > Nothing has changed\n\nTimeStamp = ${TIME}\n (I commended the ssmtp function out). 

Here is the [COLOR="#FF0000"]_PROBLEM:_[/COLOR]
When I have crontab -e run my script using the following syntax (I use 1 minute for debugging):
```
*/01 * * * * /bin/bash /home/gru/Scripts/sendip2.sh
```

If I delete/modify the .last_ip_address then it does what it is supposed to, it writes the ip and emails me.

Problem is after the 1st cycle of running the script, cron is trying to email to the invalid email address (gru@skypatrol.net) again. This doesn't make sense because I have no code in my script to request an email if the IP's match.

Any suggestions on where crontab -e might be getting this configuration?

---

### Post by steeldriver on 2014-12-31
Is gru the username of the user whose crontab you are using, and is skypatrol.net your own domain? The default behavior of cron is

```

       cron then wakes up every minute, examining all stored crontabs,  check&#8208;
       ing  each  command  to  see  if it should be run in the current minute.
       When executing commands, [B]any output is  mailed  to  the  owner  of  the
       crontab (or to the user named in the MAILTO environment variable in the
       crontab, if such exists).[/B]  The children copies of  cron  running  these
       processes  have their name coerced to uppercase, as will be seen in the
       syslog and ps output.

```

You can try setting

```

MAILTO=""

```

at the top of your crontab file

---

