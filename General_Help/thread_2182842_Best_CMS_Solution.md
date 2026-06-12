---
title: "Best CMS Solution"
date: 2013-10-22
forum: General Help
---

### Post by amish_otaku on 2013-10-22
I am wondering if anyone could provide some input on a good CMS solution. I don't want anything that is just flat HTML based, and I'm not really a WIKI based fan either. Is there anything out there anyone would recommend?

---

### Post by TheFu on 2013-10-22
There are 50+ different CMSes out there. They each of pros/cons, so what sort of content are you trying to manage?  The options are significantly reduced based on your needs.
* alfresco
* drupal
* wordpress
* apache+ plugins - checkout the apache projects.
* nginx + plugins
* remote desktops
* plus all the wordpress clones.
or you could cobble together something using template toolkit or any of the many static-file filters ... 

Whenever I need to look for stuff like this, I visit freshmeat.net and alternativeTo to get a list.

---

### Post by Habitual on 2013-10-22
[http://www.geeklog.net/](http://www.geeklog.net/)

---

### Post by amish_otaku on 2013-10-23
Sorry for the late reply. I was not able to check back in on this till just now. Basically here's what I'm looking for. 

I would like to be able to setup pages for each client that I have and keep pertinent information for them on that page. This information would include usernames, passwords, IP addresses and such. The ability to also include pictures or attachments on the pages would be a plus, but not required. 

I would like to also be able to integrate this machine with AD, although not really required. Would be nice.

I don't want to have to hack together alot of HTML files, as I'm not really wanting to have to spend all of my time piecing that together for each particular company. As exampled we have a WIKI style currently in place and it is horrid to try and get working as it doesn't really allow use of templating. At least not in the strictest sense.

I didn't really know about those sites. I will definitely start to look through them though and see if I can find a project that works for my needs. In the meantime if you guys know of one that would work somewhat for me, I would be grateful. I've always had a hard time trying to find other projects in the past and had to rely heavily on the wise and all knowing sage "GOOGLE"

---

### Post by tgalati4 on 2013-10-23
What you want is really more of a CRM then CMS.  For that I like [http://sugarcrm.org](http://sugarcrm.org).  They all have a rather steep learning curve.  Otherwise, use your contact list in Evolution, gmail, Outlook, etc.  

From your Use Case, it is not clear why linking to Active Directory would be helpful.  How many total clients would this list grow to?

---

### Post by TheFu on 2013-10-23
> **tgalati4 said:**
> What you want is really more of a CRM then CMS.  For that I like [http://sugarcrm.org](http://sugarcrm.org).  They all have a rather steep learning curve.  Otherwise, use your contact list in Evolution, gmail, Outlook, etc.  

From your Use Case, it is not clear why linking to Active Directory would be helpful.  How many total clients would this list grow to?

I've deployed vTiger for CRM.  Without marketing people, it isn't really all that useful long-term. Our install died from lack-of-use. It was slick, but ... meh.

Redmine might be more what you really want - it is a project management tool with everything based on which project you are in - wiki, file storage, issue tracking ... plus setting it up isn't too hard ... provided you follow the instructions.  None of these will be an apt-get - done - install, however.  It is possible to have both external authentication and internal mixed.  I have both here, but we use OpenLDAP, not AD. It isn't SSO, just single-password.  Your internal people can be in many different projects - just 2 clicks away.  Outside clients can be in 1 or 2 or 50 projects.  Different roles are assigned per-project too.  There isn't too much "cheese" in redmine, it is functional and simple to understand from the end-user side.  Since it is RoR, there is bloat.  Anyway, Redmine is a central tool in my business for staying on top of actions, projects and lets clients provide direct feedback.

---

### Post by amish_otaku on 2013-10-24
Basically I am wanting the AD authentication so that if I make it web accessible I can enable authentication for me any my coworkers. Reduce the number of passwords that we have to remember. 

Our list of clients varies, but is slowly and consistently growing. 

This would also enable us to login out in the field and get pertinent information instead of having to get a coworker to email it out to us.

---

### Post by TheFu on 2013-10-24
Have you considered what using AD passwords means over the internet and on non-trusted networks?
VPN?

---

### Post by tgalati4 on 2013-10-24
That is precisely why I asked the question.  Since this Use Case involves pulling client data when in the field, you might need a VPN or more robust authentication method.

CRM's are good for internal-use-only keeping track of customers and marketing efforts and estimating business pipelines.

CMS's are good for public-facing web pages with dynamic content (like blogs and new products).

What you want is a custom application to provide client data in the field.  That is an explicit requirement.  An implicit requirement is that the data remains secure and your field people can access the data.  And, you don't want to do any programming.  

Unfortunately, the intersection of those requirements is the Null Set.

---

### Post by TheFu on 2013-10-25
> **tgalati4 said:**
> What you want is a custom application to provide client data in the field.  That is an explicit requirement.  An implicit requirement is that the data remains secure and your field people can access the data.  And, you don't want to do any programming.  

Unfortunately, the intersection of those requirements is the Null Set.

The name of that app is "Redmine" - there must be others, but I don't know them.  Google "redmine vs" to get other options?

---

