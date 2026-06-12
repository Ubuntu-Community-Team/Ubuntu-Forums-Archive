---
title: "[SOLVED]Configurate postfix so i can send email using the command line!"
date: 2015-06-06
forum: General Help
---

### Post by patrikmellq on 2015-06-06
Hello - i want to install Logwatch on my Ubuntu LTS 14.04 - but before i do that i need to get Postfix to work on my system.
Now i find a guide and all setting looks correct and still i can't email my gmail account with the command line.

I belive this has to do with that i am behind a router with the name NETGEAR93 - but i am not sure.
Now i will show you the steps done installing and configurating Postfix.

First i install postfix and bsd-mailx - i install bsd-mailx because that allow me to send email using the command line.

```

sudo apt-get install postfix bsd-mailx

```

Now starts a short installation process.

[IMG]http://i59.tinypic.com/9fyuiv.png[/IMG]

I click OK to start the installation process

[IMG]http://i57.tinypic.com/2cy35fn.png[/IMG]

Here i pick internet smarthost
Next i am not sure if i am doing things right - should it be my hostname "patrik" or my email "gmail.com"

[IMG]http://i61.tinypic.com/29bc5fk.png[/IMG]

I assume it should be gmail.com so i enter gmail.com and continue.

[IMG]http://i61.tinypic.com/mlsaog.png[/IMG]

In the this dialog the SMTP-relay must be entered. This is the SMTP  address of the provider you want to use. In this case, it is  “smtp.gmail.com” and i am pretty sure this is correct.

Now the basic configuration is completed. However, some manual work is still needed to get the thing up and running.

 First, the file /etc/postfix/main.cf must be edited. 

This is how the file looks like:

```



# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = patrik
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = patrik, localhost.localdomain, localhost
relayhost = smtp.gmail.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all


```

This is the files i should add:

```

sudo nano /etc/postfix/main.cf

```
```

smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/etc/postfix/sasl_password
smtp_tls_security_level = may 

```

This is now how the /etc/postfix/main.cf should look like:

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/etc/postfix/sasl_password
smtp_tls_security_level = may

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = patrik
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = patrik, localhost.localdomain, localhost
relayhost = smtp.gmail.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all


```

As a result, authentication via SASL (Simple Authentication and Security Layer) is turned on and configured.
In addition, the encryption for TLS (Transport Layer Security) is turned on.


Now the file /etc/postfix/sasl_password is created. There the 
username and password for authentication for your  mail provider are 
entered – in this case, it is Google Mail

Now i have to configure that file

```

sudo nano /etc/postfix/sasl_password

```

[IMG]http://i58.tinypic.com/2n66bcw.png[/IMG]

And i have to protect the file with
```

sudo chmod 600 /etc/postfix/sasl_password

```
so that it is only readable for the root-user.

Now the Postfix-lookup-table must be created. This is done with the command

```

sudo postmap hash:/etc/postfix/sasl_password

```
After that restart Postfix, so that the new configuration is accepted.

```

sudo 
``````
/etc/init.d/postfix restart

```

Now postfix should be able to send mail through your mail 
acount. To test this, we can send a first test mail from the command 
line:

```
echo "First Testmail from Server"
```

When i do this i get First Testmail from Server to show in my command line.
But i don't recive any email to my gmail account.[B]

[IMG]http://i60.tinypic.com/k14awp.png[/IMG]

[/B]Now only one thing is left to do: by default, system messages 
are sent locally to the address root@yourserverhostname. So for not 
storing these mails locally, but sent them to an external address, edit 
the file /etc/aliases and add the following line: root: [EMAIL="your@mailaddress.com"]your@mailaddress.com[/EMAIL]

```

sudo /etc/aliases

```[B][B]

[IMG]http://i62.tinypic.com/5dorh3.png[/IMG]
[/B][/B]
In order for the changes to take effect, the following command must be executed:
```


sudo newaliases

```

From now on the system messages from your server will be sent to your email address!!

Now i have done everything this guide tell me to do - but i don't get any email with this configuration.
Does this have to do that i am behind a router or not.

Well i try as good i can to post everything step by step.
I use the following guide: [http://my5cent.spdns.de/en/allgemein/banana-pi-postfix-installieren-und-einrichten.html](http://my5cent.spdns.de/en/allgemein/banana-pi-postfix-installieren-und-einrichten.html)

---

### Post by patrikmellq on 2015-06-06
Now i really made an effort to show my issue and i hope and welcome all help i can get.

Many Thanks Patrik

---

### Post by patrikmellq on 2015-06-06
I run the command postconf -n to show my settings - if some one can read any default settings or if it is my router

```

sudo postconf -n

```

```

