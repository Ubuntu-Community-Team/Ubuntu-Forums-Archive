---
title: "Recommendations for Content Management Software"
date: 2008-04-02
forum: General Help
---

### Post by tripwire45 on 2008-04-02
I didn't know where to put this and so chose a "general" category. I also opened all of the threads "suggested" by the forum software that are relative to CMS and reviewed them before posting this.

I'm a technical writer and started a new contract job today. I'm taking over for a writer that had to drop out suddenly and I'm in the position of taking his work at a software company, and completing the documentation on the latest version of one of the company's products.

The previous writer pretty much did everything in Office 2007, particularly Word and PowerPoint (to the point of using PowerPoint to design his technical diagrams and create graphics, oddly enough).

The product in question is web-based, so print documentation isn't really relevant. I talked to the developer who manages the help pages for the product, and he told me that my predecessor would create in Word and save his work in xdoc format to send to the developer.

Frankly, it sounds like a pain in the pin feathers (and the developer agrees) and I'd rather compose using a tool that more directly generates web-friendly content.

The really interesting thing is that all of the software developers work on Ubuntu and the company will soon be moving their server base from BSD to the Ubuntu server.

I use Ubuntu as my desktop at home and given the opportunity to do so at work would be a dream. 

The thing is, after talking to this developer and listening to his suggestions, I am looking for a content management system where I could create and store content that could then be taken by the developers and used in whatever format they need (HTML, XML, PDF, and so on) rather than creating in one tool that requires my content to be completely recreated in a separate format. No content management system currently exists and I could potentially, suggest (and assuming they accept my suggestion) and implement such a system.

Looking at the other threads here on this subject, it seems like Joomla and Drupal are the front runners. I'm throwing Plone in the mix as well and for two reasons; a friend of mine deployed plone for his work environment, he loves it, and he's been dying to get me to try it. I've only had one opportunity to get on his plone-based site and haven't gotten to know the thing yet. Also, at least some of the packages for Plone were written in Python, which (although I'm not a programmer by a long shot), is probably the programming language I have the most (which isn't to say "much") experience with.

Again, the primary features I'm looking for in a CMS application (at least at this stage of the game) are those that would lend themselves to me being able to create help content, and various user and technical specification guides, and then have that content be available to be used in a number of formats, specifically those that are web-based.

Sorry for the long post, but I felt some background was necessary and particularly why I am posting this on an Ubuntu forum.

Oh...although not related to CMS, I'd also be interested in exploring any application that could be used to create flash-type movies to be used as tutorials. I can't recall the name of the software my predecessor used, but I checked while at work, and it's not open source.

Any ideas would certainly be appreciated. Thanks.

-Trip

---

### Post by Brucevdk on 2008-04-03
This thread probably belongs in the Community Cafe discussion forum since this is reserved for support problems dealing with Ubuntu.

I've looked into Document Management a little bit and here's some more information that might help you in making a decision.

You already mentioned Drupal, see [this discussion]("http://drupal.org/node/57400") and the [document management group at Drupal.org]("http://groups.drupal.org/document-management") for more information on Drupal.org plus Document Management. However, considering the requirements you mentioned you'll have to look into the support available through external modules for content transformations. Other than that, Drupal combined with the Views and CCK modules is quite powerful.

Another alternative would be [Alfresco]("http://www.alfresco.com/") which is an extensive document management system written in Java. It has a lot of functionality concerning document transformations, workflows and actions. For example, to manually convert (it can be done automatically using rules) an OpenDocument file to HTML, PDF etc. you:
[LIST=1]
[*]Upload an OpenDocument file and view the file details
[*]Select "Run Action" and add action "Transform and copy content to a specific space"
[*]Run the action and view the resulting files
[/LIST]

