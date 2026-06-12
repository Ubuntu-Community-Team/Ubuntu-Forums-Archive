---
title: "May 2007 - Still nothing to replace Quickbooks Pro ?"
date: 2007-05-09
forum: General Help
---

### Post by Xeor on 2007-05-09
I want to get rid of Windows for good (mainly for viruses and a bit for phylosophy).

On my personal computer I use Kubuntu and thanks to the speed and software packages that the community is offering me, I could not possibly think coming back on Windows anymore (only sometimes for Photoshop CS2, I swap quickly my hard-drive --> please don't tell me about TheGimp since I know about it and sometimes TheGimp just don't make it for a professional photographer);

The ONLY thing really bugging me to move the whole mid-size company on Linux is Quickbooks Pro 2007.

I am thinking that in 2007 they must be a way to replace it; An accouting software that can support multiple currencies, web based or not, with VAT support, that doesn't cost £5000.

Because of Quickbooks Pro 2007 I cannot ditch Windows Office, Internet Explorer and Windows (with McAfee) to make the package Firefox, OpenOffice, Linux standard in our company as well as other businesses.

To be honest, I don't expect many positive reply for this thread :-P

---

### Post by AlanRogers on 2007-05-09
Have you tried installing Internet Explorer and QuickBooks Pro on Ubuntu using Wine? I haven't but I'm interested because I find myself in a similar, if smaller, boat. You can't just install QuickBooks because it's heavily reliant on Internet Explorer, so you'll almost certainly have to install this as well. 

Alternatively, how about just having one machine on the network running QuickBooks Pro, and access it using Remote Desktop? Sorry, but I don't know what the Ubuntu equivalent is but I know there is one.

If you need a multiple user environment, have a look at a Citrix/Terminal Services server. One of these will almost certainly be cheaper and easier to maintain than many Windows Desktops, if you're looking to migrate the business to Ubuntu.

---

### Post by Xeor on 2007-05-09
Not only Quickbooks relies heavily on IE but it relies equally on Excell and Words so you would have  to install those as well.

That's a lot to install with Wine; And that's why I better stay (against my will) with Windows in this case.

I did try to install Quickbooks with Wine but would you try this when you know how many bugs you already get on a Quickbooks-Windows system? Loose data, loose business.

At best you will have to install Quickbooks on a Windows system and copy the folder and the registry changes to your Linux system because even if you manage to install IE(5 or 6) with Wine, Quickbooks Setup cannot find it.

---

### Post by zhkent on 2007-05-09
I have wine and ie installed. (feisty fawn)
I'm pretty new to this and can't get quickbooks to install. 

Kent

---

### Post by AlanRogers on 2007-05-09
> **Xeor said:**
> Not only Quickbooks relies heavily on IE but it relies equally on Excell and Words so you would have  to install those as well. That's a lot to install with Wine; And that's why I better stay (against my will) with Windows in this case.Okay, I wasn't aware of the reliance on MS Office applications as well. That would be better much a show-stopper because, between the four applications mentioned, the files go just about everywhere!

> **Xeor said:**
>  I did try to install Quickbooks with Wine but would you try this when you know how many bugs you already get on a Quickbooks-Windows system? Loose data, loose business. At best you will have to install Quickbooks on a Windows system and copy the folder and the registry changes to your Linux system because even if you manage to install IE(5 or 6) with Wine, Quickbooks Setup cannot find it.Another good point. It's looking like a Terminal Services Server for you to be able to go 100% Linux on the desktop then.:(

---

### Post by Xeor on 2007-05-09
I want to ditch Quickbooks now for the sake that they are bothering me like this ):P

---

### Post by AlanRogers on 2007-05-09
According to a quick Google search, there are alleged equivalents of QuickBooks for Linux. I say alleged because I haven't used any of them and happen to like the functionality and ease of use of QuickBooks.

Have a look at the following:
[LIST=1]
[*][SIZE=-1][GnuCash]("http://gnucash.org/")[/SIZE]
[*][SIZE=-1][Quasar]("http://www.linuxcanada.com/")[/SIZE]
[*][SIZE=-1][SQL-Ledger]("http://www.sql-ledger.org/")[/SIZE]
[*][SIZE=-1][AccPac]("http://www.accpac.com/")[/SIZE][/LIST][SIZE=-1]I have at least heard of the first two but can't offer any more than that.
[/SIZE]

