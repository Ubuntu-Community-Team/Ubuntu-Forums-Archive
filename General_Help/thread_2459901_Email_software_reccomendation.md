---
title: "Email software reccomendation"
date: 2021-03-29
forum: General Help
---

### Post by david1992 on 2021-03-29
Please reccomend me a email client software which will instantly notify me when email arrive.

---

### Post by SeijiSensei on 2021-03-29
You can configure Mozilla Thunderbird to play a sound or pop up a notification on your desktop, or both.

---

### Post by TheFu on 2021-03-29
In the olden days, we used something called xbiff.  It was a tiny icon app that watched local /var/spool/mail  directories for each userid to see if any new mail was delivered.  There were 1 icons.  
[LIST]
[*]White mailbox - flag down.
[*]Black mailbox - flag up.
[/LIST]
xbiff didn't have any network smarts, it could only check local directories. My window manager at the time had an xbiff extension that placed the icon in a specific place.

These days, there's something called **gnubiff**.  I just set it up and it is working with 4 imaps email accounts. During setup, the GUI seemed to forget the imap setting and reverted to pop3, but in the "preferences" that was easy to see and fix.  It also had problems with one of my passwords that had unmatched single and double quote characters.

It "quacks" when new mail arrives and shows a summary for total and new for each account.

Thanks for the question. It got me to find this little tool.  Running, it uses about 32Kb of RAM w/ only 10Kb resident.

---

### Post by ajgreeny on 2021-03-29
Whatever you choose for your email will need to be running all the time in order to keep checking for mail; if you open it to see your emails then shut it down again you will get no thunderbird (or any other application) notifications.

---

### Post by HermanAB on 2021-03-29
There is procmail.

With that one, you can make a rule to send you an email when you get an email...

---

### Post by ajgreeny on 2021-03-30
> **HermanAB said:**
> There is procmail.

With that one, you can make a rule to send you and email when you get an email...

Ah!
A snake swallowing its own tail situation.

---

