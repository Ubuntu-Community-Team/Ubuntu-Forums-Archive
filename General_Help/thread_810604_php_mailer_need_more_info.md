---
title: "php mailer need more info"
date: 2008-05-28
forum: General Help
---

### Post by jeff.sadowski on 2008-05-28
I can not find out how the php mail function gets the name of the machine it is mailing on.

```

<?php
 if(!isset($_POST['submit']))
 {
?> 
<form action=' <?php $_SERVER['PHP_SELF'] ?>' method='post'>
To:<input type=text name=to><br>
Subject:<input type=text name=subject><br>
Message:<input type=text name=message><br>
<input type='submit' name='submit' value='Send'>
</form>
<?php  
 }
 else
 {
  $to = $_POST['to'];
  $subject = $_POST['subject'];
  $message = $_POST['message'];
  $from = 'me@mydomain.com';
  $headers =    'From: ' . $from . "\r\n" .
                'Reply-To: ' . $from . "\r\n" .
                'X-Mailer: PHP/' . phpversion() . "\r\n" .
                'MIME-Version: 1.0\r\n' .
                'Content-Type: text/html; charset=utf-8\r\n' .
                'Content-Transfer-Encoding: 8bit\r\n\r\n';

  // Send
  mail($to, $subject, $message, $headers);
  print  "php mail test";
 }
?>

```
Note: I have this page password protected


The above php script is what I have on my machine.
It works ok to gmail.com but it is not returning from
[email]check-auth@verifier.port25.com[/email]
my SPF record should allow the machine with the above script
to mail for my domain.

I edited my /etc/host and added the machine name that the ptr record points to at the start.
So now when I look at a sent message to gmail and look at the details it shows as the expected host name in the mailed-by but still when I send to [email]check-auth@verifier.port25.com[/email] I do not get a reply to [email]me@mydomain.com[/email].
One of the times I mailed to gmail I incorrectly entered the email address and got an error message back from the gmail system
at the bottom I see a name other than the expected outbound name.

ex:
/etc/hosts

127.0.0.1 mydomain.com [www.mydomain.com](www.mydomain.com) www localhost.localdomain localhost

nslookup mydomain.com 4.2.2.2

Name: mydomain.com
Address: 1.2.3.4

nslookup [www.mydomain.com](www.mydomain.com) 4.2.2.2

Name: [www.mydomain.com](www.mydomain.com)
Address: 1.2.3.4

(same address)

nslookup 1.2.3.4 4.2.2.2

Non-authoritative answer:
4.3.2.1.in-addr.arpa name = mydomain.com


gamil's details would show

from [email]me@mydomain.com[/email]
reply-to [email]me@mydomain.com[/email]
to [email]mygmail@gmail.com[/email]
date thedate
subject thesubject
mailed-by mydomain.com

an error message from a bad address looks like so

Your message did not reach some or all of the intended recipients.

 Subject: thesubject
 Sent: thedate

The following recipient(s) could not be reached:
[email]badaddress@gmail.com[/email] on date
The e-mail account does not exist at the organization this message was sent to.  Check the e-mail address, or contact the recipient directly to find out the correct address.
  < [www.mydomain.com](www.mydomain.com) #5.1.1 SMTP; 550-5.1.1 This Gmail user does not exist. Please try double-checking>

which leads me to believe that it is still claiming that it is [www.mydomain.com](www.mydomain.com) somewhere in the outgoing mail. thus the ptr record would not match because the ptr of the address points to mydomain.com

my SPF record look like this:

mydomain.com	text = "v=spf1 a ptr ~all"


before when my /etc/hosts was missing mydomain.com at the beginning
gmail was showing

from [email]me@mydomain.com[/email]
reply-to [email]me@mydomain.com[/email]
to [email]mygmail@gmail.com[/email]
date thedate
subject thesubject
mailed-by [www.mydomain.com](www.mydomain.com)

so I thought editing the /etc/hosts would fix it.
I'm at a loss on where to go next.

---

