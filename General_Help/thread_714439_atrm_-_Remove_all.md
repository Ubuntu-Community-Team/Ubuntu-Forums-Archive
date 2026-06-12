---
title: "atrm - Remove all"
date: 2008-03-03
forum: General Help
---

### Post by JFire on 2008-03-03
Is there any way to remove all jobs or whole queues that were created using the 'at' command? :-s

I know that 'atq' will list all scheduled jobs and that its possible to individually remove each job using the 'atrm <job#>' command, but is there any way to remove -all- jobs, without actually specifiying a job number?

If not, can someone please point me in the right direction to capturing the output of the 'atq' command, so that I may isolate the job numbers from there and then loop through each one and cancel it.

Thanks

~J :)

---

### Post by paulderson on 2008-05-25
This should work.

rmall.sh:

#!/bin/bash

for job in  $(atq | awk '{print $1}' )
do
  atrm $job
done

---

