---
title: "cannot goto steve's digicams"
date: 2014-12-20
forum: General Help
---

### Post by jgw on 2014-12-20
I am using ubuntu 14.10 and firefox.  I cannot seem to be able to log into steves-digicams.  I have googled it and click on every link, to that site, says it cannot find the address.  I have no problems going to stuff like yahoo, google, etc.  I have also turned off my firewall.  Nothing seems to make any difference.  I could also find nothing that would lead me to believe that site is down.

I can ping the address.
whois gives me:
Whois Server Version 2.0

Domain names in the .com and .net domains can now be registered
with many different competing registrars. Go to [http://www.internic.net](http://www.internic.net)
for detailed information.

   Domain Name: STEVES-DIGICAMS.COM
   Registrar: GODADDY.COM, LLC
   Whois Server: whois.godaddy.com
   Referral URL: [http://registrar.godaddy.com](http://registrar.godaddy.com)
   Name Server: DNSCDC.INTERNETBRANDS.COM
   Name Server: DNSLA.INTERNETBRANDS.COM
   Status: clientDeleteProhibited
   Status: clientRenewProhibited
   Status: clientTransferProhibited
   Status: clientUpdateProhibited
   Updated Date: 19-dec-2014
   Creation Date: 13-jan-1998
   Expiration Date: 12-jan-2016

I have something set wrong, someplace, but have no idea where to look.

Thank you................

---

### Post by yancek on 2014-12-20
I just googled the site and was taken directly there and could navigate it.  Not sure what the problem is but you could try running firefox from the terminal to the site directly to see what output you get, if any:

> firefox steves-digicams.com

---

### Post by jgw on 2014-12-20
Thank you for the reply.  

Here are the results of your suggestion (I have absolutely no idea where to goto with this <g>)

greg@greg-desktop:~$  firefox steves-digicams.com 
(process:19076): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
greg@greg-desktop:~$ 

This resulted in:
Server not found
Firefox can't find the server at [www.steves-digicams.com](www.steves-digicams.com).

I should mention that I deleted all of the cookies, for this site just to see what would happen - didn't change a thing.

---

### Post by echotech2 on 2014-12-21
Just confirming yancek's post. All works OK here.

---

### Post by yancek on 2014-12-21
Are you saying that you cannot see/access the site at all?  Using firefox from the terminal, I get the same message which is a long known bug.  Google the warning output and you will see numerous links.  Even though I see that warning, I can still access the page with no problems so I'm not sure what is going on with your computer.  Have you tried a different browser?

---

### Post by jgw on 2014-12-21
thanks for the replies!

When I try to goto steve's digicams, with firefox, I get the same error, over and over again.  When I googled the error there was one thing and that was referring to a pastebin posting (not mine).  I also tried to access from the ubuntu browser - it had absolutely no problem.  I believe this is probably a firefox problem but I have posted the problem on their forum but have had no replies in 2 days.  Perhaps somebody will reply next week.

---

### Post by jgw on 2014-12-21
thanks for the replies!

When I try to goto steve's digicams, with firefox, I get the same error, over and over again.  When I googled the error there was one thing and that was referring to a pastebin posting (not mine).  I also tried to access from the ubuntu browser - it had absolutely no problem.  I have also accessed the site from another machine, sitting right next to this one, with firefox, with absolutely no problem.  I believe this is a firefox problem but I have posted the problem on their forum but have had no replies in 2 days.  Perhaps somebody will reply next week.

---

### Post by sammiev on 2014-12-21
I couldn't get in there yesterday, but no issues today with FF.

---

### Post by CantankRus on 2014-12-21
Test in safe-mode.
```
firefox -safe-mode steves-digicams.com
```

---

### Post by jgw on 2014-12-22
I have now completely removed firefox, and all its stuff, and have reinstalled the program.  I continue to have exactly the same results.  I can get to the bogus steves.digicams but not the real steves-digicams although I can go to that site on all my other machines.  I have now had a requestion in to firefox support since friday and nobody has answered.  I have also done all the stuff that they suggest, in their faq, to no avail.  This is VERY strange!

---

### Post by CantankRus on 2014-12-22
When you removed firefox did you remove the **~/.mozilla** folder as well?

---

### Post by jgw on 2014-12-22
I did, after the purging the package.  I then removed any references from both etc and usr.

---

### Post by jgw on 2014-12-24
I have fixed the problem.  I went to preferences/advanced/network/settings and set the proxy from using the system proxy settings to EITHER "no proxy" or "auto detect proxy settings for this network" (either one did the job - who would have guessed.

thanks for all the replies.................

---