patrik@patrik:~$ sudo postconf -n
[sudo] password for patrik: 
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
mydestination = patrik, localhost.localdomain, localhost
myhostname = patrik
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
readme_directory = no
recipient_delimiter = +
relayhost = smtp.gmail.com
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_password
smtp_sasl_security_options = noanonymous
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
patrik@patrik:~$ 


```

---

### Post by SeijiSensei on 2015-06-06
Run the test I described here: [http://ubuntuforums.org/showthread.php?t=2281311&p=13299156&viewfull=1#post13299156](http://ubuntuforums.org/showthread.php?t=2281311&p=13299156&viewfull=1#post13299156)

Being behind a router shouldn't matter if you're sending.  It will matter if you want to receive mail since external SMTP servers will need to connect to your incoming port 25.  If you ever decide to receive mail, you need to check your ISP's Terms of Service since most residential connections forbid running servers.

---

### Post by patrikmellq on 2015-06-06
Thanks for the topic and the code.
It looks that everything is working with my connection and port 25

```

patrik@patrik:~$ telnet alt1.gmail-smtp-in.l.google.com 25
Trying 74.125.23.26...
Connected to alt1.gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP a5si16120687pat.91 - gsmtp

```

**I quote [[COLOR=#000000]SeijiSensei[/COLOR]]("http://ubuntuforums.org/member.php?u=698195"):**

Here's a simple test.  Open a terminal and run the command:

```

telnet alt1.gmail-smtp-in.l.google.com 25

```

If you can connect, you'll see GMail reply with its "banner" like this:

```

Trying 74.125.24.27...
Connected to alt1.gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP s1si2787214wiy.52 - gsmtp

