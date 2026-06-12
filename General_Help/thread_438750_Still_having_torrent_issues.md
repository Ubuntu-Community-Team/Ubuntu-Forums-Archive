---
title: "Still having torrent issues"
date: 2007-05-10
forum: General Help
---

### Post by Angelbeast on 2007-05-10
Okay i'm still having torrent issues. If you look at the screenshot you will see what i'm talking about. In azureus i have the proper ports configured in the firewall but i still get an arror saying that connection through the port has failed. And also on the next error it says the same thing for http. How in the heck to i fix this? And also i thought that the firestarter firewall was just more or less an interface to the ip file for the 'built-in' ubuntu firewall. when i had opened up thehen i had the same thing when i turned it on again after restarting. Why is it doing that? firewall all of my internet traffic had stopped I added rules for everything but i ended up having to restart. Then i had the sme thing when i turned it on again after restarting. Why is it doing that? and the last thing. Every time i start Azureus i get a prompt for an update that i have lready done.

---

### Post by kvonb on 2007-05-10
Here is some info from my server if it helps:

I bind my incoming and outgoing connections to different ports, this makes it easier to see what is going on in the Firestarter connections window, and it is a higher port so that it's not easy for my ISP to block it as some do.

I also make sure that it's bound to my public IP address, mine is static, but if you have a dynamic IP don't bother.

Which version of Az are you using?  I think mine is 2.5.0.0, I haven't tried the 3.x version yet.

Hope that helps :)

---

### Post by Angelbeast on 2007-05-10
> **kvonb said:**
> Here is some info from my server if it helps:

I bind my incoming and outgoing connections to different ports, this makes it easier to see what is going on in the Firestarter connections window, and it is a higher port so that it's not easy for my ISP to block it as some do.

I also make sure that it's bound to my public IP address, mine is static, but if you have a dynamic IP don't bother.

Which version of Az are you using?  I think mine is 2.5.0.0, I haven't tried the 3.x version yet.

Hope that helps :)

i'm afraid to open the firewall back up coz i'll lose all my connections *LOL(*

---

### Post by kvonb on 2007-05-10
> **Angelbeast said:**
> i'm afraid to open the firewall back up coz i'll lose all my connections *LOL(*

If you have Firestarter installed on your system then it is running anyway, the GUI is simply a frontend.

Although I know exactly where you are coming from, I've had the same problem in the past, and it drove me nuts!

I believe the problem is in the Policy tab of Firestarter, have a look at my screenshot #3, see how I have 192.168.0.1/24 in the "Allow connections from host" box, if you put: 192.168.0.0/24 it won\t work!

That IP range is taken from your internal address range, find out what your IP address is (ifconfig in a terrm) and change the range in my example to your range, but for the last number use a "1".

How do you connect to the net?  My server has 2 network cards, one is connected to my modem/router thing and runs a pppoe connection.  When I setup Firestarter I used the pppoe connection as the "Internet connected device".

It will work eventually, although it can be a pain getting there!

---

### Post by kvonb on 2007-05-10
I just looked at your screenshot again, and you don't have anything in "Allow connections from host".

You have to put your internal IP range in there as I stated in my last post, otherwise your computer is in total lockdown :)

---

### Post by Angelbeast on 2007-05-10
> **kvonb said:**
> If you have Firestarter installed on your system then it is running anyway, the GUI is simply a frontend.

Although I know exactly where you are coming from, I've had the same problem in the past, and it drove me nuts!

I believe the problem is in the Policy tab of Firestarter, have a look at my screenshot #3, see how I have 192.168.0.1/24 in the "Allow connections from host" box, if you put: 192.168.0.0/24 it won\t work!

That IP range is taken from your internal address range, find out what your IP address is (ifconfig in a terrm) and change the range in my example to your range, but for the last number use a "1".

How do you connect to the net?  My server has 2 network cards, one is connected to my modem/router thing and runs a pppoe connection.  When I setup Firestarter I used the pppoe connection as the "Internet connected device".

It will work eventually, although it can be a pain getting there!

i connect wirelessly wherever i can find a connection. At my moms, over at friends houses, ect. right now ther's just a random one somewhere ner by that i'm able to connect to for the time being. Sometimes if the wether is just right it works out like that. when i get back to work though after next month i'll have my own connection with my own ip.

---

### Post by Angelbeast on 2007-05-12
> **kvonb said:**
> If you have Firestarter installed on your system then it is running anyway, the GUI is simply a frontend.

Although I know exactly where you are coming from, I've had the same problem in the past, and it drove me nuts!

I believe the problem is in the Policy tab of Firestarter, have a look at my screenshot #3, see how I have 192.168.0.1/24 in the "Allow connections from host" box, if you put: 192.168.0.0/24 it won\t work!

That IP range is taken from your internal address range, find out what your IP address is (ifconfig in a terrm) and change the range in my example to your range, but for the last number use a "1".

How do you connect to the net?  My server has 2 network cards, one is connected to my modem/router thing and runs a pppoe connection.  When I setup Firestarter I used the pppoe connection as the "Internet connected device".

It will work eventually, although it can be a pain getting there!

Okay so if i understand this correctly then the 192.168.1.100 is my ip? So what exactly would i put for the range?

> eth0      Link encap:Ethernet  HWaddr 00:0F:B0:BC:03:AD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xc400 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:1D:94:AD  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe1d:94ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:636178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:611568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:623440937 (594.5 MiB)  TX bytes:78678713 (75.0 MiB)
          Interrupt:21 Memory:c0204000-c0206000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1124 (1.0 KiB)  TX bytes:1124 (1.0 KiB)

---

### Post by kvonb on 2007-05-12
Try simply putting "localhost" or 127.0.0.1/8 as the IP range.

I was thinking that you were running Firestarter on a server, which is my setup but is not relevant to you :).

