---
title: "[SOLVED] SendMail / Contact us / PHP Form &amp;amp; server programs (help)"
date: 2008-01-04
forum: General Help
---

### Post by Syndacate on 2008-01-04
Gah, okay, I've been trying to create a HTML form, you fill it out - with a PHP page, etc. etc.

It says "successful" but no e-mail is sent - so a friend suggested that I needed the program "sendmail" - so I installed that - and not only did it not work, but it adds like a full 60 seconds to boot time trying to load that stupid thing.  

So few questions:
- Is sendmail necessary to make a contact form (with the migration of pple to web based mail, "mailto:X" just isn't cutting it - too old and archaic.

I woulda thought there would have been a internet forum here but apparently not.

I'm trying to get this damn PHP post script to work - it's not working, Grrrrrr

Any help?


Is anybody good with PHP?

(BTW:, the phpino() works - PHP isn't dead here), but I feel databases are going to be in need soon for a better "upload" system than that PHP **** I have now (just a put kinda deal).

---

### Post by MJN on 2008-01-04
The standard PHP mail() function does indeed require a backend mail service (even if it's just the sendmail binary) to function.

I don't use Sendmail (Postfix instead) but I do recall from my Red Hat days that it used to cause a massive delay during bootup - it turns out it was trying to resolve its own name - localhost.localdomain - yet my /etc/hosts only had localhost listed and so this lookup would eventually timeout and allowing the boot to continue. Hence, try adding localhost.localdomain (or whatever your Sendmail config thinks is its name) to the 127.0.0.1 localhost <and other aliases> line and see how you go.

Regarding your PHP problems I have gradually built up a contact form which also uses CAPTCHA verification (a PHP script written by someone else) to avoid spam. See [http://www.newtonnet.co.uk/contact](http://www.newtonnet.co.uk/contact) and if you're interested I'd be happy to send the script(s) to you (hey, submit a message via the form for the full experience!).

Mathew

P.S. What did you mean about the lack of an Internet forum? Doesn't this count?

---

### Post by Syndacate on 2008-01-05
> **MJN said:**
> The standard PHP mail() function does indeed require a backend mail service (even if it's just the sendmail binary) to function.

I don't use Sendmail (Postfix instead) but I do recall from my Red Hat days that it used to cause a massive delay during bootup - it turns out it was trying to resolve its own name - localhost.localdomain - yet my /etc/hosts only had localhost listed and so this lookup would eventually timeout and allowing the boot to continue. Hence, try adding localhost.localdomain (or whatever your Sendmail config thinks is its name) to the 127.0.0.1 localhost <and other aliases> line and see how you go.

Regarding your PHP problems I have gradually built up a contact form which also uses CAPTCHA verification (a PHP script written by someone else) to avoid spam. See [http://www.newtonnet.co.uk/contact](http://www.newtonnet.co.uk/contact) and if you're interested I'd be happy to send the script(s) to you (hey, submit a message via the form for the full experience!).

Mathew

P.S. What did you mean about the lack of an Internet forum? Doesn't this count?

By lack of an internet forum I mean a part of the forum directed at web design.

I ripped the script from some page and edited it to my own use - it's nothing commercial or anything, just a simple script for people to send me mail - I usually just post my address but with everybody's flock to webmail the mailto: is kind of archaic and useless.

I'm not hosting through /etc/hosts - I'm hosting through apache - /var/www.

I'm not sure where the sendmail config is, but I'll look for it, and see if I can add that.

My PHP script doesn't need to be super advanced, it's not like I run a commercial website or anything - I just want to give people the ability to contact me w/o accessing their web mail if they encounter a file error or something on my server.

It's more of a file server than it is a site - but it's got a basic cheap-**** thrown together web-page to take up the "It Works!" as apache's default index.html page - so call it what you wish.

Guess I need somebody to look at the PHP script and tell me what's wrong with it (even though that does seem lazy) - because I'm not really PHP knowledgeable - I just took the script off a site that had it posted for free and edited it to my liking/usage - but it's not working.  I don't think it's a problem with the script - i think it's a problem with my software, with sendmail and such or whatever, but I don't know :-\

I probably should have put this in the beginner forum :-\ - (refer to sig).

The script is showing 'sucess' so it's not encountering errors - but it's not sending, so I'm guessing the problem enlies with sendmail.  I only installed it - I haven't configured it, so maybe something's off.

EDIT:
Wow, the sendmail folder has A LOT of files in it - I have no idea which to edit or even look at :-\

---

### Post by Syndacate on 2008-01-05
*Bump

Anybody?

---

### Post by Syndacate on 2008-01-11
Could somebody tell me the exact location of this file/what to update - this long *** boot time is annoying me - sendmail isn't working anyways (it doesn't send an e-mail by form (php mail())).

---

### Post by #Reistlehr- on 2008-01-11
can you paste or pm me your script so i can look at it? Also, what version PHP are you using (i hope you say 5)

Did you install php from repo?

---

### Post by freymann on 2008-01-11
> **Syndacate said:**
> 
I ripped the script from some page and edited it to my own use - it's nothing commercial or anything, just a simple script for people to send me mail

 Hopefully it has some kind of 'sanitizer' code in it to prevent the spammers from trying to use it to send crap through.

> I'm not hosting through /etc/hosts - I'm hosting through apache - /var/www.

 I think you've confused these two things, which is fine.

 /etc/hosts is a nice little file where you can set up some simple DNS for your local network. That is to say, you can tell your computer that 192.168.1.1 is mygateway.mynetwork and things like that. 

 If sendmail is taking forever to load up when you restart, the delay is usually sendmail trying to figure out what the local machine's name is. It eventually times out, and your boot process carries on.

 /var/www/ is the root directory of your web tree.

> The script is showing 'sucess' so it's not encountering errors - but it's not sending.

 This isn't all that uncommon. You can look inside /var/log/apache2 for more details. You may find something in error.log and/or access.log that may point you in the right direction.

 I loaded up Ubuntu 7.10 server thinking it would be easier to end up with a LAMP installation. My install process included the installation of a MTA (which wasn't sendmail). Even so, it will emulate sendmail 'call wise'. I'm assuming the installation of a MTA doesn't happen with Desktop?

 There is so much to look at when trying to get PHP's mail() function to work.

 For starters, look in your web server's error.log and/or access.log and see if there are any complaints about the mail() function noted in there.

 There are simple tests you can do from the command line to see if sendmail is active, etc. 

 ```
telnet localhost 25
```

 for instance should give you something.

 Can you post a snippet of your PHP code around the mail() call?

 And unfortunately, I'm off to bed so I won't be around to respond further till morning.

---

### Post by Syndacate on 2008-01-12
> **#Reistlehr-]an you paste or pm me your script so i can look at it? Also, what version PHP are you using (i hope you say 5)

Did you install php from repo?[/quote]

Which script?  The PHP mail script I'm trying to use?

PHP version = 5.2.3-1ubuntu6.2

Please know that I don't know PHP - and I'm not that computer savvy - I took the code from it being free take on a website and modified it to my own use.

[QUOTE=freymann said:**
> Hopefully it has some kind of 'sanitizer' code in it to prevent the spammers from trying to use it to send crap through.

No, it's a private thing though - it's not like I'm hosting a big business or anything.  It would be a simple "mailto:" at the bottom of my page, but with everybody going webmail, mailto is kinda archaic.

> **freymann] I think you've confused these two things, which is fine.

 /etc/hosts is a nice little file where you can set up some simple DNS for your local network. That is to say, you can tell your computer that 192.168.1.1 is mygateway.mynetwork and things like that. [/quote]

Yeah, I figured that out later today (after I made that post).

Could you give me an example of what "mygateway.mynetwork" is?  I've seen that in a few places while doing research on the subject - but I just need an example - doesn't have to be real or anything but that syntaxing doesn't help me too much :(.

[QUOTE=freymann] If sendmail is taking forever to load up when you restart, the delay is usually sendmail trying to figure out what the local machine's name is. It eventually times out, and your boot process carries on.[/quote]

Yeah, I figured this out from doing research, but I don't know how to "tell" it what the name is.  Somebody said to go to /etc/hosts and add this line to my "127.0.0.1 localhost" line but I'm not sure exactly the syntaxing to add it (as saying stuff like "mygateway" doesn't mean a whole lot to me).

[QUOTE=freymann] /var/www/ is the root directory of your web tree.[/quote]

Yeah, I'm serving all my files out of there.

[QUOTE=freymann] This isn't all that uncommon. You can look inside /var/log/apache2 for more details. You may find something in error.log and/or access.log that may point you in the right direction.[/quote]

Besides a bunch of 404 errors, the only things I found was this in **error.log**

```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```
I'm using a domain service though (no-ip) - I'm not sure if that makes a difference or anything.

[QUOTE=freymann]
 I loaded up Ubuntu 7.10 server thinking it would be easier to end up with a LAMP installation. My install process included the installation of a MTA (which wasn't sendmail). Even so, it will emulate sendmail 'call wise'. I'm assuming the installation of a MTA doesn't happen with Desktop?[/quote]  

No, I installed it after somebody told me I needed it for my php mail() script to work.

[QUOTE=freymann]There is so much to look at when trying to get PHP's mail() function to work.[/quote] 

Tell me about it, and being not very computer savvy doesn't help the process any.

[QUOTE=freymann] For starters, look in your web server's error.log and/or access.log and see if there are any complaints about the mail() function noted in there.[/quote]

My **error.log** file is posted above, aside from that just a bunch of 404's (page/file not found).

As for **access.log** I just found the weirdest thing:
```
[Fri Jan 11 19:55:21 2008] [error] [client 129.21.15.131] File does not exist: /var/www/document
[Fri Jan 11 19:55:21 2008] [error] [client 129.21.15.131] File does not exist: /var/www/documents
[Fri Jan 11 19:55:21 2008] [error] [client 129.21.15.131] File does not exist: /var/www/download
[Fri Jan 11 19:55:21 2008] [error] [client 129.21.15.131] File does not exist: /var/www/downloads
[Fri Jan 11 19:55:22 2008] [error] [client 129.21.15.131] File does not exist: /var/www/hidden
[Fri Jan 11 19:55:22 2008] [error] [client 129.21.15.131] File does not exist: /var/www/hlstats
[Fri Jan 11 19:55:22 2008] [error] [client 129.21.15.131] File does not exist: /var/www/htbin
[Fri Jan 11 19:55:22 2008] [error] [client 129.21.15.131] File does not exist: /var/www/htdocs
[Fri Jan 11 21:10:21 2008] [error] [client 129.21.113.70] File does not exist: /var/www/favicon.ico
[Fri Jan 11 21:10:21 2008] [error] [client 129.21.113.70] File does not exist: /var/www/favicon.ico
[Fri Jan 11 21:10:21 2008] [error] [client 129.21.113.70] File does not exist: /var/www/favicon.ico
[Fri Jan 11 21:45:38 2008] [error] [client 129.21.15.131] File does not exist: /var/www/login.htm
[Fri Jan 11 21:45:46 2008] [error] [client 129.21.15.131] File does not exist: /var/www/intruvert
[Fri Jan 11 23:32:30 2008] [error] [client 129.21.15.131] File does not exist: /var/www/login.htm

```

I just found this - EXTREMELY weird - that's my error.log though, as for my **access.log**

What the **** is this?  Some weak kind of hack attempt?  It has the same pre-fix as my school (my IP starts with 129.21) - it's asking for every file under the sun?  What the shit?  Hack attempt?  There's a laundry list of this **** - none of which I requested, and the IP isn't mine, so it's not my computer looking for stuff.

```

129.21.15.131 - - [11/Jan/2008:19:55:21 -0500] "GET /cgiwin/ HTTP/1.1" 404 311 "-" "Mozilla/4.0 (compatible said:**
>  "GET /class/ HTTP/1.1" 404 310 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0)"
129.21.15.131 - - [11/Jan/2008:19:55:21 -0500] "GET /classes/ HTTP/1.1" 404 312 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0)"
129.21.15.131 - - [11/Jan/2008:19:55:21 -0500] "GET /config/ HTTP/1.1" 404 311 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0)"
129.21.15.131 - - [11/Jan/2008:19:55:21 -0500] "GET /credit/ HTTP/1.1" 404 311 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0)"

```

My information shows up like this:
```
[11/Jan/2008:23:51:05 -0500] "GET /phptest101.php?=PHPE9568F34-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 2524 "http://syndacate.no-ip.org/phptest101.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11

```

I think somebody's trying to hack my system or something - now I'm all scared - what the shit??  Only like 3 people know about this (I generally use it to transfer files to my computer from other places or distribute files to other people that don't have FTP equip) - and none of them are computer savvy enough to put up a script that searches for random files like that..and none of them are campus -- which is where the IP is from??

Also, it's only in access.log - it's not in access.log.1 - it must have started recently or something...

[QUOTE=freymann]There are simple tests you can do from the command line to see if sendmail is active, etc. 

 ```
telnet localhost 25
```

 for instance should give you something.

It returned:
```
$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 syndacate-desktop ESMTP Sendmail 8.14.1/8.14.1/Debian-8ubuntu1; Sat, 12 Jan 2008 00:14:28 -0500; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
```

> **freymann]
 Can you post a snippet of your PHP code around the mail() call?[/quote]

I'll post the whole thing for ya - I don't know anything about PHP and I took the script from some online source that had it for free and edited it.

```
<title>Sendemail Script</title>
</head>
<body>

<?php

$ip = $_POST['ip'] said:**
> ;
$httpagent = $_POST['httpagent'];
$visitor = $_POST['visitor'];
$visitormail = $_POST['visitormail'];
$notes = $_POST['notes'];
$attn = $_POST['attn'];


if (eregi('http:', $notes)) {
die ("Do NOT try that! ! ");
}
if(!$visitormail == "" && (!strstr($visitormail,"@") || !strstr($visitormail,".")))
{
echo "<h2>Use Back - Enter valid e-mail</h2>\n";
$badinput = "<h2>Feedback was NOT submitted</h2>\n";
echo $badinput;
die ("Go back! ! ");
}

if(empty($visitor) || empty($visitormail) || empty($notes )) {
echo "<h2>Use Back - fill in all fields</h2>\n";
die ("Use back! ! ");
}

$todayis = date("l, F j, Y, g:i a") ;

$attn = $attn ;
$subject = $attn;

$notes = stripcslashes($notes);

$message = " $todayis [EST] \n
Attention: $attn \n
Message: $notes \n
From: $visitor ($visitormail)\n
Additional Info : IP = $ip \n
Browser Info: $httpagent \n
Referral : $httpref \n
";

$from = "From: $visitormail\r\n";


mail("boostedSOHC@gmail.com", $subject, $message, $from);

?>

<p align="center">
Date: <?php echo $todayis ?>
<br />
Thank You : <?php echo $visitor ?> ( <?php echo $visitormail ?> )
<br />

Attention: <?php echo $attn ?>
<br />
Message:<br />
<?php $notesout = str_replace("\r", "<br/>", $notes);
echo $notesout; ?>
<br />
<?php echo $ip ?>

<br /><br />
<a href="email.php">Send Another E-mail To The Administrator</a>
</p>

</body>
</html>
```

[quote=freymann]
 And unfortunately, I'm off to bed so I won't be around to respond further till morning.

NP

Now I'm all scared shitless about this crap?  Is it a hack attempt?  Maybe the RIT network testing shit?

The hell?

---

### Post by freymann on 2008-01-12
> **Syndacate said:**
> 
No, it's a private thing though - it's not like I'm hosting a big business or anything.  It would be a simple "mailto:" at the bottom of my page, but with everybody going webmail, mailto is kinda archaic.

 I believe what we're trying to tell you is that even though you want to use it for a private thing, others WILL FIND YOU whether you like it or not, simply because you now have port 80 (and possibly 25) listening and those scanning IP blocks WILL FIND YOU.

> Somebody said to go to /etc/hosts and add this line to my "127.0.0.1 localhost" line but I'm not sure exactly the syntaxing to add it

 It's actually pretty well like that. You could click on System->Administration->Network and click on the Hosts tab. See if you don't already have the entry in there (usually you'll see it at the very top). 

 How are you assigned your IP address? if it's static you may want to add that IP number and an alias.

```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

 Don't worry about this for now. I think my apache server stilll complains about that and I'm just too lazy to make it happy.

> I just found the weirdest thing:
```
[Fri Jan 11 19:55:21 2008] [error] [client 129.21.15.131] File does not exist: /var/www/document
[Fri Jan 11 19:55:21 2008] [error] [client 129.21.15.131] File does not exist: /var/www/documents
[Fri Jan 11 19:55:21 2008] [error] [client 129.21.15.131] File does not exist: /var/www/download
[Fri Jan 11 19:55:21 2008] [error] [client 129.21.15.131] File does not exist: /var/www/downloads
[Fri Jan 11 19:55:22 2008] [error] [client 129.21.15.131] File does not exist: /var/www/hidden
[Fri Jan 11 19:55:22 2008] [error] [client 129.21.15.131] File does not exist: /var/www/hlstats
[Fri Jan 11 19:55:22 2008] [error] [client 129.21.15.131] File does not exist: /var/www/htbin
[Fri Jan 11 19:55:22 2008] [error] [client 129.21.15.131] File does not exist: /var/www/htdocs
[Fri Jan 11 21:10:21 2008] [error] [client 129.21.113.70] File does not exist: /var/www/favicon.ico
[Fri Jan 11 21:10:21 2008] [error] [client 129.21.113.70] File does not exist: /var/www/favicon.ico
[Fri Jan 11 21:10:21 2008] [error] [client 129.21.113.70] File does not exist: /var/www/favicon.ico
[Fri Jan 11 21:45:38 2008] [error] [client 129.21.15.131] File does not exist: /var/www/login.htm
[Fri Jan 11 21:45:46 2008] [error] [client 129.21.15.131] File does not exist: /var/www/intruvert
[Fri Jan 11 23:32:30 2008] [error] [client 129.21.15.131] File does not exist: /var/www/login.htm

```

 Fun eh. Your web server is available to everyone and everyone and they are scanning your machine for popular filenames, and when they find a match there's a good chance they'll be back to knock a little harder.

 This is part of the reason why I suggested your contact script should contain some sanitizer code to give those hackers a hard time.

 If you don't have the scripts they are looking for, that's great. If you do have the scripts and they have no bugs or known exploits, that's good too. You can't get rid of them unless you add some firewall rules that only allow traffic from known sources, but if you want your contact form to be available to anybody, well, that solution isn't going to work.

> Also, it's only in access.log - it's not in access.log.1 - it must have started recently or something...

 The system automatically 'rotates' log files for you. the access.log.1 is simply an older log file which may eventually be called .2 and .3 until you have as many as defined at once time and then it's first it/last out kinda thing. This is normal and good.

```
$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 syndacate-desktop ESMTP Sendmail 8.14.1/8.14.1/Debian-8ubuntu1; Sat, 12 Jan 2008 00:14:28 -0500; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
```

 This is great. Sendmail is working!

 What is this syndacate-no-ip thang? Is this a domain that is running on your local computer? you have to tell it what your IP # is and then traffic is pointed to your machine? Dynamic DNS style?

 If syndacate.no-ip.org is your "domain name" then you should put that into your local DNS. Where you were told to add 127.0.0.1 localhost you should also add your local IP number and syndacate.no-ip.org in there too.

 To clarify, my computer has an internal IP address (192.168.0.220) and I'm behind a router. The router is given a 'real' IP address which I then tell my DynDNS profile about. My router is told to forward port 80 to my internal IP address. DynDNS then points mydomain.homeunix.com to my real ip address (on the WAN side). When somebody types in my domain name, they are directed to my WAN IP # (my router) which in turns will send port 80 requests to my inside (private LAN) IP # and they see my web page.

 If you don't have a router but are given a static IP number which is "live" on the internet, you're pretty well doing much of the same thing, except you don't have to worry about port forwarding.

 Setting up your local DNS will make sendmail happy. You should also edit /etc/hostname to jive... 

```
sudo gedit /etc/hostname
```

 Right now it likely just says "syndacate-desktop" -- make it syndacate.no-ip.org instead.

 That may please sendmail and apache when your hostname and local DNS are talking the same thing.

 The PHP Script you're using isn't too bad. It has some small checks for abuse that may do well. You never see any errors when the mail isn't sent because there's no error checking around the mail() call.

 I usually code something like this:

```


if ( mail("boostedSOHC@gmail.com", $subject, $message, $from) ) { 
    // Success. Log it or whatever
} else { 
    // Failure; Log it or whatever
}

```

 At least this way you stand a good chance of knowing if the mail sending function fails.

 However, one other thing you now need to worry about is making sendmail able to deliver email to outside servers.

 For your IP, are there any restrictions on server ports? My ISP blocks ports and prevents me from running a full-fledged email server. I can't have sendmail accept any incoming emails from the outside and I'm only able to send mail out through my ISP's SMTP server, so I had to make a small change to sendmail.cf to tell sendmail what outbound SMTP server to use (which works fine). 

 I don't have any incoming email from my DynDns domain, nor do I want any.

 I think you can test this fairly easily by doing this at the command line:

```

sendmail -v boostedSOHC@gmail.com |echo testing

```

 (it's been a while since I've had to do that so I'm sure about the syntax. Don't worry if it fails with a syntax error)

 This *should* show you what sendmail is doing as it attempts to deliver your message. If there's a problem you most likely will be able to tell where.

 That should keep you busy for a while. Let me know how you make out.

---

### Post by Syndacate on 2008-01-12
> **freymann said:**
> I believe what we're trying to tell you is that even though you want to use it for a private thing, others WILL FIND YOU whether you like it or not, simply because you now have port 80 (and possibly 25) listening and those scanning IP blocks WILL FIND YOU.

:(

> **freymann] It's actually pretty well like that. You could click on System->Administration->Network and click on the Hosts tab. See if you don't already have the entry in there (usually you'll see it at the very top). 

 How are you assigned your IP address? if it's static you may want to add that IP number and an alias.[/quote]

I just did that and added my IP - my IP's are static - assigned / outlet here in the dorms, don't change, I have 2 outlets, 2 IP's (no router necessary :-D).  So I added the one this computer uses - I'll see if that helps any.  I'm assuming the alias doesn't matter?

[QUOTE=freymann]```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

 Don't worry about this for now. I think my apache server stilll complains about that and I'm just too lazy to make it happy.[/quote]

Yeah, it's not bogging out completely like sendmail is.

[QUOTE=freymann]```
[Fri Jan 11 19:55:21 2008] [error] [client 129.21.15.131] File does not exist: /var/www/document
[Fri Jan 11 19:55:21 2008] [error] [client 129.21.15.131] File does not exist: /var/www/documents
[Fri Jan 11 19:55:21 2008] [error] [client 129.21.15.131] File does not exist: /var/www/download
[Fri Jan 11 19:55:21 2008] [error] [client 129.21.15.131] File does not exist: /var/www/downloads
[Fri Jan 11 19:55:22 2008] [error] [client 129.21.15.131] File does not exist: /var/www/hidden
[Fri Jan 11 19:55:22 2008] [error] [client 129.21.15.131] File does not exist: /var/www/hlstats
[Fri Jan 11 19:55:22 2008] [error] [client 129.21.15.131] File does not exist: /var/www/htbin
[Fri Jan 11 19:55:22 2008] [error] [client 129.21.15.131] File does not exist: /var/www/htdocs
[Fri Jan 11 21:10:21 2008] [error] [client 129.21.113.70] File does not exist: /var/www/favicon.ico
[Fri Jan 11 21:10:21 2008] [error] [client 129.21.113.70] File does not exist: /var/www/favicon.ico
[Fri Jan 11 21:10:21 2008] [error] [client 129.21.113.70] File does not exist: /var/www/favicon.ico
[Fri Jan 11 21:45:38 2008] [error] [client 129.21.15.131] File does not exist: /var/www/login.htm
[Fri Jan 11 21:45:46 2008] [error] [client 129.21.15.131] File does not exist: /var/www/intruvert
[Fri Jan 11 23:32:30 2008] [error] [client 129.21.15.131] File does not exist: /var/www/login.htm

```

 Fun eh. Your web server is available to everyone and everyone and they are scanning your machine for popular filenames, and when they find a match there's a good chance they'll be back to knock a little harder.[/quote]

Yeah, I noticed that - I didn't realize anybody on RIT's campus used bots to try to get into peoples' ****.  I have no idea what I'm going to do now.

[QUOTE=freymann] This is part of the reason why I suggested your contact script should contain some sanitizer code to give those hackers a hard time.[/quote]

That wouldn't work against this common page scanning that somebody's doing with a bot.

[QUOTE=freymann] If you don't have the scripts they are looking for, that's great. If you do have the scripts and they have no bugs or known exploits, that's good too. You can't get rid of them unless you add some firewall rules that only allow traffic from known sources, but if you want your contact form to be available to anybody, well, that solution isn't going to work.[/quote]

Yeah but the bot they're using is using name matches on pages - all I have to do is be careful what i name ****.

[QUOTE=freymann] The system automatically 'rotates' log files for you. the access.log.1 is simply an older log file which may eventually be called .2 and .3 until you have as many as defined at once time and then it's first it/last out kinda thing. This is normal and good.[/quote]

Oh, I see.

[QUOTE=freymann]```
$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 syndacate-desktop ESMTP Sendmail 8.14.1/8.14.1/Debian-8ubuntu1 said:**
> 
```

 This is great. Sendmail is working!

Yeah but it's not doing anything, lol.

> **freymann] What is this syndacate-no-ip thang? Is this a domain that is running on your local computer? you have to tell it what your IP # is and then traffic is pointed to your machine? Dynamic DNS style?

 If syndacate.no-ip.org is your "domain name" then you should put that into your local DNS. Where you were told to add 127.0.0.1 localhost you should also add your local IP number and syndacate.no-ip.org in there too.[/quote]

Gotcha, now it's added is:
```
127.0.0.1
127.0.1.1
syndacate.no-ip.org
```

Add the external too, or no?

[QUOTE=freymann] To clarify, my computer has an internal IP address (192.168.0.220) and I'm behind a router. The router is given a 'real' IP address which I then tell my DynDNS profile about. My router is told to forward port 80 to my internal IP address. DynDNS then points mydomain.homeunix.com to my real ip address (on the WAN side). When somebody types in my domain name, they are directed to my WAN IP # (my router) which in turns will send port 80 requests to my inside (private LAN) IP # and they see my web page.[/quote]

Yeah, I know all that - I had to do it when I was hosting my server out of my house (which went through a router) - also had to port forward for some games :-\ - but my point was that I don't get what things like "homeunix" mean - and other things like that people used.

[QUOTE=freymann]
 If you don't have a router but are given a static IP number which is "live" on the internet, you're pretty well doing much of the same thing, except you don't have to worry about port forwarding.

 Setting up your local DNS will make sendmail happy. You should also edit /etc/hostname to jive... [

```
sudo gedit /etc/hostname
```

 Right now it likely just says "syndacate-desktop" -- make it syndacate.no-ip.org instead.

 That may please sendmail and apache when your hostname and local DNS are talking the same thing.
[/quote]

Alright, I changed it.

[QUOTE=freymann]
 The PHP Script you're using isn't too bad. It has some small checks for abuse that may do well. You never see any errors when the mail isn't sent because there's no error checking around the mail() call.

 I usually code something like this:

```


if ( mail("boostedSOHC@gmail.com", $subject, $message, $from) ) { 
    // Success. Log it or whatever
} else { 
    // Failure said:**
> 

It doesn't that I'm aware of - but then again, it is a college network.  I don't really know anything about the coding because I don't know/use PHP - like I said - I ripped the script from some site dealing 'em for free.

[QUOTE=freymann] I don't have any incoming email from my DynDns domain, nor do I want any.

 I think you can test this fairly easily by doing this at the command line:

```

sendmail -v boostedSOHC@gmail.com |echo testing

```

 (it's been a while since I've had to do that so I'm sure about the syntax. Don't worry if it fails with a syntax error)

 This *should* show you what sendmail is doing as it attempts to deliver your message. If there's a problem you most likely will be able to tell where.

 That should keep you busy for a while. Let me know how you make out.

Naw, it actually echoed the word "testing" ;) - ha, and now it's just hanging - I'm not sure if it's doing anything - or it just went "blah" after that.

Thanks, I'll mess with the syntaxing - see if I can get it to send.

---

### Post by freymann on 2008-01-12
> **Syndacate said:**
> 
I just did that and added my IP - my IP's are static - assigned / outlet here in the dorms, don't change, I have 2 outlets, 2 IP's (no router necessary :-D).  So I added the one this computer uses - I'll see if that helps any.  I'm assuming the alias doesn't matter?

 What you need to do is set up your local DNS (via /etc/hosts) so that syndacate.no-ip.org relates to your internal IP address.

 127.0.0.1 should be localhost.syndacate.no-ip.org
 a.b.c.d should be syndacate.no-ip.org

in your /etc/hosts file. (a.b.c.d being the IP you are using, which looks like 129.21.110.30 to me.

 If you've made your /etc/hostname contain "syndacate.no-ip.org" (and only that) then you are on your way to calming down sendmail and apache. You may have to reboot to get these new settings in place.

> 
Yeah, I noticed that - I didn't realize anybody on RIT's campus used bots to try to get into peoples' ****.  I have no idea what I'm going to do now.


 It could be windoze users that are infected, unknowingly. Very common in a dorm situation. They probably aren't picking on your specific ip, but rather scanning an entire IP block for 'hits' so don't take it personally. lol

> 
Naw, it actually echoed the word "testing" ;) - ha, and now it's just hanging - I'm not sure if it's doing anything - or it just went "blah" after that.

 I used to know the syntax that would send a simple testing message to somebody and allow you to see all the things sendmail would do to deliver it, which would help you determine delivery problems. Oh well, that's not too important at the moment. 

 What you need to find out is if your local machine can deliver mail to outside servers. Your PHP script is going to rely on PHP's mail() function, which rely's on sendmail, so that will be your next thing to check out.

 You could try this though:

```

    $ /usr/sbin/sendmail email-address
    enter body of message
    CTRL-D

```

The CTRL-D is a end of message code for standard-in.

 Then see if your email was delivered OK.

 Ok, so where does that leave us? lol

---

### Post by Syndacate on 2008-01-14
> **freymann said:**
> What you need to do is set up your local DNS (via /etc/hosts) so that syndacate.no-ip.org relates to your internal IP address.

 127.0.0.1 should be localhost.syndacate.no-ip.org
 a.b.c.d should be syndacate.no-ip.org

in your /etc/hosts file. (a.b.c.d being the IP you are using, which looks like 129.21.110.30 to me.

K, Done.

> **freymann said:**
>  If you've made your /etc/hostname contain "syndacate.no-ip.org" (and only that) then you are on your way to calming down sendmail and apache. You may have to reboot to get these new settings in place.

Okay, gotcha.

> **freymann said:**
>  It could be windoze users that are infected, unknowingly. Very common in a dorm situation. They probably aren't picking on your specific ip, but rather scanning an entire IP block for 'hits' so don't take it personally. lol

Yeah, probably some guy just bored - it's the **** people at RIT do when they're bored...

> **freymann said:**
>  I used to know the syntax that would send a simple testing message to somebody and allow you to see all the things sendmail would do to deliver it, which would help you determine delivery problems. Oh well, that's not too important at the moment. 

 What you need to find out is if your local machine can deliver mail to outside servers. Your PHP script is going to rely on PHP's mail() function, which rely's on sendmail, so that will be your next thing to check out.

 You could try this though:

```

    $ /usr/sbin/sendmail email-address
    enter body of message
    CTRL-D

```

The CTRL-D is a end of message code for standard-in.

 Then see if your email was delivered OK.

 Ok, so where does that leave us? lol

Yeah, I did that, and I received the messages (it works).

---

### Post by freymann on 2008-01-14
> **Syndacate said:**
> Yeah, I did that, and I received the messages (it works).

 Ok, so now we can go back to your PHP script...

 What happens when you try it now?

---

### Post by Syndacate on 2008-01-16
Sorry for the long response, I've been very busy with school and only came on here a few times to bump topics (yes, plural) that had no responses.

I used it now and it worked 100%.

I tried to trace back the steps we went through - but I'm not even sure what the problem is and where we fixed it...

I gotta learn PHP so I don't have to go through this crap, although even if I did know how to make the script instead of taking it, I reckon I still would have had this problem as I don't think the problem was in the script as per what we changed.

---

### Post by freymann on 2008-01-16
> **Syndacate said:**
> Sorry for the long response, I've been very busy with school and only came on here a few times to bump topics (yes, plural) that had no responses.

I used it now and it worked 100%.

 That's great! 

 I think some of it had to do with setting up your DNS properly so sendmail was happy.

 Maybe you can click on the thread tools link at the top and set this thread to SOLVED then.

 Enjoy!

---

### Post by Syndacate on 2008-01-16
> **freymann said:**
> That's great! 

 I think some of it had to do with setting up your DNS properly so sendmail was happy.

 Maybe you can click on the thread tools link at the top and set this thread to SOLVED then.

 Enjoy!

Yeah - THANKS  a lot man

---

