---
title: "Getting to port 8080 pages"
date: 2007-08-26
forum: General Help
---

### Post by catalina on 2007-08-26
I have a xubuntu machine that I am trying to connect to local browser pages in windows 2003 server and am wondering how I can tackle this.  I have the privilege of being able to address the server settings so what would be the quickest, easiest way to access the pages?

---

### Post by freebeer on 2007-08-26
Have you tried to access the pages with

```

https://*ipaddress*:8080

```

in your browser?

Unless I'm mis-reading your question...

---

### Post by catalina on 2007-08-27
Yes, it is actually [http://myweb:8080/default.aspx](http://myweb:8080/default.aspx)

I think it is either a microsoift issue or I don't have sufficient software downloaded to read the asp pages.

---

### Post by freebeer on 2007-08-27
Well, I'm no expert, but I'm pretty asp pages are server side - so the client doesn't need anything special (other than a standard browser) to read the pages.  Perhaps you were referring to the server side of things?

Also you may take note that I had https://  (note the **s**).  I've run into situations where the s was necessary in order to address sites with :8080 (secure).  Usually I get an error message to that effect, though.

---

### Post by catalina on 2007-09-01
Yes, I have tried that, but I can access them on the windows partition just by going [http://myweb:8080/default.aspx](http://myweb:8080/default.aspx)

I am still at a loss as to how to get to my local pages.  I must be missing some small thing??

---

### Post by freebeer on 2007-09-01
I'm missing something here... when you say you can access the "windows partition" do you mean that you can access the pages from the Win2003 server using that address?

If so, then from the xubuntu box you'll need to use the IP address of the Win2003 box as part of the URL.  Something like: 

```

http://192.168.1.100:8080

```

(Assuming that the IP address of the Server is 192.168.1.100, of course.)

---

### Post by catalina on 2007-09-03
Hi Freebeer,

You jogged my memory regarding the ip address.  The guy that set up the local pages did not register the domain that I was using so when I was inputting "http://myweb..." it was scanning the internet for the local pages instead of going right to the server (192.168.1.6:8080)

I put in the ip address, and voila!

Thank you for your help!  By the way, I am from Sault Ste. Marie and am an isolated Linux user.  Most guys up here are only into asp.net but I am wanting to transfer out of microsoft and into open source.

Thank you again for your help.

Dean.

---

### Post by freebeer on 2007-09-05
Glad I could be of some help (even if only in an indirect way - but often it's that little tip/observation that leads you to the solution).  :D

The Soooo, eh?  Soobuntu sounds kinda neat.  So I take it that you guys have electricity now, or are you still running on hamster power?  (just kidding, of course - I'm in an isolated area, too, as far as Linux is concerned.  Thanks to these forums, support is not an issue!)

---

