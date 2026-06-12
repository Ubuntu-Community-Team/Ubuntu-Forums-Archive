---
title: "Ubuntu/Sentora/Mondoboa DNS Issues..."
date: 2018-10-28
forum: General Help
---

### Post by x17andrew71x on 2018-10-28
Hey there,

So this is the first time I've posted here. I need help, not sure if there is a better section to put this, feel free to move it if needed.

I have a HyperV server running here at home in the other room.
On it I have a few VM's, two of which are Ubuntu Server.
I have one Ubuntu Server running Sentora CPanel for web hosting.
On the second I just recently installed Mondoboa for an email system.

I am new to DNS management and MX entries, etc. So I believe I have it right, but could be making a mistake.
I have my domain, vestraweb.com, hosted on GoDaddy and it is pointing to Server A, for Sentora.
My site works, my login.vestraweb.com sub domain works so that I can get to the cpanel.
I created a new A record for mail.vestraweb.com and an MX record as well to try and be able to log into Server B's email system.

Here's the problem: When I enter the mail.vestraweb.com it points me to the cpanel login as if i entered login.vestraweb.com instead.
I followed a few different tutorials online about DNS/MX records to get this working, however none seem to change anything.

What a I doing wrong and what can I do to resolve it?
Any help that can be provided would be wonderful!

My DNS Config at GoDaddy:
[I]A             mail                   47.202.169.176          600seconds
[FONT=uxfont]Edit[/FONT]A             vestraweb.com    47.202.169.176          600
[FONT=uxfont]Edit[/FONT]CNAME     cpanel                @                              600[FONT=uxfont]Edit[/FONT]
CNAME     login                  @                              600
[FONT=uxfont]Edit[/FONT]CNAME     panel                 @                              600
[FONT=uxfont]Edit[/FONT]CNAME     www                  @                             1 Hour
[FONT=uxfont]Edit[/FONT]MX           mail             mail.vestraweb.com         600 seconds
[FONT=uxfont]Edit[/FONT]NS           @                ns25.domaincontrol.com   1 Hour
NS           @                ns26.domaincontrol.com   1 Hour
[/I]
Thanks Much,
-x17Andrew71x

---

