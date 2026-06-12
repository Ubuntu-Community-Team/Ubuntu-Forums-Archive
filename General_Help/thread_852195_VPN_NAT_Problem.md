---
title: "VPN NAT Problem"
date: 2008-07-07
forum: General Help
---

### Post by headlessb on 2008-07-07
Hi, I'm having a problem with a VPN connection that I am establishing over a NAT Network. I'm using the pptp stuff configuring it with the webmin module. But for some odd reason I try and connect from another NAT network and it doesn't work. Does anybody have any idea as to what the problem could be? Here's a schematic of my network:

---

### Post by blackhatbrigade on 2008-07-07
What are you using to setup the VPN?  openVPN?

Are you using certs?

What's the VPN network IP range?

Need a little more info (nice picture though)

---

### Post by headlessb on 2008-07-07
I'm using pptp daemon. Not openVPN, although I've been reading and have found that openVPN can use something called NAT Traversal. With that, can I make a normal VPN connection with Windows and MAC machines? The IP Addresses that I have it allocate are 192.168.53.130-150. I wish I were at home to give you the error windows is getting when making the connection. I would rather not have to forward ports on the NAT router at my house. It would defeat the purpose of using it in a roaming situation. Anyway, what do you think? Need anything else?

Heh, thanks for the comment on the picture, I made it, and then said "It looks like a basketball court!" heh.

---

### Post by blackhatbrigade on 2008-07-07
heh, didn't notice that before but you're right. ;)

Well, I'm no professional at VPN's.  I've setup 2 of them and I'm still astounded at how many different ways you can set one up.  I'm also not 100% sure about the pptp daemon (although I think that's what my router has built in).  I just got done (within the last 2 days) setting up a openVPN server on my ubuntu machine that someone VPN'd into using the windows client of openVPN.  However it takes some seriously ... serious? :D certs to make it happen.  I'm not sure how pptp does it, but I'm interested enough in figuring it out that I'd be willing to work through it with you after you get home.  If you're interested send me a pm and we can do it over Yahoo IM or something.

Of course, we'll post the solution here if you want to try it that way. :)  Or I can give you the info needed to make it work in openVPN.  Your choice, either way works for me.

---

