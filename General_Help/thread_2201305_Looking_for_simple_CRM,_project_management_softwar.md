---
title: "Looking for simple CRM, project management software"
date: 2014-01-23
forum: General Help
---

### Post by yoshimitsuspeed2 on 2014-01-23
I own a business that does custom fabrication, welding and automotive work. I also sell aftermarket parts and have an online store. I do a lot of personalized quotes for my customers that don't go through my website. 

Baiscally what I think I am looking for is a combination of CRM and project management. My website is drupal based so when I found ERPAL I thought I'd found my solution but it requires more PHP memory than my current hosting. A hosting account with my current provider with enough memory would cost more than four times more. I am currently looking into other options to make this work. I don't want to host it on my own machine, though I may be able to install it on my machine and transfer it to my site or somethign but right now I am hoping to find a quick easy solution. 

Basically I want to be able to have an address book with customers information. From there I want to be able to make quotes that are attached to their profile, saved and easy to find. If something is a project like fabrication I would like to be able to move it into a project category that links to their profile and is easy to find. I would really like it if it included a way to track time and materials for the project. Something on a server or cloud based so I could access it from multiple computers would be very nice. It doesn't have to be free but I am also not paying $50/month for this kind of service right now. 

Does anyone have any suggestions?

---

### Post by tgalati4 on 2014-01-23
Build and manage your own server and put Drupal on it for your website and install *sugarcrm* for your CRM.  It might be too heavy for your business size, but it does a nice job of managing business pipelines.  For project management, there are some plug-ins to sugarcrm as well as several stand-alone packages.

Other CRM ideas:  [http://bitnami.com/stacks/crm](http://bitnami.com/stacks/crm)

Other Project Management ideas:  [http://bitnami.com/stacks/project-management](http://bitnami.com/stacks/project-management)

Material tracking:  [http://bitnami.com/stacks/erp](http://bitnami.com/stacks/erp)

I personally use Tracks and it works quite well.  [http://bitnami.com/stack/tracks](http://bitnami.com/stack/tracks)

All of these tools have a learning curve.  But once set up, they are powerful, customizable, and most of them are open source.

What you really want is a customized tool that manages all aspects of your business.  For instance [OpenMolar]("http://openmolar.com/om2").

---

### Post by yoshimitsuspeed2 on 2014-01-24
I don't really want to build my own server. I already spend too much time doing things that aren't making me money. 
I checked out sugar and am looking into it again right now but I couldn't find any project management available for their community edition. Their paid edditions are out of my pricerange at the moment. Do you know of any add ons that will work with the community eddition? 
I definitely want something that is integrated. I would like to move from adding a contact, to adding a quote to adding a project within one  interface that keeps them all tied to the customer. 
I am downloading the community edition right now so we will see how that goes.

---

### Post by yoshimitsuspeed2 on 2014-01-24
Dang Sugar's requirements are higher than ERPAL. 
[h=3]Memory requirements[/h] Increase the value of the memory_limit parameter in the php.ini file as follows:
 
[LIST]
[*]32-bit installations: 256M or higher
[*]64-bit installations: 512M or higher
[/LIST]
 **Note**:   Increase the memory limit to 384M or higher for 32-bit installations,  768M or higher for 64-bit installations, for demo data installations.

---

### Post by yoshimitsuspeed2 on 2014-01-24
Just an update. Even though sugar claimed higher memory requirements it installed just fine on my site with 128 m.
It also has a projects tab that should be enough for my needs and appears to be easily customizable easily enough. I think I am going to run with this for now. 
Thanks for your input [**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895")

---

### Post by tgalati4 on 2014-01-24
You only need the higher PHP memory if you are running a lot of add-ons and have some huge client records.  Remember, every time you fetch a client's page, it is created on the fly by pulling data from the mysql database and formats it and sends it out.  If you don't have enough PHP memory for that task, the page will fail to load.  You can play with the PHP values until you have problems.  The default used to be 16 MB then 64 MB, so if it works with 128 MB, keep it there for a while until you have problems then bump it up.

Although you don't want to maintain a server, your options are to do it yourself or pay someone else to do it.  You best know your business processes.  The time it takes for you to articulate those business processes to a web developer and then make and test the changes, you can do it yourself in less time.

Some people just want to get in a car and turn the key and go.  Others are a little curious as to how the car works--they can check the oil and coolant.  A mechanic is not afraid to lift the hood.   Spend some time on the [sugar forums]("http://forums.sugarcrm.com/") and you will see that there is a large community to get help from.  Customizing sugar is no more difficult than changing plug #8.  You just need the right tools, some patience, and the forums.

---

