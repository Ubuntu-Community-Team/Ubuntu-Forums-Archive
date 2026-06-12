---
title: "Property Management Software"
date: 2008-03-31
forum: General Help
---

### Post by Slushdoot on 2008-03-31
Hello ladies and gents.  I work in IT support at a university in Ohio and in my department we have a lot of equipment that we loan out to faculty, staff, and students; laptops, projectors, various cables, cameras, etc.  When I first started, back in the days of yore,  we managed it all the old-fashioned way; pen and paper.  The paperwork for it all became a bit unwieldy so the boss decided to switch to a a computer-based solution.  He bought a license  and used a proprietary property management application for Windows.  This, however, was terrible.  It implemented a half-baked database scheme where it all was held in a single binary file and the application itself was buggy as heck.  After a semester of using it my boss succumbed to the whinging from the rest of the staff so we switched back to pen and paper.

I've been using Linux for a few years now and I heard about a library management application on Chess Griffin's Linux Reality podcast.  This got me thinking about our problem.  **I figured that there must be some decent software for Linux that I could install on an old machine with Ubuntu Server + Fluxbox (or similar) that we could then use to check in and out property by scanning barcodes.**  Using an established database like MySQL or PostgreSQL, or even a well-documented light database like SQLite would definitely be a plus (Yes, I know that SQLite stores everything in one file like the above proprietary solution, but at least it's well-documented and understood).

I'm wondering if you knowledgeable fellows might be able to point me in the right direction.  I'm not much of a programmer, but I can usually figure out how to get these sort of things working.

I'd like to be able to set up a database using the application that contains all the individual items, including barcode number, serial number, make, model, and date of purchase.  The devices already have unique barcodes so it could simply be a matter of scanning what i have and filling in the rest of the data.
From there we could leave it running on an old machine acting as a kiosk.  Scan the borrower's ID card barcode, scan the item(s), and submit the entry.

i don't really require much more than that, though reports of various types would be nice, as would some sort of email function.

What do you think, guys, is there something out there that's freely licensed and fits those criteria?  I'd at least like to try a few methods out and see what's possible.

Thanks for you time. :)

---

### Post by Slushdoot on 2008-04-01
Bump?

/hides head in shame

---

### Post by Slushdoot on 2008-04-03
Final bump before I give up!

I've been looking on my own, but I think I might not be using the right search terms to find what I want.  Inventory management isn't quite what I want since most Linux inventory management is for keeping track of running machines and the software installed on them, not keeping track of items coming and going from our inventory.

Any ideas?

---

