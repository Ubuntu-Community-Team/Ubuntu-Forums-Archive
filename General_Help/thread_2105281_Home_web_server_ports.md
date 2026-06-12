---
title: "Home web server ports?"
date: 2013-01-15
forum: General Help
---

### Post by giantjoebot on 2013-01-15
I remember reading somewhere that if you're running a web server off your home internet connection, its a good idea to change the default ports of 80 and 443.  Is this still true?  

I also heard that some isp's block these ports.  I'm not sure how that works, how would you connect to the internet if those ports were blocked?

So what are some good alternative ports?  I want to hear your opinion....

---

### Post by sona1111 on 2013-01-15
the reason the ports would be blocked has something to do with past security threats, pretty stupid to me. But the reason is because they would just block port 80 outgoing, not incoming, so you could still access the internet. 

If you find using port 80 does not work, you can use another port and set up your DNS to forward FROM port 80 TO whatever port you used.

---

### Post by Cheesemill on 2013-01-15
> **sona1111 said:**
> the reason the ports would be blocked has something to do with past security threats, pretty stupid to me.
Nope. The reason they block these ports is to make you pay extra for a business connection instead of running a webserver off a home connection.
> But the reason is because they would just block port 80 outgoing, not incoming, so you could still access the internet.
You've got this the wrong way round, the port that would be blocked is incoming port 80 which is only used if you are hosting a webserver.
When you are browsing the internet your connection goes to port 80 on the webserver but the connection originates from a random high port (>1024) on your machine.
> If you find using port 80 does not work, you can use another port and set up your DNS to forward FROM port 80 TO whatever port you used.
DNS won't do this. All DNS is used for is to translate host names into IP addresses, it has nothing to do with port numbers at all.

---

### Post by giantjoebot on 2013-01-15
Yeah, but don't you have to be able to send a request to tell the server to send you stuff?  

Its starting to click.  I'm pretty sure I've been behind firewalls, and was still able to access servers, so I'm guessing requests are treated differently.

I understand that you can use port forwarding, but lets say this is a desktop, and you just installed a web server on it.  Wouldn't using port forwarding 80 screw up web browser since it uses port 80 also?  
I don't know I could be wrong.


edit: while I was typing Chessemill answered my question
> the connection originates from a random high port (>1024) on your machine. (>1024) on your machine.
I totally did not know that.  I thought it used 80


I'm really enjoying this discussion, Thank You

---

### Post by Cheesemill on 2013-01-15
Connections to web servers are made *to* port 80 on the server *from* a random high port on your machine.

The server sends the page back to the same high port on your machine that the request originated from.

So for normal web browsing there will be no incoming connections on port 80 to your machine.

Obviously if you are running a web server then requests would come into your machine via port 80. By blocking this traffic your ISP can prevent you running a web server on the standard port without affecting your browsing in any way.

---

### Post by giantjoebot on 2013-01-15
Then I assume its still a good idea to use an alternative port, but not necessary, unless your isp blocks 80 and 443.  And you could still port forward an alternative port to 80, but only incoming, because if you port forwarded both incoming and outgoing then it would screw up web browsing.  Correct?

The real reason I asked this is because I'm trying to build my own ubuntu using uck and remastersys.  Its for use in a home environment.  Its nothing special, but I wanted to make it available to the public.  I'm not sure if anyone will ever use it besides me, but just in case I wanted to configure the web server so that it would work for most people.

So I'm thinking it might be best to use alternative ports, but I'm still a little unsure.

---

### Post by Cheesemill on 2013-01-15
The problem with using alternate ports on a web server is that everyone who wants to connect needs to know you are doing so as well as the port you are using. For example if I was hosting a site and I wanted to tell other people about it I would have to say 'go to www.example.com:5642 in your browser'.

This seriously impacts on the accessibility of your site to the average user because they have to remember the port number as well as the notation for using it.

---

### Post by giantjoebot on 2013-01-15
Its just for using ajaxplorer.  And if you are running it at home, unless you use a dynamic DNS your going to have to use a complicated url anyways.

I mean, its not a website you want people to find.  Its something that you only want the people you know to access anyways.

But I do see your point.  It is harder to remember, and confusing for some.  The system I'm building has a xfce desktop, so maybe I'll just create a link to apache config file so people can change it if they want.  If I really wanted to make it easy, I guess I could create a simple script that would replace the apache config file with an altered config file with alternative ports.  I've never written a script in Linux before.  I made a couple for windows in the past.  Shouldn't be to hard.

---

