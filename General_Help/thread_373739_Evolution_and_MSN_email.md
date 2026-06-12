---
title: "Evolution and MSN email"
date: 2007-03-01
forum: General Help
---

### Post by Hugh Taylor on 2007-03-01
Can anyone help me configure Evolution to send and receive msn account emails?
I'm new to Ubuntu and Linux but did used to run a Unix software work system a few moons ago.

Thanks

Hugh Taylor

---

### Post by CocoAUS on 2007-03-01
I don't believe MSN offers POP3 access anymore, which means you can't use an external client to retrieve your mail.  Thunderbird has an extension that will let you get your MSN webmail, and there's a service that will try to change your HTML mail into POP ( [http://www.freepops.org/en/](http://www.freepops.org/en/) ).

---

### Post by fireye on 2007-10-30
Configuring Evolution Email to work with msn.com

   After three days here is the recipe that finally worked for me.  It is a compilation of bits and pieces from several LINUX forums and tech sites including msn.  I added some extra steps for those who where like me in the beginning stages of figuring out this LINUX/Evolution mail stuff.   

Go to edit/preferances/ and bring up the Account editor.
Highlight Mail Accounts on the left (usually the default highlight).
Highlight your account in the listings and click on "edit".

Identity Tab:
Full Name: [email]youremail@msn.com[/email]
Email Address: [email]youremail@msn.com[/email]

Recieving Mail Tab:

Server Type: POP (dropdown menu)
Server: POP3.live.com
Username: [email]youremail@msn.com[/email]
Security: SSL encryption
Authentication Type: password
the box to remember passord is checked.

Sending Email Tab:

Server Type: SMTP (dropdown menu)
Server Requires Authentication (box is checked)
Security: Use Secure Connection (TLS)
Authentication Type: Login
Username: [email]youremail@msn.com[/email]
box to remember password is checked.

Hope this works as good for you as it did for me!      thanx  Fireye
:guitar::guitar::guitar:

---

### Post by luke16 on 2007-12-08
Thanks fireye! Those settings worked perfectly for me.

---

### Post by jlpedlar on 2007-12-08
Thank you thank you thank you for this great info! It worked like a charm.

---

### Post by ilikepenguins on 2008-04-03
I followed your instructions but I couldn't get mine to work

I get this error message "Error while Fetching Mail.

Unable to connect to POP server pop3.live.com.
Error sending password: Resource temporarily unavailable"


 also what do you put in the blank for smtp server?

---

### Post by johnplov on 2008-04-19
Thanks to Fireye, I tried your soution and it worked for me.  My only problem was that I had my emails left on the server so I could access them from two computers, and when I set up  Evolution I mistakenly let the be sent to that computer.  Is there any way to send them back to the server?
Thanks again for the help

---

### Post by snhefowler on 2008-05-08
little letters for pop in pop3.live.com works for me 
I also had to make my msn.com & windows live.com 
passwords match for evolution to work for msn.com

---

### Post by jwesterlund on 2008-06-02
Hello fireye,

I set up Evolution as shown below and it works just fine for fetching email, but I cannot send.  Any hints that you think might work?  My email address is through msn.  

Thanks!

---

### Post by jwesterlund on 2008-06-06
I got it to work!  WOOHOO!!

---

### Post by way10c on 2008-06-10
Yes, but how?!?

--Allen

---

### Post by way10c on 2008-06-10
Found it!

In the Server box put: smtp.live.com

--Allen

---

### Post by sofaspud276 on 2008-07-13
This did not work for me. I get an error "Unable to connect to server Password error


> **fireye said:**
> Configuring Evolution Email to work with msn.com

   After three days here is the recipe that finally worked for me.  It is a compilation of bits and pieces from several LINUX forums and tech sites including msn.  I added some extra steps for those who where like me in the beginning stages of figuring out this LINUX/Evolution mail stuff.   

Go to edit/preferances/ and bring up the Account editor.
Highlight Mail Accounts on the left (usually the default highlight).
Highlight your account in the listings and click on "edit".

Identity Tab:
Full Name: [email]youremail@msn.com[/email]
Email Address: [email]youremail@msn.com[/email]

Recieving Mail Tab:

Server Type: POP (dropdown menu)
Server: POP3.live.com
Username: [email]youremail@msn.com[/email]
Security: SSL encryption
Authentication Type: password
the box to remember passord is checked.

Sending Email Tab:

Server Type: SMTP (dropdown menu)
Server Requires Authentication (box is checked)
Security: Use Secure Connection (TLS)
Authentication Type: Login
Username: [email]youremail@msn.com[/email]
box to remember password is checked.

Hope this works as good for you as it did for me!      thanx  Fireye
:guitar::guitar::guitar:

---

