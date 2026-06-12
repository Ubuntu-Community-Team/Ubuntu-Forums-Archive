---
title: "Secondary site not coming up"
date: 2015-04-06
forum: General Help
---

### Post by Baub on 2015-04-06
I will start by saying I don't have all the answers now because I inherited this server, so if I left out a detail, please ask.  

The server is Ubuntu 14.04 and has apache with a public facing web site that has been working fine.  It also has a site, stage.main.com, that was configured and working at one time - this is what I need to get working.

If I run nslookup for stage.main.com I get the correct IP address.  But when I open stage.main.com in a browser I get a DNS error about [www.stage.main.com](www.stage.main.com).  I didn't put in the "www" at the beginning but the browser is redirecting me.

The hosts file has:

<IP> main.com
<IP> stage.main.com

Also, there is a CNAME record that points from stage.main.com to main.com.  
I have a virtual hosts file for main.com and stage.main.com where they are each set to a specific directory below /var/www

From what I can tell all of the configuration issue points to something on the box but I can't tell just what.

---

