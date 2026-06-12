---
title: "[edit] Web based self hosted alternative to Evernote?"
date: 2014-07-15
forum: General Help
---

### Post by Roasted on 2014-07-15
Hello friends. I've been doing some more side work lately with tech repairs, software fixes, etc etc etc. Up until now I've simply kept the information in a calc spreadsheet. You know, just the basic info... Date, name, computer make/model, problem, quoted price, notes, etc. I got to wondering if there was a better way to set this up. I must admit, I'm not overly interested in doing some sort of elaborate database. As I do this spreadsheet I can't help but to think that there might be something that I can drop in place and run on my server (Ubuntu Server 12.04.4). 

I looked into LibreOffice Base but I must admit, I've never really gotten into the Base/Access type of setups. I guess I almost want a setup where I can see a list of the basic info in a sorted row (newest on top), and if I click it, I get the full page of the info with all of the parameters I listed above.

Is there something I'm missing? Any suggestions?

---

### Post by TheFu on 2014-07-15
This is one area where Linux solutions don't do a good job.  Running a business means that having business records is important.  I use **Quicken Home & Business** - though I'd switch to a Linux solution if it handled all the things I need for home stuff (none do).  
So ... I'd search freshmeat (soon to be dead) and AlternativeTo.net  [http://alternativeto.net/software/quickbooks/](http://alternativeto.net/software/quickbooks/) for options.  I guess it really depends on your underlying requirements.

Those are for the financial aspect.  That doesn't replace the proposal, detailed statement of work, design and user acceptance signatures.  For that stuff, we have a document management system and agreed layout by year, job. Starting with year is important for records management.