Using the above should suffice even if your IP changes.

---

### Post by Angelbeast on 2007-05-12
> **kvonb said:**
> Try simply putting "localhost" or 127.0.0.1/8 as the IP range.

I was thinking that you were running Firestarter on a server, which is my setup but is not relevant to you :).

Using the above should suffice even if your IP changes.

okay i did that and got the same thing nd had to restart...i did look in the events tab though and noticed that everything that was being blocked was from the 192.168.1.100 ip addressand was lbeled aim or http ... does that help any?

---

### Post by kvonb on 2007-05-12
> **Angelbeast said:**
> okay i did that and got the same thing nd had to restart...i did look in the events tab though and noticed that everything that was being blocked was from the 192.168.1.100 ip addressand was lbeled aim or http ... does that help any?

OK, add that IP address too, same way that you did the 127 one :)

---

### Post by Angelbeast on 2007-05-12
> **kvonb said:**
> OK, add that IP address too, same way that you did the 127 one :)

okay i added both  of them in he allow incoming connections part...still the same result...wtf? *LOL* ... i got a screenshow of the event tab this time though...i don't understand why it's doing this...it wasn't doing it before...

---

### Post by Angelbeast on 2007-05-13
*bump*

---

### Post by kvonb on 2007-05-13
> **Angelbeast said:**
> okay i added both  of them in he allow incoming connections part...still the same result...wtf? *LOL* ... i got a screenshow of the event tab this time though...i don't understand why it's doing this...it wasn't doing it before...

Can you post screenies of the other tabs as well?  Also did you set eth1 as your "internet connected device" in the Firestarter setup, not eth0?

And a silly question, but you did click on "apply rule" after adding it?

Have a look at your firestarter config file: sudo gedit /etc/firestarter/configuration

Here is the top of mine:

```
#-----------( Firestarter Configuration File )-----------#

# --(External Interface)--
# Name of external network interface
IF="ppp0"
# Network interface is a PPP link
EXT_PPP="on"

# --(Internal Interface--)
# Name of internal network interface
INIF="eth0"

# --(Network Address Translation)--
# Enable NAT
NAT="on"
# Enable DHCP server for NAT clients
DHCP_SERVER="off"
# Forward server's DNS settings to clients in DHCP lease
DHCP_DYNAMIC_DNS="on" 

```

I would guess that both your "Name of external network interface" and "Name of internal network interface" would be eth1 having seen your earlier ifconfig post.  You might want to go through the Firestarter config wizard again, and change it that way.

---

### Post by Angelbeast on 2007-05-13
> **kvonb said:**
> Can you post screenies of the other tabs as well?  Also did you set eth1 as your "internet connected device" in the Firestarter setup, not eth0?

And a silly question, but you did click on "apply rule" after adding it?

Have a look at your firestarter config file: sudo gedit /etc/firestarter/configuration

Here is the top of mine:

```
#-----------( Firestarter Configuration File )-----------#

# --(External Interface)--
# Name of external network interface
IF="ppp0"
# Network interface is a PPP link
EXT_PPP="on"

# --(Internal Interface--)
# Name of internal network interface
INIF="eth0"

# --(Network Address Translation)--
# Enable NAT
NAT="on"
# Enable DHCP server for NAT clients
DHCP_SERVER="off"
# Forward server's DNS settings to clients in DHCP lease
DHCP_DYNAMIC_DNS="on" 

```

I would guess that both your "Name of external network interface" and "Name of internal network interface" would be eth1 having seen your earlier ifconfig post.  You might want to go through the Firestarter config wizard again, and change it that way.

Okay i checked and made sure everything said Eth1 and it locked me down yet again...so i'm attaching the screenshots you asked for and the contents of my config file for firestarter...aye aye aye...such craziness *LOL*

> #-----------( Firestarter Configuration File )-----------#

# --(External Interface)--
# Name of external network interface
IF="eth1"
# Network interface is a PPP link
EXT_PPP="off"

# --(Internal Interface--)
# Name of internal network interface
INIF="eth1"

# --(Network Address Translation)--
# Enable NAT
NAT="off"
# Enable DHCP server for NAT clients
DHCP_SERVER="off"
# Forward server's DNS settings to clients in DHCP lease
DHCP_DYNAMIC_DNS="on"

# --(Inbound Traffic)--
# Packet rejection method
#   DROP:   Ignore the packet
#   REJECT: Send back an error packet in response
STOP_TARGET="DROP"

# --(Outbound Traffic)--
# Default Outbound Traffic Policy
#   permissive: everything not denied is allowed
#   restrictive everything not allowed is denied
OUTBOUND_POLICY="restrictive"

# --(Type of Service)--
# Enable ToS filtering
FILTER_TOS="off"
# Apply ToS to typical client tasks such as SSH and HTTP
TOS_CLIENT="off"
# Apply ToS to typical server tasks such as SSH, HTTP, HTTPS and POP3
TOS_SERVER="off"
# Apply ToS to Remote X server connections
TOS_X="off"
# ToS parameters
#   4:  Maximize Reliability
#   8:  Maximize-Throughput
#   16: Minimize-Delay
TOSOPT=8

# --(ICMP Filtering)--
# Enable ICMP filtering
FILTER_ICMP="off"
# Allow Echo requests
ICMP_ECHO_REQUEST="off"
# Allow Echo replies
ICMP_ECHO_REPLY="off"
# Allow Traceroute requests
ICMP_TRACEROUTE="off"
# Allow MS Traceroute Requests
ICMP_MSTRACEROUTE="off"
# Allow Unreachable Requests
ICMP_UNREACHABLE="off"
# Allow Timestamping Requests
ICMP_TIMESTAMPING="off"
# Allow Address Masking Requests
ICMP_MASKING="off"
# Allow Redirection Requests
ICMP_REDIRECTION="off"
# Allow Source Quench Requests
ICMP_SOURCE_QUENCHES="off"

