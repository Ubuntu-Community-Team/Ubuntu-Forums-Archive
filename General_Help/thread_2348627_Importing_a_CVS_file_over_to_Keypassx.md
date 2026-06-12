---
title: "Importing a CVS file over to Keypassx"
date: 2017-01-05
forum: General Help
---

### Post by RobGoss on 2017-01-05
Hello everyone I was wondering it there was anyway for me to import my passwords from another password Manger to Keypassx

The file type I currently use for my password manager is a CVS file keypassx uses a different file type for importing 

I know Keypassx uses a different file type format and when I try I get a error message saying it's the wrong file type. I would really hate to have to type this stuff over

Thanks so much

---

### Post by oldfred on 2017-01-05
What version of keypassX?

When I changed from 14.04 to 16.04, it changed it internal database to be compatible with other password managers and does export to .csv.

My export has this.
"Group","Title","Username","Password","URL","Notes"

Each entry is in quotes, and then the notes are one entry but have line returns, so each extra note entry is on extra line with quote only before first note and after last quote, but would be imported as one long line with CR/LF?

---

### Post by RobGoss on 2017-01-05
Hi Fred I'll have to see what version I have I just installed it from the app center I would think it's the latest. I downloaded it about two days ago

I have a lot of passwords from another app I'm using and would just like to import them and call it a day

Thanks so much

It would also be great to sync my passwords between computers is that possible?

I just installed Keepass2

---

### Post by howefield on 2017-01-05
> **RobGoss said:**
> Hi Fred I'll have to see what version I have I just installed it from the app center I would think it's the latest. I downloaded it about two days ago

```
keepass -v
```

will tell you the KeepassX version that you are using.

> **RobGoss said:**
> It would also be great to sync my passwords between computers is that possible?

You could store the database in a "cloud" someplace.. I use a raspberry pi to run ownCloud and have phones and computers syncing to it so they can all access the database in its current state.

Btw, I don't rate your chances of importing anything into Keepassx other than KeepassX version 1 databases. I think Keepass could do it, but not KeepassX.

---

### Post by RobGoss on 2017-01-05
Ok so it was a simple task importing my passwords from the **CVS **file from my old password manager to the new keepass password manager. There is a option for **Generic CVS Importer**, I just choose that option and imported the passwords and it complete

Thanks so much for your help guys I will mark this as solved

---

### Post by howefield on 2017-01-06
> **RobGoss said:**
> Ok so it was a simple task importing my passwords from the **CVS **file from my old password manager to the new keepass password manager. There is a option for **Generic CVS Importer**, I just choose that option and imported the passwords and it complete

Just for clarity, are you now using Keepass as you write above or KeepassX ?

---

### Post by RobGoss on 2017-01-06
> **howefield said:**
> Just for clarity, are you now using Keepass as you write above or KeepassX ?

Yes Howefield it is a much better app seeing it has that option to import CVS file worked great

---

### Post by howefield on 2017-01-06
Cool, thanks for the clarification.

---