---

### Post by 50words on 2007-05-09
Quickbooks != Quicken, and programs like Moneydance, GnuCash, etc., are more like Quicken.

I am in the same boat as you. I am looking at AppGen ([www.appgen.com)](www.appgen.com)), which is reportedly a pretty powerful financial package. Free trial available, and the full version isn't too expensive ($60 for Linux, or so).

---

### Post by Xeor on 2007-05-09
I did have look at those:

   1. GnuCash
   2. Quasar
   3. SQL-Ledger
   4. AccPac

Many of those, when working bug free, are very USA minded rather than international; This means that you can forget about multi-currencies but more often, you can forget about VAT support and Payroll.

---

### Post by zhkent on 2007-05-09
Wonder if any of these can open and preferrably export the qbw file extension quickbooks uses?
I've tried gnucash and it won't open them.

Kent

---

### Post by ChadMMc on 2007-05-09
You could also look into KMyMoney (it is in the repositories).

---

### Post by Xeor on 2007-05-09
"Wonder if any of these can open and preferrably export the qbw file extension quickbooks uses? I've tried gnucash and it won't open them."

I even don't mind inputting the data again. I can wait up to the new financial year to do the move if any and it will be far easier then (That's leave me up to September to look around).

---

### Post by Xeor on 2007-05-09
I have no doubt that Kmymoney is good for personal finances but in no way will it replace Quickbooks Pro for a business accounting software.

---

### Post by Xeor on 2007-05-09
[LedgerSMB]("http://www.ledgersmb.org/") seems promising

---

### Post by Xeor on 2007-05-09
> **50words said:**
> Quickbooks != Quicken, and programs like Moneydance, GnuCash, etc., are more like Quicken.

I am in the same boat as you. I am looking at AppGen ([www.appgen.com)](www.appgen.com)), which is reportedly a pretty powerful financial package. Free trial available, and the full version isn't too expensive ($60 for Linux, or so).

[There is a man there]("http://specialreports.linux.com/article.pl?sid=06/11/06/0850235&tid=135&tid=13") who doesn't seems to like AppGen to much; I don't know why though.

---

### Post by bbarrons on 2007-05-09
if you have the resources on your computer than I would install virtualbox and use that to install a copy windows xp. you can then run it in a window on linux. xp thinks it is running standalone and runs better than if you run it on its own pc. I would suggest you have at least a gig of memory because xp will want at least 256 but runs better with 512. This solution for me was far better than wine or crossover or any of the other emulators.... try it.... it is free...

---

### Post by jrjazzman on 2007-05-09
I'm in the same boat.  Have you tried the Quickbooks Online edition?  I'm really moving towards SaaS for lots of our business apps.  I currently still run QuickBooks in a Windows VM, but will be switching to NetSuite shortly.

jeremy

---

### Post by deba on 2007-05-09
A good accounts package replacement for quickbooks is program called Accountz. They have Personal & Business Edition & it is Cross platform, so you get Windows, Mac & Linux version for one price!. I have moved from Quick Books Pro 2005 to Business Accountz on a Mac for my business and have not looked back! :)  check them out at [www.accountz.com](www.accountz.com)

---

### Post by loserboy on 2007-05-09
I played with Mybooks by appgen, and it seems great, I don't know why anyone wouldnt like it.  Try the demo yourself I think you'll see it's pretty sweet

---

### Post by Xeor on 2007-05-09
It seems you found something great Deba;
Business Accountz has great ratings on Amazon.co.uk.

There are saying on their website that Accountz it's great for service based businesses; I suppose I have to understand it isn't great for product based businesses ?

---

### Post by Xeor on 2007-05-09
This one looks promising too even if it's more in the Sage's range of price:
Amazon.co.uk:"[Hansa First Office Professional Advanced]("http://www.amazon.co.uk/Hansa-First-Office-Professional-Advanced/dp/B000EVPT1K")"

