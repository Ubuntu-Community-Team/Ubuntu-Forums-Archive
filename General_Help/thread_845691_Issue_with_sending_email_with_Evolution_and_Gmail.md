---
title: "Issue with sending email with Evolution and Gmail"
date: 2008-06-30
forum: General Help
---

### Post by osabr22000 on 2008-06-30
I've been working for several days trying to use Evolution to send email through my Gmail account.  Right now I can receive emails into evolution, but I cannot send them.  The error I get is:
"Error while performing operation.

Host lookup failed: smtp.gmail.com : Name or service not known"
I've checked multiple websites to check what my settings should be and right now they are:
*Receiving*
server: pop.gmail.com
username:  [email]myemail@gmail.com[/email]
Security:  SSL encryption
Authentication Type:
Password

*Sending*
Server Type: SMTP
Server: smtp.gmail.com:587
Security: SSL Encryption
Authentication
Plain
Username: [email]myemail@gmail.com[/email]

Also, my under POP settings on my gmail account it says:
"POP Download:
Learn more		
1. Status: POP is enabled for all mail that has arrived"

Has anyone encountered anything like this at all?  Please let me know what I should do.  I've checked just about every reference I think I could find and none of it worked.

---

### Post by M4rotku on 2008-06-30
I also cannot get Evolution to send e-mails via gmail

---

### Post by lsutiger on 2008-06-30
The port number is not 587, it is 465, so your smtp server setting should be:
smtp.gmail.com:465
Also, I have my authentication type set as PLAIN.

---

### Post by soccerboy on 2008-06-30
I would suggest using IMAP.  It does a better job.  Here are my settings.
server: imap.gmail.com
Port: 993
username: [email]abc@gmail.com[/email]
SSL
Use Secure Connection not checked
Outgoing server: smtp.gmail.com
Port: 587
Use name and Password: [email]abc@gmail.com[/email]
Use secure connection: TLS

These settings are from thunderbird but I used to have it setup in Evolution with very similar settings.  See if these work for you.  Don't forget to enable imap from your Gmail account.

---

### Post by osabr22000 on 2008-06-30
> **lsutiger said:**
> The port number is not 587, it is 465, so your smtp server setting should be:
smtp.gmail.com:465
Also, I have my authentication type set as PLAIN.

I switched my port number to 465 and still no luck...  Also, my authentication was plain for sending.  Thank you though for the input

---

### Post by soccerboy on 2008-06-30
> **osabr22000 said:**
> I switched my port number to 465 and still no luck...  Also, my authentication was plain for sending.  Thank you though for the input

Have you turned on Authentication for smtp along with TLS Encryption?
Google documented it as SSL but only TLS works.

---

### Post by osabr22000 on 2008-06-30
> **soccerboy said:**
> I would suggest using IMAP.  It does a better job.  Here are my settings.
server: imap.gmail.com
Port: 993
username: [email]abc@gmail.com[/email]
SSL
Use Secure Connection not checked
Outgoing server: smtp.gmail.com
Port: 587
Use name and Password: [email]abc@gmail.com[/email]
Use secure connection: TLS

These settings are from thunderbird but I used to have it setup in Evolution with very similar settings.  See if these work for you.  Don't forget to enable imap from your Gmail account.


I tried these also soccerboy and recieved the same error.  It appears that the Imap change went through okay...

---

### Post by fragos on 2008-06-30
What works for me:

smtp.gmail.com:465
"Server requires authentification" checked
SSL encription
Authentification Type: PLAIN

---

### Post by M4rotku on 2008-06-30
Soccerboy,

I tried fiddling with the configs you stated and couldn't get it to work.

How well does Thunderbird work?

---

### Post by soccerboy on 2008-06-30
> **osabr22000 said:**
> I tried these also soccerboy and recieved the same error.  It appears that the Imap change went through okay...

It works for me with the exact same configurations.  Have you tried to ping the server.  Try to ping yourself.  It appears your dns is not working correctly.

---

### Post by M4rotku on 2008-06-30
Fragos,

I just tried your settings and got the following error:

> Error while performing operation.

MAIL FROM command failed: No identity changes permitted. z52sm8565415pyg.1

