---
title: "GNUCash or a Quicken equivalent"
date: 2006-11-14
forum: General Help
---

### Post by jhmacss on 2006-11-14
What version of GNUCash works?  If not is there a Quicken equivalent?

---

### Post by Buffalo Soldier on 2006-11-14
GnuCash version 2.0.1
[Grisbi](http://www.grisbi.org/) version 0.5.8

---

### Post by skirkpatrick on 2006-11-14
If you don't mind paying for a piece of software (a one-time $30 US fee), I've been very happy using [Moneydance](http://moneydance.com/).  It's been a very smooth transition from Quicken for me.

---

### Post by mark2741 on 2006-11-14
If you're looking for something with DirectConnect/Online banking capability then your choices are extremely limited. Basically your choice right now is MoneyDance. GnuCash supports it via aqBanking but as you'll see if you do a forum search, no one has been able to get it installed and working on Ubuntu (either that or they haven't responded to the numerous pleas for help over the past few months).

Personal finance is the one killer app that I haven't been able to find on linux, and I've tried just about all of them. I like things simple but also without bugs and a simple to use user interface. Most folks seems to love either Grisbi or KmyMoney2, but personally I found them both disappointing. MoneyDance is cool (but not free) but it had a difficult time with my imported transactions and I got lots of doubling and overall just not satisfied enough with the demo to pay for it. 

About 6 months ago I gave up looking and went to an openoffice spreadsheet in conjunction with my bank's online billpaying service. I don't care to track every transaction - for my purposes it is tracking/paying bills that I need to use software to help with. The spreadsheet works fine but last week I took a look at JGnash and so far it is the best of the bunch by far. The user interface is clean and simple and immediately intuitive.

---

### Post by dcstar on 2006-11-15
> **skirkpatrick said:**
> If you don't mind paying for a piece of software (a one-time $30 US fee), I've been very happy using [Moneydance](http://moneydance.com/).  It's been a very smooth transition from Quicken for me.

Me too, not as sophisticated as Quicken but I've been more than satisfied with Moneydance for over 12 months now.

It has the bonus that you can also run it on multiple platforms because it is based on Java.

---

### Post by SnTholiday on 2006-11-15
I see several people use Moneydance with Ubuntu, but how did you get it installed? I can start the installer running, but I do not have "permission" to install it. Can anyone who successfully installed Moneydance tell me how they did it?

---

### Post by mark2741 on 2006-11-15
I'm no expert but I would assume the following might work at the terminal:

sudo chmod 775 moneydance.bin

change 'moneydance.bin' to whatever the filename really is. That will give you permission. Then follow whatever directions they give you from there.

> **SnTholiday said:**
> I see several people use Moneydance with Ubuntu, but how did you get it installed? I can start the installer running, but I do not have "permission" to install it. Can anyone who successfully installed Moneydance tell me how they did it?

---

### Post by lazyart on 2006-11-15
Dunno... it installed cleanly and effortlessly for me.  Did you try sudo when you installed it?

---

### Post by jeffreyldavidson on 2006-11-17
> **SnTholiday said:**
> I see several people use Moneydance with Ubuntu, but how did you get it installed? I can start the installer running, but I do not have "permission" to install it. Can anyone who successfully installed Moneydance tell me how they did it?

How I installed it was to make sure and download the version with Java bundled. I downloaded it to my desktop. Then I went to the file properties and selected the box to make it executabel. Afterward all I had to do was click on the file and it installed...I did have to install into my home folder.

---

### Post by 900i on 2006-11-17
Google for Homebank thats another one to try, I think I located a .deb package eventually.

---

### Post by mark2741 on 2006-11-17
Wanted to followup my original posting that I now, after only a few days, completely disagree with : )

Although I think JGnash has the cleanest user interface and is fairly easy to use, it's kind of slow and at times uses up all of my processor (per the system monitor/top) and freezes my machine. Not to mention I'm at the point where, after having used Quicken/MS Money for a few years and having online transaction download/billpay with the click of a button, I just need that. Otherwise for my simple needs I may as well just use a spreadsheet like I've been doing. 

So JGnash is off my list (though I'd still use it over Grisbi and Kmymoney and GNucash). So I tried MoneyDance again and gotta say - it's very good. Works well and is easy to use and has some nice features. I'm on the fence about forking over $30 as I'm so used to not having to pay for software but if after another week it continues to work like it's been working the past couple of days for me then I will do it. Main reason is the online banking/direct connect feature. If it wasn't for that I'd just stick with a spreadsheet and my bank's website. Of course, once I plunk down the $30 I'm sure someone will have finally figured out how to get online banking working with gnucash on ubunut!!!

---

### Post by skirkpatrick on 2006-11-19
Well, I've been using Moneydance for over a year now and and very happy with the $30 I paid.  It's not liking forking over $30 every year for Quicken.  I found that running it under Windows to do the Quicken import was better than trying to import to MD in Linux.  Don't know why.  But it was nice running the Windows and the Linux version on the same dataset back when I was first converting wholly to Linux.

---

