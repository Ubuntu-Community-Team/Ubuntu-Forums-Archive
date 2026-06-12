---
title: "Help with starting web based service"
date: 2013-01-25
forum: General Help
---

### Post by AbnormalSpring on 2013-01-25
I know this is my first post and may not be taken serious. What I want to do is start a free email service. 

I have been googling for weeks and I have found nothing that tells me how to start one using my own server and own domain name.

I was wondering if anybody here would know how to start one using ubuntu server?

I have saved up 6k$ for startup costs such as server, advertising, and domain name. I just have not purchased anything as I dont know how to start or how to do this.

Any help would be greatly appreciated.

---

### Post by SeijiSensei on 2013-01-25
There are web-based email clients like SquirrelMail and RoundCube.  However if you have no experience with this at all, I'd suggest you get some help setting things up.  You need to ensure that your site is not a haven for spammers, and you need to filter all your customers' email for spam and viruses.  Are you up to setting all that up yourself?  More importantly, why would I choose your service over GMail?

---

### Post by raja.genupula on 2013-01-25
hi read this once.
[http://www.tuxradar.com/content/build-your-own-email-server-postfix](http://www.tuxradar.com/content/build-your-own-email-server-postfix)

---

### Post by AbnormalSpring on 2013-01-25
> **SeijiSensei said:**
> There are web-based email clients like SquirrelMail and RoundCube.  However if you have no experience with this at all, I'd suggest you get some help setting things up.  You need to ensure that your site is not a haven for spammers, and you need to filter all your customers' email for spam and viruses.  Are you up to setting all that up yourself?  More importantly, why would I choose your service over GMail?

Why would you choose my email service. That is a good question but I would require mobile authentication to sign up to prove it is a actual person and so that it would be a pain to set up multiple email accounts.

I would also like to scan all incoming mail and outgoing mail for viruses; limit outgoing mail to 10 at a time so that if a spammer signed up it would be an annoyance to send 100k+ emails 10 at a time.

I have other ideas and I have no programming or website making exp so once I got everything set up I would be able to pay a company or person to get everything running and to maintain it. I would prefer a person over a company since it is easier to work with a individual then it is a company.

---

### Post by AbnormalSpring on 2013-01-25
> **raja.genupula said:**
> hi read this once.
[http://www.tuxradar.com/content/build-your-own-email-server-postfix](http://www.tuxradar.com/content/build-your-own-email-server-postfix)

Thank you for the article it was helpful.

---

### Post by raja.genupula on 2013-01-25
> **AbnormalSpring said:**
> Why would you choose my email service. That is a good question but I would require mobile authentication to sign up to prove it is a actual person and so that it would be a pain to set up multiple email accounts.

I would also like to scan all incoming mail and outgoing mail for viruses; limit outgoing mail to 10 at a time so that if a spammer signed up it would be an annoyance to send 100k+ emails 10 at a time.

I have other ideas and I have no programming or website making exp so once I got everything set up I would be able to pay a company or person to get everything running and to maintain it. I would prefer a person over a company since it is easier to work with a individual then it is a company.


but why dont you be "that" person , you can learn knowledge.

forums are here to help you always,:)

---

### Post by SeijiSensei on 2013-01-25
> **raja.genupula said:**
> but why dont you be "that" person , you can learn knowledge.

forums are here to help you always,:)

What he wants to do would a take a couple months of serious work.  There are so many pieces involved in this, that it would be unfair to people here to keep asking questions over and over again seeing as he is starting from scratch.  It's not just a matter of installing some combination of Postfix, Dovecot, a spam/virus filter, and a front end like SquirrelMail.  I could do that in a day or two.  But that's just the beginning.  You need to write code to handle signing up and authenticating new users for instance.  You would need to get a website designer involved to make the public site visually appealing and functionally simple to navigate.  

Then there is the whole marketing issue.  One part of the "why would I choose you over GMail" question is what do you bring to the table that isn't available elsewhere and already widely known.  People generally way underestimate the costs of marketing a new business when they first start out.  He would be positioning this service against the likes of Google, Yahoo, and Microsoft.  The technical issues involved are actually a lot less important than the marketing and promotional issues.

My cautions are based on my own experience of trying to build an Internet consulting business and losing serious money in the process.  The problems weren't that I and my staff lacked technical abilities, or even management abilities.  It all came down to marketing and building a business.  Ultimately it becomes a question of "why you and not someone else?"  When that someone else is Google, the odds are stacked even higher.

---

### Post by mrjava on 2013-01-25
As the other posters have stated this would be a process of months.

Instead of trying to simply be a generalized email provider (I am sorry to say, against the likes of Google and Yahoo you have a miniscule chance of becoming profitable), why don't you find a specific target, HIPAA governed businesses, businesses that need a combined, customizable email/chat/file sharing service, and tailor your email service specifically for them? 

A specialized product can be quite profitable, whereas the generalized email providers are very well seated and hard to compete against.

---

### Post by AbnormalSpring on 2013-01-25
> **SeijiSensei said:**
> What he wants to do would a take a couple months of serious work.  There are so many pieces involved in this, that it would be unfair to people here to keep asking questions over and over again seeing as he is starting from scratch.  It's not just a matter of installing some combination of Postfix, Dovecot, a spam/virus filter, and a front end like SquirrelMail.  I could do that in a day or two.  But that's just the beginning.  You need to write code to handle signing up and authenticating new users for instance.  You would need to get a website designer involved to make the public site visually appealing and functionally simple to navigate.  

Then there is the whole marketing issue.  One part of the "why would I choose you over GMail" question is what do you bring to the table that isn't available elsewhere and already widely known.  People generally way underestimate the costs of marketing a new business when they first start out.  He would be positioning this service against the likes of Google, Yahoo, and Microsoft.  The technical issues involved are actually a lot less important than the marketing and promotional issues.

My cautions are based on my own experience of trying to build an Internet consulting business and losing serious money in the process.  The problems weren't that I and my staff lacked technical abilities, or even management abilities.  It all came down to marketing and building a business.  Ultimately it becomes a question of "why you and not someone else?"  When that someone else is Google, the odds are stacked even higher.

> **mrjava said:**
> As the other posters have stated this would be a process of months.

Instead of trying to simply be a generalized email provider (I am sorry to say, against the likes of Google and Yahoo you have a miniscule chance of becoming profitable), why don't you find a specific target, HIPAA governed businesses, businesses that need a combined, customizable email/chat/file sharing service, and tailor your email service specifically for them? 

A specialized product can be quite profitable, whereas the generalized email providers are very well seated and hard to compete against.

Ok talk about discouraging from the way it sounds is that I need to save up a lil bit more then 6k dollars before I attempt this.

Guess I should find some other business venture to try. I dont mind losing a few thousand dollars to say I tried something rather then being stuck in my job as a extruder operator for another 6+ years.

Thanks for all the info I will get back to the drawing board. To find something that I can start small.

---

### Post by tgalati4 on 2013-01-26
What is it that you extrude?  Perhaps you can make some Ubuntu buttons?  You might make more money selling Ubuntu trinkets that you have designed and personally made than trying to compete with Google.

For less than $1K you can buy a used Dell PowerEdge or HP Proliant server (one just out of warranty) and set it up with a bunch of services and use it to jumpstart your marketing efforts, regardless of what you end up doing.

---

