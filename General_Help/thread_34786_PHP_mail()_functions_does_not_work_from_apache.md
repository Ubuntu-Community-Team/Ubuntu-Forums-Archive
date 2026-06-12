---
title: "PHP mail() functions does not work from apache"
date: 2005-05-16
forum: General Help
---

### Post by sect2k on 2005-05-16
Hi!

After migrating our site to a new ubuntu server, the mail() function in PHP is no longer working, when a script is run from within apache (php is set up as a module).

If the same script is run from the CLI, it works fine. Both php.ini files (for CGI and apache module) have the same config for mail (sendmail_path = sendmail -t -i , sendmail_from = [email]some@email.com[/email]).

My guess, and this is only a guess, would be, that www-data (apache user) doesn't have premissions to use sendmail (postfix), since mail() returns FALSE in case of apache and TRUE in case if CLI.

What can be done about this? Pardon my igonrance, but how do I set up postifx to allow www-data to send mail?

Cheers,
/me

---

### Post by sect2k on 2005-05-17
Problem solved! :)

Nothing to do with premmissions, but rather with sendmail's path being /usr/sbin/sendmail and not /usr/bin/sendmail.

---

### Post by bendelben on 2006-08-16
hello people!

i am ben from Manila, Philippines.

please help me in my problem about php mail function.

here is my source code:

<?php

        $my_addy = "benedicto.deleon@fiti.com.ph";
        $to_addy = "bendeleonjr@gmail.com";
        $subject = "Test Subject";
        $message = "Test Message";

        $headers = "From: $my_addy \r\n";
        $headers .= "Reply-To: $my_addy \r\n";
        $headers .= "Return-Path: $my_addy \r\n";

if(mail($to_addy,$subject,$message,$headers)) {
        print "Mail sent OK";
} else {
        print "Mail did not send properly";
}
?>

this program is running and prints an output "Mail sent OK".
it only means that mail function returns true.

but my problem is that when i checked the recipient's email, the message was not received.

My OS is UBUNTU and  i am using PHP5.

My apache server is Apache 2.0.55.

if you want to know the subset of my php.ini which contains the config for
mail function, read below:

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
[mail function]
; For Win32 only.
SMTP = localhost

smtp_port = 25

; For Win32 only.
; sendmail_from = 

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
; sendmail_path = 
; Force the addition of the specified parameters to be passed as extra parameters
; to the sendmail binary. These parameters will always replace the value of
; the 5th parameter to mail(), even in safe mode.
;mail.force_extra_parameters =
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;


please help me. i don't know the reason why the recipient can't receive the message.

thanks,
ben

---

### Post by louie55 on 2006-08-25
In Response to bendelben's problem:

Do you have sendmail installed?? I was having the same problem, then I just did:

```
sudo apt-get install sendmail
```

Then I let it install and configure everything automatically and when it was done, my PHP mail worked fine.

To do a quick test, you could install nmap and do a quick portscan of localhost to test for an open port 25:

```
sudo apt-get install nmap
nmap -sT localhost
```

If you see this as part of the output:

```
25/tcp   open  smtp
```

Then you have a mail daemon running. This should show up after you install sendmail.

Louie

---

### Post by brentrussell on 2006-09-09
bendelben:

You might also want to check the type of address that you are sending to. Sometimes mail servers like Yahoo and Hotmail reject php messages as spam. So check your spam box and add these headers to make the mail message look like it's comming from a more valid source:

This gives the server a message id so it can track it better:
$headers .= "Message-ID: <".$now."root@".$_SERVER['SERVER_NAME'].">."\r\n";

And this gives the server some type of identification as to who is sending to it
$headers .= "X-Mailer: PHP v".phpversion()."\r\n"; 

Hope that helps

---

### Post by bendelben on 2006-09-12
thank you Louie,

yes, you are right. sendmail was not installed in my PC.

I successfully installed sendmail and nmap.

when i run nmap -sT localhost

i retrieved the following output:

