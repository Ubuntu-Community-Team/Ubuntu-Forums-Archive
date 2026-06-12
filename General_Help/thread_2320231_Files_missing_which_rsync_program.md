---
title: "Files missing which rsync program"
date: 2016-04-11
forum: General Help
---

### Post by sed_faster on 2016-04-11
Hello everyone,

I ran this command to copy all data between disk usb "sudo rsync -Cravzp --delete-after cp1 cp2" and when I verify the totally on both disk I has difference (almost 10 GB on dimension 50GB). I thought occur a problem and ran another time the same command, but the result was same. I ran diff command and identify the files missing. But what should I do to fix this problem? And why the file doesn't copy to another disk but for rsync program they are there?

Thanks
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
I am a enthusiastic to electronic, computers and programs. If you have any idea or doubt about the algorithmic/programmer in shell script please send email to edgaroliveira.devatgmaildotcom. I promise which I try help you.
I am improve my English, if couldn't understand anything which I wrote please give the opportunity to do better and talk with my through comment. Anyway, please give me your rating, of course, if you want and powers.

---

### Post by papibe on 2016-04-11
Hi Edgar

A few thoughts:

options -r and -p are included in -a so you don't need to use them. This way you could run with the same results:
```
rsync -Cavz --delete-after source/ destination/ 
```
The above command won't necessarily produce identical source/ and destination/ because you are using an exclude clause:
```
-C, --cvs-exclude    auto-ignore files in the same way CVS does
```
In other words, there are files that won't be send to destination. Is that what you where looking for?

On the other hand, if you want to produce identical dirs, something like this would work better:
```
rsync -avz --delete  source/ destination/ 
```
Does that help? Let us know how it goes.
Regards.

---

### Post by sed_faster on 2016-04-11
Hi papibe,

Thanks your reply and advices. The parameter -C exclude CVS file is it? I think which translate well the document (my English sometimes it is misleading :)

Only difference between ours command it is the parameter --delete, is it? Or parameter such as -r and -p could interfere on behaviour the command? I prefer parameter --delete-after because it is more safety. This parameter allows which copy the data and only delete after the difference data. Am I suer? Or this command to be prefer to environment where I want copy and delete on the source?

Ok, I could try this command again but what or which problem can I want to have this difference between files?

---

