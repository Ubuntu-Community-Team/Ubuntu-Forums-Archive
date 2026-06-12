---
title: "unable to automate (crontab)"
date: 2008-05-26
forum: General Help
---

### Post by s.jesudasan on 2008-05-26
i edited the /etc/crontab file using sudo and entered the following command to automate it 

#copy pictures to a backup folder every hour 58th minute
#created by stalin 
58 * * * * stalin cp /home/stalin/Desktop/*.jpg /home/stalin/back/

can anyone help me 
i even tried to run crontab -e command still i was unable to execute the program automatically

---

### Post by Patb on 2008-05-26
In your crontab file, do you have the mandatory blank line below the one beginning "58 * ..."?

Why the command "stalin" if all you need to do is copy?  (Apologies if this is a useless question - I don't use the program stalin).

Final, possibly silly, question:  Does "stalin" do the cp command in a gui?  If so, you would need a line something like:
58 * * * * export DISPLAY=:0 && stalin cp /home/stalin/Desktop/*.jpg /home/stalin/back/

Cheers, Pat.

---

### Post by s.jesudasan on 2008-05-26
stalin is my user id 
i use sudo to edit the /etc/crontab file

this is how my crontab fil looks like

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

#copy pictures to a backup folder every hour 58th minute
#created by stalin the master admin of this computer
58 * * * * stalin cp /home/stalin/Desktop/*.jpg /home/stalin/back/

---

### Post by mike2357 on 2008-05-26
/etc/crontab has a different format than regular crontab files.

I think you were on the right track when you ran "crontab -e".  You shouldn't have to put your user name.  Run "man 5 crontab" for details.

I suggest you try the following as your crontab command:
58 * * * * cp /home/stalin/Desktop/*.jpg /home/stalin/back/ > /home/stalin/OUT_CRON 2>&1

Sending the output to a file will allow you to check for error messages.  The "2>&1" means to send error messages to the same file that standard output is being sent to.

Good luck.

---

### Post by Patb on 2008-05-27
:) What a giggle.  There is also a program called stalin in the repositories! :)

That's why I was confused over the word.  Just delete the word "stalin" from the line, or use Mike's more sophisticated line.  And as he says, it is probably better to use the command "crontab -e".  

Don't forget the return at the end of the line or it will still not work.  "Man crontab".

Cheers, Pat.

---

