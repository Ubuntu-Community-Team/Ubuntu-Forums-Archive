---
title: "GnuCash frustration"
date: 2014-11-08
forum: General Help
---

### Post by kellyvotrenom on 2014-11-08
Is there A) any way to get help with GnuCash or B) can any one suggest a better alternative.?

I was initially pleased with GnuCash but now am having mulitple problems with categorizing transactions and reconciliations.  I have posted twice to the maling list and have received no response other than the post was waiting to be reviewed by the moderator. I have done multiple searches but found no applicable posts.

I was using Moneydance but it's got too many bells and whistles for my use.  I liked the basic functions of GnuCash but it has stopped working correctly for me.  I need to import downloaded transactions and keep track for tax info.  Also, I am not interested in web based/ cloud based programs.

Thanks

Mark Springer

---

### Post by rbmorse on 2014-11-08
I used Gnucash for more than five years and will admit that more than any other application I've used it insists on doing things its own way. No application in the open-source universe is screaming louder for a bottom-up re-architecture/re-write than Gnucash, and this is not a criticism of the current crop of maintainers who make heroic efforts keeping what they have to work with going as well as it does. 

That said, it's hard to suggest alternatives without knowing more about your needs. Are you a small business or do you just need an electric checkbook?

---

### Post by ajgreeny on 2014-11-08
I tried using gnucash a long time ago, but it quickly became obvious to me that it was both too complicated and demanding for my needs, so I gave up and searched for an alternative.

Try kmymoney2 which is a KDE application, but I use it in Xubuntu without a problem; it just looks different to almost every other application I use, but does all I want and need.

If I compare it with an other Windows application I would say it is nearest to Quicken, which I used for many years in Windows 98, and then XP.

I use it only for personal finances, nothing to do with business or tax affairs, but as far as I am aware, it can do that as well

---

### Post by kellyvotrenom on 2014-11-09
Thanks for your responses.

I am basically a sole proprietor/ small business.  I use a financial program just to keep track of my bank accounts and for accruing tax related info.

kmymoney won't work for me because of it's KDE dependencies - which I prefer not to load on my aging computer - but thanks for the suggestion.  GnuCash would be great if it worked and there was support or help available for it.

Just to give you an idea of my problems: the Importer doesn't categorize imported tranactions, it skips certain transactions and really screws up transactions that exist in the register.  At this point I am manually entering all my transactions from my bank statements. In addition, it does something to the files that prevents them from being backed up. I tried to use Lucky Backup to backup the files but it seems to be having problems with the newly changed files.  So I have reverted to deleting the previous backup file and then copying the newly changed files it to the backup drive once I finish the work I am doing.

I didn't like Moneydance because of the extra steps it takes to enter and reconcile transactions and it often skipped or missed downloaded transactions, which added time to reconciling. I liked the more 'manual' method that I seemed to be getting from GnuCash, but automatically recognizing and categorizing transactions would be nice.

So any other ideas or suggestions would be greatly appreciated.  Again, if I could get some modicum of support from the GnuCash team, that would go a long way.

Mark Springer
industrial arts

---

### Post by amanchesterman on 2014-11-10
I'm not sure that I can help you much, though I use GnuCash regularly to keep my personal financial records - a couple of bank accounts, a savings account and a few shares.

Importing data
I agree that the way the import process works is sometimes unhelpful. My bank provides download data in OFX format and I have found that the safest way to proceed is to enter transactions in GnuCash manually and then use the import wizard merely to reconcile them with the bank. If the import wizard offers to 'update' a transaction in the GnuCash register I never choose that option since, as you say, it overwrites and messes up the information I have entered already: I only allow it to confirm that the data I have entered already is correct.
In case manually entering data sounds tedious, I have found it isn't because:
1) many of my transactions are regular standing orders / direct debits and are entered automatically;
2) GnuCash remembers previous payers/payees and the appropriate categories, so they can be entered instantly with the Tab and Enter keys, rather than typing in fresh data each time.
So it takes me about five minutes each week to update and reconcile my data, and because it's all categorised I can then produce all the reports and analyses I need.

Downloading data
I have occasionally found that the OFX file I import from my bank does not include all the transactions that are shown on my bank statement. I don't know why that is, but it's clearly not the fault of GnuCash. If you are finding that GnuCash omits some transactions when importing data you may want to check that the downloaded file is OK: a simple text editor should let you view the content.

Backing up
I have no idea why your version of GnuCash won't allow your data file to be backed up -- or even how it manages to prevent that. In my case, GnuCash is set to keep all its files in a folder I have called 'Finances' (I'm very imaginative!). In the same folder I also keep other financial records, reports etc. Once a week I copy the whole folder to external data storage and I have never had any problem doing so. Are you sure that you have closed GnuCash entirely before you try to back up? Does the folder on your machine have appropriate permissions? I use a very simple backup program called ukopp, which is available from the Software Center: all it does is create a backup copy, i.e. there is no compression, encryption or anything like that.

I realise of course that your needs may be way more complex than mine, so my way of doing things may be of little use to you; and I agree with you and others that GnuCash is far from perfect. But I have tried several personal finance programs in the Software Center and have found it the best so far.

---

### Post by kellyvotrenom on 2014-11-10
I finally discovered a post somewhere that finally helped.  I don't know how I was making it work before but I found that makinbg changes in the importer window will make GC remember a transaction; I was able to reconcile a few months with little problems this time around.

 To make it brief:  
- I download and save my transactions from my bank as a QFX file and import them using the "File - Import - Import OFX/QFX".
 - Double clicking any transactions allows it to be re-categorized and it will generally be remembered next time.
 - Any item that shows up in RED has to be added by clicking the first column box (A) - I don't know why GnuCash decides to skip these transactions but it's wrong.  (All my transactions are in the QFX file - GC seems to want to skip some, Moneydance just ignored certain items) However, the Cash Transfers that I make between accounts seem to be recognized OK.  This prevents them from being double entered, which opens a whole 'nother can of worms.  

Mostly, I found I have to be very diligent while importing transactions; getting the bank transactions imported properly into the register does save a lot of time.  But I agree with you that doing most things manually helps prevent problems. I also agree that of all my alternatives, GnuCash is the least bad.  Again, like any program sometimes you have to learn to work within it's parameters, so learning about editing in the importer window helped me a lot.  I will say that the report generator works pretty well once you figure it out, so tax time wasn't so brutal this year.  So not to beat up on GnuCash too badly, in my experience it beats Quicken and Moneydance, I just wish that there was better support for it.

The back up problems are probably another issue not related to GC, I will check out the program you recommended.

 Thanks to everyone who replied, much appreciated.

---

### Post by bapoumba on 2014-11-10
Just to add that I used to use grisbi. It's in the repos.
[http://www.grisbi.org/](http://www.grisbi.org/)
[https://launchpad.net/ubuntu/+source/grisbi](https://launchpad.net/ubuntu/+source/grisbi)
Easy to use, and was adapted to a small business.

---

