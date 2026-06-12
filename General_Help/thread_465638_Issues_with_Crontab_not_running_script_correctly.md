---
title: "Issues with Crontab not running script correctly"
date: 2007-06-05
forum: General Help
---

### Post by ipsi on 2007-06-05
Sorry for the vague title, but I'm not actually sure where the error is. It runs fine from the command line, but when I have cron run it at a predetermined time, it gives me this:

```
Binary file /<PATH_REMOVED_FOR_PRIVACY>/access.log.8.gz matches
Binary file /<PATH_REMOVED_FOR_PRIVACY>/access.log.7.gz matches
Binary file /<PATH_REMOVED_FOR_PRIVACY>/access.log.6.gz matches
Binary file /<PATH_REMOVED_FOR_PRIVACY>/access.log.5.gz matches
Binary file /<PATH_REMOVED_FOR_PRIVACY>/access.log.4.gz matches
Binary file /<PATH_REMOVED_FOR_PRIVACY>/access.log.3.gz matches
Binary file /<PATH_REMOVED_FOR_PRIVACY>/access.log.2.gz matches
```

instead of what I want, which is for it to gunzip the .gz files and put them into the file...

My script looks like:

```
logdir='/<PATH_REMOVED_FOR_PRIVACY>/'
rm ${logdir}*
cp /var/log/apache2/access.log* ${logdir}
for i in $( ls -r ${logdir}access.log* );
do
  #echo $i
  ext=$(expr "$i" : '.*\(\..*\)')
  if [ $ext == ".gz" ]
  then
      gunzip $i
      fn=${i%.gz}
  else
      fn=$i
  fi
  /<PATH_REMOVED_FOR_PRIVACY>/mygrep.sh $fn >> ${logdir}'apache.log'
done
```

For what it's worth, there are two other files which are not gzipped, and are grep'd fine. Anyone have any idea why Cron is doing this? As I said, it runs perfectly fine from the command line...

My guess is that whatever is running cron doesn't like the if statement. That or the % operator...

Running Ubuntu Server Fiesty.

---

### Post by ipsi on 2007-06-06
Bump...

Anyone got any suggestions?

---

### Post by ipsi on 2007-06-09
Bump...

Surely someone has an answer here:?:

---

### Post by bizzy on 2007-06-12
No solution - but I think I may have the same bug.

I have a script that runs perfectly as a crontab on my Centos servers. It also runs perfectly as a shell script on 7.04 Kubuntu. But when run as a crontab script it does not complete.

The script takes a list of usernames as parameters and rsyncs the directories. Run from shell it works perfectly. Run as a crontab and it breaks after the first or second parameter is completed.

Is this a known crontab bug in 7.04?

---

### Post by ipsi on 2007-06-14
I think I've just solved it. Took a while before I finally found out how to get the error log. In this case, the answer was so painfully simple, it hurts. What was wrong? I used ==. It expected =. Why the hell is there a difference here?

---

