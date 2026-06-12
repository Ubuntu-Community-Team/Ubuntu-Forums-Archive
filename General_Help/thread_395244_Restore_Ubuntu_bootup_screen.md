---
title: "Restore Ubuntu bootup screen"
date: 2007-03-27
forum: General Help
---

### Post by omega13lives on 2007-03-27
Just to clarify: my Grub menu works fine, and the usplash login and logout screens work fine, showing GDM as default.  However, when I select Linux from the Grub menu the boot screen (with all the Ok, Ok, Ok....) shows Kubuntu and is blue.  How can I get it back the the brown Ubuntu screen?  tx

---

### Post by aysiu on 2007-03-28
This will help you:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

---

### Post by omega13lives on 2007-03-28
No, no, no, NO!  Please read the post.  I have no problem with the usplash screen, that is fixed.  The issue is with the boot screen BEFORE the usplash login screen.  Does anyone know how to fix THAT?

Also how can I change the size or resolution of my usplash screen?  It's to high.  tx

---

### Post by aysiu on 2007-03-28
Usplash *is* the screen before the login screen.

The Grub menu appears when you first boot up.
Then you select something to boot.
While all the boot messages fly by, **that**'s the usplash.
After it finishes booting up, you get the login screen.

---

### Post by omega13lives on 2007-03-28
I used the commands (I think) to replace the usplash screens and it replaced the login and shut down screens, but not the bootup.  what do I have to do, to fix that?  Or what file can I edit?

---

### Post by aysiu on 2007-03-28
I still think we're getting a little terminology confusion here. The login and shut down screens are what I consider "bootup."

I'm going to attach a couple of screenshots in the next posts. Can you tell me which of these it is? Or if it's something else entirely?

---

### Post by aysiu on 2007-03-28
Let's call this GDM. Is this what you're talking about?

---

### Post by aysiu on 2007-03-28
Let's call this Usplash. Is this what you're talking about?

---

### Post by aysiu on 2007-03-28
Let's call this the regular splash.

---

### Post by aysiu on 2007-03-28
Let's call this Grub.

---

### Post by aysiu on 2007-03-28
Okay. So now that we have all those screenshots... what are you trying to fix? Is it Grub? Usplash? GDM? or the regular splash? Or something else entirely?

---

### Post by omega13lives on 2007-03-28
Yes, what you list as the usplash is the screen that shows Kubuntu and blue text on mine.  I thought what you call the GDM was the usplash, so apparently I don't have it restored correctly.  Unfortunately, I can't test anything until I get home later today.  Do I have to reinstall the usplash or use the reconfigure command (I saw somewhere)?

If you're willing I have a few more questions:
Do you know how I can change the resolution of the GDM login screen?

Do you use KDE?

Another problem is, my investment web site creates a (.xls) spreadsheet for download based on a tabular display which normally opens in Excel. However, when I try to download the link in Linux using Firefox the open office program says it will open it in the spreadsheet application but then opens it in the write application as a document, not a spreadsheet.

Sorry, if I was a little (insert adjective here) before, but I keep getting other replies from people who say "I don't know how to do that but ...." which of course, does me no good at all.  tx

---

### Post by aysiu on 2007-03-28
> **omega13lives said:**
> Yes, what you list as the usplash is the screen that shows Kubuntu and blue text on mine.  I thought what you call the GDM was the usplash, so apparently I don't have it restored correctly.  Unfortunately, I can't test anything until I get home later today.  Do I have to reinstall the usplash or use the reconfigure command (I saw somewhere)? You're supposed to follow the directions in this link I gave you earlier:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

That's the only solution I know. If that doesn't work, I don't know what else does.

> 
Do you know how I can change the resolution of the GDM login screen? No. I could probably dig up a thread or two on it, though.

> 
Do you use KDE? Not any more. I use IceWM now. But if you have KDE questions, feel free to ask them. I or someone else will probably be able to answer them.

> Another problem is, my investment web site creates a (.xls) spreadsheet for download based on a tabular display which normally opens in Excel. However, when I try to download the link in Linux using Firefox the open office program says it will open it in the spreadsheet application but then opens it in the write application as a document, not a spreadsheet. Have you tried launching *oocalc* and then opening the spreadsheet from withihn Calc?

---

