---
title: "Take all lines about Networking and put into one file"
date: 2018-10-13
forum: General Help
---

### Post by wildmanne39 on 2018-10-13
Hello again, doing some file cleanup, I want to take all my notes about networking and move them to one file by themselves so no other topic is in that file, it looks like grep might be the command to use, question is how would I make it pull all networking lines out of the file and put them in the new file since networking is not in every line, will a wildcard work and what exactly would the command look like?

---

### Post by TheFu on 2018-10-13
I'd need to see the file.  It isn't like every line is labelled with "networking", right?
Searching every file isn't hard, but WHAT to search FOR **is**.

---

### Post by wildmanne39 on 2018-10-13
That is what I figured as well, that it would be a long list of search terms that would need to be used even with the use of wildcards if appropriate, I have just made the file that networking files are in a lot smaller, so I may just be able to copy and paste what I want into a file now.

I am researching right now, update after I have decided which way to go.

Thanks!

---

### Post by TheFu on 2018-10-13
Yep, you could do something like this:

```
$ egrep 'netmask|192.168|172.16|address|route|ifconfig|eth|iptable|ufw' *
```
to get started, but there are probably lots and lots of other terms to get added.

Or use full text indexing like **recoll** and be able to search across every file in your HOME.

I keep a separate text file in my ~/bin/ for every task I do and heavily comment it. So whenever I make a new RAID10 storage area, I have every command used.  Same for complex firewall setups and how to mount LUKS encrypted LVM storage.  A different file for each. Never know when each might be needed later, plus I'm religious about ~/bin/ in my backups, so that data will never be lost or forgotten.

---

### Post by wildmanne39 on 2018-10-15
Thanks TheFu, since I made the original file that contains the networking files small by editing it for duplicate content it was easy to just copy and paste the networking files to my new file, from now on I will create separate files for each topic to keep them much better organized.

---

### Post by TheFu on 2018-10-16
> **wildmanne39 said:**
> Thanks TheFu, since I made the original file that contains the networking files small by editing it for duplicate content it was easy to just copy and paste the networking files to my new file, from now on I will create separate files for each topic to keep them much better organized.

If this was for a company, I'd probably push for every admin to use a central git repo for these things.  Text, scripts all need to be versioned controlled so things that work for 1 release don't get lost as the commands change over time.

---

### Post by wildmanne39 on 2018-10-16
> **TheFu said:**
> If this was for a company, I'd probably push for every admin to use a central git repo for these things.  Text, scripts all need to be versioned controlled so things that work for 1 release don't get lost as the commands change over time.
That is a very good idea, this is for personal use but I may still store them on my github account and just mark them private.

Thanks

---

