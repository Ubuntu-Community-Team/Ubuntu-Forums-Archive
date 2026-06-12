---
title: "Query about setting up your own web-hosting server..."
date: 2015-11-29
forum: General Help
---

### Post by Mike_Walsh on 2015-11-29
Morning, everybody.

First of all, I need to make it clear that I'm making this enquiry on behalf of somebody else. (Mods; I really wasn't certain where to put this. If in your opinion it needs re-locating, please do so. Thanks.)

----------------------------------------------------------------------------

I have some friends who run their own small business, and, like any business that wants to 'get on' these days, they've found it advantageous (in point of fact, necessary), to have a web presence, and have a dedicated web-site. A friend of theirs designed the site, and it is, I believe, being hosted by one of the big names in this field (I think it's 1 & 1 My Website, but don't quote me on that).

In recent weeks, they've been having a lot of problems with the hosting company, who seems to keep changing the 'ground rules' to suit themselves; things like losing their sitename, and having to 'buy it back'.....and problems with the domain name, and so on, and so forth. Consequently, the site has been down more of the time than it's been running.

I know it's perfectly possible to host your own site, running from your own server, located on your own premises. Cut out the 'middle-man', and retain full control. I've suggested this to them as an alternative, and said I'd look into what's needed.

So; what I'd like to ask the knowledgeable folks on here, is as follows:-

1) What kind of hardware would be suitable (or necessary) to run a web-hosting server? What hardware would be considered 'minimum requirements' for such an undertaking? Having some idea of this, I can make recommendations based on my own experience; I'm one of those individuals who is good with the hardware side of things.....but not so good (yet!) with the software, or how to set it up.

2) What extra software (over and above the server OS itself) would be needed to get the server operational, and subsequently the site itself up-and-running? 

I'm beginning to get a grip on a lot of Linux-related day-to-day stuff by now, but I know precious little about servers. Any sensible advice, therefore, would be appreciated.....including links to easy-to-follow useful resources. If anybody has any practical advice, garnered through actual experience of running commercial stuff like this, that would be great!


Regards,

Mike. ;)

---

### Post by Lars Noodén on 2015-11-29
First, be sure that their domain name registrar is a separate company from their hosting service.  If you get a domain name as part of a package deal, **switch** to another registrar as soon as it is allowed as early as possible in the contract period.  If you wait to the end of the contract, they will abuse your friend as you have found out.  In a worst case scenario they could even  lose the name completely if left with a shady registrar.  

Second, a VPS is often better than running one's own server.  The advantages are that power and hardware maintenance are covered.  Usually you will keep better uptimes with that method.  

Next, what kind of web site are they looking for?  I'd keep it as simple as possible, and recommend clean XHTML + CSS with SSI (noexec) for standardized headers, footers and menus.  That is the most secure and easiest to maintain.  If you are looking at a CMS instead, then they have to budget for extra maintenance including timely security updates by someone who is at least on call.

---

### Post by Mike_Walsh on 2015-11-29
Thanks for that, Lars.

OK; that'll give me one avenue to explore. Would you, by any chance, happen to be able to recommend any **reputable** registrars? I want to be able to pass on good recommendations, obviously.

As far as the kind of web site goes, well; as I explained, I don't know very much about this kind of thing at all. Do you have any links, or otherwise, that would explain the differences between the different scenarios you've outlined?

I know all this is possible, but my own lack of knowledge in this area is the sticking point! This is why I need some good, reliable advice.....I want to get a handle on this myself, first.

Thanks.


Regards,

Mike. ;)

---

### Post by coldraven on 2015-11-29
> Second, a VPS is often better than running one's own server.
You might want to research the yearly electrical bill for an in-house server vs. the cost of a VPS

