---
title: "Sendmail Not Working..."
date: 2008-05-27
forum: General Help
---

### Post by jlacroix on 2008-05-27
I have a text file that I want sent to myself to my gmail account each week. I set up a cron job for it, but the email that is sent is never received.

The thing is, I set up a web server at work that does this, and I got it working, but I can't remember what I did. I scoured over the configuration files on the server but I can't find what magic trick I used to get it working.

Now, I am trying to get this to work on a home machine and I'm pretty sure its not sending due to a problem with the fully qualified domain name. I don't have a domain name for the machine I'm working on now. What do I need to type and where to get the emails to my gmail account? Below is the command my server uses and it works:

```
cat /root/update.txt | mail -s "PC Updated" jlacroix82@gmail.com
```

---

### Post by mattress on 2008-05-27
Depending on how you connect to the internet you will probably have to relay your outgoing email through your ISPs smart host. There is a SmartHost entry in your sendmail.cf file which will allow you do do this.

If you could paste a section of your mail log when you actually try and send the mail, it would be a lot easier to find the problem. Personally I would use something like Postfix or Exim as sendmail is a bit of a handful to work with...

m

---

### Post by jlacroix on 2008-05-27
> May 10 18:10:08 krystal-desktop sendmail[2626]: My unqualified host name (krysta
l-desktop) unknown; sleeping for retry
May 10 18:11:08 krystal-desktop sendmail[2626]: unable to qualify my own domain 
name (krystal-desktop) -- using short name
May 10 18:11:08 krystal-desktop sm-mta[2687]: My unqualified host name (krystal-
desktop) unknown; sleeping for retry
May 10 18:11:10 krystal-desktop sm-msp-queue[2692]: My unqualified host name (kr
ystal-desktop) unknown; sleeping for retry
May 10 18:12:08 krystal-desktop sm-mta[2687]: unable to qualify my own domain na
me (krystal-desktop) -- using short name
May 10 18:12:10 krystal-desktop sm-msp-queue[2692]: unable to qualify my own dom
ain name (krystal-desktop) -- using short name
May 10 18:17:52 krystal-desktop sendmail[4348]: My unqualified host name (krysta
l-desktop) unknown; sleeping for retry
May 10 18:18:52 krystal-desktop sendmail[4348]: unable to qualify my own domain 
name (krystal-desktop) -- using short name
May 10 18:18:52 krystal-desktop sm-mta[4410]: My unqualified host name (krystal-
desktop) unknown; sleeping for retry
May 10 18:18:54 krystal-desktop sm-msp-queue[4415]: My unqualified host name (kr
ystal-desktop) unknown; sleeping for retry
May 10 18:19:52 krystal-desktop sm-mta[4410]: unable to qualify my own domain na
me (krystal-desktop) -- using short name
May 10 18:19:52 krystal-desktop sm-mta[4465]: NOQUEUE: SYSERR(root): opendaemons


I think that's it.

I'm not opposed to using exim or whatever else there is. Whatever gets this job done is fine with me. I would just need to know how to set up my command (which I posted above) to make it work. I'm very good at linux administration but I'm a complete noob when it comes to sending email from a Linux box so I'd need for someone to tell me exactly what to type and where.

---

