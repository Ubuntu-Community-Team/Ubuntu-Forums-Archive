---
title: "To everyone with slow internet"
date: 2007-03-29
forum: General Help
---

### Post by stchman on 2007-03-29
Hello all, there are a lot on here that have complained (myself included) about their internet being REALLY slow.  Well, I have the answer.

Go to [http://www.opendns.com](http://www.opendns.com)

Use their DNS nameserver and your internet will be blazing fast.  I used their numbers:

nameserver 208.67.222.222
nameserver 208.67.220.220

and all is right in the world.  OpenDNS ROCKS!!!!!!

Just put these nameservers in your router and reboot.  When you com back online you are off to the races.  Website will pop up with speed you did not think you had.

If you don't use a router (which you should), then go to System---Administration---Network and then select the DNS tab.  Write down your old DNS numbers and then use the ones I have listed above.  Reboot and you are going to be amazed.  TO test if you are hooked up to openDNS go to the following link:

Visit [http://welcome.opendns.com/](http://welcome.opendns.com/) to test your new settings.

They will let you know if you are hooked up.

I hope this helps.

---

### Post by BLTicklemonster on 2007-03-29
Cool!

---

### Post by Motoxrdude on 2007-03-29
so what exactly does this do?

---

### Post by 95aspire on 2007-03-29
> **Motoxrdude said:**
> so what exactly does this do?

yes what does it do? ive heard of it before but never what it does

---

### Post by stchman on 2007-03-29
> **95aspire said:**
> yes what does it do? ive heard of it before but never what it does

They are an alternate DNS (doamin name servers) that are far better than the ones issued to yuo by your ISP.  The DNSs issued to me by Charter are terrible compared to the one openDNS lets you use.  I am by no means a DNS expert, you will have to go to their website and read more.  Just trust me in the fact that they work better.

---

### Post by smartbei on 2007-03-29
Well, the internet certainly seems faster, but I have one complaint - previously, leaving out the TLD of a website would still take me to the website. Now, It takes me to an OpenDNS search page the apparently uses results from a search engine (I couldn't identify which, and the results didn't fit the ones on Google, Yahoo etc.).

---

### Post by david_ulevitch on 2007-03-29
> **smartbei said:**
> Well, the internet certainly seems faster, but I have one complaint - previously, leaving out the TLD of a website would still take me to the website. Now, It takes me to an OpenDNS search page the apparently uses results from a search engine (I couldn't identify which, and the results didn't fit the ones on Google, Yahoo etc.).

Hi!

The results are from Yahoo.  In a few weeks we'll put a nice "Powered by Yahoo! Search" button on the page.  We're also about to fix the TLD issue not showing you that as the immediate result.

For example, check out the difference between:

[http://guide.opendns.com/?url=dell.xom](http://guide.opendns.com/?url=dell.xom)
versus
[http://guide.opendns.com/?url=dell](http://guide.opendns.com/?url=dell)

On the first one we give you the corrected link to dell.com -- on the second we think you're doing a search and so we give you results...  

What would you like to see happen?

-david ulevitch (from OpenDNS)

---

### Post by Fireblend on 2007-03-29
Hmm, this does look interesting. My Internet is already fast and good, but the other features look interesting enough to try out. Thanks!

---

### Post by stchman on 2007-03-29
> **Fireblend said:**
> Hmm, this does look interesting. My Internet is already fast and good, but the other features look interesting enough to try out. Thanks!

Give OpenDNS a try, it worked wonders for my internet connection.

---

### Post by 95aspire on 2007-03-29
ok ive got hte dns numbers in my router and when i put them in my net connection thing i cant access the net, but when i put my router as the dns on my comp i can access the net, but i get the oops page when i try to make sure it worked

---

### Post by Rui Pais on 2007-03-29
> **david_ulevitch said:**
> Hi!

The results are from Yahoo.  In a few weeks we'll put a nice "Powered by Yahoo! Search" button on the page.  We're also about to fix the TLD issue not showing you that as the immediate result.

For example, check out the difference between:

[http://guide.opendns.com/?url=dell.xom](http://guide.opendns.com/?url=dell.xom)
versus
[http://guide.opendns.com/?url=dell](http://guide.opendns.com/?url=dell)

On the first one we give you the corrected link to dell.com -- on the second we think you're doing a search and so we give you results...  

What would you like to see happen?

-david ulevitch (from OpenDNS)
the issue that **smartbei** refers - and that i second as very annoying - is that when one uses the opendns and type on firefox something not an url, as an example, plain "ubuntu", it goes to opendns search page, while with other dns it goes directly to ubuntu site.

In my case i am very used to that behavior, and with OpenDNS, I'm forced to type and then click or otherwise be capable or memorize all urls correctly :(

About your question, in my case i would like to go directly to Dell site, without going to any search page (unless an obvious page was not found).

Thank you.

---

### Post by stchman on 2007-03-29
> **95aspire said:**
> ok ive got hte dns numbers in my router and when i put them in my net connection thing i cant access the net, but when i put my router as the dns on my comp i can access the net, but i get the oops page when i try to make sure it worked

What kind of router do you have?  You will not have to edit anything in Ubuntu as it will get the DNS numbers from your router when using DHCP.

On my Linksys all I did was put the DNS number is the static DNS section and hit save settings.  My router will use the ISP assigned DNS if you have 0.0.0.0 in it.

On Unbuntu if you run a static IP on a machine (for say bittorrent) then you will have to add the DNS numbers on the DNS tab of Administrator-->Networking.  DHCP requires nothing.

---

### Post by 95aspire on 2007-03-29
well this machine is xp

and yes it is static ip addressed.

but the router is a linksys wrt54g with the dd-wrt firmware on it.

---

### Post by stchman on 2007-03-29
> **95aspire said:**
> well this machine is xp

and yes it is static ip addressed.

but the router is a linksys wrt54g with the dd-wrt firmware on it.

Easy, in WinXP go to the TCP/IP properties and specify a DNS.  Type in the numbers and away you go.  Also enter the numbers in your router as other PCs on your network that use DHCP can use OpenDNS.

---

### Post by 95aspire on 2007-03-29
i added the opendns to my xp tcpip dns settings and couldnt access the net

---

### Post by stchman on 2007-03-30
> **95aspire said:**
> i added the opendns to my xp tcpip dns settings and couldnt access the net

You have the same router as I do (WRT54G).

Do this, type in your web browser 192.168.1.1 and enter your password.

First page Basic Setup go down to Static DNS1 and Static DNS2, enter the values listed.  Save settings.

Ok now for XP.  Go to the TCP/IP settings and specify the DNS.  That is all you need to do.

---

### Post by ramjet_1953 on 2007-03-30
For Ubuntu, simply do this:

[COLOR="Red"]sudo network-admin[/COLOR]

The network admin GUI will now open under admin rights. 
Click on the DNS tab and then you just add the two DNS server addresses ( 208.67.222.222 and 208.67.220.220 ) to the [COLOR="Red"]TOP[/COLOR] of the list and then re-enter your old address, as a back-up at the BOTTOM.

Works like a charm!

Regards,
Roger 8)

---

### Post by BLTicklemonster on 2007-04-14
So what is the verdict on this? Has anyone/everyone tried this yet?

---

### Post by Sencer on 2007-04-14
> **BLTicklemonster said:**
> So what is the verdict on this? Has anyone/everyone tried this yet?

It depends entirely on the quality f the DNS-servers that your ISP runs. My ISP (Arcor, Germany) has 10 DNS servers (well, at least ten IPs, who knows how many servers are behind them) that are very fast. Though I've heard that in some countries with some very cheap ISPs they don't build up a strong DNS-offerring, and in those cases it might hep a little.


You can find out if you install "dig". 

dig domainname @IPofDNSserver

it will show the query time. Once a DNS-Server has resolved a name, it will cache the response, so the next time it will be a lot faster. For me uncached queries take a little over 100-130ms, and cached queries are around 25-30 ms, my ISPs DNS-Servers being a little bit faster.

You read more about the supposed benefits of opendns in their faq: [http://www.opendns.com/faq/](http://www.opendns.com/faq/)

Personally, I wouldn't use them, because they wildcard domain-names (i.e., for non-existant domains they lie in their answers to show you their ad-pages - to be fair though, it's probably the only way to finance such a service other than direct subscription/payment), and I wouldn't want to share my surfing haibts with yet another party. They touch on all these subjects in their FAQ, though, so if you find their answers satisfying and their benefits convincing, you may want to try them out.

---

