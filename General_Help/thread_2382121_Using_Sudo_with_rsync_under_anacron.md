---
title: "Using Sudo with rsync under anacron"
date: 2018-01-09
forum: General Help
---

### Post by hundred1906 on 2018-01-09
I want to backup my wife's .thunderbird folder on a daily basis. For simplicity I have anacron daily point to a .sh file under my login from where several rsync commands back-up parts of my system onto a remote server.

when I manually run the following:
```
rsync -a /home/maria/.thunderbird/ /culture/users/trevor/deskbackup/maria/.thunderbird
```
I get:
> rsync: opendir "/home/maria/.thunderbird/zqbljcvp.default/gmp/Linux_x86_64-gcc3" failed: Permission denied (13)
rsync: send_files failed to open "/home/maria/.thunderbird/Crash Reports/InstallTime20171122155701": Permission denied (13)


Repeat the same under sudo and it works (of course).

The question is how can I achieve the same from within a script called by anacrontab?

---

### Post by TheFu on 2018-01-09
Use the root crontab, not the one from your userid.

```
$ sudo crontab -e
```

BTW, using mounted storage for the backup target is less security than using an ssh-type connection.  Just look at all the Windows malware that encrypts all mounted storage for a reason why.

---

### Post by hundred1906 on 2018-01-09
TheFu, thanks but I don't follow that answer. 

In /etc/anacrontab I have this line so that it auto runs on a daily basis:
> 1	40	usersbak.daily		/home/trevor/cronjobs/UsersBak.sh
then in UsersBak.sh I have:
> rsync -a /home/maria/.thunderbird/ /culture/users/maria/deskbackup/trevor/.thunderbird 
where does crontab fit in?

---

### Post by TheFu on 2018-01-09
There 5-10 different ways to solve this.  While you specified "anacrontab", I've never seen that used *in the wild*.  Using different crontabs is what I have seen everywhere, so that is the answer provided.

cron will launch different crontabs using different userids.  The **crontab -e** command launches an editor for the current userid. If you prepend with sudo, then it launches for 'root', which is what you said you wanted.  Then it just comes down to knowing the crontab file format.  There are hundreds, no thousands, of examples on the internet.

You could just place the script into /etc/cron.daily/, chmod +x it and be happy.  It will run when all the other "daily" scripts are run. I wouldn't touch the /etc/anacrontab file at all. For something like backups, I prefer having more control as to when they run. I know when systems aren't so busy, which would let me have the backups run when they are least likely to interfere with work.

If you are interested, I could provide other suggestions about this to make things "better" for certain values of better. ;)  That is pretty subjective, however.

---

### Post by hundred1906 on 2018-01-10
Thanks for the example and for your time. I use Cron on my file server for internal actions which is fine there because it is always on.

My desktop however is on only for limited periods and at differing times of the day so I use anacron here as it is the generally recommended solution in that case. Eg from the man page:

> Anacron can be used to execute commands periodically, with a  frequency
       specified in days.  Unlike cron(8), it does not assume that the machine
       is running continuously.  Hence, it can be used on machines that aren't
       running 24 hours a day, to control daily, weekly, and monthly jobs that
       are usually controlled by cron.

I have not yet tried your crontab daily recommendation, not because there is anything wrong with it but because I wanted to try staying with anacron and fixing that through shear cussedness. Anyways, I have found articles out there about using sudo with anacron but have not tried anything yet. When I do come up with a solution for me I will post it here.

---

### Post by untrustytahr on 2018-01-10
Hi hundred1906,

While you are not wrong about cron and anacron (glad you referenced the man page ;)), if you dig a bit deeper into how the overall system of anacron works you will see that there are 3 lines in the anacrontab file that call run-parts on particular directories.  One for daily, weekly, and monthly jobs.  It is designed for you to drop scripts in the corresponding  directory and run-parts will execute it at a given time.  There are some caveats though:

1. the file has to owned by root and be executable
2. the file cannot be writable by group or other
3. the file cannot have any extension such as .sh.

Most people do not alter anacrontab directly, they just drop their script in the needed directory.

---

### Post by hundred1906 on 2018-01-12
anacron is confusing. In the documentation it says that entries in anacrontab define the period and the start delay for each script.

I want my daily scripts to start after a delay because I hate it if they run just when I am starting other work as I don't want my server hit with another file transfer action. So that is why I use anacrontab directly but I would happily use another approach, especially if it enabled me to achieve the ambition set at the start of this thread.

---

### Post by TheFu on 2018-01-12
Use **nice** to make any program be nicer for the CPU.  That's really easy with any script.  

man nice:
```
NAME
       nice - run a program with modified scheduling priority

SYNOPSIS
       nice [OPTION] [COMMAND [ARG]...]

```
Basically, it lowers the priority of background processes so that the things you are point-n-clicking on have a higher priority.  If 500 things are running, the system will slow down, but if less than 5 are running in the background with lower prioriteis, the Linux scheduler should handle that just fine.

Sometimes I have a need to queue up a bunch of batch things. There are tools that are part of cron for that, but I prefer taskspooler.  It lets me control how many tasks are run concurrently (usually just 1) and it let's me control multiple queues.  I think the package is 'task-spooler', but the command is 'tsp'.  This probably doesn't help you for crontab stuff.

If you script stuff and want it to run daily via anacron, put the script in /etc/cron.daily/ and let it go.  If you want a delay, then add a delay to the script;  *sleep 30s* or something, if that is what you want.  And don't forget to use 'nice'.

---

### Post by hundred1906 on 2018-01-12
Thanks to TheFu, I have taken up your suggestions with nice and sleep. However (and this is going off topic slightly) my bottleneck is not really the CPU but the nfs file server. So nice is not going to be a great help. I guess I could optimize block-sizes etc but that is likely to need some experimentation and I really need to be getting on with some real application stuff so, Pareto-wise, will live with what I have for now.

---

