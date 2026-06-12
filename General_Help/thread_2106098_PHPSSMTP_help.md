---
title: "PHP/SSMTP help"
date: 2013-01-18
forum: General Help
---

### Post by hootie318 on 2013-01-18
I apologize if I am not supposed to post this here but I am having trouble using a PHP mail() command to send comments to my email from my ubuntu server 12.4
 
I am using SSMTP for the mail client. I think I have things configured properly but I doubt it since nothing works.
 
I am posting the php file and the ssmtp config file hoping someone can offer some advice? It would be greatly appreciated.
 
PHP FILE------------
<?php
  $name = $_REQUEST['name'] ;
  $email = $_REQUEST['email address'] ;
  $message = $_REQUEST['comments'] ;
  mail( [EMAIL="myemail@cox.net"]myemail@cox.net[/EMAIL], "Customer Comments",
    $message, "From: $name, $email" );
  header( "Location: thankyou.html" );
?>
 
SSMTP.CONF file---------------
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=postmaster
# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=smtp.east.cox.net:587
AuthUser="my account login"
AuthPass="my password"
UseTLS=YES
UseSTARTTLS=YES
# Where will the mail seem to come from?
#rewriteDomain=cox.net
# The full hostname
hostname=cox.net
# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
#FromLineOverride=YES

 
I complete the form and the thank you page loads, but no email is sent. I tried sending from the terminal line (I receive an error from cox so I must be getting somewhere) but the mail will not send.

---