Starting Nmap 4.03 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-09-12 14:29 PHT
Interesting ports on localhost (127.0.0.1):
(The 1663 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
902/tcp  open  iss-realsecure-sensor
3306/tcp open  mysql
5432/tcp open  postgres
6543/tcp open  mythtv
6544/tcp open  mythtv

Nmap finished: 1 IP address (1 host up) scanned in 0.181 seconds


when i run my mail program, it is too slow.

the output is "Mail Sent OK". but, when i checked the recepient's email, it did not receive the message.

i think, there is still something wrong although i already installed sendmail and nmap.

i am just wondering because it took 1.5 minute to process sending of mail. it is too slow.


i want also to thank brentrussell. i tried your suggestion but it did not work also.

thank you for your reply,
ben

---

### Post by xtophe on 2006-09-12
Okay! Nice to read I'm not the only one: I have exactly the same problem after installing sendmail: It takes (to) long, then the script says it returns an 'ok' but no mail has been sent... 

What's the solution!?

Anyone ?:confused:

---

### Post by jon23d on 2006-09-23
I too am having this issue.  I can telnet locally to the server, but mail is not being sent and scripts are taking forever to execute....

---

### Post by Contrid on 2006-09-24
I can send emails from my email client, but I can't send emails with the PHP mail() function.

I have postfix installed.

My 'sendmail_path' is "usr/bin/sendmail -t -i"

Could anyone help, please?

---

### Post by keithnorris on 2006-10-23
Contrid: I'm still battling with some php/mail issues myself, but I think your sendmail_path SHOULD be: "/usr/sbin/sendmail -t -i". Note the "sbin" rather than "bin". Good luck.

---

### Post by cshelswell on 2007-04-24
Ok i realise this is sometime after the initial post but i've just spent over a day trying to get sendmail to deliver mail from a php mail() function to no joy. Eventually i did get it working but it took ages to run the script.

Eventually i installed exim, it set up really easily and now i can send php mails really easily.

Just thought i'd post this incase anyone else just had the terrible day i did with sendmail

---

### Post by pr0fess0r on 2007-05-29
Can you tell me what you did to get exim working?
I have exim 4 installed, and in php.ini I have configured 

```
sendmail_path = /usr/sbin/exim -t
```

I read that if you dont use a command line switch, php adds its own (-t -i by default) and that breaks exim, so the above works.
The problem is I am sending mail through my ISP who doesnt like the sender www-data@hobbiton
Here's the exim log:

```
2007-05-29 16:23:22 Start queue run: pid=14255
2007-05-29 16:23:22 End queue run: pid=14255
2007-05-29 16:23:27 1HstF1-0003i1-6f <= www-data@hobbiton U=www-data P=local S=1484
2007-05-29 16:23:31 1HstF1-0003i1-6f ** lucas@xxx.co.nz R=smarthost T=remote_smtp_smarthost: SMTP error from remote mail server after RCPT TO:<lucas@xxx.co.nz>: host xxx.co.nz [69.39.89.54]: 550-Verification failed for <www-data@hobbiton>\n550-unrouteable mail domain "hobbiton"\n550 Sender verify failed
2007-05-29 16:23:31 1HstF5-0003i6-OD <= <> R=1HstF1-0003i1-6f U=Debian-exim P=local S=2487
2007-05-29 16:23:31 1HstF1-0003i1-6f Completed
2007-05-29 16:23:31 1HstF5-0003i6-OD => www-data <www-data@hobbiton> R=local_user T=mail_spool
2007-05-29 16:23:31 1HstF5-0003i6-OD Completed
2007-05-29 16:53:22 Start queue run: pid=15024
2007-05-29 16:53:22 End queue run: pid=15024
```

I guess I need to change my sender to someone that my ISP will accept - [email]webmaster@xxx.co.nz[/email] would do it.
How do I do this? I tried changing /etc/email-addresses but that didnt work:

```
user: www-data@hobbiton
otheruser: webmaster@xxx.co.nz
```

My /etc/exim4/update-exim4.conf.conf settings are:

```
dc_eximconfig_configtype='smarthost'
dc_other_hostnames=''
dc_local_interfaces='127.0.0.1'
dc_readhost=''
dc_relay_domains=''
dc_minimaldns='false'
dc_relay_nets=''
dc_smarthost='mail.xxx.co.nz'
CFILEMODE='644'
dc_use_split_config='false'
dc_hide_mailname='false'
dc_mailname_in_oh='true'
dc_localdelivery='mail_spool'

```

I just want to be able to send out from PHP. Also, if I need to authenticate with my ISP's SMTP server, how do I set that up?

thanks in advance for any help

---

### Post by dgath on 2007-08-15
FYI, I wasn't able to get sendmail working either, but I used exim and it worked like a charm, so I'd suggest people try that if they are having issues.

---

