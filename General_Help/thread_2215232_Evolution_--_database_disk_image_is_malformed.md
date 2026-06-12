---
title: "Evolution -- database disk image is malformed"
date: 2014-04-05
forum: General Help
---

### Post by cigtoxdoc on 2014-04-05
This in on a DELL Vostro 3500 with 256 GB SSD running 12.04 64-bit.  Everything was running fine.  I shut off PC to change locations.  On restart, I get Error while generating message list, database is malformed.  I did a Evolution backup about 6 hours ago, and only thing I did after the backup was to delete perhaps 100 or so messages from the inbox.

After first occurrence of the error , I checked the Internet for suggestions and followed suggestion to start evolution from the command line.  That did not give errors, but inbox did not come up.  I closed evoluton, and started again from icon bar.  It has been several minutes now and evolution is still saying it is generating message list.

I am 4000+ miles from home office.  I have two 500 GB WD Passport drives with me as well as Boot Recovery CD as well as Macrium Reflect software CD.

I have also seen suggestions about loading sqlite to fix problem.

I have meetings with clients on Monday and need to resolve situation before then.

I can limp by using webmail instead of evoluton if needed.

Thank you,

John

---

### Post by cigtoxdoc on 2014-04-05
Looks like I bailed myself out of trouble by installing sqlite3 and running the command:
[email]john@john-Vostro-3500:~/.local[/email]/share/evolution/mail$ sqlite3 folders.db "pragma integrity_check;"
ok
then I killed all evolution related processes; deleted folders.db and restarted evolution.

There is a closed thread which describes similar steps, but since that thread was written, evolution files are in a different location.

John

---

### Post by chris36 on 2014-07-01
I had the similar problem of the "Malformed database issues"

My Fix for Evo 3.8.4

Backup and close Evolution

In Caja - file manager
Show "Hidden files"

Locate in Home folder ./local -> share -> evloultion -> mail ->  

Then Identify your "problem folder" in my case (eg  .pc help files) - and delete it. Yes I know this is fine if you dont want to rescue the data!!

close and restart Evo - import you saved Backup data and evertying will be there - except the folder you had that was malformed. This will get you running again.

Cheers
Chris

---

