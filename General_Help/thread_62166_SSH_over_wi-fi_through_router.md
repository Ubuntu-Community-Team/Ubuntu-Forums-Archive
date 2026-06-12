---
title: "SSH over wi-fi through router"
date: 2005-09-03
forum: General Help
---

### Post by matthew on 2005-09-03
Preface: I have never used ssh in my life. Even though I have read everyone of the howtos, the wiki and what I could find on google I still only understand the basic idea and have no clue how to set up an ssh connection in the first place. Total noob on this.

I have the ethernet cable coming out of the cable modem into my Linksys WRT-54g router. 
My wife's computer (also running Ubuntu) is connected to this router via an ethernet cable.
I connect my laptop to the router via wireless with wpa enabled.

I would like to be able to do maintenance on her computer without having to disturb her when she is using it or sleeping (it's in the bedroom) by connecting to it from my laptop using ssh.

I have installed the ssh-client and server on both computers via apt-get.

I can ssh to localhost and log in to my own computer, for what that is worth.

I have absolutely no clue what to do next to find her computer though and I'm afraid that I just don't know where to look next for info I need like:
-how do I find the ip address for her computer?
-how do I open the necessary port(s) so her computer doesn't ignore the ssh connection request?
-is it possible to do what I am trying to do via wi-fi through the router?

EDIT: and finally, is there a better way to do what I am tryng to do than by using ssh?

Any links will be followed and read and any advice will be appreciated!

---

### Post by matthew on 2005-09-04
[QUOTE=matthew]-how do I find the ip address for her computer?
-how do I open the necessary port(s) so her computer doesn't ignore the ssh connection request?
-is it possible to do what I am trying to do via wi-fi through the router?[/QUOTE]
I found the answers to my questions, mostly through trial and error and also through a bit of web searching and I thought I would share them in case anyone else has the same questions.

1. The ip addresses for each computer attached to the router are available on the router. I connected to the router's setup using the method provided in it's documentation, in this case by using my web browser and putting the ip address given in the documentation in the address bar. Then I found the menu where the router lists computers connected to it, discovered which address had been assigned to my computer and which had been assigned to my wife's. Logging in to either computer from itself was easy, but I still had the ssh ports closed on them both so I couldn't log in to either externally..

2. I had used lokkit to make/configure the iptables firewall rules on both computers. It is available in the repos and is an easy, one-time run that sets the rules for you. There is a gui version as well called gnome-lokkit which I have never used but which I imagine does the same thing. I had a brainstorm and ran it again. There is a button labeled "options" which I chose and it gave me the option to open several ports, one of which was the ssh port. I selected that, closed lokkit and voila! port 20 was open and I could log in to either computer from the other one via the router.

3. It makes no difference whether I am connected to the router via ethernet cable or wireless. I didn't have to set anything up or change anything other than numbers 1 & 2 above.

Okay, hope that helps someone else. I'm off to set up my private key logins and figure out how to run xserver sessions via ssh.

---

