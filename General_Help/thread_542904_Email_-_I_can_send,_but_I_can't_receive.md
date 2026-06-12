---
title: "Email - I can send, but I can't receive"
date: 2007-09-04
forum: General Help
---

### Post by lowracer on 2007-09-04
I've just installed Feisty on a new HP dv9410us laptop.  Got the wireless working and it looks good.  Just one problem.  No matter if I use Evolution or Thunderbird, when I go to send email, it sends fine.  When I ask it to receive, it doesn't receive any email.   I'm using the exact same server names and account settings as on an old G4 iBook through the same router, so it can't be a router issue.

What could be happening?  I've googled the heck out of this and can't find the same issue.  I'm thinking there must be something set up wrong in the new ubuntu install.  It's maddening because setting up email is about the easiest thing in the world to do, especially compared to what I just had to go through to get the broadcom wireless chip to work.

For the record I'm trying to access pop-server.san.rr.com and smtp-server.san.rr.com.  I can ping both just fine.

Thanks,
-Mark

---

### Post by thelocust on 2007-09-04
Probably a stupid question but did you check the security settings (do you need to be using SSL?):confused:

---

### Post by reckless2k2 on 2007-09-04
i'm just putting it up there about any firewall business on your box as well. i don't know if you're using a firewall on the ubuntu box that might be blocking incoming.

---

### Post by lowracer on 2007-09-04
> **reckless2k2 said:**
> i'm just putting it up there about any firewall business on your box as well. i don't know if you're using a firewall on the ubuntu box that might be blocking incoming.

Thanks for the responses, and there are no stupid questions...  There's no SSL required for this account, and I've double-checked all the settings are identical to the mac box that is working send/receive.

Is there a firewall that comes up by default in ubuntu Feisty?  Because I didn't do anything to enable one or install one.  I've installed Ubuntu on at least 4 widely different systems now and have not encountered this problem before...

---

### Post by thelocust on 2007-09-04
Yes Ubuntu comes with a built in firewall. There is a GUI for it called Firestarter. You can install that, open it and disable it and that will open all ports. Then try to receive mail, if that doesn't work then you can at least rule out the firewall (on that computer)

---

### Post by lowracer on 2007-09-04
OK thanks, I've loaded Firestarter and have disabled the firewall.  The email receive problem persists...

Edit to add...  The plot thickens.  I added another san.rr.com email account to Evolution and it is able to receive.   This could be a roadrunner issue.

---

### Post by thelocust on 2007-09-04
You can check your connection settings in thunderbird. Whats the exact error it give you? Did you try turning it off and on, haha sorry I'm all out of ideas. Strange problem.

---

### Post by Irony on 2007-09-04
In Evolution if you go to;

Edit > Preferences > Mail Accounts > Edit > Receiving E-mail

You can edit this for receiving.

---

### Post by lowracer on 2007-09-04
> **thelocust said:**
> You can check your connection settings in thunderbird. Whats the exact error it give you? Did you try turning it off and on, haha sorry I'm all out of ideas. Strange problem.

There is no error message at all.  It appears to connect to the pop-server normally.  There is just no received email.

---

### Post by lowracer on 2007-09-04
> **Irony said:**
> In Evolution if you go to;

Edit > Preferences > Mail Accounts > Edit > Receiving E-mail

You can edit this for receiving.

Thanks for the tip.  I've been all over that tab, still haven't found the right setting that will bring in the email.

---

### Post by amadeus266 on 2007-09-04
Perhaps the mailbox you are trying to receive from is empty? I know it seems obvious, but... Can you access that account online with firefox and verify that there is indeed a message for you to download?

---

### Post by caricc on 2007-09-04
check with your isp and have them open port 25.  I had mine at home do this and it works just fine now.

---

### Post by lowracer on 2007-09-04
Definitely looking like a roadrunner problem.  Just created a brand new sub-account in roadrunner, and it sends/receives just fine.

---

### Post by caricc on 2007-09-04
Time Warner/Roadrunner do block port 25. You may have to beat up ](*,)] on their tech support to get it done though.

---

### Post by lowracer on 2007-09-04
OK you're not going to believe this.  I told my wife (it's her account the one with the receiving problem) about the issue, and she said "it works fine on my Mac," and then I told her all I tried with the new accounts and it being received over here and all, and how I could send email and it would show up on webmail for the other accounts but not hers, and she told me that she has all her messages forwarded to her gmail account.  

So I checked in her roadrunner webmail account and sure enough, they're all being forwarded to her gmail account, which is where they were coming from on the mac.  Her mac was checking both the roadrunner account and her gmail account, and dumping them all in the same bin.

So I removed that "forward" instruction from her webmail account...  And now it works.  I can receive her email here on her new ubuntu laptop.

Argh.

It's been one of those days.  Thanks for all the help.  :)

---

### Post by wireddad on 2007-09-04
Doesn't that drive you crazy?

---

### Post by caricc on 2007-09-04
I know I'll get in trouble for this...BUT....it takes a wife....

---

