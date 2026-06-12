---
title: "PHP mail() issues"
date: 2007-06-09
forum: General Help
---

### Post by xenoix on 2007-06-09
Hello fellow ubtuntu members,

I am running ubuntu edgy (with KDE interface). 

I have PHP 5 installed, MySQL 5 and apache2. I have also recently installed sendmail and "exim" as another post requested.

I however, can NOT get the mail function to send mail from my localhost. I have created a registration script and I am currently trying to have it email my members an activation code. The code is as follows:

```

$email = 'xxxxxxxxx@hotmail.com';
if(isset($_GET['email'])){

if(mail($email,'Account Activation',"Thank you for registering an account on " . $site['title'] . ".\r\n Your activation code is: " . $code . "\r\nIf you accidentally closed your web browser or your web page, you can activate your account by going to the following URL:\r\n " . $site['URL'] . "activate/" . $code . "\r\n",'xxxxx@xxxxxx.xxx')){
	echo 'Email [OK]';
	}
	else{
	echo 'Email [FAILED]';
	}

}

```

However, i simply do not get the email. The code takes close to 1 minute to load and does not send the email. I receive the "Email [OK]" message, i dont receive the email. My php.ini section is as follows:
```

[mail function]
; For Win32 only.
SMTP = localhost
smtp_port = 25

; For Win32 only.
;sendmail_from = me@example.com

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail -t

; Force the addition of the specified parameters to be passed as extra paramete$
; to the sendmail binary. These parameters will always replace the value of
; the 5th parameter to mail(), even in safe mode.
;mail.force_extra_parameters =


```

As you can see I have set sendmail to the sendmail executable.

I have run nmap to see if the SMTP is installed, and the results are as follows:

```

scarvell@casper:/etc/init.d$ sudo nmap -sT localhost

Starting Nmap 4.20 ( http://insecure.org ) at 2007-06-09 22:02 EST
Interesting ports on localhost (127.0.0.1):
Not shown: 1692 closed ports
PORT     STATE SERVICE
25/tcp   open  smtp
80/tcp   open  http
587/tcp  open  submission
631/tcp  open  ipp
3306/tcp open  mysql

```

As you can see, SMTP is installed and running.
What MUST i do to receive the email? Its starting to annoy me seriously.

I cannot continue with out that working. 

Thank you,

Kind regards,
Brendan

---

### Post by darkrose on 2007-06-09
This is a hotmail problem, you need to register your mail server (and a pile of other info like who you are, who uses your mail server etc.) with Microshaft before they will 'allow' you to send emails to hotmail addresses.

---