If they are allowing customers to create accounts then the Data Protection Act will apply. AFAIK the USA is off limits now
[https://en.wikipedia.org/wiki/Data_Protection_Act_1998](https://en.wikipedia.org/wiki/Data_Protection_Act_1998)
> 8. 
[LIST=1]
[*]Personal data shall not be transferred to a country or territory outside the [European Economic Area]("https://en.wikipedia.org/wiki/European_Economic_Area")  unless that country or territory ensures an adequate level of  protection for the rights and freedoms of data subjects in relation to  the processing of personal data. 
[/LIST]


Edit: You may need to comply with ISO 27001:2013, this can be expensive.
Below is some info, no particular recommendation as it was just the first search result.
[https://www.ukfast.co.uk/pci-compliant-hosting.html](https://www.ukfast.co.uk/pci-compliant-hosting.html)

---

### Post by Lars Noodén on 2015-11-29
I used to use Gandi.net for some years as a registrar and only had good experiences, but there are some other good ones.  Hopefully others can mention them, too.    

Gisol (and I think anything with -ol in the end of the name) needs to be avoided or at least scrutinized carefully.  They once gave an active .org domain to a squatter even though it should have been locked for transfer, it would have cost thousands to sue to get it back even following the official Internet conflict process.  I tried helping the .org get the name back and all the rules seemed arranged for very large companies with huge budgets and a lot of staff to throw at such problems, best to stick  with the good registrars.  

How fancy of a web site do they want?  The more bells and whistles the more they will have to spend active staff time in maintaining the tools behind the site.  If they go crazy and add a discussion forum or comments then they will have to actively curate the content too.  There are then not just spammers to contend with but also competitors who will deface it.  So regular, frequent, manual monitoring is needed even if the work load (outside of attacks) is low.  

Either Apache2 or nginx can be used for XHML+CSS or XHTML+CSS+SSI.  I'll look around for a good SSI tutorial but it's one of those things that is rather easy and the tutorials tend to be made instead for activities requiring effort or are just plain painful.  Which web server are you going to use, Apache2 or nginx?

---

### Post by jim_deadlock on 2015-11-29
One very important factor to consider is bandwidth. A normal customer ISP account is optimised for download speed but the upload speed is often very poor in comparison. For a web server it's the upload speed that matters, so in my opinion that's the main reason to use a commercial hosting company rather than doing it yourself, plus the other reasons given above.

---

### Post by Mike_Walsh on 2015-11-29
Sorry for the delays in replying, everybody; I'm trying to fit this in round doing the Sunday roast..! Bear with me, please; in the meantime, any replies are still very welcome.

----------------------------------------------------------------------

@coldraven:-

Yes, you're right; residing in the EU as I do, there **is** all that Data Protection Act stuff to remember. Thanks for reminding me!

----------------------------------------------------------------------

@jim_deadlock:-

Would we be talking here about a commercial company for hosting a VPS? The bandwidth thing has occurred to me, also, this last half hour or so...

----------------------------------------------------------------------

@ Lars Nooden:-

If they decide to go for the hardware option (because I basically want to give them as many options as I can, and point out the pros & cons to each option), then I, personally, would recommend Apache 2. It's widely used, and well-understood.....and there's a hell of a lot of support for it. Nginx I can't comment on, as this is the first I've heard of it.

There's already been some mention of using a VPS (Virtual Private Server? I'm extrapolating, here...) What are the pros & cons between the hardware method, and this?

As far as the website content is concerned, nothing fancy; basically all that's required is a modern-day, electronic version of the old noticeboard. It's a private member's club; lists of upcoming events, timetables, opening hours, where to find them, that kind of thing. No forums or anything like that; the only external links are to a handful of other websites, where their own link can be found. And that's pretty much it.

So; what, in the community's considered opinion, would be the best recommendations?


Regards,

Mike. ;)

---

### Post by SeijiSensei on 2015-11-29
I'd also recommend renting a virtual server from a reputable hosting company like [Linode]("http://www.linode.com").  A basic server costs $10/month and includes sufficient disk space for a web site and essentially unlimited bandwidth.  I was happy to no longer have to worry about the server having a hard drive failure or the power going out.  

