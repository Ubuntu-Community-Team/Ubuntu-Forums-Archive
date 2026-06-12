---
title: "Quicken 2002 vs. GnuCash"
date: 2007-08-05
forum: General Help
---

### Post by elyk on 2007-08-05
I just opened a checking account, and I'm trying to decide which accounting software to use. I've got an old copy of Quicken 2002 basic that seems to run fine under wine, but I'm also considering GnuCash. I'm trying to use open source whenever possible, and I'd prefer a program that I'll continue to get updates for. So I've got two questions.  First, what, if any, features would I miss by going with GnuCash instead of Quicken 2002 (or vice versa). Secondly, if I choose one and end up liking the other program better, how easily would I be able to transfer my accounts to the other?
Thanks for your help.
EDIT: Forgot to mention it, but I'd also consider kmymoney or grisbi, but from what I've read GnuCash seems to be the best of the open source options

---

### Post by wjp.reg on 2007-08-05
Would you be wanting to be able to connect to the bank to reconclie your accounts?  If so, you need to check the individual apps for this capability.  I think it depends on the app and country you live in (from those you mentioned).  With Quicken you will also need to run MS Explorer to do this.  You would have best results with crossover, the commercial version of Wine to run Quicken with MS Explorer.

My 2 cents worth, lol.

---

### Post by Wharf Rat on 2007-08-05
> **wjp.reg said:**
>   With Quicken you will also need to run MS Explorer to do this.  You would have best results with crossover, the commercial version of Wine to run Quicken with MS Explorer.

I have not been able to set this up under Xandros.  Quicken 2006 and IE6 just puke.

---

### Post by Midahed on 2007-08-05
I've been thinking about converting to another financial package ever since Intuit effectively dumped it's UK customer base out in the cold and left us with no upgrade path for Quicken.  I've had a look at the GnuCash documentation and it seems to do everything that's needed.  In some ways it appears better than my current version of Quicken (2003) because it claims it can get current prices for mutual funds - something I've been unable to get Quicken 2003 to achieve. I also prefer the idea of being able to select and change the source of market information, rather than have to trust that the one used by Quicken 2003 will continue to work in perpetuity!

Like elyk, I'd be interested to know where GnuCash and Quicken are better/worse than each other, what functionality is missing from each offering, how they compare as far as stability/bugs are concerned, and how easy (or otherwise) it was to make the switch from Quicken.

I have around 15 years of personal financial records on Quicken, so making the move to GnuCash would be a fairly major task.  But it would be one less Windows app and one step closer to dropping the Windows environment altogether. :)

Mike

---

### Post by elyk on 2007-08-05
> **wjp.reg said:**
> Would you be wanting to be able to connect to the bank to reconclie your accounts?  If so, you need to check the individual apps for this capability.  I think it depends on the app and country you live in (from those you mentioned).  With Quicken you will also need to run MS Explorer to do this.  You would have best results with crossover, the commercial version of Wine to run Quicken with MS Explorer.

My 2 cents worth, lol.

That capability would be nice, but not essential. I don't mind going through my statement by hand and checking the entries once a month.  I'm more interested in which program (GnuCash, KMyMoney2, or Quicken 2002) offers the best features and useability at this point, as I've been unable to find reviews newer than the end of last year, long before 2.2 was released.

---

### Post by Wharf Rat on 2007-08-05
> **Midahed said:**
> I have around 15 years of personal financial records on Quicken, so making the move to GnuCash would be a fairly major task.  But it would be one less Windows app and one step closer to dropping the Windows environment altogether. :)

Mike

Exactly. I have used Quicken since '87

---

### Post by seauerbach on 2007-08-05
From my perspective it depends on the services provided by your bank. The bank that I have my accounts with allows me to download checking, savings and  credit card transactions in QIF or QFX format. Periodically I import QIF downloaded transactions with GnuCash. I find it necessary to edit the QIF transactions with a text editor since my bank includes some superfluous information  on the payee line. This is only a minor nuisance since I do not have all that many transactions.  This process probably could be automated with sed if one were willing to take the time to do so.

