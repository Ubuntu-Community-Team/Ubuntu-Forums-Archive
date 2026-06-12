---
title: "Get rid of Orbiscom's Controlled Payment Numbers client application for Windows"
date: 2007-03-22
forum: General Help
---

### Post by Jonathan Métillon on 2007-03-22
Hi,

  Today I wanted to install the [Controlled Payment Numbers]("http://www.orbiscom.com/product.php?product=cpn")    (CPN)  client application my bank provides. But I can't, as Orbiscom does not support Linux. Maybe because we use FOSSs they think we don't buy anything on the Internet?

 Orbiscom is the company that license the CPN technology. It's used by a large number of banks worldwide, like Bank of America and Citibank.

 Since it's first release in France I use the [E-Carte Bleue]("http://www.e-cartebleue.com/client/home.asp")   system, the CPN branding supported by the French [CB Bank card association]("http://en.wikipedia.org/wiki/Groupement_des_Cartes_Bancaires_CB"). Thanks to it I will never put my real credit card data on the Internet again. 0% fraud GUARANTEED!

  Personally, I have only two applications that prevent me from totally get rid of Windows:[LIST=1]
[*][Neo Mule]("http://neomule.sourceforge.net/"), because it supports Protocol Obfuscation, which is mandated to use P2P networks if you are a Free.fr ISP subscriber (they use traffic shaping with [IP Service Control]("http://www.cisco.com/cdc_content_elements/flash/csc/cisco_FINAL_no-loop.html")    from Cisco). But I can run on Wine. Until aMule supports Protocol Obfuscation...
[*]The CPN client.[/LIST]By searching the different French banks distributing the client, I found this page from the LCL bank website: [https://service.e-cartebleue.com/cleo/](https://service.e-cartebleue.com/cleo/)

Then I realized that the Windows client is just an embedded Flash applet served through a HTTPS connection! If LCL permits the use of the applet directly from the web, why other banks don't? Why they force their customers to use a Windows client?

Anyway, I want it too. But I'm not a LCL customer, I'm a [La Banque Postale]("https://www.particuliers.labanquepostale.fr/index/e-carte_bleue/ecarte_chargement.html")    customer. Hey, the service is hosted by the E-Carte Bleue website. Let's Google a bit:

[http://www.google.com/search?q=site:service.e-cartebleue.com&filter=0](http://www.google.com/search?q=site:service.e-cartebleue.com&filter=0)

Yipee!

[https://service.e-cartebleue.com/labanquepostale/visa/thinclient_mem.html](https://service.e-cartebleue.com/labanquepostale/visa/thinclient_mem.html)

Looks familiar. Yep, this is exactly the Flash applet that's embedded in my Windows client.


[SIZE=4]**BYE BYE WINDOWS! ):P**[/SIZE]

---

### Post by bapoumba on 2007-03-22
Hello :)
I'm not sure I really got all your points here, but "Caisse d'Epargne" has been doing this for some time now (two years, I think). The "e-carte bleue" is in a flash (/o\) web interface, and never had issues with it, even with the random keyboard application to enter the password to log into my account.

---

### Post by Jonathan Métillon on 2007-03-22
Hi [[IMG]http://ubuntuforums.org/customavatars/avatar171805_1.gif[/IMG]]("http://ubuntuforums.org/member.php?u=171805")                                                                                     [[COLOR=#d40000]**bapoumba**[/COLOR]]("http://ubuntuforums.org/member.php?u=171805")

Well you said it: Caisse d'Epargne may have been doing this for some time, and I was not aware because I only used E-Carte Bleue service from Société Générale and La Banque Postale.

Those two banks never advertised any online client. Both force you to install the Windows client, and show no alternative. And I did not know until today that the client is just embedding a Flash applet that is available directly from the web.

Finally, there was no question to answer nor issue to solve here, I'm just sharing what I discovered. It may be old news for some, and it may be gold for others ;-)

---

### Post by bapoumba on 2007-03-22
Hello Jonathan Métillon, just fine then :)

---