[http://www.hansafinancials.com/]("http://www.hansafinancials.com/")

---

### Post by Xeor on 2007-05-09
webERP is open source and work on Lamp server with stock control (lacking in GNUcash)
They seem to have good support with this latest release made on 12 Jan 2007,

You can log on a demo site to look at it : [http://www.weberp.org]("http://www.weberp.org")

---

### Post by Hannah on 2007-05-11
Hi all,

I work for Accountz.com just thought I would reply to Xeor. We do have a product based business package coming out in July, called Business Accountz Professional. This package will have the added features of a Stock and Supplier databases.


P.S. Thanks for the shout out deba :)

---

### Post by Xeor on 2007-05-11
Great, can't wait to see if there is finally something on Linux that will match Quickbooks Pro 2006  :popcorn:

---

### Post by eugenevdm on 2007-05-14
I would like to add that I cannot migrate my company with 15 employees to Ubuntu because we are reliant on Quickbooks.

Come on you linux gurus get a decent GUI / Web based multi-user, multi-currency, international bookkeeping system going with an open-source database backend going, you'll make a killing.

:popcorn:

---

### Post by telengard on 2007-06-10
> **Hannah said:**
> Hi all,

I work for Accountz.com just thought I would reply to Xeor. We do have a product based business package coming out in July, called Business Accountz Professional. This package will have the added features of a Stock and Supplier databases.


P.S. Thanks for the shout out deba :)

I'm also looking for a Quickbooks replacement but I'm not sure I want to trust 5 years of financial transactions to "Accountz".  Any particular reason for using pseudo-l33t speak for a professional business program?  Just wondering...

~telengard

---

### Post by LakeWind on 2007-06-10
> **Xeor said:**
> I did have look at those:

   1. GnuCash
   2. Quasar
   3. SQL-Ledger
   4. AccPac

Many of those, when working bug free, are very USA minded rather than international; This means that you can forget about multi-currencies but more often, you can forget about VAT support and Payroll.

That may be true of the others but SQL-Ledger works internationally including foreign currencies, VAT support, COA etc... I've been using SQL-Ledger for my business for about 1 1/2 years now with much success. It can be a pain to get up and running at first, but once it's up it runs nicely.There is no payroll module however.

It's a free, multi-user, web based interface and relies on postgresql, apache, perl and latex. Check out their website here:

