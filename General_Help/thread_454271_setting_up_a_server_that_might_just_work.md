---
title: "setting up a server that might just work"
date: 2007-05-25
forum: General Help
---

### Post by SteveHillier on 2007-05-25
Am I trying to do anything that others have not tried before?
I have a basic Window network.  Win  2003 server as domain controller.  Windows workstations.
We are doing a bit of website development mainly for ourselves but also for some others.  We are using dynamic content with PHP so I need a testbed to develop end check the work on.
Welcome to Linux and Ubuntu.
Dead easy!  Use an older machine, set up Ubuntu, set up LAMP servers and Bob's your uncle.  Host the test websites on the Ubuntu machine and access then via the web browser on my windows workstations.
I have now got it so that I can program the websites in PHP, host them as appropriate on my Ubuntu machine and from FIrefox access then from the address bar OK.  So I type in [http://hcintranet](http://hcintranet) and the website I have developed which sits on /var/www/hcintranet is displayed.  Thank you Mr Apache2, Mr PHP5 and so on.  I can also access this as 'intranet' and 'hillierconsult.co.uk' thanks to setting up /etc/hosts in the correct manner.
Now the rub.
Try to access from any Windows machine and I get page cannot be displayed message.  Ok so this might be a DNS problem.  Should be simple.  Set up  DNS server on Ubuntu.  Get me WIn 2003 DNS to point to Ubuntu DNS and we should fly.  What a heap of cr.. - sorry garbage.
Who on earth designed DNS.  It is supposed to translate web addresses into IP addresses.  So why does it not consist of a list of web addresses and a corresponding list of IP  addresses.  Look up the web address.  If its in the list pick up the IP address.  Poke the stuff to the IP address and let Apache (or what ever server is required) deal with it.  Not in the list then bounce to next DNS server in the line.  
But no.  We have stuff about name servers.  Zones.  Aliases.  A records.  CNAME records.
In my Windows DNS Server, I cannot simply add A records because it appends by 'hillierconsultants.local' to the name so I would get hillierconsult.co.uk.hillierconsultants.local which of course is going nowhere.
If I try to add a new DNS server I can choose whether the server ois on the local machine of some other machine.  So I tell it its on a machine called 'ubuntu' and it says 'Access is denied' so I cannot a connection to the ubuntu DNS server.  Both exist as an island, unseen by anyone else.
I was able to access the sites by typing [http://ubuntu/hcintranet](http://ubuntu/hcintranet) (which went directly to the folder) but now I cannot seem to do that.  I have SAMBA playing up by picking its moments when it allows me to access other machines on the network.
What should be simple has taken me most of this week to get nowhere.
Anybody out there got any clues?
Thanks in advance
Steve

---

### Post by gerscht on 2007-05-25
That doesn't look like a DNS on ubuntu problem, more of a misconfiguration of the windows DNS server.
Why is the domain set up with the name 'hillierconsultants.local ' and not with 'hillierconsult.co.uk' (if you own the name anyway and the website is hosted on site)?
You don't need to run a DNS on your ubuntu server if you just want to run it as webserver, Virtual hosts in your httpd.conf will do.

---

### Post by SteveHillier on 2007-05-25
Thanks for your comments.
I only set up a DNS on the Ubuntu machine because I was not getting any luck without it.  You might be right about it being a WIN DNS server issue but I don't know how to fix that.
When I set up the domain server (Win 2003) it was set up simply as a domain server.  It does not host and websites itself and the Win setup appends .local to the domain name you give it.  That's what gets set up in the DNS records.
The domain name I am using to test is not a registered domain name but as it is internal to my network I don't see that it should be a problem.  Perhaps I am wrong, but surely we should be able to set up a website locally and test it before we ftp it up onto a server somewhere?
Sorry to confuse anyone but it seems the problems I was reporting about SAMBA have been known for some time a an Edgy problem.  I might just revert to Dapper unless someone tells me I should go Feisty!
Thanks
Steve

---

