---
title: "evolution export/save to mbox in error"
date: 2013-03-12
forum: General Help
---

### Post by kuifje09 on 2013-03-12
I know there is already been some posts about it, but I still cannot save my evulution mail to mbox format.
The version I use is the distributed version of ubuntu 11.10 , 3.2.2 .
The buildin save as mbox makes still a lot of rubbish inside the mbox file including characters who sould not be there.


Losts of ^@  and other control chars... like 
```


^L^L^L^L^L^L^L^L^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^M^L^L^L^L^L^L^L^L



^G^G^G^G^E^E^E^E^D^D^D^D^C^C^C^C^B^B^B^B^A^A^A^A^A^A^A^A^A^A^A^A^A^A^A^A^B^B^B^B^C^C^C^C^E^E^E^E^G^G^G^G



^N^N^N^N^Q^Q^Q^Q^Q^Q^Q^Q^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^R^Q^Q^Q^R^Q^Q^Q^Q^N^N^N^O


```

And I am not talking about the code64 which is normal use for encoding non-text.
When will it be repaired, who is responsible for it.  I am a bit disappointed now. No tools for the commandline to export tens of mboxes at ones. You have to do them 1 by 1, ( ridiculous ) , maybe add an "save all boxes" .And stiil the other question, why using sqlite for storing the messages.
You see right now what a lot of trouble it causes.  PLEASE, revert it back to mbox style, or something else but readable.
I even have no clue how extract the parts of the email spread over the several files myself. ( as pointed to in de folders.db Column parts )

---

### Post by kuifje09 on 2013-03-15
Silly , no reaction at all, why?
I have read there are more complains about the export to mbox, since early 2012, almost a year ago now.

Well I did some reading en testing and found : the mail is readable in .local/share/evolution/mail/.......  
Then on the stipples a number and a string,  uname/domain alike.
That directory contains a lot files numbered 00 -- ??  and the mails are there. But the organiziation is a mistery to me.
Looks like mails, sent and recieved for that account are scattered over those files, I did not see a pattern.
I even found some mail pieces as broken parts in those files... Most files contain a perfect singel or multipart mail.
There nust be some relation to the parts column in the folders.db I think ....

Can someone point me to a piece of doc that will telll me about how to "decode" it.

For evolution I found only a very litle user documentation within the gnome docs.
Maby I have to read some developpers doc ?  please any help is appreciated.

I would love to build some export tool for myself at least... for now I feel like prisoner to evolution-mail.

---

### Post by kuifje09 on 2013-03-19
Sorry the get back to this again, but how would you export the mail from within evolution into mboxes.
Or did you ever create a evolution-backup and could you import/restore it in a previous version of evolution ?

---

### Post by kuifje09 on 2013-03-23
Can't give it up so search a bit further and found a way to transfer from evolution to thunderbird. Well, that doc was old and does not comply to the current versions.
I made a backup of evolution, import to evolution on a fresh installed evolution. It created the new mail structure at once instead asking for what to do.
Just tried to convert 1 of my 95 mboxes in evolution to mbox format. ( not shure of the content - read above.. )
Then moved the mbox to the mail-dir of thunderbird. ( there seems to be no way to import them directly, import tool remains empty )
Thunderbird recognized it as it uses the same mbox format ( that where a format is for, always handy those standards ) and created its indexes etc.
But when it came to reading the mail,  wow.... incredibly slow.  thunderbird version 17.0.4
And this is only 1 mbox containing 140 mails,  some text and html mail and attachments as usual.
I am not shure if this it the right way to go...

Is it normal for thunderbird to be so slow in contrast to evolution ??

---

