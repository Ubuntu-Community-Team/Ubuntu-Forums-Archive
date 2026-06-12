---
title: "Can you see my Apache Server?"
date: 2007-07-28
forum: General Help
---

### Post by thomasaaron on 2007-07-28
Hi, guys.

I'm trying to get an Apache web server set up on my ubuntu computer here at home.
Can someone see if they can access it? (I won't be able to test it from outside until Monday).

[http://67.177.234.61](http://67.177.234.61)

of maybe

[http://67.177.234.61/index.html](http://67.177.234.61/index.html)

Thanks,
Tom

---

### Post by Happy_Man on 2007-07-28
> **thomasaaron said:**
> Hi, guys.

I'm trying to get an Apache web server set up on my ubuntu computer here at home.
Can someone see if they can access it? (I won't be able to test it from outside until Monday).

[http://67.177.234.61](http://67.177.234.61)

of maybe

[http://67.177.234.61/index.html](http://67.177.234.61/index.html)

Thanks,
Tom
Sorry, no.

---

### Post by davidjmayo on 2007-07-28
again NO
cannot connect to either
 but can ping from a terminal with no error

---

### Post by thomasaaron on 2007-07-28
OK. I just fiddled with my Linksys router's port forwarding settings.
Could someone please try again? I appreciate the help.

Best,
Tom

---

### Post by davidjmayo on 2007-07-28
Now it's worse error:
Problem loading page

before it said connecting but didn't

---

### Post by thomasaaron on 2007-07-28
OK. Well, that's confusing. I'll try to see if Apache has some kind of firewall in place.

---

### Post by thomasaaron on 2007-07-28
OK. I've diddled with some config files.
I doubt it will work, but can you give it a try.
If it doesn't work, I've got one last idea for today.

Thanks again.

Best,
Tom

---

### Post by davidjmayo on 2007-07-28
Still problem loading page
Unable to connect

does this help you figure out what's wrong

david@david:~$ tracepath 67.177.234.61
 19:  12.122.86.249 (12.122.86.249)                        asymm 15 266.239ms
20:  12.116.159.6 (12.116.159.6)                          asymm 17 239.869ms
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  c-67-177-234-61.hsd1.co.comcast.net (67.177.234.61)  asymm 127 270.289ms reached
     Resume:

hops 1-18 are all ok so I didn't include them to cut down the length.

---

### Post by fjgaude on 2007-07-28
Still no-go: "67.177.234.61" refused the connection.

Sorry about that. <smile>

frank

---

### Post by thomasaaron on 2007-07-28
Thanks for sticking around. I've got one last idea.
Should only take a few minutes to set up.

If it doesn't work, I found a big, complicated tutorial I'll try to work through over the weekend.

Standby...

---

### Post by fjgaude on 2007-07-28
Okay on pinging you, 52.3 ms time, but no-go on the web page.

Has to be with your router and how it is letting ports through. Wish I could be of more help.

frank

---

### Post by Mustafa Temizel on 2007-07-28
Lets take a look to my server. I have just installed lighttpd.

[http://85.104.63.7/](http://85.104.63.7/)

---

### Post by thomasaaron on 2007-07-28
OK, that's all I can think of at the moment.
If it doesn't work, I guess I've got my work set out for me.

If it doesn't load, what message do you get on your browser?

I'm not sure what to make of the ping results. It looks like it was working for you, but then I tried to get on the page at the same time and you started to get errors.(?)

I can access it from in my house no problem.

Thanks for all your help.

Best,
Tom

---

### Post by davidjmayo on 2007-07-28
> If it doesn't load, what message do you get on your browser?

Unable to connect
      
Firefox can't establish a connection to the server at 67.177.234.61

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

---

### Post by fjgaude on 2007-07-28
I'm using Epiphany and I get this as before:

   “67.177.234.61” refused the connection.

frank

---

### Post by por100pre1 on 2007-07-28
> **Mustafa Temizel said:**
> Lets take a look to my server. I have just installed lighttpd.

[http://85.104.63.7/](http://85.104.63.7/)

This one works...

---

### Post by fjgaude on 2007-07-28
Yes, works here too, and nice place holder page:

  [http://85.104.63.7/](http://85.104.63.7/)

frank

---

### Post by thomasaaron on 2007-07-28
It sounds like you guys are getting blocked by my router.

I just made some adjustments to it.
And this really *IS* the last one for the day! :^o

---

### Post by rillip on 2007-07-28
nope, sorry

---

### Post by thomasaaron on 2007-07-28
I think I figured it out.
It appears Comcast blocks incoming Port 80 so that people can't run web servers from their home.

---

### Post by thomasaaron on 2007-07-28
Can someone try these and let me know if it works?

[http://67.177.234.61:1234](http://67.177.234.61:1234)

and if that doesn't work...

[http://67.177.234.61.1234/index.html](http://67.177.234.61.1234/index.html)

Thanks,
Tom

---

### Post by jm2003uk on 2007-07-28
Your top link is working for me. The 2nd link isn't working though, you've put a "." instead of a ":" between the IP and port, otherwise that link will also work.

Good job on sorting it out :)

---

### Post by fjgaude on 2007-07-28
Wow, that's a strong possibility... I think AT&T has the same policy... no home web sites. You have to pay lots more for a fixed URL.

Tom's link works for me, yes.

frank

---

### Post by thomasaaron on 2007-07-28
Well, in retrospect, if it weren't for having to luck across that solution, Apache is VERY easy to set up.

Download it, tell it what port to listen on, start it.

Thanks for the help, guys. Much appreciated.

Best,
Tom

---

### Post by p_quarles on 2007-07-28
I'm on AT&T, and have no problem opening up port 80 for public access. In fact, it's one of the specific configuration options in the modem they sold me. 

That said, I did need to configure both my modem and my router to get that access working. If you have an all-in-one modem/router, then that's not going to help, but if they are separate devices I would check the modem for any firewall that might be operating on it. Just a thought.

Another thought is that (hypothetically) you could set up a domain name with dynamic DNS, and have the DNS server send the requests for your server to a port that you can use.

---

### Post by thomasaaron on 2007-07-28
When I googled "Comcast Block Port 80" there were a bunch of hits. About half of them swear Comcast IS blocking port 80, and the other half say they are not.

I've got a feeling it may vary depending on where you are. Probably the same with other ISPs as well.

---

### Post by fjgaude on 2007-07-28
From what I've heard both Comcast and AT&T monitor usage and if they see a home connection out of line with the average they pay attention... if it gets too high you get a phone call, a notice to get a business license.

Anyway, glad you see where you are going, got things working.

frank

---

### Post by thomasaaron on 2007-07-30
Mine is mostly for personal experimentation. So hopefully, I'll slip the noose. :-\"

Also, so far I've only checked out freedns.afraid.org.
It looks like they don't allow you to put a port designation on your ip address. Hmmm...

---

