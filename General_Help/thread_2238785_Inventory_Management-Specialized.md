---
title: "Inventory Management-Specialized"
date: 2014-08-10
forum: General Help
---

### Post by Flaming_Tire_Iron on 2014-08-10
So.. I work on the AMF 82-70 Pinspotters.. and we have way to many parts scattered int he back in the organuized chaos of the faded unlabled drawers, boxes and such. With the ok from the Head mechanic, I am going to try and get things organized documented, and what not.

The alleys budget is uncouthly tight and will be until the busy season starts for us, so I am doing this odf my own volition, donating one of my computers to the alley for the back. 

Sadly, doing Google searches has proved less than expected for Inventory Management stuff that would meet the needs of the back..

Something open source and that wont cost a dime would be helpful..

Due to the nature of the 82-70s, we have both old/used and new parts alike that wed like to keep track with.. And given I still dont know them all, a management system that allows one to take pictures and use them for each part.

Something NOT SQL based as that is a damn headache to set up, pardon my language. For my personal use yes, since I can, but the others here are less than computer savvy when it comes to Linux based OS, and SQL.. I can at least show them how to use the whatever program if I find one.

Anyone have any idears, My organization twitch is firing.

I may or may not be using Ubuntu as the OS, Ill be doing testing to which works with the system later.

---

### Post by amanchesterman on 2014-08-10
In the Ubuntu Software Center there are a couple of inventory programs: both require payment but aren't expensive. One of them lets you associate pictures, descriptions and even documents with items, and says that the records are kept in a portable format for transfer to other OS platforms. It's marketed at householders wanting to keep an inventory of their stuff, but you might be able to adapt it to your needs? Possibly worth a look, anyway.

---

### Post by tgalati4 on 2014-08-10
A simple *spreadsheet* in gnumeric might do the trick.  Otherwise you want to look into trouble ticket systems (such as *redmine*--in the repos) or ERP--enterprise resource planners.  They require SQL (sorry) but if you want to attach documents or photos you will need a database backend.

Windows has OneNote which some folks like--which includes audio notes which is helpful for when you are doing walkthroughs and taking verbal notes on maintenance issues.

Evernote is a cloud solution with a Web client that can be used in Linux or nixnote which can be used.  Android clients can take pictures, video, and audio notes.

If you need a simple note-taker with inserted images and an outline format, check out *zim*.

---

### Post by ian-weisser on 2014-08-10
I suppose it depends upon what you want from your inventory management software.
To know where a part is located?
Picture of a part?
Prompt to reorder low parts?

So far, what you have described seems more like "order the right number of bins...and a labelmaker" in terms of organization.
How many part numbers are you talking about? Hundreds? Thousands?
Do you want to track each part used at the time? Or will you use periodic inventories to update?
Will everyone be entering/changing data? Or just you?

---

