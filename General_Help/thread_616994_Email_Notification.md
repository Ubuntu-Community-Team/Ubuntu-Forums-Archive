---
title: "Email Notification"
date: 2007-11-18
forum: General Help
---

### Post by Fanjita101 on 2007-11-18
Hi, I just installed mail notifier from the ubuntu repos and was wondering how to configure it so that:
When I get a new message from my gmail account a pop-up notifies me that I have new mail
2. When I click that pop-up it opens up mozilla thunderbird

Thanks

---

### Post by ugm6hr on 2007-11-19
> **Fanjita101 said:**
> Hi, I just installed mail notifier from the ubuntu repos and was wondering how to configure it so that:
When I get a new message from my gmail account a pop-up notifies me that I have new mail
2. When I click that pop-up it opens up mozilla thunderbird

Thanks

I use this for POP3 rather than Gmail, but it should be similar:

Install Mail Notification ("mail-notification" in Synaptic Package Manager) 
Go to System->Preference->Mail Notification
In Status Icon tab, under "Click Action", select "Launch the mail reader"
In General tab, select Add
Mailbox type: Gmail, and enter username and password for Gmail account
Exit from this by clicking "Close"

This will achieve Q1, and almost Q2 - you have to click on the letter icon in System Tray (top right) to launch Thunderbird (not on the message itself).

---

