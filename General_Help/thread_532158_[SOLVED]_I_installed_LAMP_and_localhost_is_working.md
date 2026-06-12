---
title: "[SOLVED] I installed LAMP and localhost is working, but how do I make it public?"
date: 2007-08-22
forum: General Help
---

### Post by RonB123123 on 2007-08-22
I installed LAMP and localhost is working, but how do I make it public? I see people now and then with just an IP for their website, no domain name or anything. Can I do that?

---

### Post by irish_flu on 2007-08-22
There are a lot of questions here.

To start with:

Do you have a static IP from your ISP?

If yes,
Are you behind a router and/or firewall?

If yes,
does your machine get a static IP from the router?

If yes,
you'll need to set up port forwarding from the router to your box.

If the answer to any of these questions was "no", then we'll back up and start from there.

---

### Post by leonardopsantos on 2007-08-22
That's abolutely correct. If you want some DNS name for your machine but you use some residential access with dynamic IP,  you can use some services like no-ip.com, dyndns, etc.
If you have cable access and this machine is/will be your router, don't forget to close all the unused ports and not strickly necessary services.

---

### Post by RonB123123 on 2007-08-23
irish_flu, thanks but I'm not sure if I have a static IP or not. How do I check if I do? And if I do, how do I go about the rest of the steps? 

leonardopsantos, thank you. I've heard of no-ip.com, but I need my IP to be accessible to people on the internet before I can use that kind of service, right?

---

### Post by PokerJoker on 2007-08-24
Jumping on the bandwagon here, as i can't find thread with my problem....

I have:
ISP dynamic ip, but changes rarely, mostly when i reboot my modem for some reason. 
Router setup with dhcp but fixed assignments to mac-addresses, and port 80 forwarded to ubu-desktop with working LAMP

Localhost works fine, as expected. 

