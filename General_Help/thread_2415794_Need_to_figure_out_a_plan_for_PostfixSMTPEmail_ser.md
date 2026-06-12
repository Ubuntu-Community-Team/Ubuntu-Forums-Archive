---
title: "Need to figure out a plan for Postfix/SMTP/Email server - Ubuntu 16.04"
date: 2019-03-31
forum: General Help
---

### Post by peppy3 on 2019-03-31
Greetings,

I need to set up a simple email server with Postfix/SMTP, something I've never done before. I have one server which hosts all of my domain names. I am now setting up a separate server intended to deal with sending emails for all of these domain names. I had something working good on Dreamhost, but they have an SMTP quota of 100 emails per hour. One of my websites is becoming so active that it likely sends out more than 100 emails per hour. Dreamhost has no other solution other than for me to set up my own email server.

Here is what I require:

1) send-only emails - The bulk of the emails are automated notifications sent to site members on an email address like "no-reply@mysite.com".

2) forward-only emails to Gmail - Other emails are simply forwarded to my personal Gmail for me, email addresses like "support@mysite.com".

3) Be able to respond via Gmail - If a member sends a support question to "support@mysite.com", I want it to forward to my personal Gmail account. I would like to respond on Gmail, have it get sent to the user and make it look like it came from "support@mysite.com". This SMTP configuration is already setup with my site email addresses with the way Dreamhost has it hosted. Now I need to be able to do it on my own SMTP email server.

4) Automated security updates, anti-spam, anti-blacklist, email-reliability - I have no idea how any of this works, so it needs to be as simple and automated as possible to secure the emails and prevent unintended blacklist issues that block emails.

5) No mailboxes are required, don't want any emails saved on the server.

6) Emails on 30+ domain names.



How should I set this up? Do people usually install Postfix on the same server as their domain name web hosting server, or put it on a separate email-only server? I read a little bit into the tutorials and I got stuck in the configuration section where it asks for a domain name. If "mysite.com" is suppsoed to be listed as a "hostname" in the postfix configuration, how to do I go about it if it's already hosted on a separate server? Plus what should I do if I plan on having email addresses on 30 different domain names? Do I just have to pick 1 domain name as the main "hostname" on my postfix server or something?

How would I go about the DNS settings if I pick something like "email.mysite.com" as the hostname? Do I set up an "A" record like email.mysite.com > 192.168.1.1 (the IP address of my email server)? Or do I need to set up an MX record?

Thanks
Kind regards

---

### Post by SeijiSensei on 2019-04-01
E-mail is a vastly more difficult service to set up in these days when most mail is spam, and most providers have lots of filters.

Let's start with the DNS side.

Each domain will need to have an MX record that designates the name of the server to which the mail should be sent.

```

@  IN SOA example.com. ....
[...]
      IN MX 0 mail.example.com.

mail  IN A  10.10.10.10

[...]

```

You need to specify the public-facing address in the A record for this machine, not any private addresses in 10. or 192.168.

Even more important these days, though, is to make sure your provider has reverse-resolution established for your server.  You cannot do this yourself.  But many services (Google is one) refuse mail unless there are both hostname=>IP and IP=>hostname records for your server.  I use virtual machines on Linode, where you can set up reverse-resolution from the server's dashboard.  Also, with a virtual machine, there are no limits on traffic or the like.

Usually you can just run the mail and web servers on the same machine.  

To forward mail automatically, you would use the /etc/aliases file that both sendmail and Postfix recognize.  Each entry looks like this:

```

support:     you@gmail.com

```

You need to run the command "sudo newaliases" every time you change this file so the software can rebuild its database.

As far as I know, you cannot use a [email]me@somewhere.else[/email] alias as the From: at gmail unless you buy Google's full mail services for domains.

You could send such mail from your own server though.

You only need to worry about anti-spam, etc., if you are receiving mail.  As I said above, though, you must have DNS correctly configured in both directions to avoid being blocked by spam filters on your recipients' end.

If you have thirty domains, each domain's DNS records must be configured as above.  The MX for domain1.com can be a host in domain2.com, so you just need to put the server in one domain and reference it in the others.  You then have to [tell Postfix]("http://www.postfix.org/postconf.5.html#mydestination") the names of all the domains for which it validly accepts mail.

