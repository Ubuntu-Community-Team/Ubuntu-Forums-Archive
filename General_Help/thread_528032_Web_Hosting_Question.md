---
title: "Web Hosting Question"
date: 2007-08-17
forum: General Help
---

### Post by jay0316 on 2007-08-17
Hi,

The company I work at  is bringing our web hosting in house, and I was
hoping you could give us some feedback on using a Linux server.  We will eventually have 5 domains we plan on hosting.  As their hosting plans expire, we will be adding them to the in house server. We are interested in installing an Ubuntu server, however our IT staff has limited
experience with Linux.

Have you or someone you know used the Ubuntu server software before?

What if any problems did you run into?

Were you able to resolve issues on your own?

Did you purchase any support packages?

Is it difficult to support?

What are the advantages to using Ubuntu over Windows?

What is the best Linux Server distribution for web hosting?

Do you recommend CPanel?  Why or Why Not?

Any other information/recommendations you can add would be great!

Thanks a lot.  Your response will help us to decide whether to install
windows or Linux on our new server.

Jason Peterman

---

### Post by az on 2007-08-17
> **jay0316 said:**
> 

Did you purchase any support packages?

Is it difficult to support?

What are the advantages to using Ubuntu over Windows?

What is the best Linux Server distribution for web hosting?

Do you recommend CPanel?  Why or Why Not?


It depends on exactly what you want to do.  If you want to emulate what your web hosting provider is currently doing, all you really need is a LAMP stack:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Will you be hosting DNS or mail, too?  
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

Whether you need Cpanel or not depends on you.  Cpanel helps users accomplish tasks remotely through a web interface.  Since your servers will be right in front of you, or completely accessible through ssh, you may find it simpler to just do the jobs using the command line.  

Is it difficult to support?  That's a good question.  You can't install any software on any operating system and expect it to run itself and to take care of security by itself.  What you are going to have to do and what you are going to have to be careful about really depends on exactly what you are going to do.  Certainly a support contract is a good idea.  That being said, other than keeping up to date with security updates and being mindful of potential vulnerabilities, the system is easy to maintain.

Just grab any 'ol box you have lying around and install LAMP on it.  Try it out.  Copy your sites onto that box and run them in-house for a little while.  There is no cost in doing that.  And you will have a better idea of what you will be dealing with.

I'm sorry but I never ran a windows server, so I can't compare.  I don't really know what you are expecting to be there and what not to be.

---

### Post by dysolve on 2007-09-03
I currently look after a webserver running on win2003 SBS server and I found it very easy to configure and keep running,

But the down falls are as follows

1. Price: SBS cost AU$1000's hardware had to be upgraded costing $5000. all the extras you need cost extra money. I could easily say it cost over $10000 to get the web server up and running..
2. basic configuration was easy but beyond basic became tricky

I am currently looking in to setting up a Ubuntu web server with FTP access at home but my major problem with that is theres so many different ways to do it and I have found very few people can explain the pros and cons to each setup.

the major advantages are as follows

1. cost: my old dual P2 400mhz machine will be over kill( got free from work when they upgraded) Ubuntu was free.. (my ISP even hosts the latest copy so the 4gig download did not effect my monthly usage) just about every piece of software you need is free..
2. lots of help on the web..(THANKS!)

now I just have to pick which setup to use..

---