I did use Quicken until approximately five years ago. I found that I could do my banking via my banks web site much more quickly than I could with Quicken.  I only use GnuCash for record keeping and sometimes budgeting. It works very well  for those purposes.

I tried Grisbi about a year ago or so. It may have improved since then, but it had too many serious bugs at that time. 

sea

---

### Post by Midahed on 2007-08-08
Well, I've just spent the best part of two days evaluating GnuCash 2.0.2. 

I've been looking to move away from Quicken 2003 for the reasons outlined in my earlier post in this thread.  I liked the idea of going with GnuCash - if only to get away from having to rely on a closed-source application who's vendor was prepared to walk away from its UK customer base.

I was prepared to have to get to grips with a system based on double-entry accounting and I recognised that I would probably have to spend a _lot_ of time cleansing my Quicken data before it could be sensibly imported into GnuCash.

To be honest I've been very disappointed by GnuCash.  OK, I've only spent a little time trying to find a resolution to the problems, but it's got to the point where I'm just not prepared to risk my financial data on something that is, apparently, still fairly rough and ready.

If I was starting out with no historical data and I was prepared to give it a bit more time, maybe things would be different, but I'm used to Quicken 'just working' and doing the job I bought it for.

Generally I found GnuCash 'clunky' and non-intuitive to use.  Just the fact that it starts out by not displaying anything is off-putting.  OK, you can save your file with various account registers being displayed and it will remember that when the file is next loaded, but initially I was left wondering 'OK, where is everything, then?'

Two areas that were important to me were reporting and stock price tracking.  I found both areas to be unacceptably weak.  The system has a number of built-in standard reports.  Some of these are fairly slow to run - 15 to 20 seconds at least on my AMD Athlon 64 3700+ with a gig of ram.  The start date for reports seems to default to January 1st in the current year.  This can be changed by clicking the options button on the reports toolbar, but that button only becomes available once the report has already been run.  This would be OK if reports ran fairly quickly, but, as things stand, you have to run a slow report then wait for the results before you can change the start date and run it again!  Unfortunately, the revised start date isn't even carried through into the next report you run.  The consequence is that if you want a whole load of reports for, say, the last quarter, you have to face the fact that you'll be running them all twice.

Most of the reports I looked at are not at all pretty - in fact most are pretty horrible!  I saw plenty of examples of headings that don't line up, layouts that result in most report lines requiring two lines on the page and excessive indenting that pushes everything over to the right of the page.  I was unable to print most of the reports I wanted without having to go onto a second page - even in landscape format.  