# --(Broadcast Traffic)--
# Block external broadcast traffic
BLOCK_EXTERNAL_BROADCAST="on"
# Block internal broadcast traffic
BLOCK_INTERNAL_BROADCAST="off"

# --(Traffic Validation)--
# Block non-routable traffic on the public interfaces
BLOCK_NON_ROUTABLES="off"

# --(Logging)--
# System log level
LOG_LEVEL=info

---

### Post by kvonb on 2007-05-13
Ha ha, I think I found it!

Change your outbound policy to "permissive".

---

### Post by Angelbeast on 2007-05-13
> **kvonb said:**
> Ha ha, I think I found it!

Change your outbound policy to "permissive".

oooo...you rock!

can i do it right in the file without havingto open up firestarter?

---

### Post by Angelbeast on 2007-05-14
anyone...anyone?beuhler? can i change that setting right in the file or will it mess up firestarter?

---

### Post by kvonb on 2007-05-14
> **Angelbeast said:**
> oooo...you rock!

can i do it right in the file without havingto open up firestarter?

Sorry, I thought you would have tried it by now :)

It should work by putting it in the config file, but it won't hurt anything to simply run firestarter and change it from the GUI.

Make a backup copy of the config file first, just in case :)

---

### Post by Angelbeast on 2007-05-14
> **kvonb said:**
> Sorry, I thought you would have tried it by now :)

It should work by putting it in the config file, but it won't hurt anything to simply run firestarter and change it from the GUI.

Make a backup copy of the config file first, just in case :)

dude...don't you sleep? *LOL* 

i'm just a bit paranoid about trying stuff that i haven't done before with 'system' files after how easy it is to critically damaged windows..

it worked anyway so would i still have to add torrent rules if it's allowing traffic now 

i'll check back after school...

---

### Post by Angelbeast on 2007-05-15
> **kvonb said:**
> Sorry, I thought you would have tried it by now :)

It should work by putting it in the config file, but it won't hurt anything to simply run firestarter and change it from the GUI.

Make a backup copy of the config file first, just in case :)

i tried copying the settings that you have...iwaswondering thoughdo i need to have NAT enabled? the dot to the left in Azureusstays yellow...maybe that has to do with my speed problem

---

### Post by kvonb on 2007-05-15
Glad to see you got it working :)

The NAT in firestarter is only for what Microsoft call "Internet Sharing", ie if you are using your computer as a server or gateway for other computers in your house, but I don't think that applies to you so just leave that as it was (disabled).

That "NAT" thing at the bottom of Azureus' window is something entirely different, and I would simply ignore it as it looks like your downloads are working.

Remember how I said earlier that I "clamp" my incoming and outgoing Azureus connections to specific ports?  Well if you did that, then you will want to put those rules into Firestarter.

For example, in Azureus under tools->options->connection, I have my "Incoming TCP listen port and UDP listen port set to 42042, so in Firestarter I added the rule (under policy->inbound traffic policy, middle window "Allow service") 42042 for "Anyone", that opens the port to the outside world.

Having gone through my settings, I don't think you need to add the the outgoing port, and in Azureus v2.5.0.4 which I use, it doesn't seem to work anyway!

And unfortunately sleep is rather rare for me at the mo :(

Regards, Kev :)

---

### Post by Angelbeast on 2007-05-15
> **kvonb said:**
> Glad to see you got it working :)

The NAT in firestarter is only for what Microsoft call "Internet Sharing", ie if you are using your computer as a server or gateway for other computers in your house, but I don't think that applies to you so just leave that as it was (disabled).

That "NAT" thing at the bottom of Azureus' window is something entirely different, and I would simply ignore it as it looks like your downloads are working.

Remember how I said earlier that I "clamp" my incoming and outgoing Azureus connections to specific ports?  Well if you did that, then you will want to put those rules into Firestarter.