---

### Post by peppy3 on 2019-04-01
Thanks for the info, I've decided to set up Postfix on the same server as my websites. With DNS settings:

email.mysite.com > A Record > [public-facing IP ***.***.***.***]
MX Record > 10 email.mysite.com

When I installed Postfix, it asked for the "System Mail Name" in the "Internet Site" setup. I entered in "mysite.com". Does this sound correct? I'm not sure what to do next. 

First, I would like to set up one email address "peppy@mysite.com" and then send an email to an external test email account. Ultimately, I'm going to have something called phpmailer that will send automated notifications to members, using something like:

    ```

    require("phpmailer/PHPMailerAutoload.php");
    $mail = new PHPMailer();
            
    $mail->IsSMTP();                                      // set mailer to use SMTP
    $mail->Host = "email.mysite.com";  // specify main and backup server
    $mail->SMTPAuth = true;     // turn on SMTP authentication
      $mail->Username = "peppy@mysite.com";        // Make sure to replace this with your shell enabled user
      $mail->Password = "******";      // Make sure to use the proper password for your user
         
    $mail->From = "peppy@mysite.com";
    $mail->FromName = "MySite.com Notification From Peppy";
    $mail->AddAddress("test@yahoo.com");


    $mail->AddReplyTo("peppy@mysite.com");
            
    $mail->IsHTML(false);                                  // set email format to HTML
    
    $mail->SMTPOptions = array(
      'ssl' => array(
        'verify_peer' => false,
        'verify_peer_name' => false,
        'allow_self_signed' => true
      )
    );
            
    $mail->Subject = 'This is a test subject';
    $mail->Body    = 'This is a test message body';
    $mail->Send();
```


If I have 30+ domains, the "$mail->Host" variable in their PHP scripts is always going to be "email.mysite.com", right? I think the next step is getting one individual email address to work, like how do I get "peppy@mysite.com" to work? I read a little bit into aliases. Preferably, I don't want to have a ton of separate Unix usernames for each individual email address, especially since some of my website usernames are the exact same name as the user is my email addresses. Although maybe I could create a Unix username in email format like "peppy@mysite.com" (if the Unix usernames are even required)?

---

### Post by SeijiSensei on 2019-04-02
An alias like the one above for "support@mysite.com" might be the best approach.  You don't need to set up a local mailbox for support.  Mail that arrives addressed to that name gets forwarded immediately to the destination.  So you could use support@ with every domain the box receives mail for, and all the mail would go to the aliased destination.

PHPMailer seems like a lot of work.  Usually I just use [PHP's native mail() function]("https://www.php.net/manual/en/function.mail.php").

```

<?php

$from="support@mysite.com";
$to="someone@example.com";
$subject="Here's a sample email!";
$body=
"This is the first line of the body.

This is the next line of the body.

This is the end of the body.
";

mail($to,$from,$subj,$body);

?>

```

Now there's a subtle issue with sending mail from PHP regardless of the method you use.  Every email message actually has two From addresses.  One is the From: in the body represented by $from above.  However there's also something called the "envelope sender" which may, or may not, be the same as the From: in the body.  (If you expose the full headers of an email message, the top line is almost always "Return-Path: [email]someone@example.com[/email]".  That's the envelope sender's addresss.)  

If you send mail with PHP, the envelope sender is likely to be "www-data@myserver.mysite.com" because PHP scripts are run with the same UID as the web server, usually "www-data". The envelope address is the one remote servers see and use to determine if something might be spam.  As a result, it's often preferable to let the mail software alter the header to something like "bounce@mysite.com" which will match your DNS records.  Then you can have a "bounce:" alias for each domain just like "support."  I don't know how to do this in Postfix since I use sendmail, but I'm sure there's documentation.

If everything is configured correctly, you can force a sender address with a fifth parameter to mail():
```

<?php
mail($to,$from,$subj,$body,"-f bounce@mysite.com");
?>

```
See the "additional_headers" parameter in the documentation for mail() cited above.

Doesn't sound like you worked out reverse name-resolution yet.  It's pretty mandatory these days for mail servers.

---

