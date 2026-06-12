---
title: "Apache2 behind router"
date: 2005-09-09
forum: General Help
---

### Post by mealots on 2005-09-09
Ok I have read may forums and have yet to find the answear to this question.

I want to set up a webserver that my friends around the contry can goto and look at text behind this router:  Linkskey lkr-604.

I installed apache with synaptic and can type 127.0.0.1 and see the apache web server parent directory.

I cannot type 192.168.1.152 on my windows pc that is on same internal network under same router and see apache.

I have tried DMZ, and opening port 80 and 21 and setting external port as 8080 and internal as 80.  Does nothing useful.

If I type in the gateway that charter gives me I can see my router not the DMZ computer on 192.168.1.152.  

If I try http://"charterip"/192.168.1.152; or http://"charterip"/8080 nothing.

So what am I missing to make it possible to simply see through my router to the apache folder like I can with 127.0.0.1 on the linux server thanks all :).

p.s. i have not domain name server registered, will this present a problem?

---

### Post by dave9191 on 2005-09-09
127.0.0.1 is a local address of the computer, which will only work on that comptuer. You need to be able to type the IP address of the comptuer on the local network. From the ubuntu machine and any other computer on the network. If you cant do that its probably the apache config which might be set up to only allow local connections as opposed to ones from the network. 

Once you can access the webpage using the LAN IP, you need set the router up to forward port 80 or whatever port you are running apache on over to the IP of the ubuntu machine. Then people from the net will be able to access your server. And not having a domain isnt a problem, they will just need your internet IP address. Or you can get a free domain from homeip.net. 

Dave

---

### Post by mealots on 2005-09-09
Ok I can access server on lan now, should i just be able to type the charter ip they gave me to access the server from a windows machine.?

and I have to port trigger or port forward to get port 80 to go through like I said ealier with 8080 external 80 internal?

Thanks.

---

### Post by billy314159 on 2005-09-09
[QUOTE=mealots]Ok I can access server on lan now, should i just be able to type the charter ip they gave me to access the server from a windows machine.?

and I have to port trigger or port forward to get port 80 to go through like I said ealier with 8080 external 80 internal?

Thanks.[/QUOTE]
 You know what, I don't even recommend using the router ip for a webserver, as every time the power goes out, or you unplug the router, it caontacts tour isp and gets a NEW ip address, which is a pain.

---

### Post by billy314159 on 2005-09-09
[QUOTE=mealots]Ok I have read may forums and have yet to find the answear to this question.

I want to set up a webserver that my friends around the contry can goto and look at text behind this router:  Linkskey lkr-604.

I installed apache with synaptic and can type 127.0.0.1 and see the apache web server parent directory.

I cannot type 192.168.1.152 on my windows pc that is on same internal network under same router and see apache.

I have tried DMZ, and opening port 80 and 21 and setting external port as 8080 and internal as 80.  Does nothing useful.

If I type in the gateway that charter gives me I can see my router not the DMZ computer on 192.168.1.152.  

If I try http://"charterip"/192.168.1.152; or http://"charterip"/8080 nothing.

So what am I missing to make it possible to simply see through my router to the apache folder like I can with 127.0.0.1 on the linux server thanks all :).

p.s. i have not domain name server registered, will this present a problem?[/QUOTE]
 I wouldn't use the router ip as the domain, as it changes, say when the power goes out or you unplug the router.  I learned the hard way

---

### Post by mealots on 2005-09-09
so what ip should I use since I have to get through the router, also I just changed the ports.conf file to Listen 80 Listen 8080 is that correct?

---

### Post by mealots on 2005-09-09
still nothing what am i suppose to type in on windows computer to see apache web server if I was on a computer on the internet?