Another option is to use a more free-form, but searchable solution if you just want to have the data. BasKet Note Pads, Zim, Tomboy, or even an internal WIki. Other note taking solutions [http://alternativeto.net/software/basket/?platform=linux](http://alternativeto.net/software/basket/?platform=linux) might be useful, but having a calculation field is nice.  Rate x hrs x Tax-Rate = $cost.  As jobs become more complex, having an estimate spreadsheet is nice ... customers like to see things broken down by SW-CAP, HW-CAP, Expense for them and for different subtasks to be spelled out.  At least our clients do.  We provide a cost breakdown along with the SoW.

BTW, we pay an external accountant to maintain the official books - they use Quickbooks. I tried to get our internal books setup using **anything** Linux, but was overruled. Some fights aren't worth it.  The rest of our business runs on Linux.

If you are profitable, it is probably time to become an official business and protect your other assets from lawsuits. Creating an LLC where I live (USA) is $50/yr and 2 hrs of time.  It also means that if a client decides to sue the business, my home, cars, furniture isn't up for them to grab.  Just the business assets - which aren't really that much.  We are a service company and try NOT to own much inside the business. There are reasons NOT to do this, but it works for our needs.

Going too far down the

---

### Post by tgalati4 on 2014-07-15
If you want more of a customer-focused approached, you can look into customer relations management (CRM) packages:

[http://sugarcrm.org](http://sugarcrm.org) is one that I use.

There are several:  [https://bitnami.com/stacks/crm](https://bitnami.com/stacks/crm)

They all have a learning curve; they are all powerful; they are all scaleable.

Learning Base might be the easiest--then it is custom-designed for your business.  The others require some templates and configurations to be built.  The Agony Units are probably the same.

If you are more interested in a trouble-ticket tracker (such as what an IT Help Desk would use) there is *redmine* and *trac*.  Then you are keeping a database of "issues" instead of "clients".  

CRM's are helpful for multiple contacts with multiple customers.  You can generate all sorts of reports and even estimate future business pipelines.  Bug-trackers are helpful for single issue, single client, again with all sorts or reports available.

What is your User Story?  Describe how you would like to use this system and what it would provide for you.  Do you need mobile access?  Are you out in the field a lot?  Do you need to generate billing/invoices on-the-spot?  Once you describe your business process in detail (and you don't have to post it) then the solutions become clear.  Reading the sugarcrm forums will also provide insight, as several small businesses have gone down this path.

---

### Post by Roasted on 2014-07-15
Thanks for the input. Quite honestly, I pretty much want something like Evernote (sorta kinda), but just on my computer OR (preferably) my server. I just want a list of things on the side. I'd sort it by date + name, aka, "2014 - July 15th - Bob Johnson". I click, and I get more info in a bigger body to the side with the details.

I have ownCloud running on my server. It almost looks like their "Tasks" plugin may suit. I'll have to tinker with it more.

---

### Post by oldfred on 2014-07-15
These are not databases, but may be closer to what you want. 

 Collections - music, books, etc: both in repositories
Tellico - qt4 & python, xml for data
[http://tellico-project.org/](http://tellico-project.org/)
Gcstar - perl & gtk, xml for data
[http://www.gcstar.org/](http://www.gcstar.org/)

A full database then needs a query tool, report tool and forms to input data. That starts to get more complicated.
When my spreadsheets went over two pages of greenbar paper I had to convert to dBase as back then that was all SuperCalc could handle. :)

---

### Post by Roasted on 2014-07-15
So here's what I found so far...

Cherry Tree - downright brilliant. Downsides are it's not web based (however I can just save the Cherry Tree file to ownCloud sync folder which synchronizes accordingly), and the most irritating downside, is I cannot permanently set it so it sorts the items in descending order. If I create new items, they just get listed as ascending, so I have to repeatedly hit descending. Eh.

ownCloud (Notes app) - This is nearly perfect. My one (and only) peeve with it is the fact that it continually puts the most recently edited file up top. I want it to *always* show the most recent file at the top. If I edit an older file, I still want it to be further down in the list where it originally was.

And of course, Evernote - Perfect in every way functionality wise, aside from the fact that it does not live on my server, which is a must.

All in all I didn't really need a database oriented solution I suppose... just something with basic features and a clean interface. Evernote, Cherry Tree, and ownCloud Notes app hits that mark, but as mentioned above, both options that I would prefer to go with over Evernote have some sort of limitation. While Evernote is the clear winner, I simply won't use it. I don't want to store client information in an external source. It's not fair to them, and quite frankly, it's just plain wrong.

Meh.

---

### Post by Roasted on 2014-07-15
The more I dive into this, the more I'm realizing I basically want Evernote, but hosted on my own server. I edited the title of the thread to reflect that. I found something known as Tagspaces, but I'm not sure I understand it. I read a few posts indicating it was a nice self-hosted alternative to Evernote, but it seems to be a... tagging application. It basically is a web frontend for your file browser, and you can tag things to organize them accordingly. Not sure I really understand the point of it, but it looks really nice and it's super easy to install. Basically just unzip the download and drop it in your web root, boom, done. Thing is I'm not seeing how I can create notes. I could make it work easily if I could just create text files instead of needing to link up to a specific remote location in an effort to utilize it. If anybody has any info on Tagspaces I'd greatly appreciate it.

The next best thing looks like Laverna, but it requires a git clone and etc/etc/etc to run. Based on the screenshots it looks very nice, though.

I tinkered with ownCloud but it doesn't seem as if I can control the sort behavior. I need the newest to be at the top, regardless of when any file was edited. 

That said, does anybody have any input for a self hosted alternative to Evernote? That would be the real ticket.

---

### Post by tgalati4 on 2014-07-15
I like *zim*.  You can run it remotely if you point your note storage to a fileserver that you have access to.

---

### Post by TheFu on 2014-07-16
I've made quick DBs using text files and a few bash/perl scripts.  With a full-text indexer like Recoll, the query-tool part is solved too.  Between directory names, filenames, and full-text search - it holds anything I want and can be sorted by any column easily.  If you put projects into year directories, that solves most real organization needs.  You could have a job-number that is based on the data and client too - that is fairly common and easy.

I think if you look a **BasKet Notes**, you'd be surprised.  However, I've never used evernote - we don't use 3rd party apps for client stuff here.

---

