---
title: "tracker problem with email"
date: 2008-02-15
forum: General Help
---

### Post by buttari on 2008-02-15
Hi all,
I have a problem making tracker work on my evolution emails. "Evolution email" is checked inside tracker-preferences, tracker-stats returns
```

Emails : 13455 
EvolutionEmails : 13455 
ThunderbirdEmails : 0 
KMailEmails : 0 
EmailAttachments : 113 
EvolutionAttachments : 113 

```

but if I search for ANY word inside tracker-search-tool (or tracker-search from the command line) no email is returned. I had this same problem in the past and I solved it by deleting the tracker db but this trick does not seem to work anymore...
Can anybody help me?

Alfredo

---

### Post by jamiemcc on 2008-02-17
Hi,

please try following in terminal

1) killall trackerd

2) trackerd --reindex

3) once reinde xis ocmplete email should be searchable

Its likely a bug in 0.6.3 that caused this. 0.6.4 is much more stable

---

### Post by buttari on 2008-02-18
> **jamiemcc said:**
> Hi,

please try following in terminal

1) killall trackerd

2) trackerd --reindex

3) once reinde xis ocmplete email should be searchable

Its likely a bug in 0.6.3 that caused this. 0.6.4 is much more stable

Thanks Jamiemcc,
I just launched the reindexing.

Alfredo

---

### Post by buttari on 2008-02-20
> **jamiemcc said:**
> Hi,

please try following in terminal

1) killall trackerd

2) trackerd --reindex

3) once reinde xis ocmplete email should be searchable

Its likely a bug in 0.6.3 that caused this. 0.6.4 is much more stable

Jamiemcc,
it worked.
Thanks

Alfredo

---