[http://68.117.5.38:8080](http://68.117.5.38:8080)    ?
[http://68.117.5.38/192.168.1.151:8080](http://68.117.5.38/192.168.1.151:8080)   ?

---

### Post by dave9191 on 2005-09-09
[QUOTE=mealots]still nothing what am i suppose to type in on windows computer to see apache web server if I was on a computer on the internet?

[http://68.117.5.38:8080](http://68.117.5.38:8080)    ?
[http://68.117.5.38/192.168.1.151:8080](http://68.117.5.38/192.168.1.151:8080)   ?[/QUOTE]

[http://68.117.5.38](http://68.117.5.38) should do the trick. But it wont work on a computer on the LAN. So you will have to get someone on the net to check if your server is accessible. 

Dave

---

### Post by mealots on 2005-09-09
hmm I had another friend type in my real address xxx.xxx.xxx.xxx:8080 and xxx.xxx.xxx.xxx and they got nothing on 8080 and an error on just the number?

---

### Post by dave9191 on 2005-09-10
[QUOTE=mealots]hmm I had another friend type in my real address xxx.xxx.xxx.xxx:8080 and xxx.xxx.xxx.xxx and they got nothing on 8080 and an error on just the number?[/QUOTE]

By number I assume you mean IP address rather then the port number. And what error? 

Dave

---

### Post by mealots on 2005-09-10
My friend gets a 404 file not found error, and yes I mean xxx.xxx.xxx.xxx as ip and :8080 as port # thanks.

---

### Post by dave9191 on 2005-09-10
Well a 404 error would be generated by a server. If he couldnt connect to it then he would get a no route to host message from the browser. So he is either connecting to another server, or its an apache config prob. 

Dave

---

### Post by FastZ on 2006-11-28
> **mealots said:**
> Ok I have read may forums and have yet to find the answear to this question.
 
I want to set up a webserver that my friends around the contry can goto and look at text behind this router: Linkskey lkr-604.
 
I installed apache with synaptic and can type 127.0.0.1 and see the apache web server parent directory.
 
I cannot type 192.168.1.152 on my windows pc that is on same internal network under same router and see apache.
 
I have tried DMZ, and opening port 80 and 21 and setting external port as 8080 and internal as 80. Does nothing useful.
 
If I type in the gateway that charter gives me I can see my router not the DMZ computer on 192.168.1.152. 
 
If I try http://"charterip"/192.168.1.152; or http://"charterip"/8080 nothing.
 
So what am I missing to make it possible to simply see through my router to the apache folder like I can with 127.0.0.1 on the linux server thanks all :).
 
p.s. i have not domain name server registered, will this present a problem?
 
Ok first of all, go to [http://www.dyndns.org](http://www.dyndns.org) and register yourself a free domain name that you can assign to your router. You will need the IP address that your ISP is giving you, not any of the ones the router assigns to computer within your network (basically not an IP address that starts with 192.168.x.x). [http://"charterip"/192.168.1.152]("http://") and [http://"charterip"/8080]("http://") are both invalid URLs. The URL to your router should be (before you get a free domain name from DynDNS.org) [http://{IP](http://{IP) address from your ISP}/ and that's it. There is no need to place your internal IP address in your URL. By default, the Hyper-Text Transfer Protocol uses port 80. Port 8080 is used as an alternate and it's use requires a port override which I am not going to get into because I dont know how that works. Dont use port 8080 unless you really, absolutely, necessarily have to use it for some weird reason....there's not need to use it if you dont have to. All I know is, you need to forward port 80 on the router to port 80 on your server. If you are going to be using FTP services on your server, you need to set up a separate port forwards, following the same method as above for port 21, which is the default FTP port. So forward port 21 on the router to port 21 of the server computer. Remember to go into your Apache configs and get rid of all the 8080 stuff and change it to 80 instead.  Oh, and make sure your server computer is set up with a STATIC IP ADDRESS.
 
 
> **mealots said:**
> Ok I can access server on lan now, should i just be able to type the charter ip they gave me to access the server from a windows machine.?
 
and I have to port trigger or port forward to get port 80 to go through like I said ealier with 8080 external 80 internal?
 
Thanks.
 
Here, I still dont understand why you want to use port 8080. Set everything to port 80 for http and you should be able to just type in your Charter IP address and you will access your web server.
 
 
> **mealots said:**
> so what ip should I use since I have to get through the router, also I just changed the ports.conf file to Listen 80 Listen 8080 is that correct?
 
Get rid of the 8080.
 
> **mealots said:**
> still nothing what am i suppose to type in on windows computer to see apache web server if I was on a computer on the internet?
 
[http://68.117.5.38:8080](http://68.117.5.38:8080) ?
[http://68.117.5.38/192.168.1.151:8080](http://68.117.5.38/192.168.1.151:8080) ?
 
The second one is an invalid URL, again, there is no need to add your internal IP address in the url. If you set your router up to forward port 80 (the default http port) coming from the internet to port 80 of your server, you will be good to go and all you will have to type in is your IP address from Charter.
 
 
Hope this helps. It's rather simple once you get it working and look back on how you made it work. Good luck.

---

### Post by dave9191 on 2006-11-28
Hey, 

Don't get me wrong, a good informative post, we always need more of them on the forums. 

But this thread is over a year old... what possessed you?

--
Dave

---

### Post by FastZ on 2006-11-28
Holy crap!  My mistake.  I guess I didnt see the year...just the September and though it was only a few months old.... Oops.

Hmm...maybe some of these older threads should be archived after they age for a certain amount of time so people like me overlook the obvious and revive a dead thread when he/she shouldnt?

---

### Post by dave9191 on 2006-11-29
That may well be a good way to go. Why don't you suggest it to the forum admins?

---

