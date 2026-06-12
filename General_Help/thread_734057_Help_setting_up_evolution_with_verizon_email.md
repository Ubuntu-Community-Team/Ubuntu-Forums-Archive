---
title: "Help setting up evolution with verizon email"
date: 2008-03-24
forum: General Help
---

### Post by Terminating.proprietary on 2008-03-24
I have done some searching and have only found things I already know. I want to set up evolution to access my verizon email. I know the incoming POP is incoming.verizon.net and outgoing SMTP is outgoing.verizon.net. All of this is very simple. I have the check ticked that server requires authentication. I have done this setup with outlook and that is why I am not sure why it isn't working. I tried entering for username [email]myusername@verizon.net[/email] as well as just username. I know my password is correct. when I hit the sen/recieve button Evolution connects to the outgoing, but says it is waiting to connect to the incoming. Within a few seconds it returns the message

Unable to connect to POP server incoming.verizon.net.
Error sending password: -ERR [AUTH] Authentication failed

Please enter the POP password for Bgreise24 on host incoming.verizon.net

I have to retype the password to no avail. Besides if the password was incorrect it would not connect to the outgoing. Please, help me, I am assuming I am not the only one who has had this issue.

---

### Post by Terminating.proprietary on 2008-03-24
Edit: When I try to send an outgoing email I can not connect to SMTP either

---

### Post by wca on 2008-07-21
I Have Verizon FIOS with MSN Premium
This is the way I finally got verizon.net to work for me.

On account Information
Name= your name for your evolution email account (mine was WCA's Email)

Full Name = your first and last name

email address = your [email]name@verizon.net[/email]
-----------------------------------------------------------------------
Receiving Mail

server type= POP
-----------------------------------------------------------------------
Configuration

user name= your [email]name@verizon.net[/email]
-----------------------------------------------------------------------

security

use secure connection= NO Encryption
(this is the only way I could get it to work for me)

authentication type= password
check remember password
------------------------------------------------------------------------

Receiving options

your choice
I checked leave messages on server
------------------------------------------------------------------------

Sending Email

server type = smtp

server configuration = outgoing.verizon.net

check server requires authentication
-------------------------------------------------------------------------

security

use secure connection= NO encryption
(again, this is the only way I could get it to work for me )

authentication type = login

user name = [email]yourname@verizon.net[/email]

check remember password
-------------------------------------------------------------------------

This is how I had to set up the verizon.net email to work for me.
I still cannot get the web based email in MSN premium to work---don't think it will work in evolution yet ------------anybody????

Hope this helps 
william Adcock

---

