---
title: "Moving from procmail to FDM -- mail arrival statistics and parser question for FDM"
date: 2021-07-15
forum: General Help
---

### Post by llamabr on 2021-07-15
I've been using procmail for many years to sort my incoming mail into folders. I then run mailstat on the procmail log, which parses (that is, gives me a report) of what mail went where. So if procmail tells me I have a new gmail, I can just look in the gmail folder. This means that I can have 25 different folders, but I don't have to open all 25 folders every day to look inside and see if there's anything there.

I'd like to replace procmail with FDM. I'm using it successfully to fetch via IMAP, as well as sort incoming mail into folders. So far, it's a superior replacement, and also drops right in and does what procmail does for me. The only thing that's missing for me is the parsing. mailstat is part of the procmail program. Is there a separate tool, or something native to the FDM program that does something similar? I'd like to avoid writing some script to do it if there is a tool that already does this for me.

Thanks!

---

### Post by HermanAB on 2021-07-15
Geez... 'many years' - about a hundred?  Next you are going to ask a question about using Mutt... :)

I had a quick look, but can't figure out how to get stats with FDM either.  Mailstat scans the log files - maybe you can still use it.

---

### Post by llamabr on 2021-07-15
> **HermanAB said:**
> I had a quick look, but can't figure out how to get stats with FDM either.  Mailstat scans the log files - maybe you can still use it.
Thanks for looking. I looked too, but I didn't see anything. Mailstat does seem to look through the log files, though I'm hoping for something other than mailstat. First, it's part of procmail, which I'm worried will eventually go away. Second, I was hoping for something FDM-native, or at least, general use, failing that. And third, I'm running fdm in my .forward to process all mail from stdin, and I'm not sure how to get that into the logs (FDM is logging just what gets "fetched"). I could probably figure out the third thing, but the first two are really central to my question. Thanks for looking.

---

### Post by HermanAB on 2021-07-15
You will probably do better by installing Postfix.  It doesn't use much resources when it is doing virtually nothing.

---

### Post by llamabr on 2021-07-15
> **HermanAB said:**
> You will probably do better by installing Postfix.  It doesn't use much resources when it is doing virtually nothing.

Thanks for that advice? I'm running smptd. But I'd like to do mail filtering as a user, rather than on the system level. That's why I use procmail (for a hundred years smiley emoji) but I'm looking to move it over the FDM.

Anyway, if anyone does something like what I'm trying to do, or knows of a way, I'd be interested in hearing. Alternatively, if mailstat and procmail are just superior given my needs, I'd be interested in learning that, too.

Thanks!

---

### Post by HermanAB on 2021-07-16
I would rather write a filter for smtpd.  Using procmail or fdm is a bit kludgy to me.  

I have used procmail in the past - at the time I also edited a sendmail configuration file by hand - so I think I was certifiably crazy and cannot recommend the experience to anyone…

---