For example, in Azureus under tools->options->connection, I have my "Incoming TCP listen port and UDP listen port set to 42042, so in Firestarter I added the rule (under policy->inbound traffic policy, middle window "Allow service") 42042 for "Anyone", that opens the port to the outside world.

Having gone through my settings, I don't think you need to add the the outgoing port, and in Azureus v2.5.0.4 which I use, it doesn't seem to work anyway!

And unfortunately sleep is rather rare for me at the mo :(

Regards, Kev :)

yeah i got it to allow traffic when the firewall is open but my original issue was with the speeds of my downloads...what yu see in the screen shot is the highest it gets then is goes don to about 2 or 3 and just hovers there...athough earlier today i did try the default torrent client and it did get all the way up to 150 but then it went down to 3 and stayed there...and now in azureus where it said NAT it now says "firewalled" ... how do i make it faster? *LOL*

yeah i remember the days of no sleep...mine were mostly alchohol induced though...haha

---

### Post by Angelbeast on 2007-05-15
and shouldn't the tracker status be green? *LOL*

---

### Post by Angelbeast on 2007-05-15
oh yeah i forgot i was getting this also...

---

### Post by Angelbeast on 2007-05-16
la la la la

---

### Post by kvonb on 2007-05-16
> **Angelbeast said:**
> and shouldn't the tracker status be green? *LOL*

Quoting the infinite wisdom of Homer Simpson.....


Yeah, it'll do that!


Azureus is a strange creature, it does whatever it wants sometimes, and no end of fiddling seems to fix it!

You should find that after a while the NAT problem will vanish, and everything will be rosy.  Honestly, read their wiki, they say that it doesn't necessarily mean that you have a NAT problem!

Which version of Az are you running?  Maybe try a later one.

As for the lousy speeds, I am of the belief that they have written some kind of share limiting thing into it!  Like if you download too much and limit your uploads, they purposely slow you down!  Also that "distributed database" thing worries me, it has a continuous upload/download going on, it drives me nuts!

If you are getting connections in your torrents, and stuff is coming down, then all I can say is that it IS working, I really don't know much beyond that :(.

---

### Post by Angelbeast on 2007-05-16
> **kvonb said:**
> Quoting the infinite wisdom of Homer Simpson.....


Yeah, it'll do that!


Azureus is a strange creature, it does whatever it wants sometimes, and no end of fiddling seems to fix it!

You should find that after a while the NAT problem will vanish, and everything will be rosy.  Honestly, read their wiki, they say that it doesn't necessarily mean that you have a NAT problem!

Which version of Az are you running?  Maybe try a later one.

As for the lousy speeds, I am of the belief that they have written some kind of share limiting thing into it!  Like if you download too much and limit your uploads, they purposely slow you down!  Also that "distributed database" thing worries me, it has a continuous upload/download going on, it drives me nuts!

If you are getting connections in your torrents, and stuff is coming down, then all I can say is that it IS working, I really don't know much beyond that :(.

even when it'ssaying firewalled where the NT was? im using 2.5 ... think i should try the 3.0?  you think that might cure the repeating update each time i start?

---

### Post by Angelbeast on 2007-05-16
it looks like the onoy way i can get 3.0 is a source file which i have no idea how to compile

---

### Post by Angelbeast on 2007-05-16
i dunno...i still think something isn't right...i should be gettig better speeds than this...and now it says firewalled AND DHT Firewalled...

i would just go to ktorrent since iseem to gt t at least slightly better speeds but it chokes off all of my bandwidth and i can't browse websites at the same time...

---

### Post by Angelbeast on 2007-05-16
What is DHT?

---

### Post by kvonb on 2007-05-16
> **Angelbeast said:**
> What is DHT?

DHT is the distributed database tracker, it is the primary link between all clients.

Here are some more screenshots of my Firestarter, and also one of the "About" box from Azureus.  I see that you are using the same version, but have a look at your java version.

