---
title: "Cannot get GMX email working with Claws Mail nor Sylpheed."
date: 2016-01-28
forum: General Help
---

### Post by Rytron on 2016-01-28
Hi.

Can anyone get GMX ([http://www.gmx.com](http://www.gmx.com)) email working with Claws Mail and Sylpheed?

If so, please post screenshots of the correct settings here.

Thanks.

---

### Post by howefield on 2016-01-28
What settings do you need, setting up my gmx account (imap) with the Sylpheed account wizard was enough to get it going without trauma.

---

### Post by Rytron on 2016-01-29
> **howefield said:**
> What settings do you need, setting up my gmx account (imap) with the Sylpheed account wizard was enough to get it going without trauma.

Hi howefield.

I get no errors in both Claws Mail and Sylpheed so I'm unsure as to what I've gotten wrong or omitted.

Some settings:
IMAP4: imap.gmx.com
SMTP: mail.gmx.com

P.S. I can use GMX in Thunderbird no problem. I just want to try out Claws Mail and Sylpheed as well. ;-)

Edit: I matched where I saw fit -- the settings in Thunderbird to Sylpheed but no joy -- nor any error messages to tell me where I am going wrong.

---

### Post by howefield on 2016-01-29
Well, easy enough to delete the ~/.sylpheed folder and start again :)

These are the settings that got me going.. (with the obvious deleted)

---

### Post by Rytron on 2016-01-30
> **howefield said:**
> Well, easy enough to delete the ~/.sylpheed folder and start again :)

These are the settings that got me going.. (with the obvious deleted)

Hi howefield.

Your way worked fine. ;-)

I also setup Claws Mail and it gave me the option to import the Sylpheed settings but I chose to set it up manually. The 3 screenshots attached have the right settings. I'm not sure if I should select more or less options (particularly re ssl) but this works anyway. ):P

---

### Post by howefield on 2016-01-30
Cool, I did read that using STARTTLS with outgoing mail could/should be used but to be honest if it is working, I'd leave well alone especially if your goal is simply to test out the applications :)

---

