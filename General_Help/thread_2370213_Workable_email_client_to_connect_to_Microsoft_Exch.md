---
title: "Workable email client to connect to Microsoft Exchange Server"
date: 2017-08-31
forum: General Help
---

### Post by abbasali31 on 2017-08-31
I am running Ubuntu 17.04 and tried both thunderbird and Evolution to connect to corporate exchange server.  Does anyone have instructions how-to.  I did google search, but didn't find any resolution.

Thanks,

---

### Post by SeijiSensei on 2017-09-01
If the administrators on your network have [configured Exchange to include support for the SMTP and IMAP protocols]("https://support.mozilla.org/en-US/questions/1152028"), then programs like Thunderbird should work fine.  If they have not turned on support for Internet protocols, then I believe you're limited to the native Microsoft clients.

Does the company support Outlook Web Access?  That would be your best choice since it requires only a browser.

---

### Post by abbasali31 on 2017-09-01
Thanks,

Yes, Company does support Outlook Web Access.  

I also believe that SMTP and/or IMAP are configured to support.  Is there anything else besides the program Thunderbird.  I mean any other connector such as Microsoft Exchange Connector.  I read somewhere that the in order to connect to Exchange Server, one will need to download the Thunderbird Exchange Connector from Ubuntu Software Repository which I couldn't locate.

Regards,

---

### Post by SeijiSensei on 2017-09-02
I'd guess the Exchange connector is an [add-on for Thunderbird]("https://addons.mozilla.org/en-US/thunderbird/search/?q=microsoft+exchange"). I don't see any such package in the Ubuntu repos.

However I'd first try simply creating a new account in TBird and manually configuring the servers.  Tell it to use SMTP on port 25 and IMAP on 143 unless the server enforces encryption.  Then you'd be using 465 (SSMTP) and 993 (IMAPS).  Thunderbird can often diagnose the best choices during configuration.

---

### Post by Frogs Hair on 2017-09-02
You might look into Nylas  as well. 

[https://www.nylas.com/nylas-mail/](https://www.nylas.com/nylas-mail/)

---

### Post by ppmotskula on 2017-12-06
Install evolution and evolution-ews, then you should be able to add an Exchange account.

---

### Post by ratell on 2017-12-06
I've never used it but Hiri claims to be for working with Exchange accounts [https://www.hiri.com/](https://www.hiri.com/)

---

### Post by jayram on 2018-01-13
> **ratell said:**
> I've never used it but Hiri claims to be for working with Exchange accounts [https://www.hiri.com/](https://www.hiri.com/)

It does work - I installed it and it connected fine to a server even though it has two-factor authentication. Both email and calendar are working.  Neither Thunderbird + Exquilla or Evolution+EWS would work because of the 2FA, so was pleased Hiri worked.  That said, the program is slow and a couple of times a day I have to kill the program and restart it by going into the monitor and killing about 4 hirimail processes running.  As far as I can see you can only have one account at a time too, so not a solution for a main email driver.

I am still searching for a solution that nails the exchange problem.

---

### Post by pythagorean1804 on 2018-05-16
Hiri works great.  It syncs calendars and tasks for outlook.com accounts, which was a constant pain point in using Linux full time for me.

---

### Post by sash112 on 2018-05-16
It does work! But it is not without limitations, i.e. only one Office365/Exchange account can be used and software is not free. 20USD a year subscription or 119 for a lifetime is kind of expansive, imho
When playonlinux gets updated with office 2016 support I will probably use that one.

---

