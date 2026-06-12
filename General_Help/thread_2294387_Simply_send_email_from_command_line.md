---
title: "Simply send email from command line"
date: 2015-09-10
forum: General Help
---

### Post by snakyjake on 2015-09-10
What is the simplist way to send email from the command line?

I run some simple monitoring scripts on my standard Ubuntu Server.  I need to send a simple email to my hotmail account with the results.  
For example: When my wan IP address changes, just send the IP address to my hotmail account.

I've tried a bunch of different methods, none seemed to work, and then I got lost when experimenting too much.  It seems some of the mail commands are for local mail, and some aren't accepted by hotmail.

I can do ssmtp, but I have to manually enter the TO FROM SUBJECT MESSAGE.  
I've tried mail, but I get an error message "mail: cannot send message: Process exited with a non-zero status"

Help?

Ubuntu Server 15.04

---

### Post by HermanAB on 2015-09-11
That is what the mail command is traditionally for.  If you want to attach a file, then scripting mutt is easier.

---

### Post by SeijiSensei on 2015-09-11
Is your server running on a public IP address, or on a residential Internet connection?  If the latter, the chances of your reliably sending mail to remote SMTP servers are pretty low.  First, your ISP may block outbound connections to remote SMTP servers as an anti-spam device.  Also the remote server may reject mail sent from a residential address as likely spam.  If either of these apply to you, you need to ask your ISP if they maintain a relay server you can use.  Be aware, though, that running servers usually violates the terms-of-service on residential Internet accounts, and your ISP may thus not be very helpful.

If your server is directly on the Internet with its own public IP address, then you should be able to send mail from the command prompt with the traditional "mail" utility found in the [**bsd-mailx**](https://launchpad.net/ubuntu/trusty/+package/bsd-mailx) package.  You should make sure your forward and reverse DNS lookups match exactly, since many mail servers will reject messages from servers where the reverse lookup for the machine's IP does not match its announced hostname.

---

### Post by snakyjake on 2015-09-11
I'm on a residential IP.  
Not sure what a "public" IP address is.  I have a WAN IP address that is available to the public, and have no problems accessing my server remotely.
Not sure the true meaning of "relay".
I have no problems sending/receiving email from my Hotmail account, so my ISP isn't blocking SMTP messages.
Not sure if Hotmail accepts email from any SMTP server.  I can see how spammers would have exploited that.

If I need to use my hotmail SMTP to send email, what is the best utility to use from the a single command line (so I can use it in my scripts)?


> **SeijiSensei said:**
> Is your server running on a public IP address, or on a residential Internet connection?  If the latter, the chances of your reliably sending mail to remote SMTP servers are pretty low.  First, your ISP may block outbound connections to remote SMTP servers as an anti-spam device.  Also the remote server may reject mail sent from a residential address as likely spam.  If either of these apply to you, you need to ask your ISP if they maintain a relay server you can use.  Be aware, though, that running servers usually violates the terms-of-service on residential Internet accounts, and your ISP may thus not be very helpful.

If your server is directly on the Internet with its own public IP address, then you should be able to send mail from the command prompt with the traditional "mail" utility found in the [**bsd-mailx**](https://launchpad.net/ubuntu/trusty/+package/bsd-mailx) package.  You should make sure your forward and reverse DNS lookups match exactly, since many mail servers will reject messages from servers where the reverse lookup for the machine's IP does not match its announced hostname.

---

### Post by SeijiSensei on 2015-09-11
If you're sending mail *from* your residential server, it will originate with your public IP address within the subnet managed by your ISP.  Some remote servers will not accept mail from IPs that map back to residential connections.  

Let's run a test.  From your server issue the command
```
telnet mx1.hotmail.com 25
```
That tries to connect to the SMTP port (25) on mx1.hotmail.com.  On my machine that returns
```
Trying 207.46.8.199...
```
but it never connects.  I'm on a Verizon FiOS residential account and am blocked from connecting to port 25 on remote servers.

If I run the same test from my public mail server out in the "cloud" I get
```

telnet mx1.hotmail.com 25
Trying 207.46.8.199...
Connected to mx1.hotmail.com.

```
followed by a greeting message that describe Microsoft's anti-spam policies. 

If you cannot connect using this test, you cannot send mail from your server to your hotmail account.

---

### Post by snakyjake on 2015-09-11
Here's what I did...

```
jake@ubuntu:~$ telnet mx1.hotmail.com 25
Trying 134.170.2.199...
Connected to mx1.hotmail.com.
Escape character is '^]'.
220 BLU004-MC1F13.hotmail.com Sending unsolicited commercial or bulk e-mail to Microsoft's computer network is prohibited. Other restrictions are found at http://privacy.microsoft.com/en-us/anti-spam.mspx. Fri, 11 Sep 2015 15:47:41 -0700

```

---

### Post by SeijiSensei on 2015-09-11
Good! Install bsd-mailx and try sending yourself a message.

---

### Post by snakyjake on 2015-09-11
Results...

```
echo "something" | mailx -s "subject" [email]myemail@hotmail.com[/email]

Unfortunately, messages from XXX.XXX.XXX.XXX weren't sent. Please contact your Internet service provider.  You can tell them that Hotmail does not relay dynamically-assigned IP     ranges. You can also refer your provider to...
```

So now I'm guessing my steps would be to somehow send from my hotmail email account using SMTP?
What's the best utility for that?

---

### Post by jason_gibson2 on 2015-09-12
Open a gmail account and use ssmtp. Is what I do to have my server email my outlook.com when my minecraft server bites the dust.

[http://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html](http://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html)

---

### Post by snakyjake on 2015-09-12
When I tried ssmtp:

```
echo -e "Test" | ssmtp -s "SUBJECT" myemail@hotmail.com
```

I get this error message:

```
ssmtp: 501 5.5.4 Invalid Email address
```

---

### Post by snakyjake on 2015-09-12
I can get ssmtp to work if I do this:

```
$ ssmtp  myemail@hotmail.com
To: myemail@hotmail.com
From: myemail@hotmail.com
Subject: Testing
Test message
```

The problem is I need to figure how to do this from a bash script.
I would prefer a single command line including the subject, to, from, and message.
Would be nice if ssmtp had those parameters.

---

### Post by jason_gibson2 on 2015-09-12
My minecraft status checking functions. Should give you an idea. I just create a little temp file then email the contents of the file, delete the file when done.

```
base_message() { # skeleton notification email for ssmtp
    echo "To: $NOTIFYEMAIL
From: $OUTPUTEMAIL
Subject: $1
            
$2" > "$3"
}

```

```
mc_status() { # checks whether server running. if not sends emails
    if ! pgrep -u "$USERNAME" -f "$SERVICE" > /dev/null ; then
        if [[ ! -e "$MCSTATUSMSG" ]] ; then
            base_message minecraft "server stopped running @ $NOW" "$MCSTATUSMSG"
            ssmtp "$NOTIFYEMAIL" <"$MCSTATUSMSG"
        fi
    else
        if [[ -e "$MCSTATUSMSG" ]] ; then
            rm "$MCSTATUSMSG"
        fi
    fi
}

```

---

### Post by snakyjake on 2015-09-13
Did you have to do anything special to get the cron job to send an email using ssmtp?
I get this error message:

```
sSMTP[29666]: 501 5.5.4 Invalid Email address
```

---

### Post by jason_gibson2 on 2015-09-13
Probably because hotmail is a PoP3 service and doesn't use smtp.

---

### Post by snakyjake on 2015-09-14
It appears the problem I had with cron is the cron is also trying to email the results of the job.  So I piped the cron job results to null.

---