[http://www.sql-ledger.org/](http://www.sql-ledger.org/)

There is also a very active support mailing list if you run into problems. The folks on the list are very friendly and helpful!

---

### Post by moschops on 2007-06-29
> **Xeor said:**
> Not only Quickbooks relies heavily on IE but it relies equally on Excell and Words so you would have  to install those as well.

That's a lot to install with Wine; And that's why I better stay (against my will) with Windows in this case.

I did try to install Quickbooks with Wine but would you try this when you know how many bugs you already get on a Quickbooks-Windows system? Loose data, loose business.

At best you will have to install Quickbooks on a Windows system and copy the folder and the registry changes to your Linux system because even if you manage to install IE(5 or 6) with Wine, Quickbooks Setup cannot find it.

You could consider running VMWare on your Ubuntu machine - I'm browsing this from IE on a virtualized PC on my Ubuntu machine, runs great and I have a full Office 2003 install too (not that I use it much).  Plus VMWare make it really easy now - they have a "converter" that you run on your Windows machine and it turns the entire installation into a virtual installation.  You'll probably need to reactivate when you first run the Windows VM - MS did this for me with no questions asked - but after that you can move it between host machines as you wish.

But I can see this probably wouldn't work well for you if you have a multi-user Quickbooks environment since you probably don't wat to have everyone using a VMWare as well as Ubuntu.  Although why not? You already purchased the Windows licenses so it wont cost you extra and when the VM isn't running it will just get swapped out.  On a dual core machine with 1GB or more of memory you probably wouldn't even notice its impact 99% of the time!

Eventualy Quicken will probably figure it out and port to Linux, they will probably be the last to do so - perhaps after Adobe ports their stuff, but eventually...  in the mean time their answer to platform compatibility IS the web version (which my small biz uses although I know there are many things it can do and its no replacement for the POS versions etc.)

---

### Post by marksgirls on 2007-07-05
I hate to be the bearer of bad news but for the past 2 months my computer tech (who is expert in linux and all things linux) has been trying to find a way we could load and open QB.  it does not work on wine or any of the wine updates.  

Linda Slasberg
A Ubuntu user.

---

### Post by Xeor on 2007-07-20
> **telengard said:**
> I'm also looking for a Quickbooks replacement but I'm not sure I want to trust 5 years of financial transactions to "Accountz".  Any particular reason for using pseudo-l33t speak for a professional business program?  Just wondering...

~telengard

Why not; Accountz has been developed by a very good software development company called Bugless
[http://www.bugless.co.uk/index.html](http://www.bugless.co.uk/index.html)

and also, the reviews speeking about this software seems to be very good.
I love the fact you buy one software and it works on Windows, Mac and Linux (Especially Linux) but I did find something somehow negative -> the fact you need an extra £25 license if you want to run more than one company on it. I hate to feel limited and I love the word unlimited.

Still waiting for the Accounts Business Pro though. Any news? 

Anybody have experience using Accountz?

---

### Post by podfish on 2007-07-24
how about crossover office?  they have modest licensing fees, and I believe quickbooks is on their list of working software.  Support is included in the license price.

---

### Post by cssutto on 2007-07-24
I am a long time Peachtree user and I keep one Windoze machine just to run it.

Appgen is crap.

Try doing a payroll.

Then try to do your withholding 8109.

Then try your state withholding and unemployment tax forms.

It is crap.

CSSJR

---

### Post by justhave on 2007-08-31
I have a small business and have used Quickbooks for years. I recently installed Ubuntu (it is awesome) and vowed never to again use another Microcrap product (except xbox360), but I have the same problem. **NOTHING** can replace Quickbooks, I have looked, and looked, and looked some more. Plus every accountant uses quickbooks, and it is important that files can be accessed often by my accountant. So I guess I will get IEs4linux and signup for quickbooks online service (they have a free trial). Has anyone tried this? Will it work? I know I can't track the inventory as well as QBPRO, but besides that most everything is the same, just stored on Intuit servers and runs off IE, but will it work with Ubuntu? Any help would be appreciated. THANKS!

---

### Post by moschops on 2007-09-04
My business uses Quickbooks online and when I first switched my desktop to Ubuntu about a year ago the browser compatibility problem was an issue for me too.

I found that using IE4Linux did work - I was surprised because they use ActiveX plugin.  Unfortunately it didn't look very nice - flashing of the UI and such - and was slow.  However if you are patient and not fussy it was apparently usable.  I could not comment on if it is working at present since they could easily have changed the ActiveX plugin in some way that it is no longer compatible.  

In the end what I did was used the free VMWare converter product to make my old XP installation into a virtual machine, then use the free VMWare player to run it.  It runs great and all I had to do was call Microsoft to do the activation (you may not have to do it, but so long as it is XP you should have no problem as Microsoft doesn't care about running on VMs except for the Vista Home licenses). 

If you have already trashed your old XP installation then you can still use VMWare Server to create a new VM and install XP on it from scratch using your old Windows lic code.  That is slightly more complicated because putting VMWare server on Ubuntu is slightly more involved - may require some extra downloads and tweaking.  There are guides elsewhere on this forum.

If that works for you then you really have no need to go with QB Online - you can just run your old QB client.

I have filled out the QB request form to ask for QB on Firefox support many, many time - they keep saying they are working on it and will let me know when it is ready, but somehow I think they think it is not worth it.  Building a really solid Web 2.0 app that works like a regular client is hard and also subject to many portability issues across browsers and between versions - those things cause lots of support calls which cost money...   They are basically doing what Apple does - support your software on a single platform - it makes support cheaper and keeps the majority happy. So my bet is they will probably never support Firefox or Linux native.  

I suggest you also investiigate online accounting packages with QB export compatibility.

---

### Post by jungleexplorer on 2008-07-18
I am going to have a look at GnuCash.  I run a small Non-Profit.  I hoping it will serve me needs.  Thanks

---