Knowing my external ip, from my cell (or work desktop) i can access the webpage on my ubu-desktop, but only the text part comes up, when loading images or following a link it shows that the domain in the url changes to 'localhost'  ie.  [http://localhost/apache2-default](http://localhost/apache2-default)......

Same on my work pc, hovering over the links on the home-page they all show [http://localhost/apache2-default/....etc](http://localhost/apache2-default/....etc)

This off-course doesn't work from the outside. But no matter what i do in de apache2config, regarding Virtualhost or ServerName, can't get this to work.......I even tried using the DNS name of my external IP used by my ISP (using **whois.domaintools.com/my_external_ip** ) as ServerName in VirtualHost (not tried that as global ServerName yet...hmmmm)

So somewhere in the http request the domain/servername is changed from ip to localhost
But i can't be this hard, everybody has it working, apart from people not using port-forwarding or blocked 80 ports by ISP.....


EDIT: 
Base_URL problem here? 
I manage to login to my admin area of home based joomla site. Funny thing, apart from the grapchics not loading. The links in the interface al but the home button seem to point to the correct URL.
Example: Link to adminhome should be 
**[http://<my.isp.ext.ip>/apache2-default/administrator/index2.php](http://<my.isp.ext.ip>/apache2-default/administrator/index2.php)** but instead hovering the link shows **[http://localhost/apache2-default/administrator/index2.php](http://localhost/apache2-default/administrator/index2.php)**, and of course subsequently the request fails.

However the link to a submenu of home, the admin component, shows the correct URL when hovering and gets me there when requesting it......Doesn't make sense to me, as the administrator/index2.php is not the base_url. 
This doesn't work on the not-admin part of the side, Entering the base_url gets me the home-page minus images, all the links now point to localhost. Changeing the url in my browser to get me to a subsection of the site, gets me there, but still all links begin with localhost.

UPDATE:
Went away from the default dir. Created new dir:  /var/www/<new-dir> and added it to sites-available/enabled and removed the default from enabled.  Pumped a new Joomla1.5 install in it, ready to be installed. 
Next: changed ports.conf to the incoming ip, ie 192.168.1.242:80 
Also the sites-available config file is now:

[I]ServerName 80.56.209.57
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName 80.56.209.57

        DocumentRoot /var/www/joom15/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/joom15>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

[/I]Tried connecting from my cellphone again et Voila.....home-page images and all.

I think the ports.conf change from just 80 to <local-ip>:80 did the trick. This does mean however that typing localhost in my local browser now gets me an UNABLE TO CONNECT. Makes sense to me as ubuntu has 127.0.1.1 pinned as localhost, and apache doesn't listen to 127.0.1.1 anymore. No problem there, my hosts file has an entry for home-base now. Cool

/etc/hosts:
[I]127.0.0.1                      localhost
127.0.1.1                         ubuntu-64
192.168.1.242                 homebase
[/I]

---

### Post by RonB123123 on 2007-08-28
Oh man... I'm still lost. :(

I tried editing that file and I put in.

Listen 192.168.1.1:80

But still no luck. When I go to 192.168.1.1, I just see my modem login, but I don't see my apache server.

---

### Post by PokerJoker on 2007-08-30
> **RonB123123 said:**
> Oh man... I'm still lost. :(

I tried editing that file and I put in.

Listen 192.168.1.1:80

But still no luck. When I go to 192.168.1.1, I just see my modem login, but I don't see my apache server.

If you go to 192.168.1.1 and get your modem admin screen, then your accessing the webserver on your modem/router, so using the wrong ip address?

What is the ip of the ubuntu machine? (ifconfig, or Connection Information on Desktop using networkmanager). Probably omething like 192.168.1.2 or 192.168.1.3 etc..

---

### Post by RonB123123 on 2007-09-02
Hmm. I typed in ifconfig and I received this.
> 
eth0      Link encap:Ethernet  HWaddr 00:11:11:A6:11:4A  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60412647 (57.6 MiB)  TX bytes:1853775 (1.7 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:756 (756.0 b)  TX bytes:756 (756.0 b)


So I guessed I should be using the IP 192.168.1.2? So I changed my ports.conf file to this.
> 
Listen 192.168.1.2:80


Then I saved the file and I went to my IP address and received a login screen from my modem.

By the way, this is my sites-available's default file in case there is a problem.
> 
ServerName 71.168.68.161
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	ServerName 71.168.68.161
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


and here is my host file.
> 
127.0.0.1	localhost Ronak-Desktop
127.0.1.1	Ronak-Desktop

# The following lines are desirable for IPv6 capable hosts
# ::1     ip6-localhost ip6-loopback
# fe00::0 ip6-localnet
# ff00::0 ip6-mcastprefix
# ff02::1 ip6-allnodes
# ff02::2 ip6-allrouters
# ff02::3 ip6-allhosts


Do I need to configure my modem to redirect traffic from my IP address to my localhost on port 80? If so, how do I do that? 

I am so lost with this. If no one can help me with the above, do you know of a tutorial that could help? Thank you very much. :)

---

### Post by Seti on 2007-09-02
Looking at your last post tells me that your machine is on a LAN, in other words, your computer connects to a router which in turn connects to your ISP. RIGHT??
What kind of sevice do you have? Cable? ADSL?
If you're on ADSL MOST LIKELY you have a dynamic IP address. In that case, there is a way you can set your router (there usually is) such that every time you get a new IP via DHCP you can update your public hostname automatically. 
For example, (and this brings me to my question) you can sign up for an acct with dyndns.org like I have, and then you can have a permanent hostname (for free) instead of having to use your IP to get to your site from the internet.
Here is my setup.
I have an account through dyndns.org, it might be called forexamle.homeunix.org. My linksys router allows me to configure this hostname to update so that every time my ISP gives me a new IP, the router updates my account @ dyndns.org with that new IP. Cool huh?
Now my question is this, hopefully someone knows what I'm talking about. How do I set up my account @ dyndns.org such that I can add a second (or third) hostname to point to the same IP? After all, the linksys router only allows for one hostname to be updated to dyndns.org. 
Any ideas???

thanks

---

### Post by PokerJoker on 2007-09-03
> **RonB123123 said:**
> Hmm. I typed in ifconfig and I received this.

So I guessed I should be using the IP 192.168.1.2? So I changed my ports.conf file to this.

Then I saved the file and I went to my IP address and received a login screen from my modem.


Can u be MORE specific when u say: i went to my ip-address......If u are trying to reach your website using your internet ip (76.etcetc) from within your local network, that is NOT going to work. Just how the modem/router work. There is no way to tel your modem to loop your http request going outside your lan and back in again. This is normal, i have the same problem, i solved it at home by using my cell-phone's internetconnection to test it, or connect from another network, ie, my pc@work which bossman doen't care for too much....but hey, i was on my lunchbreak

> 
Do I need to configure my modem to redirect traffic from my IP address to my localhost on port 80? If so, how do I do that? 


Yes you need to do that, and there are plenty of posts explaining it. It's called port-forwarding.
If you look at your network topology it makes sense too, your modem has 2 sides to it, one is the internet side, and one your local network side. The internet has no way of knowing what is connected on the lan side of your  modem, therefore u can use the same private ip-address as i do at home. These ip-ranges of 192.168.x.x etc ar for INTERNAL use only. When surfing your modem just makes sure that everyting is sent t the right pc. Like SETI says, u can work around this by using port-forwarding AND dyndns. 


> 
I am so lost with this. If no one can help me with the above, do you know of a tutorial that could help? Thank you very much. :)

Do not despair, one step at a time, and keep those questions coming...

---

### Post by RonB123123 on 2007-09-03
Thank you PokerJoker. :)

Oh, so that's why I couldn't access my server. Here are my portforwarding rules on my modem. 
[img]http://img508.imageshack.us/img508/817/portforwardingrulesal3.png[/img]
Do I check the Specify Public IP? If so, what do I set it to?For the Network/Computer Device, should I set the drop down box to Specify Address or Ronak-Desktop? And what do I input into the Input Box? I set the protocol to Web Server. What should I set for WAN Connection Type? I have the following options for that: All Broadband Devices, Broadband Connection (Ethernet), WAN PPPOE, and WAN PPPOE 2. What should I set for the Forward to Port? Same as Incomming Port or should I specify the port?

If I get this to work, then I'll do the dyn dns. I already signed up for dyndns but I don't know  how to set that up either. :( I hope you can help me, I really need someone to hold my hand through this. I've tried looking online for tutorials on setting up a server in Ubuntu but the tutorials are either for Dapper Drake, Ubuntu Server, or the tutorials just don't work. 

And I changed my ports.conf file back to **Listen 80** because when I went to localhost, I got a 404 page. 

Thank you,
~Ron

---

### Post by PokerJoker on 2007-09-03
> **RonB123123 said:**
> Thank you PokerJoker. :)

Oh, so that's why I couldn't access my server. Here are my portforwarding rules on my modem. 
[img]http://img508.imageshack.us/img508/817/portforwardingrulesal3.png[/img]

Do I check the Specify Public IP? If so, what do I set it to?For the Network/Computer Device, should I set the drop down box to Specify Address or Ronak-Desktop? And what do I input into the Input Box? I set the protocol to Web Server. What should I set for WAN Connection Type? I have the following options for that: All Broadband Devices, Broadband Connection (Ethernet), WAN PPPOE, and WAN PPPOE 2. What should I set for the Forward to Port? Same as Incomming Port or should I specify the port?

If I get this to work, then I'll do the dyn dns. I already signed up for dyndns but I don't know  how to set that up either. :( I hope you can help me, I really need someone to hold my hand through this. I've tried looking online for tutorials on setting up a server in Ubuntu but the tutorials are either for Dapper Drake, Ubuntu Server, or the tutorials just don't work. 

And I changed my ports.conf file back to **Listen 80** because when I went to localhost, I got a 404 page. 

Thank you,
~Ron

Ok Ron, now on the last question, if your read my rather lengthy post, you'll see why localhost doesn't work anymore. Locally you'll need to use the 192.x.x.x address. (and change your ports.conf back) 
As for port-forwarding, i don't have an elaborate modem like yours, in fact i have a router connected to my modem, which in turn does the port-forwardign. General rule here:
have incoming port 80 (http or webserver) forwarded to the ip and port 80 your apache is listening to, in your case the 192.168.1.2 ip and of course port 80....(seems u can use the option "same as incoming port"  on the Forward to port item in your modem menu. The other ones....dont think you need to specify public address....so try whitout that one first...

Edit: 
Form the pic u posted it looks as though u already have port 80 and 443 forwarded, but the icon with the little erd cross next to it, what's that mean? Look in the modem manual, might be blocked right now.....Also it seems its forwarding ANY to 80, which is not good, 80 --> 80 is the way to go. Maybe the icon under Action means delete the Webserver rule. Not sure, i suggest u read up on port forwarding in the modem documentation....

---

### Post by RonB123123 on 2007-09-03
Hmm, I follow you but now I have a new problem. When I type in ifconfig to get my incomming IP (which is how I got 192.168.1.2 before), I now get a different IP.

These are my results. My inet addr is now 192.168.1.5. If that is my incomming IP that I need to set my ports.conf to, then how do I set the ports.conf to that IP if it keeps changing?
> 
eth0      Link encap:Ethernet  HWaddr 00:11:11:A6:11:4A  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52429311 (50.0 MiB)  TX bytes:1925391 (1.8 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1300 (1.2 KiB)  TX bytes:1300 (1.2 KiB)


By the way, that icon with the red cross will just delete that protocol from the rule.  I'll try to put in 192.168.1.5 for the Network Address and I'll leave the other settings the same. Hope it works. 

Edit: Eureka! It works! But! One problem is that the IP keeps changing. 192.168.1.5 will probably change when I reboot my computer. Any way to keep it static?
Edit2: Mmm.. Turns out it only works for my computer. When I sent my IP address to other people, they could not see my localhost. :( This is so hard...

---

### Post by PokerJoker on 2007-09-03
> **RonB123123 said:**
> Hmm, I follow you but now I have a new problem. When I type in ifconfig to get my incomming IP (which is how I got 192.168.1.2 before), I now get a different IP.

These are my results. My inet addr is now 192.168.1.5. If that is my incomming IP that I need to set my ports.conf to, then how do I set the ports.conf to that IP if it keeps changing?


By the way, that icon with the red cross will just delete that protocol from the rule.  I'll try to put in 192.168.1.5 for the Network Address and I'll leave the other settings the same. Hope it works. 

Edit: Eureka! It works! But! One problem is that the IP keeps changing. 192.168.1.5 will probably change when I reboot my computer. Any way to keep it static?
Edit2: Mmm.. Turns out it only works for my computer. When I sent my IP address to other people, they could not see my localhost. :( This is so hard...

Off course you can change the way you get an ip. Just to make sure, your modem acts as router also, i mean you dont have a router attached to your modem right? Just your pc, or more pc's 
If your modem supports fixed bindings with it's dhcp server, u can use that, otherwise you'll need to hardwire all your pc's, i.e. not use dhcp but give each one a fixed address (hey, you're becoming a sysadmin now...;-) Let's try fixed bindings first. Ifconfig provides you with the right info here:
> eth0 Link encap:Ethernet HWaddr 00:11:11:A6:11:4A
inet addr:192.168.1.5 Bcast:192.168.1.255 Mask:255.255.255.0

Your eth0's mac, i.e. HWaddr. go find the DHCP settings in your modem and look for fixed bindings or something thereof, oh i see in my case it's fixed mappings:

[IMG]http://i154.photobucket.com/albums/s252/PokerJoker_bucket/Vista_hell/dhcp1.png[/IMG]

I need to Disable the DHCP first, press Save, then change the fixed mapping, entering an ip together with a mac address for each pc connected to modem, though you can do it ONLY for the pc you want to have static address, then save, then enable dhcp again and Save that. 
Now you have the one you entered after every boot, if u entered a different one from what it is at the moment, u would need to restart your connection to give your dhcp server (modem) the chance to get it to you, hope you still with me.

---

### Post by RonB123123 on 2007-09-04
Here are my DHCP settings.
[img]http://img299.imageshack.us/img299/8006/dhcpsettingstp8.png[/img]

Now I'm not sure what I should do. I have 2 computers connected to this modem, would this affect my other computer's internet. 

What do I change the fixed mapping? and what do you mean by entering an IP together with a mac address?

---

### Post by PokerJoker on 2007-09-04
> **RonB123123 said:**
> Here are my DHCP settings.

Now I'm not sure what I should do. I have 2 computers connected to this modem, would this affect my other computer's internet. 

What do I change the fixed mapping? and what do you mean by entering an IP together with a mac address?

Have you checked the manual for this modem? It should explain the options it has with the dhcp server settings. If you dont have a manual i'm sure it is available online. 

Normally dhcp dishes out ip address to whomever asks for it, so whichever pc is booted first gets the first number that is available, and leases it out for a preset period, Next one gets next available number etc. If you reboot and your pc doesnt tell the modem or the modem doesnt get the message that the ip address isn't in  use anymore, it will not be available until the lease period runs out, so now your rebooted pc again asks for an ip address and might get a different one. 
Fixed mapping is setting up a table in your modem to have your one pc receive the same ip every time. How does the modem's dhcp server know which pc to serve with the right ip? By means of the hardware-address i.e. MAC, in your case 00:11:11:A6:11:4A 
MAC addresses are unique per network device. or so it should be.*  Check the MAC on your other pc.  If it's a windows macine, use a DOS box and type " ipconfig /all" it should tell you the hardware or MAC number. So using these you can have both pc's have their own ip. Another way is to hardwire your pc's, setting up the interface on both machines to NOT use dhcp, but that requires more info, like telling them up front what DNS to use etc.....not so easy.


*Sometimes mainboard manufacturers save money by only buying one driver for thousands of mainboard ethernet interfaces, so they copy the driver and mac address, which is a big no-no....

---

### Post by RonB123123 on 2007-09-04
I received a manual for the modem, but it didn't go much in depth. I tried to look up my router which is Actiontec M1424WR. And I disabled ICMP, I read somewhere that one may need it to host a server. Is that true? 

And I can find the mac address for the 2 computers no problem with ifconfig, but I don't think my modem will let me input the mac addresses. I'll keep looking though.

There is an option on my modem called a DMZ host. Could I use that and be able tos etup the server? By the way, thank you so much for all this help. I'm really sorry it's still not working. It's just hard to figure it out.

---

### Post by PokerJoker on 2007-09-04
> **RonB123123 said:**
> I received a manual for the modem, but it didn't go much in depth. I tried to look up my router which is Actiontec M1424WR. And I disabled ICMP, I read somewhere that one may need it to host a server. Is that true? 

And I can find the mac address for the 2 computers no problem with ifconfig, but I don't think my modem will let me input the mac addresses. I'll keep looking though.

There is an option on my modem called a DMZ host. Could I use that and be able tos etup the server? By the way, thank you so much for all this help. I'm really sorry it's still not working. It's just hard to figure it out.

Your manual should mention what DMZ means, it stands for De-Militarized Zone, which is short for, i'm not protecting this. So not really save to use, it opens up all ports for the DMZ host you specify, using IP address, 

But the first question someone else asked your before is what is your setup? You mention a router....so is it   internet --> modem --> router ---> pc's  ?  

If i google  "Actiontec M1424WR" the first document i get is all about security, but only for wireless setting, so you shouldn't have a hard time finding the specific info....are u using wireless connections only?
Could also be your actiontec is your isp provided modem/router?

---

### Post by RonB123123 on 2007-09-04
> **PokerJoker said:**
> Your manual should mention what DMZ means, it stands for De-Militarized Zone, which is short for, i'm not protecting this. So not really save to use, it opens up all ports for the DMZ host you specify, using IP address, 

But the first question someone else asked your before is what is your setup? You mention a router....so is it   internet --> modem --> router ---> pc's  ?  

If i google  "Actiontec M1424WR" the first document i get is all about security, but only for wireless setting, so you shouldn't have a hard time finding the specific info....are u using wireless connections only?
Could also be your actiontec is your isp provided modem/router?

My Actiontec is my modem and router and I'm not using wireless internet. The manual is lost, I was speaking before from memory. It only explained enough to access the internet and didn't get into anything complicated. I have googled the same thing but couldn't find anything on setting up a web server. 

It's like this. Internet --> Modem --> computers

---

### Post by PokerJoker on 2007-09-04
> **RonB123123 said:**
> My Actiontec is my modem and router and I'm not using wireless internet. The manual is lost, I was speaking before from memory. It only explained enough to access the internet and didn't get into anything complicated. I have googled the same thing but couldn't find anything on setting up a web server. 

It's like this. Internet --> Modem --> computers

Well the manual of the modem wouldn't be talking about setting up a webserver, as u can't do that on the modem off course, Just carefully browse thru all the setup pages on your modem, and try and see if you can find all the dhcp options. On the google doc i found it talked about mac filtering for wireless security so i'm sure it has an option to do this for wired connections, i think it's even on one of your images, dhcp settings i think, there it says something about Vendor specific stuff including MAC, see if you can figure that one out, 
Maybe it, like mine, has an option which shows you which dhcp clients, i.e. pc's are connected at the moment, showing ip's and macs, mine is a button called client list....

---

### Post by RonB123123 on 2007-09-04
Okay then. Thank you very much for everything. I'll get right to that. :)

---

### Post by RonB123123 on 2007-09-04
I got it working. You'll never believe why. 

Turns out Verizon blocks ports 25 and 80 unless you upgrade to their business plan which is $100 a month! Talk about ripping off their customers!

Anyway, I changed the listening port to 8080 and the port forwarded on the modem to 8080 and it worked just fine. Thank you very much for all your help. :)

~Ron

---

### Post by PokerJoker on 2007-09-05
> **RonB123123 said:**
> I got it working. You'll never believe why. 

Turns out Verizon blocks ports 25 and 80 unless you upgrade to their business plan which is $100 a month! Talk about ripping off their customers!

Anyway, I changed the listening port to 8080 and the port forwarded on the modem to 8080 and it worked just fine. Thank you very much for all your help. :)

~Ron

Great! Have fun Ron.

---