Do they need to design a site from scratch, or can they just suck down the site they have and move it elsewhere?  In most cases authoring a website constitutes a "work made for hire" and the copyright in the site's materials belong to commissioning party.  However your friends may have abrogated their rights to site's materials in their contract with the designer.  Your friends may need to ask their attorney.

As for the Data Protection Act, does that apply to "accounts" like those at Ubuntu One?  If the site is hosted in another jurisdiction like the US, while the owners reside in the UK, does the Act still apply?

I have used a little DNS registrar called [DirectNIC](http://www.directnic.com/) for years.  They're inexpensive and responsive to support questions.

---

### Post by jim_deadlock on 2015-11-29
By commercial I just mean any hosting service that you pay for (including VPS), as opposed to doing it yourself.

If you're planning to hire a web designer you could ask them to recommend a host - they often provide hosting themselves - that way you kill 2 birds with 1 stone. The advantage is that if there's any problem with the website you only have one person to contact instead of having headaches with the host blaming the designer and vice versa.

---

### Post by Mike_Walsh on 2015-11-29
Hallo, SeijiSensei.

Umm. Yes. The UK's Data Protection Act is a pretty wide-ranging document. I personally have only needed to cursorily skim through the main points at certain times, over the years.....but it's beginning to look as though I may need to look through it in more detail.  This gives an overview, with links for further detail:-

[https://www.admin.ox.ac.uk/councilsec/compliance/dataprotection/](https://www.admin.ox.ac.uk/councilsec/compliance/dataprotection/)

Thanks for the links, by the way. It's beginning to look as though the general consensus of opinion is more in favour of a VPS, then. That's fair enough; I know there's some extremely knowledgeable individuals on the Forums, which is why I decided to begin here, in order to canvas advice, opinions and information.

I'm not certain what the position is, with regards to their existing site. I'll need to collect further information on that point. Thanks for mentioning it.


Regards,

Mike. ;)

---

### Post by Lars Noodén on 2015-11-29
> **Mike_Walsh said:**
> As far as the website content is concerned, nothing fancy; basically all that's required is a modern-day, electronic version of the old noticeboard. It's a private member's club; lists of upcoming events, timetables, opening hours, where to find them, that kind of thing. No forums or anything like that; the only external links are to a handful of other websites, where their own link can be found. And that's pretty much it.

That fits within my earlier recommendation of XHTML+CSS or XHTML+CSS+SSI.  Either can be done with a page template or two.

About the SSI, if you've decided on Apache2, then you would activate the [SSI module](https://httpd.apache.org/docs/2.4/mod/mod_include.html) with *sudo a2enmod include*.  Then in the relevant <Directory ...> or <Location ...> stanza put *Options +IncludesNOEXEC* to allow SSI there.  

Then name the documents .shtml instead of .html.  (Or, alternately, use the [x-bit hack](https://httpd.apache.org/docs/2.4/mod/mod_include.html#xbithack)).  Inside the documents, you can then link to files containing fragments of XHTML, such as navigation menus, headers and footers.  

Inside the file you would point to the files containing the fragments for inclusion using *virtual=* or *file=*

```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
 <title>A web page</title>
 <link href="anicestylesheet.css" rel="stylesheet" type="text/css" media="screen" />
</head>
<body>
 <!--#include virtual="/header.html" -->
 <!--#include virtual="/navmenu.html" -->
 <h1>A web page</h1>
 <p>Hello, World</p>
 <!--#include virtual="/footer.html" -->
</body>
</html>

</body>
</html>


```

As I see it, the advantages of SSI are that it is very secure ( and very low maintenance, and very easy once you get the idea and work out a process.  The disadvantages are that some web designers might not see it as glamorous, there is a lower number of billable hours in the site development, and the drama/visibility of the maintenance is lower.

---

