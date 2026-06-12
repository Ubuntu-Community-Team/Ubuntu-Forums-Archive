---
title: "Evolution Problem"
date: 2008-03-21
forum: General Help
---

### Post by cartisdm on 2008-03-21
Whenever I open Evolution rather than just simply check for new messages I get this little window (see attached).  All I have to do it hit cancel and it goes away and I can simply check my messages without any problem.  It never comes up again until I close evolution and open it again.

It's just kind of annoying that's all, any suggestions?

---

### Post by richard356 on 2008-03-21
hi if you havent tryed it already you can go onto evolution go onto the edit tab and click on the preferences option.Choose the account your using ~> Edit tab ~> Recieving E-mail ~> Authentication Type ~> Password ~> remember password 
This might fix it

---

### Post by cartisdm on 2008-03-21
unfortunately it's already checked.  The window that's listed in the screenshot I posted is already filled out with info.  All I have to do is hit cancel I don't have to type my password or anything

---

### Post by dcstar on 2008-03-21
> **cartisdm said:**
> unfortunately it's already checked.  The window that's listed in the screenshot I posted is already filled out with info.  All I have to do is hit cancel I don't have to type my password or anything

I you hit cancel then it is not checking that account - if keeps appearing because **you** have your system set up to check that account.

The error message clearly says "Error sending username", fix it and the message should stop appearing.

---

### Post by cartisdm on 2008-03-22
> **dcstar said:**
> I you hit cancel then it is not checking that account - if keeps appearing because **you** have your system set up to check that account.

The error message clearly says "Error sending username", fix it and the message should stop appearing.

Not quite sure if I get what you mean.  I verified the account information and it's set up how it should be as far as I can tell.  I only have one account setup.

---

### Post by dcstar on 2008-03-22
> **cartisdm said:**
> Not quite sure if I get what you mean.  I verified the account information and it's set up how it should be as far as I can tell.  I only have one account setup.

So instead of hitting Cancel, what happens when you hit OK?

---

### Post by cartisdm on 2008-03-24
> **dcstar said:**
> So instead of hitting Cancel, what happens when you hit OK?

It just goes away and reappears instantly

---

### Post by dcstar on 2008-03-24
> **cartisdm said:**
> It just goes away and reappears instantly

Then you have incorrect settings for that account.

---

### Post by stenka on 2008-03-29
Just got the same problem. It seems to be a bug rather than a misconfiguration.

---

### Post by GrouchoMarx on 2008-04-03
I am also seeing this behavior. My accounts are properly configured and had worked without incident for a long time. Then spontaneously this started happening. I have gone through the configuration and can't find any changes.

This behavior seems to depend on the folder that is selected at startup. Depending on what folder you have selected when evolution starts, the prompt either appears or it doesn't. I have no imap accounts, only pop accounts.

If anyone has any idea why this is happening that would be great as it's really irritating.

---

### Post by cartisdm on 2008-04-03
Well, I'm glad to see I'm not the only one experiencing problems.  Too bad nobody has a fix yet:-/

---

### Post by GrouchoMarx on 2008-04-03
Ok, I found a solution to the problem in Launchpad bug report [#140450]("https://bugs.launchpad.net/evolution/+bug/140460").

The problem is caused when the meta-data of a particular folder somehow gets corrupted. First identify which folder is causing the problem. Not all folders that trigger the prompt may be broken: parent folders may seem broken if they have broken children. Once you've identified the folder that is causing the problem, move all your email into a separate temporary folder. Then find the problem folder's meta data under ~/.evolution/mail/local/ and delete (or just move elsewhere) those fileswhich begin with the broken folder's name: FOLDER, FOLDER.cmeta, FOLDER.ev-summary, FOLDER.ev-summary-meta, FOLDER.ibex.index, FOLDER.ibex.index.data. Make sure not to delete your temporary folder with all your email by accident, and make sure to backup any sub-directories if you are deleting a parent folder. Then you can restart evolution, and either rename your temporary folder to the original, or copy back all your email into a replacement.

Hope this was clear.

---

### Post by dndrich on 2008-04-06
I had the same problem, and I followed the instructions to fix it.  It is a very simple fix, and it works perfectly.  Now I don't get the annoying remember password window!  All is well for me now.

---

### Post by cartisdm on 2008-04-07
Dude....awesome.  That's been annoying the crap out of me forever.  Good work.

---

