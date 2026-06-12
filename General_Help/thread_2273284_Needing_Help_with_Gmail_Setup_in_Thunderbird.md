---
title: "Needing Help with Gmail Setup in Thunderbird"
date: 2015-04-11
forum: General Help
---

### Post by miranda2 on 2015-04-11
Hello, I searched the forums a bit looking to see if anyone had a solution to my problem but came up empty handed. I'm new to Ubuntu so please bare with me. I was wanting to set-up my Gmail account to Thunderbird but for some reason once I go through the initial set-up steps and after selection POP3 it comes back with an error saying "Configuration could no be verified - is the username or password wrong?" I have made sure (triple checked) that the username and password was correct but still nothing. I have changed my settings to enable POP3 from my Gmail account. 

If anyone could point me into fixing this problem it would be greatly appreciated.

Miranda

---

### Post by amanchesterman on 2015-04-12
Do you have a particular reason for wanting to set up your Gmail as a POP3 account?
Gmail themselves recommend using IMAP: see here [https://support.google.com/mail/troubleshooter/1668960?hl=en](https://support.google.com/mail/troubleshooter/1668960?hl=en) under the heading 'What is the difference between POP and IMAP?'
Personally I have my Gmail account on Thunderbird set up as IMAP. It works flawlessly and as far as I recollect (I've had it for some years now) the initial setup was trouble-free and almost automatic. It also has the advantage that if I access the account from another computer, any changes I make are reflected immediately in  Thunderbird.
So I would suggest that's the way to go, but you may have special reasons for not wanting to use IMAP?

---

### Post by miranda2 on 2015-04-12
> **amanchesterman said:**
> Do you have a particular reason for wanting to set up your Gmail as a POP3 account?
Gmail themselves recommend using IMAP: see here [https://support.google.com/mail/troubleshooter/1668960?hl=en](https://support.google.com/mail/troubleshooter/1668960?hl=en) under the heading 'What is the difference between POP and IMAP?'
Personally I have my Gmail account on Thunderbird set up as IMAP. It works flawlessly and as far as I recollect (I've had it for some years now) the initial setup was trouble-free and almost automatic. It also has the advantage that if I access the account from another computer, any changes I make are reflected immediately in  Thunderbird.
So I would suggest that's the way to go, but you may have special reasons for not wanting to use IMAP?

Thank you for your response. I have actually tried setting it up both IMAP and POP3. I do not have a reason for choosing POP3 over IMAP just which ever will work will be fine with me. I will take a look at the link. Thank you again.

---

### Post by user_of_gnomes on 2015-04-12
You might have to tell Gmail settings that you want to allow "less secure apps" access to your account. It blocks these by default and I believe it includes Thunderbird as well. After that you might also need to tell Gmail (in a security log somewhere) that the blocked attempt was a valid attempt otherwise it still won't work (Welcome to the "free" world of Google, have you considered an alternative such as GMX.com?).

See [this]("https://support.google.com/accounts/answer/6010255?hl=en") article for the less secure app thing. 
I believe [this]("https://support.google.com/accounts/answer/6063333?hl=en") is the article that links to (and explains) the suspicious activity page.

Also, I'd set it to IMAP and not POP3 but that's up to you.

---

### Post by miranda2 on 2015-04-12
> **user_of_gnomes said:**
> You might have to tell Gmail settings that you want to allow "less secure apps" access to your account. It blocks these by default and I believe it includes Thunderbird as well. After that you might also need to tell Gmail (in a security log somewhere) that the blocked attempt was a valid attempt otherwise it still won't work (Welcome to the "free" world of Google, have you considered an alternative such as GMX.com?).

See [this]("https://support.google.com/accounts/answer/6010255?hl=en") article for the less secure app thing. 
I believe [this]("https://support.google.com/accounts/answer/6063333?hl=en") is the article that links to (and explains) the suspicious activity page.

Also, I'd set it to IMAP and not POP3 but that's up to you.

You were totally right I did need to allow less secure app to access my account. Thank you tons I really appreciate it. Have a fantastic day!

---

### Post by user_of_gnomes on 2015-04-12
Glad to hear!

---

### Post by fould12 on 2015-06-09
> **user_of_gnomes said:**
> You might have to tell Gmail settings that you want to allow "less secure apps" access to your account. It blocks these by default and I believe it includes Thunderbird as well. 

See [this]("https://support.google.com/accounts/answer/6010255?hl=en") article for the less secure app thing. 

This worked for me as well. Thank you!

---

