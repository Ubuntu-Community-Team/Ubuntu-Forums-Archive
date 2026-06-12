---
title: "Crontab with perl scripts"
date: 2006-07-12
forum: General Help
---

### Post by mikeym on 2006-07-12
Hi,

I'm having problems getting crontab to run a perl script on my computer, and I can see from searching the forum that others have as well. I can only assume that it has something to do with the reduced PATH that cron seems to run with. I noticed someone had been adviced to use 'sh /my/bash.sh' so I tried 'perl /my/perl.pl' but still to no avail. I have also tried wrapping the perl command in a bash script but it just does't do that line (I have checked with logs). 

Has anyone found out how to get round this?

I don't realy want to use 'anacron' as I want the script to run at midnight when the network traffic is slow.

---

### Post by Gus Tarballs on 2006-07-12
Have you checked /var/log/syslog for any error messages?
The output should normally be send to the users local mail account.
There might be more information there.

---

### Post by mazirian on 2006-07-12
As long as the script is set to be executable by the user calling it, has a shebang in it with the proper location for perl, and is listed in the crontab by it's full path, it really should "just work."  I take it the script is executing fine outside of cron?

---

### Post by mikeym on 2006-07-12
Just tried it and got the following messages:

```

Jul 12 15:04:01 localhost /usr/sbin/cron[4795]: (mikey) RELOAD (crontabs/mikey)
Jul 12 15:04:01 localhost /USR/SBIN/CRON[10735]: (mikey) CMD (sh /home/mikey/GetNZBFiles.sh)
Jul 12 15:04:04 localhost /USR/SBIN/CRON[10734]: (mikey) MAIL (mailed 114 bytes of output but got status 0x0001 )

```

---

### Post by mazirian on 2006-07-12
What did the message cron mailed you say?

---

### Post by mikeym on 2006-07-12
Sorry it didn't even occur that it was actualy trying to email me something. How do I access my users email on the system?

---

### Post by Gus Tarballs on 2006-07-12
If you are logged in as the user that is running the cronjob, just type "mail".
If not you should try "sudo mail -u *username*"

---

### Post by mazirian on 2006-07-12
Cron mails the stdout/stderr of the scripts it runs to you.

I don't know that dapper automatically installs a local mail system for you, so this may be best answered by someon with more ubuntu experiance.  I like exim4 as a debian fan, and so I installed that.   Unless you have special needs just select local mail delivery only when prompted.  By default it will send mail to a mail spool file located at /var/mail/username.  It is trivial to change the location of local delivery if you care to.

EDIT: Sorry, I was late.

---

### Post by mikeym on 2006-07-12
Nope.

There's no mail program on my system. I have also checked the /var/mail and /var/spool/mail directories. 

Also I have tried to install - just in case - 'apt-get install mail'.

---

### Post by Gus Tarballs on 2006-07-12
Sorry I got confused (mixed it up with a debian system with exim4 installed by default).](*,) 
On Ubuntu you probably have to install some kind of mail-system to receive the output of cron. 
You can do that by installing mutt (which is a textbased mail-reader). 
*sudo apt-get install mutt*
It will automatically install postfix as a dependency. While installing postifx will ask on what kind of site it is running on. Just choose local delivery here if you don't plan to send and receive mail from the net.
This might explain the error message "mailed 114 bytes of output but got status 0x0001 " in your syslog. Looks like cron could not send an email to you, but this should not be the reason for your script to fail.
Still you might be able to get more information by looking at the mailed output after installing mutt/postfix.

---

### Post by mazirian on 2006-07-12
Not to spark a flamewar, but you may find exim4 a bit easier to install and manage.  It's probably a personal bias, I used postfix for years on gentoo before converting to Debian, and I really prefer exim4.  sudo aptitude install exim4 will do take you to a working mail install with you only having to answer one question (select local mail delivery only).  Very easy.  You can use your existing mail client and configure a new account, giving it the location of the mail spool, which will be /var/mail/username.

Postfix is ok too.  It's all about choices!

---

### Post by jmacak on 2006-07-12
Hi

If the problem is in the script (e.g. the crontab entry is set up correctly), it's a good policy to have messages and errors routed to file.  e.g.

00 20 * * 6 . $HOME/.profile; $HOME/script.pl >$HOME/script.out 2>$HOME/script.err


Note that the above entry also reads the user's korn shell profile, another good convention.

cheers

joe in seattle

---

### Post by Gus Tarballs on 2006-07-12
> **mazirian said:**
> Not to spark a flamewar, but you may find exim4 a bit easier to install and manage.  It's probably a personal bias, I used postfix for years on gentoo before converting to Debian, and I really prefer exim4.  sudo aptitude install exim4 will do take you to a working mail install with you only having to answer one question (select local mail delivery only).  Very easy.  You can use your existing mail client and configure a new account, giving it the location of the mail spool, which will be /var/mail/username.

Postfix is ok too.  It's all about choices!

I agree. I think the difference comes into play mostly when using your system as an internet mail host. For local delivery both should be ok.

---

### Post by mikeym on 2006-07-12
OK. thanks.

This is what the email from cron said:

