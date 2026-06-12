---
title: "dapper + samba - print queue doesn't clear"
date: 2006-09-14
forum: General Help
---

### Post by I_M_smbody on 2006-09-14
I have a production system of dapper and I'm using samba 3.0.22 which comes as a package and cups to do the print serving. Today i noticed that the print queues on my windows machines aren't clearing after the job is completed. It hasn't actually caused a problem ie no printer crashes. And the printer still print quickly and well, my issue is having 50 or so old print jobs in the queue is not particularly useful and doesn't give the  appearance of seamless server operation to my clients.

Cups seems to be working okay.

And after searching here and elsewhere for answers, I find out it is a known samba problem with older versions and was supposedly fixed  in samba 3.0.8.

the posible solutions I can think of are
manually delete queue content( have to find the file with the jobs)

write script to empty queue contents( ditto plus have to figure out how to delete completed jobs only.)

upgrade samba

have windows clients print directly to printer without using samba( possible on older clients?)

My questions are many but First, has  anybody solve this problem?

If not how hard is it to upgrade to the current version of samba without a package? ( I've never had to do it. and I'm not sure I should for what is essentially an aesthetic problem.)

Thanks

I_M_smbody

---

