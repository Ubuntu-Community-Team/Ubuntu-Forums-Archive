---
title: "personal finance software"
date: 2016-04-02
forum: General Help
---

### Post by Lloydb39 on 2016-04-02
Does anybody know anything about Moneyspire? It's personal finance software. I just downloaded it and it doesn't require .deb or the Software Center or anything. You just click on it and it starts. I'm interested in learning how this happens and whether it is any kind of potential problem. Also interested in whether anyone has used the software and found it useful. I've been using Quicken in Windows and want to make a switch to Ubuntu.

---

### Post by kurt18947 on 2016-04-02
I have no experience with Moneyspire or any other personal finance package though Gnucash is often mentioned. Having a 'click to run' binary is not unprecedented - VueScan, a popular shareware scanner package is like that. Copy 3 files to a folder, make sure the main file is executable and click. Sort of like the DOS days with far better memory management among other things. Here is a site that you might find useful when looking for linux equivalents to Windows programs:

 [https://alternativeto.net/software/quicken/](https://alternativeto.net/software/quicken/)

---

### Post by TheFu on 2016-04-02
Interesting ... I downloaded moneyspire and looked at the package internals.

I did not install it or run it.  Looked through the files, because I'm slightly interested in moving from Quickbooks and Quicken for my needs.  I've been a Quicken user since the early 1990s and heavily use the investment tracking parts in Quicken.  If all I needed was a check register to aid with balancing, almost any money program would work. I need more.

Opinions follow:

There is a big difference between "free" and Free/Libre Open Source Software.  You may not care about those differences, but many people do. This is a pre-compiled, binary program.  It isn't clear how the company behind mineyspire earns any profits to me.  That usually means that the users ARE the product being sold.  They claim that none of your data is sent off the PC, so I'm guessing that metadata is transmitted or they get a tiny bit of any online transactions.> Your data is encrypted and stays on your computer &#8212; Moneyspire Inc. does not collect or store your financial information.
This doesn't say anything about collecting and accessing all the other data on the machine.  They probably don't, but we cannot know without hooking up a network packet capture tool.

The company appears to be in Bellflower, Cali, USA - they have a P.O. Box there.  My personal company has a P.O. Box too.  Could be good, nice, people or crooks.  They are probably nice people, but I don't know. More research needed.  Spent 10 minutes googling and didn't find **anything** more than what is here: [http://www.moneyspire.com/about/#contact](http://www.moneyspire.com/about/#contact) - which doesn't provide "a name" - a real human.  Didn't see anything on LinkedIn either. That is strange - not to have anything on LinkedIn.  I worked for a company founded in 2007 (same year as moneyspire inc.) and the first thing we all did was to update our LinkedIn accounts with the company info and setup social media accounts for the company too.  We didn't sell directly to end-users, but to corporations, so the social media stuff wasn't very important - just another way to build trust.

Any company that wants to help me manage my financial life needs to build trust. I need to know there are real humans behind the company. Photos of the management team, leaders, developers, and their families with pets would be good. Of course, all those things could be lies, but I'd feel better believing they were real, honest people ingrained in their community.  Do they sponsor a kids soccer team?

Potential problems iwth software like this?  Lots, but since it doesn't run as root, in theory, nothing too bad that normal, versioned, backups wouldn't solve should be possible. There are always zero-day issues unknown to almost everyone, including security researchers.  I don't want to say anything bad about this software or the company - just don't know.  Worth giving them a chance? Perhaps.

No install?  Ok. They didn't bother to make an package.  I wrote installations for Unix programs for years. Looked at the way they distribute this.  I like it, but it doesn't integrate into the KDE or Gnome menu systems.  They also include their own C++ library - with debug information in all the libraries. Not good. Development versions of libraries should never be shipped. This is a noob mistake, IMHO.

I did run Quicken 2011 under WINE for a few years, but eventually it became too much hassle to keep doing that with newer Quicken versions and since I had a Windows VM for 2 other needs already, running Quicken in that wasn't a big deal.  In 2020 when Win7 support ends, I'll have to review how to manage finances.  Intuit forces an upgrade on me every few years that I don't really need - I've been happy with the investment features in Quicken since the late 1990s - for me - it really comes down to having stock data updates that drives new versions.

I've been using Beancounter [http://dirk.eddelbuettel.com/code/beancounter.howto.html](http://dirk.eddelbuettel.com/code/beancounter.howto.html) for almost a decade in parallel to Quicken for just stock tracking. No GUI. I like the daily and weekly reports - have those emailed to me. Use paid websites for most stock decisions based on the NAIC methods and training.  Quicken really is just the "system of record" for transactions and longer-term ROI.

If you use this software for a week and post back your experiences, I would find it helpful.

---

### Post by Lloydb39 on 2016-04-02
Very helpful, TheFu. I'll give it a whirl, but apparently it isn't really free. The first thing it does is offer to upgrade.... and nowhere on the company's site does it tell you the cost of the product! That's a really bad sign. Maybe the best thing to do is run Quicken in virtualbox....

---

### Post by oldfred on 2016-04-02
I used Quicken from DOS days and if they offered a Linux version, I probably would be first in line to purchase it.

I converted to Linux in 2007, but kept XP for another 4 years just for Quicken. But XP took 3 minutes to boot, many updates with reboot required, so it often took all Sat AM just to use XP & Quicken.

Finally converted to Kmymoney. But that was just for expense tracking. For Assets I wrote my own download program from Yahoo but modified standard versions to download history into sqlite database and generate reports. i violate all the database rules and directly edit files to fix or add a missing entry.

I did try importing a lot into Kmymoney from Quicken, but that did not go particularly well. I should have just bitten bullet and re-recreated from scratch.

---

### Post by Lloydb39 on 2016-04-02
Thanks, OldFred. That's helpful too. Also occurs to me I could just use Quicken on a Windows 10 laptop I have, but I'm also going to try Gnucash.

---

### Post by amanchesterman on 2016-04-02
I have used GnuCash for several years now and find it very reliable. (I used to use Quicken when I had a Windows computer years ago.) However my needs aren't complex: mainly tracking income and expenses, a few asset and savings accounts, a small portfolio of stocks and shares. I use it just for keeping records and producing reports, I don't use it for tax returns which I do directly online.

---

### Post by Lloydb39 on 2016-04-02
My main thing is to be able to pay my bills online and track it in the software. Will Gnucash do that? And does it convert Quicken files easily?

---

