---
title: "Thunderbird crashes when viewing an email"
date: 2008-03-10
forum: General Help
---

### Post by gorkau on 2008-03-10
Hi,

My Thunderbird was working fine till last weekend when it started to crash everytime I access the email preview.

1) It downloads all emails correctly.
2) I can see the email listing (subject, from, etc...)
3) No addons installed.
4) I can write emails.

It only crashes when trying to view an email.

I've tried many things:

1) Enter in safe-mode (it also crases).
2) Create a new profile.
3) Reinstall (remove and install).
4) Compact folders.

But the problem persists. It dumps a core (which I can't locate, any help?).

Does anyone have an idea of what the problem can be?

---

### Post by 6205 on 2008-03-10
As far as i know, TB crashes only when skinned. With default theme it should be stable, but will not blend with rest of the icon theme :((((((((((((((((

---

### Post by gorkau on 2008-03-10
Sorry, I forgot that one... I also removed all skins and am using the default but the problem persists.

---

### Post by astrotech226 on 2008-03-10
What process did you use to create a new profile?

---

### Post by ajgreeny on 2008-03-10
Have you tried uninstalling and then reinstalling TB?  I have no idea if it will do anything but it seems worth trying, and even using a different profile to start with, so rename your ~/mozilla-thunderbird folder to ~/mozilla-thunderbird~ and restart the app to see if it will at least work properly.  If it does you can then copy back your mail folders one by one to see if one of them contains a corrupt message which is crashing the program.

---

### Post by 6205 on 2008-03-10
just go back to evo :) [http://ubuntuforums.org/showthread.php?t=719399&highlight=Tangoized+Evolution](http://ubuntuforums.org/showthread.php?t=719399&highlight=Tangoized+Evolution)

---

### Post by gorkau on 2008-03-10
> **astrotech226 said:**
> What process did you use to create a new profile?

> **ajgreeny said:**
> Have you tried uninstalling and then reinstalling TB?  I have no idea if it will do anything but it seems worth trying, and even using a different profile to start with, so rename your ~/mozilla-thunderbird folder to ~/mozilla-thunderbird~ and restart the app to see if it will at least work properly.  If it does you can then copy back your mail folders one by one to see if one of them contains a corrupt message which is crashing the program.

I've tryed reinstalling, deleting the mozilla-thunderbird and creating a new account, creating a new profile with profiler-admin but none of them solves the problem.

Don't think there is any corrupted files as I copied them to another computer (only email folders) and it works ok on the other computer.

---

### Post by astrotech226 on 2008-03-10
> **gorkau said:**
> I've tryed reinstalling, deleting the mozilla-thunderbird and creating a new account, creating a new profile with profiler-admin but none of them solves the problem.

Don't think there is any corrupted files as I copied them to another computer (only email folders) and it works ok on the other computer.

Have you tried a manual download of thunderbird?  Decompress it somewhere like in your home folder and try to run it and see what happens.  If that works, then like you are already suspecting, something is hacked with your install.

---

### Post by desialex on 2008-03-14
Finally I found somebody with the same problem as mine. Again Thunderbird downloads the emails correctly in the "list" panel, but whenever I try to display them as Preview or open in a new window, here's what happens:

- either nothing appears (as if there's no subject, sender or receiver) 
- or the more frustrating case is that Thunderbird displays a text body and sender details of an older e-mail (I believe it's the oldest one in the Inbox) .... imagine you receive a fresh new piece of spam, but when you open it - it turns out to be your very first e-mail in the mail box. And it happens with all new messages I got. 

The first thing I tried was deleting the oldest e-mail (and some more from the same period) but it keeps displaying its content !!! that got me really confused....
Afterwards, I did what **ajgreeny** advised but didn't help. Actually fixed the problem for a while, but right after the first restart, the "bug" was back again. 
I also tried uninstalling, installing and degrading to an older version with Ubuntuzilla, but again - no effect. 

The interesting part is that the problem "affects" just some of my Thunderbird accounts. It tends to happen with the POP3 mails and not with Gmail. RSS feeds also work properly. 

I tested the troubled accounts with Evolution but some error appeared .... not sure what was the problem, but I'm pretty convinced it wasn't the same one. Meantime, the before mentioned accounts are accessible through webmail client and Outlook.

Finally, I don't have any plugins/themes installed.... If somebody comes up with something I haven't tried, I'll be very thankful!

---

### Post by gorkau on 2008-07-03
As I don't have much time to solve this problem and I really need to access my emails what I finally did was to reinstall Ubuntu on my computer. That solved the problem.

I have my /home directory in a separate partition so when I reinstalled I was using exactly the same data and it worked fine (same accounts, configuration, plugins, etc...)

---

