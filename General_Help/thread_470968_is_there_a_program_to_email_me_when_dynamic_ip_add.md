---
title: "is there a program to email me when dynamic ip address changes"
date: 2007-06-11
forum: General Help
---

### Post by harty83 on 2007-06-11
I use a dnsexit dynamic dns and the stupid program that updates my ip address always seems to fail while I'm out and about and have need to get to my home pc.  Is there a program in existence or a script I can run via a cron job that will check the ip address given to my router (not my local one given by the router) regularly and email me if the address changes or put a text file on an ftp server or something?  This way I can manually update my ip address if need be.

Thanks!
Alan

---

### Post by rscott5 on 2007-06-11
I know of someone who has a script which posts his IP Address to a page on his website, so that if he is ever in need, he can go to his website to fetch the address. Not entirely sure how he does this though, sorry. I'm really curious to see everyone's responses here because something like emailing me the IP Address would certainly be useful!

---

### Post by harty83 on 2007-06-11
Well, I answered my own question.  After I posted this I thought, well I'm a web developer I should just do something in php.  So I did.

1)  I created this php script and named it checkip.php:

```

<?php
//EDIT THE FOLLOWING
$email = "email@email.com"; //email the ip change is sent to
$filename = "../ip.txt";  //in relationship to this script
$password = "mypassword"; //just a little something in an attempt to keep others from using the script
//END OF WHAT YOU NEED TO EDIT


$pw = $_GET["pw"];
$out = $_GET["op"];

if($pw==$password)
{
	$html = "<html><head></head><body>\n";
	$ip = $_SERVER["REMOTE_ADDR"];

	if(file_exists($filename))
	{
		$fh = fopen($filename, 'r');
		$old_ip = fread($fh, 15);
		$old_ip = trim($old_ip);
		fclose($fh);

		$html .= "Old ip: $old_ip<br>";
		if($old_ip != $ip)
		{
			$html .= "New IP: $ip<br>";
	 		$mail = mail( $email, "IP Change", "IP changed from $old_ip to $ip.", "" );
			
			if($mail) $html .= "Email sent to $email<br>";
			else $html .= "Email failed on send to $email<br>";

			unlink($filename);
			$handle = fopen($filename, 'w'); 
			fwrite($handle, $_SERVER["REMOTE_ADDR"]); 
			fclose($handle);
		}
                else $html .= "IP has not changed.<br>";
	}
	else
	{
		$html .= "$filename does not exist.  Will now create it.<br>";
		$handle = fopen($filename, 'w');
		fwrite($handle, $_SERVER["REMOTE_ADDR"]); 
		fclose($handle);
	}
	$html .= "</body></html>";
}
else die("Bad password");

if($out=="1") echo $html;
?>

```

2) Upload the script to a webserver.

3) Install lynx on your pc
```
sudo apt-get install lynx
```

4) Set up a cronjob to access the site via lynx however often you want
```
crontab -e
```
I added the following to check every 10 minutes
```

10 * * * * lynx http://www.my-server.com/checkip.php?pw=mypassword

```
Press ctrl-o Enter to save then ctrl-x to exit.

If my ip changes, the script will email the change to me. 

I have also set a little thing in there to help with debugging.  Access the script from a browser like the following to get an html output of what is going on like this:
```
http://www.my-server.com/checkip.php?pw=mypassword&op=1
```

---

### Post by rscott5 on 2007-06-11
Any idea how I could do this without using a webserver? I just want a script to run on my machine that will check every day or say and email me when the IP changes.

---

### Post by dbott67 on 2007-06-11
There's a free service at DynamicDNS (_[www.dyndns.org](www.dyndns.org)_) that allows you to register a hostname (such as [COLOR=Purple]rscott5.dyndns.org[/COLOR]) and then it will keep track of your IP address either via client software ([http://www.dyndns.com/support/clients/](http://www.dyndns.com/support/clients/)) or by a setting supported in many NAT routers.

There's also other sites (such as [www.no-ip.com]("http://www.no-ip.com")).  These sites generally also have a page that you can login to to check the current status of any host computer that you have registered.

When you need to connect to your computer, you would just SSH to rscott.dyndns.org:
```
dbott@feisty:~$ [COLOR=Red]**ssh you@rscott5.dyndns.org**[/COLOR]
you@rscott5.dyndns.org's password: 
Linux feisty 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Sun Jun  3 14:15:14 2007

```-Dave

---

### Post by rscott5 on 2007-06-11
That is awesome! Thanks so much.

---

### Post by hikaricore on 2007-06-11
[http://www.no-ip.com/](http://www.no-ip.com/) is great too, though their dynamic update client is somewhat of a bother to setup.

---

### Post by rscott5 on 2007-06-11
Note: There was a typo in the link you provided. Should have been [www.dyndns.org](www.dyndns.org)

---

### Post by dbott67 on 2007-06-11
> **rscott5 said:**
> Note: There was a typo in the link you provided. Should have been [www.dyndns.org]("http://www.dyndns.org")

Sorry.. thanks for pointing it out.  I have fixed the typo.

As hikaricore pointed out there is also no-ip.com (I use them personally) and my router supports their service natively, so I don't need to install the client.

There are also lots more, I'm sure.

-Dave

---

### Post by harty83 on 2007-06-11
That is the type of service I use but like I said in my original post, there are times that the program used to update my ip address fails thus leaving me hanging away from my house and not able to connect to my network.  That is why I wanted a "backup system" if you will.

FYI, I use ipUpdate to update my ip address with dnsexit where I purchased a domain name through.

(Watch my cron job fail after this...)

---

### Post by ramjet_1953 on 2007-06-11
This may be a bit off-topic, but may be useful

I use a package called [COLOR="Blue"]giple[/COLOR]t , which is available in Synaptic.

It is a aplet that sits in either bar, that dynamically checks your ip address.

In preference, you can change the frequency that it checks for a change.

Regards,
Roger :cool:

---

### Post by harty83 on 2007-06-12
> I use a package called giplet , which is available in Synaptic.

It is a aplet that sits in either bar, that dynamically checks your ip address.

Giplet seems pretty cool.  If only it could email me if the ip changes then it would be perfect!

---

### Post by rscott5 on 2007-06-12
dyndns.org is working great for me because you can use the app ddclient to update your ip and ddclient is available in the Ubuntu repository which makes it even easier to install :-)

---

### Post by dbott67 on 2007-06-12
> **rscott5 said:**
> dyndns.org is working great for me because you can use the app ddclient to update your ip and ddclient is available in the Ubuntu repository which makes it even easier to install :-)

Glad it's working for you.  Also nice to know that ddclient is in the repos.

-Dave

---

