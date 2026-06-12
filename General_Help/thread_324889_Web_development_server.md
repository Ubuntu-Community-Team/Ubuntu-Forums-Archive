---
title: "Web development server"
date: 2006-12-24
forum: General Help
---

### Post by chocolatetoothpaste on 2006-12-24
Hey all,
  I setup a LAMP server in my small office, I setup our website and it works good locally.  Now I run into a problem.  There are 3-4 web programmers that work on a contract basis.  In order to ensure we all have the same version of the website, I setup this webserver.  All of us need to be able to connect to this like it were an actual web hosting server.  Problem is, I can't connect.  I tried typing in the IP address, and the IP address:80, but it just takes me to my Actiontec modem setup.  I tried adding port-forwarding to my Actiontec rules, but it didn't seem to work.  It sent me to the setup page.  Does anyone have any ideas to try, or point me to a guide that can help me work this out?  I am not sure what I am looking for exactly, which is why I am having trouble getting this to work.  Thanks.

---

### Post by cilynx on 2006-12-24
Your LAMP box is behind a modem / router job from your ISP.  You need to get through it before you can begin you troubles with Linux =).  

Start here:
[http://www.actiontec.com/support/index.php](http://www.actiontec.com/support/index.php)

Find the user manual for you modem and figure out how to punch the hole you need in the firewall.  

From there, are you trying to view the website on the server or FTP in or SSH in or...?  What you're trying to do defines what ports you need to open / forward on your modem / router.

---

### Post by chocolatetoothpaste on 2006-12-24
> **cilynx said:**
> 
From there, are you trying to view the website on the server or FTP in or SSH in or...?  What you're trying to do defines what ports you need to open / forward on your modem / router.

I want other programmers to view it on the server, in a web browser.  So, they login to the server, do some programming, save their changes, then view it on this server to test the programming.  Basically, just a live server, with very low traffic.  I just need to know which holes to punch to get it to the outside world.
EDIT:
Actually, I will need ftp and ssh access to this server too.  So, if you can offer any further advice, I would really appreciate it.

---

### Post by chocolatetoothpaste on 2006-12-24
> **cilynx said:**
> Your LAMP box is behind a modem / router job from your ISP.  You need to get through it before you can begin you troubles with Linux =).  


So, I checked into this a little, and it says all I need to do is enable port forwarding.  I did this all ready, and it does not solve the problem yet.  What do I need to do on the linux side?

---

### Post by DrMoxie on 2006-12-24
Hmmm, I'm still thinking the problem is with the setup of the modem/router but just to be sure check and see if Apache is running (ps -aux on the command line is a quick way) if not start it (sudo /etc/init.d/apache2 start).  

As for the modem/router, do you have remote management turned off? If it is have you tried moving the server into the DMZ to see if you can access it (not recommended as a final solution though)?

:-k

---

### Post by cilynx on 2006-12-24
Agreeing with DrMoxie.  It sounds like you're still stuck behind your modem/router.  Putting the 'nix box in the DMZ is a good test to make sure your 'nix box is doing its thing properly as it automagically forwards all requests that hit the modem to the 'nix box.  As for final setup, you'll need port 80 (www), 21 (ftp), and 22 (ssh) forwarded from the outside interface on the modem to an interface on the 'nix box.  Let us know what headway you make...

Just as a thought:  your 'nix box does have a static IP behind the modem, right?  DHCP won't allow for proper port forwarding without more advanced wizardry.

---

### Post by chocolatetoothpaste on 2006-12-27
Thanks for the comments.  I just realized that I didn't have a static IP address setup.  I will do that this weekend, then post any progress.  I have not had troubles in the past when I setup an internet radio server for myself, but this is a different setup.  Actually though, it is the same modem, so it should work the same I would presume.  I give your suggestions a try and report on my progress this weekend.

---

### Post by chocolatetoothpaste on 2007-01-05
Just an update on this problem.  I added a static IP to my development server, made sure remote management was off, enabled ports 21, 22, and 80 in port forwarding, and I still get the actiontec setup screen when I type in the IP address.  Something isn't right.  If anyone can offer further help on the matter, I would appreciate it.

---

### Post by cilynx on 2007-01-05
Are you accessing the forwarding router from inside or outside of the LAN?  I have a Linksys WRT54GS running OpenWRT.  If I hit [my ip]:80 from inside the LAN, I get the Admin Interface.  If I hit it from outside the LAN, the request is forwarded to one of my web servers.  It's not a bad configuration.  

Did you try SSHing in to your machine through the router?  Maybe the router just doesn't want to give up the default location for it's Admin Page.  As for port forwarding, you did forward them to the proper static IP (the IP of the actual server) and not just "open" them on the router, right?

---

### Post by chocolatetoothpaste on 2007-01-08
> **cilynx said:**
> Are you accessing the forwarding router from inside or outside of the LAN?  

I was trying to do it from inside the LAN, and I was going to do it from somewhere else today, but forgot the IP address.  Have to try tomorrow and post an update.

> **cilynx said:**
>  Did you try SSHing in to your machine through the router?  Maybe the router just doesn't want to give up the default location for it's Admin Page.  As for port forwarding, you did forward them to the proper static IP (the IP of the actual server) and not just "open" them on the router, right?

I used the "Port Forwarding" menu on the router.  So I am pretty sure I set it up right.  when I did the ssh, I actually did it from the same machine, so maybe it was having problems connecting to itself.  I didn't even think of that.  I will try to do these things tomorrow, since I work in a different office during the week, and post the results.  Thanks for the suggestions!

---