```

I got the exact same result, so there is nothing wrong with port 25 or that i have a router, then i am back to the configuration of postfix.
This test and solution to check things comes from this topic [http://ubuntuforums.org/showthread.php?t=2281311&p=13299156&viewfull=1#post13299156](http://ubuntuforums.org/showthread.php?t=2281311&p=13299156&viewfull=1#post13299156) as has been mention above.

---

### Post by patrikmellq on 2015-06-06
I test one more guide that was similiar to the one above.
[https://rtcamp.com/tutorials/linux/ubuntu-postfix-gmail-smtp/](https://rtcamp.com/tutorials/linux/ubuntu-postfix-gmail-smtp/)

And it did not work.
This sucks - i really wanted to install Logwatch.

All this was using gmail.com - now my last attempt will be with outlook as its running smooth with Thunderbird.

---

### Post by nerdtron on 2015-06-07
SSMTP worked for me making my gmail account as the relay for emails alerts.
[http://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html](http://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html)

If it does not work. Then post the contents of the /var/log/maillog here.

A note on this method, it won't work permanently since gmail will block unsolicited email. My email address was eventually locked down due to this.

---

### Post by GrouchyGaijin on 2015-06-07
Have you seen this How to?

[https://rtcamp.com/tutorials/linux/ubuntu-postfix-gmail-smtp/](https://rtcamp.com/tutorials/linux/ubuntu-postfix-gmail-smtp/)

---

### Post by patrikmellq on 2015-06-07
@Nerdtron i will test your guide as my last attempt - if is not working i have to change Linux Distro - because i don't give up and want Logwatch up running - i think it contribute great for my security solution.
About gmail stop sending - i find this - troubleshooting - Error: "SASL authentication failed; server smtp.gmail.com"
You need to unlock the captcha by visiting this page [https://www.google.com/accounts/DisplayUnlockCaptcha](https://www.google.com/accounts/DisplayUnlockCaptcha)

@GrouchyGaijin i test that guide and more advance guides and it not working - but i will test Nerdtron guide as it handle smtp.

Many Thanks

---

### Post by patrikmellq on 2015-06-07
Thanks Nerdron - it is working - even if gmail gets angry with each email - i hade to activate a function with gmail to allow my emails from my sstmp configuration - but its working - so now i can install Logwatch - many thanks and now i will mark this topic SOLVED.
But i want to show how gmail react with each email i send.
I wrote "It is working great i am happy"
[TABLE="class: cf hX"]
[TR="class: hR"]
[TD="class: hV hM, bgcolor: #ddd"][/TD]
[/TR]
[/TABLE]
[IMG]https://ssl.gstatic.com/ui/v1/icons/mail/profile_mask2.png[/IMG]

[TABLE="class: cf gJ"]
[TR]
[TD="class: gF gK"]My Computer Name[/TD]
[TD="class: gF gK"][/TD]
[TD="class: gH"]11:07 (6 minuter sedan)[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG][/TD]
[/TR]
[TR]
[TD="class: gF gK, colspan: 3"][TABLE="class: cf iB"]
[TR]
[TD]It is working great i am happy[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]








[IMG]https://ssl.gstatic.com/ui/v1/icons/mail/profile_mask2.png[/IMG]


[TABLE="class: cf gJ"]
[TR="class: acZ"]
[TD="class: gF gK"][TABLE="class: cf ix"]
[TR]
[TD]**Mail Delivery Subsystem <mailer-daemon@googlemail.com>**[/TD]
[/TR]
[/TABLE]
[/TD]
[TD="class: gH"]11:10 (3 minuter sedan)[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG][/TD]
[TD="class: gH"][/TD]
[TD="class: gH acX"][/TD]
[/TR]
[/TABLE]











[TABLE="class: cf gJ"]
[TR="class: acZ xD"]
[/TR]
[/TABLE]
[TABLE="class: cf gJ"]
[TR="class: acZ xD"]
[TD="colspan: 3"][TABLE="class: cf adz"]
[TR]
[TD="class: ady"]till mig 
[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
   Översätt meddelande

Inaktivera för: engelska



Delivery to the following recipient failed permanently:

     [EMAIL="recipient_kirtap42@gmail.com"]recipient_Myemail@gmail.com[/EMAIL]

Technical details of permanent failure:
Google tried to deliver your message, but it was rejected by the server for the recipient domain [gmail.com]("http://gmail.com") by [gmail-smtp-in.l.google.com]("http://gmail-smtp-in.l.google.com"). [2a00:1450:4010:c03::1b].

The error that the other server returned was:
550-5.1.1 The email account that you tried to reach does not exist. Please try
550-5.1.1 double-checking the recipient's email address for typos or
550-5.1.1 unnecessary spaces. Learn more at
550 5.1.1 [https://support.google.com/mail/answer/6596](https://support.google.com/mail/answer/6596) oc5si8243646lbc.151 - gsmtp


----- Original message -----

DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/relaxed;
        d=[gmail.com]("http://gmail.com"); s=20120113;
        h=message-id:from:date;
        bh=nqD5Gd3AVWd1OSYcwFNuQCJtYkgoFWOOYMGLvgaYejI=;
        b=WAtGJzXiQcvfNWqs37dV1qucpQ0pG4Tll2/P+1kFL+YuMO/Bk961Ucsr3wc6hQUPaO
         l//ZwGt+7wapJ6Q+xCJ7ItkXHJIXUOiSCFcMFiMCGH6oolUXavyMbIys0b48nBXdCo4M
         C35U9FE0ySDosMLWZN6VAsIMOxojEts7PQ5w70lJ2TxkLm+8EzlqdPmynfC67ZOGa6be
         TB2VMmi91HbMT0m30Bm+nqZQlvGSjC1M795M/icBekjjMruvXAeQD2ANziv14kEIy7To
         P7UCdu1jLoU2t6TKCQx9ijr1+RrFJCW5jybBl6KdIlAN9LrK/zZJU8BsiExgKSVvOrgG
         O88A==
X-Received: by 10.112.199.10 with SMTP id jg10mr11081201lbc.24.1433668234801;
        Sun, 07 Jun 2015 02:10:34 -0700 (PDT)
Return-Path: <[EMAIL="kirtap42@gmail.com"]Myemail@gmail.com[/EMAIL]>
Received: from [EMAIL="kirtap42@gmail.com"]Myemail@gmail.com[/EMAIL] ([hMyIP.dynamic.se.alltele.net]("http://h83-209-7-40.dynamic.se.alltele.net"). [MyIP])
        by [mx.google.com]("http://mx.google.com") with ESMTPSA id jq10sm3218799lab.23.2015.06.07.02.10.32
        for <[EMAIL="recipient_kirtap42@gmail.com"]recipient_@gmail.com[/EMAIL]>
        (version=TLSv1 cipher=RC4-SHA bits=128/128);
        Sun, 07 Jun 2015 02:10:34 -0700 (PDT)
Message-ID: <[EMAIL="55740a8a.ca73980a.71f5.ffffada6@mx.google.com"]55740a8a.ca73980a.71f5.ffffada6@mx.google.com[/EMAIL]>
From: Familjen Mellqvist <[EMAIL="kirtap42@gmail.com"]@gmail.com[/EMAIL]>
X-Google-Original-From: "Familjen Mellqvist" <patrik@kirtap42@[gmail.com]("http://gmail.com")>
Received: by [EMAIL="kirtap42@gmail.com"]@gmail.com[/EMAIL] (sSMTP sendmail emulation); Sun, 07 Jun 2015 11:07:53 +0200
Date: Sun, 07 Jun 2015 11:07:53 +0200[IMG]https://ssl.gstatic.com/ui/v1/icons/mail/images/cleardot.gif[/IMG]

---