You can produce your own reports, but you'll have to get to grips with a LISP-like language called Guile.  The manual also states that you'll need a copy of the GNUCash source in order to be able to produce your own reports - I'm not sure whether this is because the new reports need to be compiled with the source or whether it's because you need the source to properly understand whatever API is used in the reporting environment.  The manual also seems to say that it is difficult to avoid formatting problems. :(

There is a handy view of all accounts on the 'accounts' tab.  It shows the account name, balance, etc.  There are other fields that can optionally be included for display as well.  This provides a much more readable form of account summary than any of the reports I found, but there's no way to print it!

Due to the structure of accounts, their names can become very long, i.e. Income: Dividends:TD Waterhouse Trading:Teesland Advantage Property Trust.  Some of mine were even longer than that.  Careful thought needs to be applied when naming accounts to ensure they don't get too long and to simplify data entry.

While reports are being produced - something that can take 20 seconds or so - all menu options and buttons are greyed-out, so you can't even do something else while you wait.

I had a similarly sorry experience with trying to get stock pricing to work.  Having eventually found how to add the London Stock Exchange to the list of (mostly American) markets that are pre-configured, I tried to get prices for Barclays plc, Alliance and Leicester plc and Marks and Spencer plc.  The first two consistently failed.  Marks worked eventually, but insisted in downloading the price in US Dollars!

I thought having the option of multiple sources of stock pricing data would be a big advantage over Quicken.  Apparently not.  Maybe it's possible to configure the use of some of the more commonly used UK sources for pricing data, but I couldn't see any way to do it.

Searching the GnuCash mailing lists revealed that other people had been having the same problem.  I didn't see anything that claimed to offer a solution.  As you might imagine, I didn't get a warm feeling about this.

I had a couple of instances where the application just shut down all on its own, and I had two or three instances where I got a fairly unfriendly and uninformative error message - "there was a system error when retrieving the price quotes' was one of them.  The other was when I clicked the 'help' button on one of the screens.

There were a number of other things that I didn't like about GnuCash and, on their own, they wouldn't have been show-stoppers.  But viewed along with the reporting deficiencies and the problems with stock quotes, it was all too much to get over,

I was using the 2.0.2 version from the Ubuntu repository.  This isn't the latest stable release by any means (2.2.0 is the latest and greatest), but I wasn't interested in having to compile my own binaries and therefore had to rely on the earlier version.  

There have been a number of bug-fixes included in the intervening releases, so it's possible that trying  2.2.0 would have been a smoother ride.  It's also possible that I failed to find the right bit of the documentation, or I missed a crucial solution documented in the mail archives but, either way, I'll not be taking GnuCash any further - not yet.

I don't like the way Intuit dumped its UK customer base, and I don't like relying on a piece of ever-ageing software to run my finances - especially when a crucial aspect is its ability to retrieve stock prices online.  However, it works, and it does so absolutely painlessly.  GnuCash doesn't seem to achieve that just yet.

For me, the score is Quicken 7, GnuCash 4.  I'll be staying with Quicken for the moment.

Mike

---

### Post by wjp.reg on 2007-08-08
And that's the sad conclusion I came to as well.  We can only hope! lol

---

### Post by r1d1 on 2007-08-14
> **Midahed said:**
> 
I don't like the way Intuit dumped its UK customer base, and I don't like relying on a piece of ever-ageing software to run my finances - 

Me neither - I've transferred 14 year's worth ( 7.8Mb file) of data to GnuCash 2.0.5. It went OK, took me  a few days to get the accounts balanced, as I had to manually edit the exchange rate on every £ to euro conversion.

I've decided to persevere with the data on Gnu, in parallel with using Quicken - if the hard drive with Quicken on it fails, and the Quicken install CD decides to stop playing, then it's game over. Also, there may be a data file size limit in Quicken that I don't know about. 

I'm trying to take the view that GnuCash can only improve, I've found it to be the best currently on offer for Linux.

---

### Post by notoriousdbp on 2007-08-20
I use Grisbi for my personal finances and the current build is very stable.  Very user friendly and I found it more usable than Microsoft Money.  It handles QIF's from my bank very well and the transaction scheduler is handy.  I've never used the budgeting tool so can't say what that's like.  My only little gripe is when you select Car as a category you actually get care as a category.
The reporting tool is excellent and completely configurable to your preferences.  It also handles multiple accounts too.

One other alternative I read about is eqonomize which has received good reviews

---

### Post by b5baxter on 2008-01-03
> **Midahed said:**
> .  Having eventually found how to add the London Stock Exchange to the list of (mostly American) markets that are pre-configured...

Mike

How did you get that to work?

---

### Post by Midahed on 2008-01-04
It's a while since I was testing out GnuCash and I've had several power downs since then, so my memory is a bit hazy... :)

As far as I recall, the 'exchange' entry is no more than a label.  It's the suffix to the ticker that tells the system which stock exchange the ticker references.

Just to check this theory out, I set up an exchange called 'fred' and got the correct prices for the UK companies Barclays plc, Alliance and Leicester plc and Marks and Spencer plc using BARC.L. AL.L and MKS.L respectively. From this I concluded that the exchange name itself is indeed just a label - it's the .L in the stock symbol that identifies the London exchange.

Don't ask me why you have to set up an exchange entry at all - I haven't a clue.  It seems completely irrelevant.  Maybe there's a hint somewhere in the documentation, but by that time I couldn't be bothered to look any further - I'd given up on GnuCash as a bad job.

Mike   (who is still using Quicken)

---