```

TERM not set at /usr/local/bin/nzbperl.pl line 39
/home/mikey/GetNZBFiles.sh: line 3: shutdown: command not found

```

* The shutdown thing is something I'm awair of in the launch script and happens after the error in the perl script.
* The line that is causing an error in the perl script is:

```

my $terminal = Tgetent Term::Cap { TERM => undef, OSPEED => $ospeed };

```

This is obviously trying to get information on the termainal type and throwing a strop because there isn't one.

---

### Post by mikeym on 2006-07-12
I found the solution to this was to use my initial bash script to export any parameters I needed for the perl script. After having setup my mail as mentioned before I found these were:

```

export TERM=xterm
export PATH=$PATH:/usr/local/bin

```

I then had to direct the ouput of my perl script to /dev/null

```

perl /my/perl.pl > /dev/null 2> /var/log/my.log

```

P.S. The option mentioned above for making sure that any scripts called by cron are redirected to logs in a similar manner is a much better way to handle them than using a mail server.

---

### Post by mazirian on 2006-07-12
You can place environment variables like that right at the top of the crontab.  For example, I have in mine:

```

PATH=$HOME/bin:/usr/local/bin and so forth ...
SHELL=/bin/zsh

```

You could just add TERM in there and dispense with the wrapper script altogether.

---

### Post by mikeym on 2006-07-13
I'm now trying to pull together all the ideas that have been expressed on this thread to make a robust crontab, but I have hit a problem. This is what I have:

```

# Export parameters for crontab
TERM=xterm
SHELL=/bin/bash
PATH=$HOME/bin:/usr/local/bin:/usr/bin

# m h  dom mon dow   command
00 14 * * * . $HOME/.profile; $HOME/bin/getnzbfiles.sh > $HOME/log/cron-getnzbfiles.out.log 2> $HOME/log/cron-getnzbfiles.err.log

```

and this is the error I get mailed to me:

```

From: 	Cron Daemon <root@localhost>
To: 	mikey@localhost
Subject: 	Cron <mikey@Bush> . $HOME/.profile; sh $HOME/bin/getnzbfiles.sh > $HOME/log/cron-getnzbfiles.out.log 2> $HOME/log/cron-getnzbfiles.err.log
Date: 	Thu, 13 Jul 2006 14:00:01 +0100 (BST)

stdin: is not a tty

```

Any ideas?

I have just checked and the stdin error occurs only when '. $HOME/.profile' is called. 

But even without this I get the following errors in $HOME/log/cron-callnzbfiles.err.log:

```

/home/mikey/bin/getnzbfiles.sh: line 2: date: command not found
/home/mikey/bin/getnzbfiles.sh: line 4: date: command not found
/home/mikey/bin/getnzbfiles.sh: line 5: fixdvdownership: command not found
/home/mikey/bin/getnzbfiles.sh: line 6: date: command not found
/home/mikey/bin/getnzbfiles.sh: line 7: myshutdown: command not found

```

All of these are calls to files in the path I have set up. Does this method not work or am I doing it wrong?

I tried 'export PATH=***' but crontab wouldnt accept it.

---

### Post by mazirian on 2006-07-13
You might get that error if you are calling something in cron that requires interaction on the commandline, like user input. It could be related to sourcing the .profile file as well, though I doubt it.

Also, please note that I truncated my PATH variable and was just offering an example.  You might try using PATH=$HOME/bin:$PATH instead, to make sure you get everything in there.  But, in your case you probably don't need it at all as long as you specify the absolute path to the script you want cron to run for each task.  

Does this work?

```

00 14 * * * /home/username/bin/getnzbfiles.sh 2>&1 | tee /home/username/log/cron-getnzbfiles.log

```

Note, that will dump all the output into a single log file, which is more more of a user preference thing. Also, I'm assuming the first line of your bash wrapper script has a shebang in it.

---

### Post by mazirian on 2006-07-13
Ok, saw you edit.  Just remove the PATH from the top of your crontab for the reaosns stated above and it should work now.

---

### Post by mikeym on 2006-07-13
I don't understand. You are saying now that the PATH can't be changed as I have done in my crontab?

All the programs it has identified as not found are in the PATH I have given.

I haven't tried your ouput dump line because I am happy viewing them separately - I take it this is all it does?

---

### Post by mazirian on 2006-07-13
My assumption was that your script was not finding commands like date because PATH did not include them.  I was concerned that the reason for this was becasue I included only a portion of my actual PATH in the example I gave above.  For example, the date command resides in /bin typically, which is not included in the PATH you specified in your crontab.  All the commands run in your shell script will need to be in PATH or called by an absolute path.

---

### Post by mikeym on 2006-07-13
I didn't realise that date was in /bin, but the other files it failed to find were mostly in $HOME/bin.

I have checked and rechecked and any changes you make to PATH in the crontab doesn't make it to the scripts it calls. 

The ~/.profile which I take it is ment to be the same as the one form /root/.profile always generates an error when run from crontab:

```

stdin: is not a tty

```

I don't know if it _is_ possible for a script to change the PATH variable for the script that it's calling.

---

