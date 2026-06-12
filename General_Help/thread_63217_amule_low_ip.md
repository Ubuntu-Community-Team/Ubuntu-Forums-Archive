---
title: "amule low ip"
date: 2005-09-07
forum: General Help
---

### Post by oliwally on 2005-09-07
I have been trying to get amule going but I keep on running on low IP. 

I'm running Guarddog Firewall and have configured it so that the appropriate ports (4662) are available. I have even disabled guarddog / the firewall and tried, but with no luck.

Have gone to the amule site ([http://www.amule.org/testport.php](http://www.amule.org/testport.php)) to test my connection and had the following return:

> Error: TCP port 4662 is unavailable. Make sure your firewall or router is allowing/forwarding this TCP service port and your ED2K client is running (i.e. aMule, eMule).

Detailed Error Message
TCP Error 111 Connection refused

Explanation
The port is available for connections but a connection was refused meaning there is nothing listening on that port. This most likely means you can use ED2K but your client is not currently running. Try running this test again with an ED2K client running to make sure you can really establish a connection. No info available; this TCP error probably indicates a problem with the networking on your system (i.e. the TCP/IP stack). 

What do I need to do to enable me to download using amule? I can connect to servers, but it's always with low ID. I'm stuck. Please help.

---

### Post by jeremy on 2005-09-07
Do you use a router, and, if so, have you enabled NAT?

---

### Post by oliwally on 2005-09-07
Hi jeremy. thanks for helping out.

> Do you use a router
I go through an adsl modem (D-Link Dsl-302G) and a small 6 port ethernet hub. I'm not sure if that qualifies as a router.

> have you enabled NAT
I have checked my modem for this and appears to be enabled ([http://10.1.1.1](http://10.1.1.1)) but I have no idea if the settings are what they need to be...

---

### Post by oliwally on 2005-09-08
Your question about NAT has sparked a whole new line of searches. It appears that my modem has a particular issue with letting amule do it's thing (see [http://forum.swiftdsl.com.au/archive/index.php/t-1824.html)](http://forum.swiftdsl.com.au/archive/index.php/t-1824.html)).

Seemingly there is a lot of mucking around to get it working and I can't be bothered trying to give it a go only to find that I have to reset everything to default and then reconfigure bla, bla, bla

The question then would be - is there another method of filesharing in linux that does not use the bittorrent / amule / emule / azureus or any of those? Are there other options?

---

### Post by rafakl on 2005-09-08
i have a low id in amule, and still can download files.

The reply from the page you posted to test the port was:

Error: TCP port 4662 is unavailable. Make sure your firewall or router is allowing/forwarding this TCP service port and your ED2K client is running (i.e. aMule, eMule).

... and my client is running!!!

Did you select a good and fast server??? sometimes amule selects for me a really bad server and i cant search or donwload anything!!!
 ](*,)

---

### Post by oliwally on 2005-09-08
Yes, I tried all the various servers but still no luck. I partially downloaded one file very slowly once, but it just wasn't usable that way

I have just found a solution to my problem though - use Apollon instead. I followed the instructions at [http://ubuntuforums.org/showthread.php?p=339689#post339689](http://ubuntuforums.org/showthread.php?p=339689#post339689) and it worked beautifully. 

It would be interesting to know the difference between the two - that is, why would it be better to use the networks amule is accessing opposed to the networks apollon is using (as I understand it they use different networks, but please correct me if I'm wrong). Are there any pros and cons?

---

### Post by rafakl on 2005-09-08
i dont know very well the other networks that apollon supports, but its worth a try!!!

---

### Post by wickwire on 2006-01-07
Hello,

I'm using Ubuntu and amule 2.0.3 - I always connect with Low ID, I have TCP port 10000 set in the Preferences area, but when I go to

[http://www.amule.org/testport.php](http://www.amule.org/testport.php)

I get this:

"Success The TCP port 10000 is available. You should be able to use the ED2K P2P service without any problems.

Your public address is 84.39.xx.xx (84.39.xx.xx)

I replaced with "x" up there. So I'm a bit puzzled with this... all the servers, always LowID.

Bittorrent connects fine with firewall warnings...

Any ideas?

---

### Post by wickwire on 2006-01-07
Uhmmm there was an ticked option in Preferences --> Security: IP Filtering. Once I unticked it, reconnected, I have High ID :D

---

