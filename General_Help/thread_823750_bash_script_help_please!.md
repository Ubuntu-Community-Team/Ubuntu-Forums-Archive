---
title: "bash script help please!"
date: 2008-06-09
forum: General Help
---

### Post by cclofton on 2008-06-09
hello everyone, I've spent all day working out how to sync my live website including a mysql database to my local xampp installation. The commands all work fine when copied and pasted into the terminal, but when I try to automate it in a bash script.....well I don't really know where to start. 

here's what I've got so far to copy my live site to my local pc - simply the commands put in an executable text file with "#!/bin/bash" at the top:

##################################
#!/bin/bash
ssh xxxx@ssh.phx.nearlyfreespeech.net
mysqldump --user=xxxxx --password=xxxxx --host=xxxxx.db xxxxx > xxxxx.sql
exit
scp xxxx@ssh.phx.nearlyfreespeech.net:/home/htdocs/xxxx.sql /home/xxxx/documents/websites/xxxx/backup/xxxx.sql
/opt/lampp/bin/mysql --user=xxxx --password=xxxx  --host=localhost xxxxxx < /home/xxxx/documents/websites/xxxx/backup/xxxx.sql
rsync -az -e ssh --progress --exclude='configuration.php' --delete xxxx@ssh.phx.nearlyfreespeech.net:'/home/htdocs/' /home/xxxx/documents/websites/xxxx/livemirror/ 
########################################

obviously, I've changed personal information to x's! I assure you, these commands work absolutely perfectly, but at the minute when I run the script in a terminal the first thing that happens is I have to enter my password (it would be nice to automate this, but not essential) - but the real problem comes after that. It just starts the ssh session then doesn't execute any more commands.

I am currently going through a bash tutorial (http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) but if someone could give me some more specific help it would be wonderful. 
The other script is essentially the same, just in reverse.

Thanks for any help you can give or pointers in the right direction

---

### Post by Titan8990 on 2008-06-09
Here is a tutorial (script included) on backing up to a remote server via SSH. Also, you will never automate this as long as you have to enter a password for SSH.

[http://ubuntuforums.org/showthread.php?t=639979&highlight=backup+rsync](http://ubuntuforums.org/showthread.php?t=639979&highlight=backup+rsync)

---

### Post by wdaniels on 2008-06-09
> **cclofton said:**
> ssh [email]xxxx@ssh.phx.nearlyfreespeech.net[/email]
mysqldump --user=xxxxx --password=xxxxx --host=xxxxx.db xxxxx > xxxxx.sql
exit

It doesn't work like this. You shouldn't think of a script as simply replaying keystrokes into a terminal, it is more like a program. In the script, after executing the ssh command, it will be waiting for that command to exit before running the next one (mysqldump), which it will continue to do locally.

What you can do here is send the command to be executed remotely as part of the ssh command itself:

```
ssh xxxx@ssh.phx.nearlyfreespeech.net 'mysqldump --user=xxxxx --password=xxxxx --host=xxxxx.db xxxxx > xxxxx.sql'
```

(the 'exit' is not needed because ssh will return automatically to the script once the mysqldump has finished)

As for removing the need to enter the password for ssh, you can do this by setting up a a key pair between the two machines. Google turned up [a script to automate setting that up]("http://programminglinuxblog.blogspot.com/2008/02/automatic-ssh-login-script-all.html") but I have always done it manually myself, so I can't vouch that this script works (it should point you in the right direction though).

---

### Post by cclofton on 2008-06-09
thanks very much to both of you. I knew that bash scripts weren't just copy and paste command lines, but I just didn't know where to start looking for help. I'm going to try the suggestions and I'll report back in a little while

Thanks again

---

### Post by cclofton on 2008-06-09
thankyou thankyou thankyou! All that was needed was to execute the ssh command like you said and it works beautifully. Sure, I still have to put in my password three times, but that's no big deal, I won't be executing it that often. I don't think I can easily set up a key pair as it's a webserver that I have no access to users and groups etc....

for now, I am absolutely tickled pink. I can make offline changes to either the database or the php files, and with one simple command it's all uploaded. If I'm working away from home, I can edit online (it's a joomla website), then sync it all up when I get back.

thanks again

---

### Post by Sydius on 2008-07-31
On a related note, you might look into sshfs... it lets you mount you web site as if it were a local hard drive.  I absolutely love it, and it's very easy to do.  It also works with your host, as I happen to use the same host (I picked that host because they support it).

---

