---
title: "Enabling TLS/SSL in Pan Newsreader 0.136 Ubuntu 12.04"
date: 2013-04-10
forum: General Help
---

### Post by bob12564 on 2013-04-10
I'd like to enable encryption in the Pan Newsreader which now supports TLS/SSL.  The only tutorials I can find are for older versions of Pan that did not support TLS/SSL and those tutorials use stunnel to get around the issue.  I don't think stunnel is needed anymore for Pan.  Does anyone have a simple tutorial on how to enable encryption in Pan?  I see the check boxes under "edit newsservers" to turn it on but I'm sure it's more complicated than that.  There's also an "edit SSL certificates" menu that implies I need something more.

I'm in over my head with this so any help is appreciated.  Thank you!

---

### Post by weq92f on 2013-04-12
Reading your thead got me past an issue with Pan and stunnel config.  I was clicking the USE SSL option in Pan config AND having it hit localhost to go through the SSL tunnel created by stunnel.  Searching on this forum for help, I stumbled onto your post, which opened my eyes to see that Pan now has built in SSL support ( although I too have no idea how to use it ).  So, to make my Pan=>Stunnel=>news_servers_on_net connectivity work, all I had to do was uncheck the USE SSL in Pan!!!!!

Thank You.

Now, to OP question:  I'd continue to use stunnel.  It's simple to setup and works like a charm.  Set it up as you see in the tutorials you've read and then disable Pan's SSL config.

Hth,

-klb

---

### Post by bob12564 on 2013-04-12
I may have stumbled onto the answer:  I checked the "use TLS/SSL" box and saw that Pan changed the port number from 119 to 563.  I then took a chance and tried to connect to the newsserver and I was able to access it immedialtely.  Pan doesn't give any indication that you're actually in a secure connection, unlike a web browser, but I have to presume it's working.  So I think the stunnel method is now obsolete.  If you already have it working you can stay with that method, but for the less skilled person like me, I'll take the check box method any day!

You'd think the Pan developers would document this feature better, especially now that most newservers are offering SSL for no added cost.  I'm new to Pan, having come from Forte Agent under WINE, which doesn't offer SSL.  Pan looks like a nice tool but it has its quirks which I have to get used to.

---

### Post by weq92f on 2013-04-13
I like the fact that I know absolutely that my traffic is encrypted over the stunnel link.  Gives me a nice warm feeling :). 

-klb

---