You can download [the Tomcat bundle over at SourceForge.net]("http://sourceforge.net/project/downloading.php?group_id=143373&use_mirror=garr&filename=alfresco-community-tomcat-2.1.0.tar.gz&34240523"). Note the the transformation functionality requires a headless OpenOffice.org, you can start this using (make sure OOo isn't running before doing so):
```
soffice "-accept=socket,host=localhost,port=8100;urp;StarOffice.ServiceManager" -nologo -headless
```

It might also be interesting to look into [KnowledgeTree]("http://www.knowledgetree.com/"), though I am not familiar with it myself.

However, I'd advise against building something from scratch. If anything, grab one of the existing projects and expand it with the functionality you require. There are a lot of people working on document/content management and it would be a shame to not build upon that work.

Also there's a chance someone might mention Microsoft SharePoint, I'd recommend reading the following articles so you at least know what to counter with:
[LIST]
[*][Matt Assay, VP Business Development Alfresco, concerning "The Future of Lock-in"]("http://asay.blogspot.com/2006/05/future-of-lock-in.html")
[*][Dries Buytaert, the founder and maintainer of Drupal on SharePoint 2007]("http://buytaert.net/sharepoint-2007")
[*][Matt Assay in response to the post by Dries Buytaert talks about SharePoint]("http://asay.blogspot.com/2006/12/drupal-founder-on-sharepoint.html")
[/LIST]

Good luck.

Best regards,

Bruce

---

### Post by tripwire45 on 2008-04-03
Thanks for the detailed response, Bruce. That's a lot to digest and I'll need to have a closer look at the links you've provided. Also, I apologize for selecting the incorrect forum. I wasn't sure which one to choose for this topic. 

In terms of SharePoint, I've actually [got some experience](http://www.wiredwriter.net/publications/publication.html) in that area, but don't think it would fit the environment or my specific requirements. ;)

---

### Post by zazuge on 2008-05-13
Well i think his needs  cover more the CMS area that th DMS
[joomla]("http://www.joomla.org") is worth a look
with it you you can publish article in the intranet
or maybe you need a wiki?

---

### Post by tripwire45 on 2008-05-13
Wow. Thanks for the reply, but I've pretty much moved on since I posted this in early April. Turns out our needs were very much different than what was first communicated. Cheers. :)

-Trip

---

### Post by Brucevdk on 2008-05-14
> **tripwire45 said:**
> Wow. Thanks for the reply, but I've pretty much moved on since I posted this in early April. Turns out our needs were very much different than what was first communicated. Cheers. :)

Hey Trip,

I thought it was great that in your original post you supplied a lot of information concerning the needs/requirements this particular piece of software should fulfill. The fact you took the time to write out your post like that triggered me to write my original reply, quite a welcome change from some of the 'Can you help me?!' threads :)

I'm quite interested in the software development process of which requirements gathering is an important part. Would you care to share some more information on how the needs/requirements differed from originally understood? 

Best regards,

Bruce

---

### Post by tripwire45 on 2008-05-14
Hi Bruce. Actually, this is kind of embarrassing.

There was a miscommunication between me and the developer I was talking to. He really didn't mean "content management" at all but rather, "markup language". He was suggesting that content be written in a language that would be able to "port" to other formats (HTML, XML, and so on). 

We settled on LaTeX (actually, the "powers-that-be" settled on it) and I ended up teaching myself how LaTeX works, using Kile on Ubuntu, manually transferring the content from the Word documents into LaTeX docs and compiling them as PDFs. 

I've got a pretty good handle on things now and submit my work to a Subversion repository. The developers than then take what I commit and use it for their own purposes. It seems to be a unique way to write this sort of content, since most LaTeX users are either software developers, mathematicians, or scientists. 

The whole "content management" suggestion was a red herring. They do have a wiki here, but I only use it occasionally. 

Anyway, thanks again for your inquiry. Hope this is what you were looking for. Cheers. :)

-Trip

---

### Post by zazuge on 2008-05-16
Glad that you settled on LaTex  i used it to write my engineering thesis without suffering, considering the nightmare I lived throught
to write my passt thesis with office apps.

a hint: use a make file to acclerate the gs/ps/pdf compilation.
I also used versioning (even if i worked on solo), TODOs,BibTex...
keep the good work, Persever and dont't give to easiness.

---