Now, I do notice that I am using Edgy, and you are using Feisty, but I wouldn't think that would be a problem :/

If it came to the crunch, you could always un-install Firestarter and see what happens.  You will still have the default firewall which is how I had my server until a week or so ago when I installed some more services that I needed more control over.  Otherwise you should be quite safe without Firestarter!

---

### Post by Angelbeast on 2007-05-16
> **kvonb said:**
> DHT is the distributed database tracker, it is the primary link between all clients.

Here are some more screenshots of my Firestarter, and also one of the "About" box from Azureus.  I see that you are using the same version, but have a look at your java version.

Now, I do notice that I am using Edgy, and you are using Feisty, but I wouldn't think that would be a problem :/

If it came to the crunch, you could always un-install Firestarter and see what happens.  You will still have the default firewall which is how I had my server until a week or so ago when I installed some more services that I needed more control over.  Otherwise you should be quite safe without Firestarter!

well forthe moment i uninstalled azureus...i went to ktorrent and started to download this: [http://www.mininova.org/tor/705697](http://www.mininova.org/tor/705697)

the speed on there got all the way up to 160 but like i said it chokes my bandwidth...is there any way to fix THAT? 

i don't keep firestarter running normally so would it still make a diff if i uninstalled it?

---

### Post by kvonb on 2007-05-16
> **Angelbeast said:**
> well forthe moment i uninstalled azureus...i went to ktorrent and started to download this: [http://www.mininova.org/tor/705697](http://www.mininova.org/tor/705697)

the speed on there got all the way up to 160 but like i said it chokes my bandwidth...is there any way to fix THAT? 

i don't keep firestarter running normally so would it still make a diff if i uninstalled it?

Yes, search in synaptic for "bandwidth" you should find something to limit the bandwidth there.

I guess if you click on "Stop the Firewall" it should just bypass all of Firestarter's rules, I'm not 100% sure though.

And I forgot to attach the bloody images to my last post, so here they are :)

---

### Post by Angelbeast on 2007-05-16
thank you sir...i'llcheck it out tomorrow...time for sleep now *LOL* ... 

thank you for all of your help :-)

---

### Post by Angelbeast on 2007-05-17
hey man...after i unistalled Azureus i seem to be getting better performance out of ktorrent...now i'm getting an average speed of 100Kbps and it's not choking my bandwidth now either...what the heck? *LOL* ... i had no clue that they could effect each other like that...

---

### Post by Angelbeast on 2007-05-19
well i found it's something with the network i'm on probably...i connected over at my moms on her network and even in the default torrent client i was getting close to 100Kb/s ... then when i get back here itgoes right down to 2-4 ... then i tried Aureus again and it says it's all firewalled no matter what settings i try...man this i just SO @$^@$!@#@ frustrating...i don't know why i had no problem on windows but i'm having all this trouble on Ubuntu...

---

### Post by direwolf08 on 2007-06-06
I would like to echo your frustration with Azureus.  I love that client for mac and pc (even though it is a total resource hog), but I must say I am unimpressed by the linux one.  

I set it up downloading a torrent with a REALLY good seed:leach ratio, and it would run for about 5 minutes before dying and going to 0 B/s down speed.  I tried all of the stuff in many of the threads on here (with firestarter, port forwarding, etc) and nothing helped.  I actually had to turn off firestarter because it was interfering with another device (an HD Homerun network HDTV tuner) . . . 

So, I decided to try KTorrent, and VOILA!  No problems whatsoever.  It is currently working perfectly (and has been for a 1/2-hour).    

Perhaps Azureus just doesn't play nice with my network (although the mac version on my laptop does fine).  Whatever the reason, I will switch to using KTorrent, and maybe go back to playing with Azureus some other time.

---

### Post by Angelbeast on 2007-07-20
Well i had some success by completly uninstalling and reinstalling Azureus with Automatix and it was working perfectly until a day or two ago and now i'm right back to square one...I guess it's back to KTorrent...

---

