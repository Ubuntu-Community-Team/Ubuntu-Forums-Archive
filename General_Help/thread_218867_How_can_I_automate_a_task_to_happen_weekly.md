---
title: "How can I automate a task to happen weekly?"
date: 2006-07-19
forum: General Help
---

### Post by CzarAlex on 2006-07-19
I think I'm progressing within my Linux knowledge. I've gotten to the point where I'd like to automate a few tasks to happen once a week.

Every Friday, I would like 4 individual files to be tar'ed (in separate tar files..so i have 4 of them) and then emailed off to 4 separate addresses.

Is this a chron (cron?) job? If so, its something I've never fiddled with before and no nothing about. Where can I find more information ragarding the task at hand? :-k 

Thanks!

---

### Post by asimon on 2006-07-19
Yes, cron is the tool you want to use. First install the package 'cron'. I think since Dapper it's no longer part of the default installation.

Then take a look at the [Cron Howto](https://help.ubuntu.com/community/CronHowto) in the Ubuntu documentation. If you have questions left, just ask. ;-)

If you want some little GUI help with setting up cron jobs you can look at kcron (KDE) or gcrontab (GNOME). But I never used them and thus can't really recommend them. There are probably other cron editors too.

If you just want the task at hand done once a week, without a specific time, you could also use anacron, which is installed and started by default in Ubuntu. It's like cron, but intended for systems which are not up around the clock and ensures that tasks are started hourly, daily, weekly, etc. So in this case you could just put your script under /etc/cron.weekly/ and anacron will make sure it's started once a week, but no guarantee on what week day or time. If you want to specify specific week days or times, you have to use cron.

---

### Post by CzarAlex on 2006-07-19
Ah okay. So I need to create a file with the commands all on separate lines? Can I call it what I want or do I need to provide a special name/extension? Im looking at a file that is already located in cron.weekly called popularity-contest for suggestions. It seems that I may need to write/find some more advanced code (okay..for me any linux code is advanced.) to send the mail with the files attached.

---

### Post by mvaniersel on 2006-07-19
Yes, you'll probably need to write a little shell script to get this done. I would focus first on writing a shell script that actually does the stuff you want to do, and when that works, it is a trivial step to do it automatically with cron.

First make sure you can get all individual commands to work from the command line. You'll need to get the packages **mailx** and **sharutils** from synaptic to be able to send email from the command line.

When you know the sequence of commands on the command line, put them together in a text file. On the first line, put the magic #!/bin/sh line. This simply tells linux which interpreter to use to run the script. After that put all the commands you need to get the job done. 

It will probably look something like this:
```

#!/bin/sh
tar zxf outfile.tar file1 file2 file3 file4
uuencode outfile.tar outfile.tar | mail yourname@yourdomain.com -s subject  

```
(But I'm writing this from memory, so don't replicate this blindly)


Save the file as myjob.sh, and make it executable with 
```

chmod +x myjob.sh

```

then you can run the script like this:

```

./myjob.sh

``` 

See also [http://www.brandonhutchinson.com/Sending_email_attachments.html]("http://www.brandonhutchinson.com/Sending_email_attachments.html")

edit:
Note that it is the executable flag that you set with chmod, together with the magic first line, that determine that this is a shell script. The extension of the script doesn't matter at all, but .sh is good for convenience.

---

### Post by CzarAlex on 2006-07-19
Okay. I decided that the shell script is the way to go as suggested by mvaniersel.

Here is the code I'm using. Its my first attempt at something like this so be prepared to laugh :???: I had to use mutt because it didn't butcher the attachments.

```

#!/bin/sh
# This script will backup the four moo database files
# and email them to their proper owners. Afterwards,
# it will erase the backups.
cd /home/czar/Desktop/mooserver
tar cvf drakebackup.tar.gz drake.db.new
tar cvf hopebackup.tar.gz hope.db.new
tar cvf icsbackup.tar.gz ics.db.new
tar cvf lusitaniabackup.tar.gz lusitania.db.new
mutt -a drakebackup.tar.gz -s MOO dude@site.com < "."
mutt -a hopebackup.tar.gz -s MOO email@email.com < "."
mutt -a icsbackup.tar.gz -s MOO foo@bar.baz < "."
mutt -a lusitaniabackup.tar.gz -s MOO baz@zot.qux < "."
rm drakebackup.tar.gz
rm hopebackup.tar.gz
rm icsbackup.tar.gz
rm lusitaniabackup.tar.gz

```

(I changed the emails for privacy reasons)

After i save this as myjobs.sh (actually I used moobackup.sh) and properly chmod it, how can I get it to run weekly automatically?

---

### Post by mvaniersel on 2006-07-19
then you have to add a line to /etc/crontab. For example

```

5 1 * * 0 alex /home/alex/myjob.sh >> /home/alex/myjob.log

```

This will run the script in /home/alex/myjob.sh on 5 min past 1 every sunday, as user alex. The output of the script will be added to the file /home/alex/myjob.log, so you can see what is going on.

Do a "man 5 crontab" to get more info on the formatting of that line.

---

### Post by mr_ed on 2006-07-27
As strange as it sounds, I had to **remove** the .sh from my file.

I had stuck my dyndns_update.sh file in /etc/cron.hourly and was totally bamboozled why it wouldn't update.

I ran run-parts --list /etc/cron.hourly and nothing came up.  (For anyone that doesn't know, cron calls run-parts every hour by default)
Once I removed the .sh from the end, it works!  :confused:

---

