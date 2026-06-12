---
title: "WebServer"
date: 2007-09-27
forum: General Help
---

### Post by ghostcrab on 2007-09-27
Hi I was wanting to host a web sight I put together. 
But I was looking for software that is easy to use and a GUI to see who is browsing the page?

---

### Post by LaRoza on 2007-09-27
Hosting a website is easy. Maintaining, ensuring security, and keeping online is harder.

Most servers don't use GUI's for a reason. 

I have written scripts to record traffic, but you can not see who is browsing the page at the moment because http is a stateless protocal.

---

### Post by gautada on 2007-09-27
> **ghostcrab said:**
> Hi I was wanting to host a web sight I put together. 
But I was looking for software that is easy to use and a GUI to see who is browsing the page?

Web servers are fairly easy to administer but the are no means simplistic.

1.) You need a server.  Usually a service like go-daddy.com can host pages for you.  If you want to do it from home then a broadband connection is a must.  And that is for very few viewers of your website.

2.) Analytics need to be setup.  You can do this using either log processors like [webalizer]("http://www.mrunix.net/webalizer/") or [google-analytics]("http://www.google.com/analytics/").


To install these packages 

```
%> sudo apt-get install apache2 webalizer
```

---

### Post by ghostcrab on 2007-09-27
Maintaining, ensuring security I could not agree more..
I found digging in this forum their is some free hosting sight's I'm looking into them now as we type.

I'm thinking it will be easer for me just to go with one of the free hosting services then go from their..
thank you for the quick reply

---

### Post by ghostcrab on 2007-09-27
> **gautada said:**
> Web servers are fairly easy to administer but the are no means simplistic.

1.) You need a server.  Usually a service like go-daddy.com can host pages for you.  If you want to do it from home then a broadband connection is a must.  And that is for very few viewers of your website.

2.) Analytics need to be setup.  You can do this using either log processors like [webalizer]("http://www.mrunix.net/webalizer/") or [google-analytics]("http://www.google.com/analytics/").


To install these packages 

```
%> sudo apt-get install apache2 webalizer
```

Well I was going to do a smooth wall and then build another PC to put a server on  and just use my laptop.
just in case anything happends to the sight I really would not care and I can run away with my laptop screming OMG...:) ... J/K

thank you I'm still looking into all this I guess the GUI's are bad because people like to play game's anyway thank you all you guy's are great

---