---

### Post by soccerboy on 2008-06-30
> **M4rotku said:**
> Soccerboy,

I tried fiddling with the configs you stated and couldn't get it to work.

How well does Thunderbird work?

Thunderbird works great.

---

### Post by osabr22000 on 2008-06-30
> **fragos said:**
> What works for me:

smtp.gmail.com:465
"Server requires authentification" checked
SSL encription
Authentification Type: PLAIN

Fragos, I still received the exact same error...

---

### Post by soccerboy on 2008-06-30
gmail imap uses SSL but the SMTP uses TLS encryption.

---

### Post by osabr22000 on 2008-06-30
> **soccerboy said:**
> It works for me with the exact same configurations.  Have you tried to ping the server.  Try to ping yourself.  It appears your dns is not working correctly.

What exactly do I need to do to ping the server?  I'm such a noob.  Do I need to open the terminal?  Thanks for helping.

---

### Post by soccerboy on 2008-06-30
> **osabr22000 said:**
> What exactly do I need to do to ping the server?  I'm such a noob.  Do I need to open the terminal?  Thanks for helping.

you open up a terminal and type ```
ping smtp.gmail.com
```

post the output.

No problem about the noob.  I am pretty new at linux too and I learn as much as possible by just browsing through the forums.

---

### Post by fragos on 2008-07-01
> **osabr22000 said:**
> Fragos, I still received the exact same error...

The configuration works for me on on multiple systems. I'd think your problem lies somewhere else. In Gmail settings 'forwarding and POP/IMAP", IMAP should be enabled and don't forget the "Save Settings" button.

---

### Post by osabr22000 on 2008-07-01
> **soccerboy said:**
> gmail imap uses SSL but the SMTP uses TLS encryption.

I switched smtp to TSL and kept imap SSL but still the same error.

---

### Post by osabr22000 on 2008-07-01
> **soccerboy said:**
> you open up a terminal and type ```
ping smtp.gmail.com
```

post the output.

No problem about the noob.  I am pretty new at linux too and I learn as much as possible by just browsing through the forums.

Thanks for helping w/ this.  The results of pinging google's server are 64 bytes from yw-in-f109.google.com (74.125.47.109): icmp_seq=950 ttl=243 time=719 ms
64 bytes from yw-in-f109.google.com (74.125.47.109): icmp_seq=951 ttl=243 time=808 ms
64 bytes from yw-in-f109.google.com (74.125.47.109): icmp_seq=952 ttl=243 time=781 ms
64 bytes from yw-in-f109.google.com (74.125.47.109): icmp_seq=953 ttl=243 time=710 ms
64 bytes from yw-in-f109.google.com (74.125.47.109): icmp_seq=954 ttl=243 time=828 ms
64 bytes from yw-in-f109.google.com (74.125.47.109): icmp_seq=955 ttl=243 time=746 ms
64 bytes from yw-in-f109.google.com (74.125.47.109): icmp_seq=956 ttl=243 time=757 ms
64 bytes from yw-in-f109.google.com (74.125.47.109): icmp_seq=957 ttl=243 time=825 ms
64 bytes from yw-in-f109.google.com (74.125.47.109): icmp_seq=958 ttl=243 time=778 ms
64 bytes from yw-in-f109.google.com (74.125.47.109): icmp_seq=959 ttl=243 time=717 ms


And it just keeps going.

---

### Post by soccerboy on 2008-07-01
i would say, check your account settings to make sure imap and pop3 are enabled.  Besides that I am out of ideas.

---

### Post by osabr22000 on 2008-07-01
> **fragos said:**
> The configuration works for me on on multiple systems. I'd think your problem lies somewhere else. In Gmail settings 'forwarding and POP/IMAP", IMAP should be enabled and don't forget the "Save Settings" button.
In my Google settings it says:
	
1. Status: IMAP is enabled

Is there any way to ping the google server through evolution?

---

### Post by Perkins on 2010-09-10
I just had this same problem.  Was because the username I put into evolution didn't have the @gmail.com on the end of it somehow.  Hence the "no identity change permitted" when trying to set the from field as having the @gmail.com.

---

