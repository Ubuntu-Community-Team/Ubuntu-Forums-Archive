---
title: "Evolution can't set up Gmail IMAP account"
date: 2013-06-02
forum: General Help
---

### Post by simon1986 on 2013-06-02
Hey folks,

The last days, I desperately tried to set up an gmail account (IMAP) in Evolution.

My distro is Ubuntu 12.10 with Gnome Shell ("Ubuntu Gnome") and I installed Evolution 3.6.2. At the moment, I'm using Thunderbird without any problems, but I'd like to try Evolution.

When I start Evolution, the Evolution Account Assistant starts up and I can configure my account without any problems. I'm using these instructions: [http://wazem.blogspot.de/2007/10/hot-to-configure-imap-on-evolution-and.html](http://wazem.blogspot.de/2007/10/hot-to-configure-imap-on-evolution-and.html)
I also have IMAP activated in Gmail (obviously, since I'm already using IMAP successfully in Thunderbird). When the Account Assistant is finished, Evolution starts, but there's no account created. Only "on this computer". When I restart Evolution, the Account Assistant pops up again and I can create my account again, which again leads to no result. So my account is not only not working, it's not even created.

Can anybody help me with this? What am I doing wrong?

Thanks a lot,
Simon

---

### Post by Charlotte18 on 2013-06-02
Do you have the folders called .evolution and .gnome2_private/Evolution in your home folder? Show the hidden files and see if these folders are there. Then, check the .gnome2_private/Evolution folder to see if any info about your gmail account is being stored.

---

### Post by Frogs Hair on 2013-06-02
Check for more current instructions (2007) . I encountered this problem on a different mail client and the sever information provided with the instruction was outdated so no account was created.

---

### Post by simon1986 on 2013-06-02
Thank you for you answers.

@charlotte: No there's nothing happening in these folders, they're empty. 

@Frogs Hair: I've noticed that the instructions are old, but there are several comments on that page, stating that they still work. But I'll try it with the latest instructions.

---

### Post by simon1986 on 2013-06-02
Hey, 

I fixed it. It's a reported bug: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1049028](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1049028)

When setting up the account, I had to uncheck the options "Add Google Calender" and "Add Google Contacts". It's working now. 

Simon

---

