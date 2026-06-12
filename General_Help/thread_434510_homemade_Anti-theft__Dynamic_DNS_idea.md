---
title: "homemade Anti-theft / Dynamic DNS idea"
date: 2007-05-06
forum: General Help
---

### Post by superyounan1 on 2007-05-06
I'm even sure if this is an appropriate place to post this, its not really ubuntu related, per se, but whatever, here goes.

I have a simple idea that can serve as an alternate to a dynamic dns service or an anti-theft ip-look up service. I currently pay a yearly fee for "thatip" and I also pay for some web space, i figured I could save a tad of money by using my web space to fill both need.

I started by making a simple php script that logs your IP when you visit the page and added a meta refresh tag to refresh every 5 minutes, I put the script on my web server and now I can get my home pc's ip from anywhere without a dynamic dns service. The problem is I dont always remember open up my browser and go to that page whenever i leave home. 

I want to use crontab to do this automatically instead, but I dont know of any programs that can just "ping" a url, or in other words, just navigate to a url and exit. 

If anyone knows of a program like that, let me know. Otherwise maybe i'll just make one...

---

### Post by lloyd_b on 2007-05-06
Take a look at the "wget" terminal command ("man wget" in a terminal window).  You'll have to download something, but it shouldn't be too much hassle to fetch the "index.html" or equivalent file.

Lloyd B.

---

### Post by superyounan1 on 2007-05-06
:)   why in the world didnt i think of that, thanks!

---

### Post by superyounan1 on 2007-05-06
Great, I have it working nicely now! I can immediately get my laptop's and desktop's IP addresses from anywhere, without using a dynamic dns service :guitar: . I have it set up to update four times an hour and to keep a local record. 

If anyone is interested in how i did it exactly, post a message and i'll go into more detail

---

### Post by nonewmsgs on 2007-05-06
sure. what is the script to get your ip from a webpage and how do you record it?

---

### Post by superyounan1 on 2007-05-06
here are more details on what i did:

what you need:
- a web server with PHP installed and a fixed url
- a desire to have a way to track your laptop (or desktop i suppose) in case of theft
- or a need to be able to get your computer's IP from anywhere, for such things as SSH, remote desktop, ftp, etc.

I put together this php script:

[PHP]
<?php

if($_GET['location']){ 
	$location = $_GET['location'];
	$ip=$HTTP_SERVER_VARS["REMOTE_ADDR"];
	$host=gethostbyaddr($ip);

	if( $location ){
		$file = $location . ".html";
		$fp = fopen($file,"w");
		$output = "location $location IP address: <strong>$ip</strong><br>updated by host: $host<br>updated on: ".date('l dS \of F Y h:i:s A')."<br><br>";
		echo $output;
		fputs( $fp,$output );
		fclose($fp);
	}
}
	
else if($_GET['pass']=="not_really_my_password"){

	$lpf = fopen('laptop.html', 'r');
	$laptop_contents = "<em>laptop</em><div style=\"padding:5px;\">".fread($lpf,filesize('laptop.html'))."</div>";
	fclose($lpf);
	$cpf = fopen('desktop.html','r');
	$desktop_contents = "<em>desktop</em><div style=\"padding:5px;\">".fread($cpf,filesize('desktop.html'))."</div>";
	fclose($cpf);

	echo $laptop_contents;
	echo $desktop_contents;
	
}

else {
<?
this area is off-limits, <a href="http://www.google.com">google</a>
?>
	
}
?>
[/PHP]

the most interesting part of it is the few lines at the top:
[PHP]	
$ip=$HTTP_SERVER_VARS["REMOTE_ADDR"];
$host=gethostbyaddr($ip);
[/PHP]

which gets your IP address.

then on each computer i added new directory in my home folder called 'iphistory' opened my crontab file:
```
crontab -e
```

added this line on my laptop:
```

15,30,45,0 * * * * wget --output-document="iphistory/`date`.html" http://location.of.phpscript.above/?location=laptop

```

and on my desktop, the last part of the command would be `?location=desktop` instead (because of the way i wrote the script)

This will schedule wget to go to the locaiton of the script at 15min, 30min, 45min, and the top of every hour of every day. If you want  different interval, check out this site to see how to format the crontab entry:

[http://www.crontabrocks.org/]("http://www.crontabrocks.org/")

now if you navigate to the script as such:
[http://address.com/?pass=not_really_my_password](http://address.com/?pass=not_really_my_password)

you'll see something like this:


[HTML]
laptop
location laptop IP address: xx.x.xx.xx
updated by host: adsl-x-x-xx-xx.dsl.chcgil.sbcglobal.net
updated on: Sunday 06th of May 2007 04:44:18 PM

desktop
location desktop IP address: xx.x.xx.xx
updated by host: adsl-xx-x-xx-xx.dsl.chcgil.sbcglobal.net
updated on: Sunday 06th of May 2007 04:40:49 PM
[/HTML]

and if you go to the ~/iphistory folder, you'll see html files there logging your ip changes each time it updates to the server, the name of the file will be `date_and_time_command_executed.html`

I should note that you can make another crontab entry to delete these every week or month, or you can delete them manually, otherwise they accumulate.

You could also make it more elegent, with maybe an HTML form with username and password, currently the possword is entered into the url, not the safest way to go.


cheers

---

### Post by pilpi on 2007-05-09
Seems to me you are allowing anyone to write to any file on your server. How about opening 
[http://address.com/?location=/etc/passwd%20](http://address.com/?location=/etc/passwd%20)
or similar? (not sure if my example works but you get the point)
See this: [http://devzone.zend.com/node/view/id/1793](http://devzone.zend.com/node/view/id/1793)

Anyway, thanks for the script, considering using, though modified.

---

### Post by superyounan1 on 2007-05-09
excellent suggestion. 

This script was highly customized for my specific needs and isnt ideal for any serious deployment or usage in a serious business environment. I'm not sure what will happen if you navigate to [http://address.com/?location=/etc/passwd%20](http://address.com/?location=/etc/passwd%20)  , but i suspect not much since its not my server, I just have an account on it and I dont have the privileges needed to access directories such as /etc/.

Anyone thinking about using it or abstracting it to something more robust ought to use the suggested string filtering method found in the link that **pilpi** posted, but I have since modified the script so that 

[http://address.com/?location=laptop](http://address.com/?location=laptop)
[http://address.com/?location=desktop](http://address.com/?location=desktop)

are the only valid locations since thats all i need.

[PHP]
<?php

if($_GET['location']=="laptop" || $_GET['location']=="desktop"){ 
	$location = $_GET['location'];
	$ip=$HTTP_SERVER_VARS["REMOTE_ADDR"];
	$host=gethostbyaddr($ip);

	$file = $location . ".html";
	$fp = fopen($file,"w");
	$output = "location $location IP address: <strong>$ip</strong><br>updated by host: $host<br>updated on: ".date('l dS \of F Y h:i:s A')."<br><br>";
	echo $output;
	fputs( $fp,$output );
	fclose($fp);

}
	
else if($_GET['pass']=="not_my_pass"){

	$lpf = fopen('laptop.html', 'r');
	$laptop_contents = "<em>laptop</em><div style=\"padding:5px;\">".fread($lpf,filesize('laptop.html'))."</div>";
	fclose($lpf);
	$cpf = fopen('desktop.html','r');
	$desktop_contents = "<em>desktop</em><div style=\"padding:5px;\">".fread($cpf,filesize('desktop.html'))."</div>";
	fclose($cpf);

	echo $laptop_contents;
	echo $desktop_contents;
	
}

else {
	echo "this server and directory are private.";
	
}
?>
[/PHP]

---

### Post by Subban on 2007-05-09
In the OP you mentioned the original reason for the script was to save a bit of money on the ""Thatip" service hence the php coding etc.

[www.dyndns.com]("http://www.dyndns.com")  host a completely free service, with your choice of hostname on several domains they offer, I've used them for around 6 or 7 years now I guess with no problem, and its free. I don't work for them or am in any way affiliated but it seemed like a simpler solution ;)

The last couple of years my router has dealt with updates, but for a scripted updated check this [Howto]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service") (more suited to your anti-theft/Ip tracking solution too)

---

### Post by superyounan1 on 2007-05-09
> **Subban said:**
> In the OP you mentioned the original reason for the script was to save a bit of money on the ""Thatip" service hence the php coding etc.

[www.dyndns.com]("http://www.dyndns.com")  host a completely free service, with your choice of hostname on several domains they offer, I've used them for around 6 or 7 years now I guess with no problem, and its free. I don't work for them or am in any way affiliated but it seemed like a simpler solution ;)

The last couple of years my router has dealt with updates, but for a scripted updated check this [Howto]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service") (more suited to your anti-theft/Ip tracking solution too)

wow... all this time i've been waisting my money? I thought I searched for free services when I first got into it. I'll read more about it, theres got to be a catch.

You're right, if i knew about this, i probably wouldnt have gone through the trouble. The only benefit of my method is that the binding of the URL usually takes a while to propagate throughout the internet, you bypass the need to wait with the custom script.

I cant count the number of times I was working on remote desktop and got disconnected when the IP switched on me, I usually cant get back on for an hour, but by scheduling the updates with crontab, you can have it update every minute if you want 

Thanks for the input!

---

### Post by Subban on 2007-05-10
> **superyounan1 said:**
> wow... all this time i've been waisting my money? I thought I searched for free services when I first got into it. I'll read more about it, theres got to be a catch.

No catch, as I say I have used them for years keeping the same DNS longer than I have ISP's ;). They also do a URL cloaking and MX Forwardy thingies and perhaps more

> You're right, if i knew about this, i probably wouldnt have gone through the trouble. The only benefit of my method is that the binding of the URL usually takes a while to propagate throughout the internet, you bypass the need to wait with the custom script.

I cant count the number of times I was working on remote desktop and got disconnected when the IP switched on me, I usually cant get back on for an hour, but by scheduling the updates with crontab, you can have it update every minute if you want 

Most modem/routers (combo units) seem to have DynDNS.com supprt these days (mostly netgear and dlink that i've used), theres a page on them to enter the hostname, login and password, then each time the modem connects it updates your IP from the router with no need for any scripting at all.

For the anti theft aspect you mentioned, a script on the OS would be more logical (there are details to a couple on the DynDNS.com pages btw) and yeah, slap them in a cron and update as you wish.

> Thanks for the input!
Your welcome :]

---

