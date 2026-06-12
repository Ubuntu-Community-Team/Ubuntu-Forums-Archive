---
title: "Difficulty logging into exchange server with Thunderbird or Evolution"
date: 2015-07-15
forum: General Help
---

### Post by mfox on 2015-07-15
The issue mainly occurs on my 2009 Mac mini running Ubuntu 15.04, but it also occurs on my PC laptop running Ubuntu 14.04, so I have not specifically listed it in the Mac section. My university moved its mail server to Microsoft about 6 months ago, so it now has to be accessed through outlook.office365. Accessing my mail from my house or office is 100% reliable on any of my Macs running OS X using Outlook or Apple Mail clients. It is also 100% reliable on a PC in my university set up with Ubuntu 14.04 (via Thunderbird or Evolution). In the past it used to be 100% reliable at home from my PC laptop running Ubuntu 14.04 (Thunderbird or Evolution), but it hasn't been for the past month or two. When it is not successful, the mail client starts up all right and shows all my mail folders, but it will not refresh the mail contents, and gives me an error message indicating it cannot connect to the server. The internet is working fine in my house; I can use a browser at the same time that my mail client cannot connect to the server.

The trouble started around the time I set up the Mac mini with Ubuntu 15.04 (Thunderbird and Evolution), but it might have predated that. One difference from the laptop is that on the mini, both mail apps are running with extensions that provide access to my calendars and contacts. Also, I have tried, and eventually removed from the mini, extensions that supposedly provide better support for exchange servers when they weren't 100% reliable either; I'm talking about Exquilla (Thunderbird) and DavMail.

To make matters more complicated, I also have the Geary email client also installed on the mini, and it seems to be 100% reliable. While the solution would seem to be to use Geary only, Geary is pretty basic and doesn't allow one to create local mail folders, which I use in my workflow. One other oddity: accessing my university Outlook exchange mail account with webmail using a link I set up in Chromium is 100% reliable, whereas doing the same in Firefox is only 95% reliable.

This is driving me nuts and delaying my complete move from Mac to Linux. Any suggestions, including how to diagnose the problem, would be appreciated. Incidentally, I did report the problem to IT at my university, but they don't support Linux and couldn't help me because the problem wasn't occurring in Windows or OS X.

---

### Post by SeijiSensei on 2015-07-15
Are you using an add-on like [ExQuilla]("https://addons.mozilla.org/en-us/thunderbird/addon/exquilla-exchange-web-services/")? Or connecting to the Exchange server using IMAP?

---

### Post by mfox on 2015-07-15
I tried ExQuilla originally on my Mac mini installation. It didn't seem to solve the problem so I removed it. But yes, I am connecting with IMAP.

---

### Post by SeijiSensei on 2015-07-15
I'd see if you can enlist the help of an IT support person who can watch the server while you attempt to log in and see what errors it throws.  Without some information from the server, it's going to be hard to diagnose this problem.

---

### Post by mfox on 2015-07-18
That's a thought. My university doesn't support Linux and the IT folks there aren't up on it, but they might be able to watch server traffic while I log on from home. (I never get the problem when I log on from the university.)

---

