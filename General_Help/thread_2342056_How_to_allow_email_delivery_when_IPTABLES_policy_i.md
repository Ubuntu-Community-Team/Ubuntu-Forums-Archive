---
title: "How to allow email delivery when IPTABLES policy is DROP for all ip's not declared"
date: 2016-11-03
forum: General Help
---

### Post by albubu on 2016-11-03
[COLOR=#242729][FONT=Arial]Hello.

Whenever I am finishing a website and I want to test it online, I use IPTABLES rules to allow access only to certain IP&#8217;s (me and rest of the developers).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]This way we can be sure the website is yet not public, but the developer team can navigate through it and check if there is any issue to be addressed before making the website public.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
The only problem found with this method is the fact that when IPTABLES rules are set, we are not able to send emails through our website.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
These are the rules we use:[/FONT][/COLOR]

1.- iptables -A INPUT -s IP_DEVELOPER -j ACCEPT

2.- iptables -A OUTPUT -d IP_DEVELOPER -j ACCEPT

3.- iptables -P INPUT DROP

4.- iptables -P OUTPUT DROP
[COLOR=#242729][FONT=Arial]
With this, we are only allowing access to the developer, and any other other IP will be denied.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]For emails, we use Gmail, SMTP, port 465 and SSL:[/FONT][/COLOR]

$mail->Mailer = "smtp";
$mail->IsSMTP();
$mail->CharSet = 'UTF-8';
$mail->Host = "ssl://smtp.gmail.com";
$mail->SMTPAuth = true;
$mail->Username = [EMAIL="myname@mydomain.com"]myname@mydomain.com[/EMAIL]
$mail->Password = "mypassword";
$mail->Port = 465;
[COLOR=#242729][FONT=Arial]
*It is important to note that emails are being sent with no problem when these IPTABLES are not present.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Now, to allow email delivery from our website when these iptables are present, we have been setting some specific rules, however none of them has worked to us so far.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
We have tried:[/FONT][/COLOR]

5.-  iptables -A INPUT -s smtp.gmail.com -p tcp -m tcp --sport 465 -j ACCEPT

6.-  iptables -A OUTPUT -d smtp.gmail.com -p tcp -m tcp --dport 465 -j ACCEPT
[COLOR=#242729][FONT=Arial]
After that, we tried:[/FONT][/COLOR]

7.- iptables -A INPUT -p tcp &#8211;s 64.233.160.0/19 --sport 465 -j ACCEPT

8.- iptables -A OUTPUT -p tcp &#8211;d 64.233.160.0/19 --dport 465 -j ACCEPT
[COLOR=#242729][FONT=Arial]
After that, this:[/FONT][/COLOR]

9.- iptables -A OUTPUT -o eth0 -p tcp --sport 465 -m state --state NEW,ESTABLISHED -j ACCEPT

10.- iptables -A OUTPUT -o eth0 -p tcp --dport 465 -m state --state NEW,ESTABLISHED -j ACCEPT

11.- iptables -A INPUT -i eth0 -p tcp --sport 465 -m state --state ESTABLISHED -j ACCEPT
[COLOR=#242729][FONT=Arial]
And it did not work either&#8230;[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
My question is:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
What IPTABLES rules should I set in this case to allow email delivery from my website??[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Thank&#8217;s in advanced, any insight is appreciated.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Regards[/FONT][/COLOR]

---

### Post by kpatz on 2016-11-03
First of all, you don't need to block packets going out from the server to the internet at large, unless you want to restrict what services can connect.  Also, you need to use RELATED, ESTABLISHED on the first rule, so:```
 iptables -A OUTPUT -p ALL -m state --state RELATED,ESTABLISHED -j ACCEPT
```will allow outbound packets for all established connections.  To allow outbound connections to be initiated, add:```
 iptables -A OUTPUT -p ALL -j ACCEPT
```  You can add --dport 465 if you only want to allow outbound connections on port 465.

You'll want to do the same on the INPUT chain, so established connections can also receive packets:```
 iptables -A INPUT -p ALL -m state --state RELATED,ESTABLISHED -j ACCEPT
```

After these rules, set up the rules on the INPUT chain to allow your developers access to your website: ```
iptables -A INPUT -s $IP_DEVELOPER --dport 80 -j ACCEPT
```I added dport 80 to allow access only on port 80, but you can change or remove this if you like.

---

### Post by albubu on 2016-11-03
Ohhh man, your answer really made the job.

Thank you so much!

---

