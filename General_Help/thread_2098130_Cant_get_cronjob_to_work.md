---
title: "Cant get cronjob to work"
date: 2012-12-25
forum: General Help
---

### Post by SmickSmack on 2012-12-25
Hello there,

I´ve tried to start my first cronjob but I didnt succeed... I do not use any panel like cpanel, just SSH via Putty.

I logged in as root and wrote:

```
*/30 * * * * php /var/www/module/directory/LoadDataFromFeed.php
```

Of course I have a file (that works) under this directory.

This is a cronjob to update RSS-feeds but this did not happen after more than 30 minutes. Does it matter which user is creating the cronjob (root or admin etc)?

When I open the cronjob in my editor (nano) it says > File: /tmp/crontab.93hcW0/crontab is this really the right place for a cron file? Or does it even mean that this is the file I´m in?

By the way, I want to change to hourly updates so guess I will write 0 * * * * when I update the cronjob next time?

Does anyone have any idea what has gone wrong? If you could provide me with an accurate code I would jump from joy :)

Thanks in advance!
/Daniel

---

### Post by spynappels on 2012-12-25
Howdy.

Two things to  note, firstly, you need to use different syntax to edit the crontab.
```
crontab -e
``` will allow you to edit the crontab of the user you are logged in as, the user does matter. The editor is basically whatever you selected when you first edited the crontab, I presume you selected nano, based on the fact that you mentioned Nano. The file name is correct as it is a temp file created by the editing process.

Secondly, and this is the important bit, you need to give the full path to the php executable as well as to the actual script, or alternatively place the path to the php executable after the shebang in the script itself, which may work.

Sorry for the first bit, not sure if you'd edited the crontab using crontab -e.

Also, to do the update hourly you are right to use 0 * * * * /path/to/command as this will run the command every hour on the hour.

---

### Post by SmickSmack on 2012-12-25
Yes, I used "crontab -e" when I opened the file and edited.

You write that the user does matter, so would it work if I start the crontab as "adminuser" instead of "root" for example?

> Secondly, and this is the important bit, you need to give the full path to the php executable as well as to the actual script, or alternatively place the path to the php executable after the shebang in the script itself, which may work.
Here I´m not sure I follow. The directory I mentioned below is the full path to the php-file I want executed once an hour. Should I not have that path directly after the "0 * * * *"? Have I missed some code?

Lastly I came to think of the "php" I have before the path, should it not be there and what does it do?

Thanks for your support, really appreciate it.

---

### Post by superdaveozzborn on 2012-12-25
try using "sudo crontab -e" and add your php file like so at the bottom of the page.

once an hour
00 * * * * /usr/bin/php /pathto/script/scritp.php

also make sure you use full address to any included files or links in your php script.

---

### Post by StinkySQL on 2012-12-25
I don't think you can sudo remote. We always have to log in remote, SU, then edit our cron jobs. We are coming from a windows world so maybe from anther GNU/L it is different, but I don't thinks so.

SS

---

### Post by Cheesehead on 2012-12-26
> **SmickSmack said:**
> You write that the user does matter, so would it work if I start the crontab as "adminuser" instead of "root" for example?

User matters because the permissions of that user matters. For example, a user-level cron job would fail if it tried to do a system-level task like rebooting the system.

If you run the job in Terminal as a user, you should put it in the user crontab ([FONT="Courier New"]crontab -e[/FONT]).
If you run the job in Terminal as sudo or root, put the job in root crontab ([FONT="Courier New"]sudo crontab -e[/FONT]).
If you run the job in Terminal as a different user (like webserver or couchdb), put the job in root crontab and assign it to that other user.

If you use the crontab command, the contab file will be stored properly in /var/spool. Since that's not editable by you, a temporary-for-editing version is saved in /tmp. After crontab verifies your syntax, it updates your real crontab.

> **SmickSmack said:**
> The directory I mentioned below is the full path to the php-file I want executed once an hour. Should I not have that path directly after the "0 * * * *"? Have I missed some code?

Lastly I came to think of the "php" I have before the path, should it not be there and what does it do?

syntax is: /path/to/executable /path/to/data-used-by-the-executable.
php is the executable.
Use the full path. Use the command [FONT="Courier New"]which php[/FONT] to find the full path if you don't know it ().

The three biggest reasons cron jobs don't work as expected:
1) Used a path cron doesn't know about (like /usr/lib/foo)
2) Assigned it to the wrong user, who doesn't have permission to do it. (like a user moving or deleting files in /var)
3) Ran an executable that requires a DISPLAY variable. DISPLAY tells the system which display your current tty session is using (try the command [FONT="Courier New"]ps[/FONT] - see the TTY column?). Cron jobs don't have a DISPLAY assigned, so if the application requires one it will fail...unless you specifically assign it. For example, using VLC Media Player to download audio streams. If #1 and #2 don't fix the problem, the next step is to check that php script.

---

### Post by spynappels on 2012-12-26
Yeah, Cheesehead explained it much better than I did, but essentially that is what I was trying to say. PHP should not require root to run, but you may have to run it as the apache user, depending on whether you have the web directories locked down.

---

### Post by SmickSmack on 2012-12-26
Ok, first of all thank you guys for helping out. Your explanation was really good Cheesehead, now I understand the logic behind as well.

I can still not get it to work. I´ve done everything as root and used ```
sudo crontab -e
``` to access the file.

I did a test to see if cronjob could create a folder just to see if a simple job like that could be done, but with no success. The test looked like this:

```
PATH=/usr/sbin:/usr/bin:/sbin:/bin
25 13 * * * mkdir /home/adminuser/crontest
```

and also tried just:
```
25 13 * * * mkdir /home/adminuser/crontest
```

Note that this is all the code in the crontab file, nothing else is added.

Some minutes after 1:25 PM I looked in my ftp for the folder "crontest" under home/adminuser but there was nothing. I´ve checked that usr/bin/php is the directory by doing "which php".

1. Do I have to do anything else besides saving (Ctrl-O in nano) when I´ve edited the file, like restarting something?
2. The first line (PATH=/usr/sbin...) I just added since I read about it on the forum, dont know if it is correct for me...? All I know is that I have those directories, I figure they are standard in the Ubuntu server.

My God am I stupid or what´s this about? I´m sure I´ve overlooked something elemental...

---

### Post by rnerwein on 2012-12-26
> **SmickSmack said:**
> Ok, first of all thank you guys for helping out. Your explanation was really good Cheesehead, now I understand the logic behind as well.

I can still not get it to work. I´ve done everything as root and used ```
sudo crontab -e
``` to access the file.

I did a test to see if cronjob could create a folder just to see if a simple job like that could be done, but with no success. The test looked like this:

```
PATH=/usr/sbin:/usr/bin:/sbin:/bin
25 13 * * * mkdir /home/adminuser/crontest
```and also tried just:
```
25 13 * * * mkdir /home/adminuser/crontest
```Note that this is all the code in the crontab file, nothing else is added.

Some minutes after 1:25 PM I looked in my ftp for the folder "crontest" under home/adminuser but there was nothing. I´ve checked that usr/bin/php is the directory by doing "which php".

1. Do I have to do anything else besides saving (Ctrl-O in nano) when I´ve edited the file, like restarting something?
2. The first line (PATH=/usr/sbin...) I just added since I read about it on the forum, dont know if it is correct for me...? All I know is that I have those directories, I figure they are standard in the Ubuntu server.

My God am I stupid or what´s this about? I´m sure I´ve overlooked something elemental...
hi
about the PATH in crontabs - have a look in /etc/crontab:
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
and you see if you don't have "#!/bin/bash" in your script the dash will be used and this can be a problem. dash and bash are not 100% compatible !
hm - do you have a /etc/cron.allow or /etc/cron.deny ?
have a look at /var/log/syslog --> grep CRON /var/log/syslog to see if your job was started.
cheers

---

### Post by Cheesehead on 2012-12-26
Start simple.
Once you have proven that cron is really working properly, checking your scripts for syntax errors is easy.

This is a very simple test to prove that cron is working, and that crontabs really do launch jobs.

User-level crontab.
```
crontab -e
```

Add a line that looks like:
```
* * * * * /usr/bin/touch /tmp/testfile
```
See the full paths for the application (touch) and the data (testfile)
We use /tmp for this test because it's globally writable.
The test simply touches an empty testfile once each minute. It proves that cron is working.

If you are using nano, use CTRL+X to save and exit.
The terminal should indicate success with the line [FONT="Courier New"]crontab: installing new crontab[/FONT]

Wait for the clock to tick over.

See the result with
```
ls -l /tmp/testfile
```
and the result looks like:
```
-rw-rw-r-- 1 caliban caliban 0 Dec 26 12:54 /tmp/testfile
```
Each minute, that time will increment. That's all the test does.

Clean up:
- Use the crontab -e command to remove the test line. Or simply comment it out with a leading '#'. You might need it again someday.
- Remove /tmp/testfile . Or don't - it will be deleted upon reboot anyway.

---

### Post by SmickSmack on 2012-12-26
This is what I get from the test, no file generated...

```
adminuser@ubuntu:~$ crontab -e
no crontab for adminuser - using an empty one
crontab: installing new crontab
adminuser@ubuntu:~$ ls -l /tmp/testfile
ls: cannot access /tmp/testfile: No such file or directory
```

What I wrote in crontab was:
```
* * * * * /urs/bin/touch /tmp/testfile
```

This is a fresh install on the server so I dont really get why it does not work.

---

### Post by spynappels on 2012-12-26
Did you use /urs/bin/touch or /usr/bin/touch?

The first one is a typo, so if that was what you used, try the second one.

---

### Post by steeldriver on 2012-12-26
you may also find it helpful to look in syslog for messages from cron e.g.

```
$ tail -f /var/log/syslog
```

---

### Post by fdrake on 2012-12-26
> **SmickSmack said:**
> 
What I wrote in crontab was:
```
* * * * * /urs/bin/touch /tmp/testfile
```

this is wron you have urs for usr! as mention before it's a typo.

also for the php server you can tru this:
firast of all check if you need php or phpd as user:
```
less /etc/passwd | grep php
which php
ls -l /var/www/module/directory/LoadDataFromFeed.php

```


then use this command to add the cron job

```
sudo crontab -u name_of_PHP -e
```
add the job > */30 * * * * path_of_php /var/www/module/directory/LoadDataFromFeed.php

then post bakc the
```
sudo crontab -u php_user  -l 
```

---

### Post by SmickSmack on 2012-12-26
Now thats embarrassing... Yes, it was a typo and that command works. :redface:

I have never gotten the "crontab: installing new crontab" text before after saving so I tried with the code that I actually want. I got the confirmation again, but sadly it did not work :(.

So now to the million dollar question. Why does not the other code work?

I got this after running the command "steeldriver" suggested:
```
Dec 27 00:00:02 ubuntu CRON[4662]: (adminuser) CMD (/usr/bin/php /var/www/module/foxfo/LoadDataFromFeed.php)
Dec 27 00:00:02 ubuntu CRON[4661]: (CRON) info (No MTA installed, discarding output)
```

So it seems no MTA is installed, what is MTA?

---

### Post by fdrake on 2012-12-26
> **SmickSmack said:**
> 
```

Dec 27 00:00:02 ubuntu CRON[4661]: (CRON) info (No MTA installed, discarding output)
```


you need a mail transfer agent-MTA.
```
sudo apt-get install sendmail
```

---

### Post by SmickSmack on 2012-12-27
Ok, thank you all for your patience.

Now I get this info instead:
> Dec 27 11:54:01 ubuntu CRON[8052]: Authentication token is no longer valid; new one required

This will never end... :/

---

### Post by spynappels on 2012-12-27
Are you trying the /usr/bin/touch test or the php script provided by fdrake?

I don't think the problem lies with cron as such, I suspect the php script needs some form of authentication.

You could try using cron to run a simple php script which writes the date to a logfile to test if php scripts run from cron correctly, and if it works you can then start troubleshooting the php script which is giving you errors.

---

### Post by fdrake on 2012-12-27
> **spynappels said:**
> Are you trying the /usr/bin/touch test or the php script provided by fdrake?

I don't think the problem lies with cron as such, I suspect the php script needs some form of authentication.

You could try using cron to run a simple php script which writes the date to a logfile to test if php scripts run from cron correctly, and if it works you can then start troubleshooting the php script which is giving you errors.
the test command with touch works check post #15

> Now thats embarrassing... Yes, it was a typo and that command works. 



@OP
shows us what exactly you have written in cron
I do believe the script you have is running fine and the error you get is possibly related to the script instead.
Make sure you have used "sudo crontab -e " with root permissions when creating the job! Check my prev post.

---

### Post by SmickSmack on 2012-12-27
> Are you trying the /usr/bin/touch test or the php script provided by fdrake?
I have done part of it. "which php" gives me /usr/bin/php. "ls -l" gives me:
> -rwxrwxrwx 1 adminuser adminuser 734 Dec 25 14:13 /var/www/module/foxfeedspro/LoadDataFromFeed.php (where the actuall path is in green)

Regarding "less /etc/passwd | grep php" I dont understand how to write it. Should I first write "less /etc/passwd"? And then what? I get a long list of things. If I write "grep php" the marker just goes to the left and nothing more happens.

So maybe the sollution is in what fdrake is writing, but I then I need more explanation on how to do it I´m afraid.

I have tried to run some simple jobs and it works, so you are probably right that there is something wrong with php.

Exactly what is written in my cronjob is:
```
0 * * * * /usr/bin/php /var/www/module/foxfeedspro/LoadDataFromFeed.php
```
The reason why I dont think it is anything wrong in the "LoadDataFromFeed"-file is that it is used by many users of their scripts and works fine. And I have, of course, not edited anything in that file provided by them.

---

### Post by fdrake on 2012-12-27
> **SmickSmack said:**
> 

Regarding "```
less /etc/passwd | grep php
```" I dont understand how to write it.

just copy and paste the whole line ito the terminal.


> The reason why I dont think it is anything wrong in the "LoadDataFromFeed"-file is that it is used by many users of their scripts and works fine. And I have, of course, not edited anything in that file provided by themcan you tells us shortly what the script does. Is the script saving/reading any info outside /var/www ? If so then the user needs to have root-priveledge!

---

### Post by SmickSmack on 2012-12-27
> can you tells us shortly what the script does. Is the script saving/reading any info outside /var/www ?

Well I´m no expert but I have a page on my site with news. The site takes RSS-feeds from all around and collects them on this page. What the script should do is to tell that onece an hour all the feeds should be updated.

---

### Post by rnerwein on 2012-12-27
> **SmickSmack said:**
> Now thats embarrassing... Yes, it was a typo and that command works. :redface:

I have never gotten the "crontab: installing new crontab" text before after saving so I tried with the code that I actually want. I got the confirmation again, but sadly it did not work :(.

So now to the million dollar question. Why does not the other code work?

I got this after running the command "steeldriver" suggested:
```
Dec 27 00:00:02 ubuntu CRON[4662]: (adminuser) CMD (/usr/bin/php /var/www/module/foxfo/LoadDataFromFeed.php)
Dec 27 00:00:02 ubuntu CRON[4661]: (CRON) info (No MTA installed, discarding output)
```So it seems no MTA is installed, what is MTA?
hi
just a question: have you set a password for the adminuser and whats about the 
date of expiry.
cheers

---

### Post by fdrake on 2012-12-27
@ SmickSmack:
we need 2 info from you:

1-- which user are you using while creating a cron job (adminuser, php, or root)
    

2- check the expiration date of the password of that user
```

sudo chage -l expired_user

```

if the date is expired change the password with
```

sudo passwd expired_user

```

---

### Post by spynappels on 2012-12-27
Do any of the sources you pull data off require you to authenticate in some way?

Just another question, when this script is run by others, what user do they run it as? Can you run the script manually successfully as your own user?

---

### Post by SmickSmack on 2012-12-27
@ fdrake
1. I´m using root.
2. I´m getting this:

```
root@ubuntu:~# sudo change -l expired_user
sudo: change: command not found
```

@spynappels
1. I dont know, but if that was the case the provider of the script should have mentioned that (I´m having a discussion with them as well, regarding the script it self).
2. I don´t know how they run them. But since I´m running it as root it should not be any issue regarding permissions and stuff right? I have also tried to run it as "adminuser" both with and without sudo. But now I only use root (and all old cronjobs are of course removed)
If I can run it manually is an interesting question, what command do I use to run the file /var/www/module/foxfeedspro/LoadDataFromFeed.php ?

---

### Post by spynappels on 2012-12-27
> **SmickSmack said:**
> 
If I can run it manually is an interesting question, what command do I use to run the file /var/www/module/foxfeedspro/LoadDataFromFeed.php ?

You just use the same command as you placed in the crontab.

```
/usr/bin/php /var/www/module/foxfeedspro/LoadDataFromFeed.php
```

---

### Post by SmickSmack on 2012-12-27
Yupp, I ran the script manually and it did work. All my feeds were updated on my site.

So now we have established that the cronjob funktion works and the script works but when I combine them it does not work...

---

### Post by spynappels on 2012-12-27
Ok, then I suggest that for the next test, you place the command in the crontab again, but this time redirect any stdout and stderr to a file by adding the following to the end of the command:
```
&> /path/to/logfile
```

This should mean that any output or error messages which are normally dropped by cron are logged and might give an indication as to what is going on.

---

### Post by SmickSmack on 2012-12-27
I´ve placed an empty file named "cronlogfile" under /var/tmp/cronlogfile and tried:
```
0 * * * * /usr/bin/php /var/www/module/foxfeedspro/LoadDataFromFeed.php &> /var/tmp/cronlogfile
```

and

```
0 * * * * /usr/bin/php /var/www/module/foxfeedspro/LoadDataFromFeed.php&> /var/tmp/cronlogfile
``` (no space between)

But I get nothing written in the file.

---

### Post by Cheesehead on 2012-12-27
Keep testing methodically. One step at a time. Simple tests.

You know that cron works.
You have made a cronjob work.

Next, try a very simple php script, something very simple and equivalent to the 'touch' test. This will show that the problem is not with your version of php.

I don't use php myself, so I'm sorry I cannot offer you something ready-made for that test.

Finally, once you know that the problem is really with your script, then post your script here. We can probably spot the problem pretty quickly.

---

### Post by spynappels on 2012-12-27
A very simple php script is found below. Run it from crontab instead of the other script you have and redirect output to a log file. Appending is probably better (>>). It should just print the full date at the interval set in cron.

```
#!/usr/bin/php
<?php
// This is a script to check cron execution
echo date('l jS \of F Y h:i:s A');
?>

```

This should allow you to check if the crontab executes php scripts. Try sending the output to a few different places too to see if that makes any difference.

FWIW, the above ran fine for me every minute on a vanilla Ubuntu Server install.

---

### Post by steeldriver on 2012-12-27
Likewise this works for me as a plain user (non root) crontab

```
* * * * * /usr/bin/php /var/www/phpinfo.php >> /tmp/phpinfo 2>&1
```where phpinfo.php is

```

$ ls -l /var/www/phpinfo.php 
-rw-r--r-- 1 root root 22 Dec 27 17:42 /var/www/phpinfo.php
$
$ cat /var/www/phpinfo.php 
<?php

phpinfo();

?>

```I'm not sure you can use &> in crontab since I think it's a bashism and iirc crontab runs stuff in /bin/sh (which is symlinked to dash)

---

### Post by fdrake on 2012-12-27
> **SmickSmack said:**
> @ fdrake
1. I´m using root.
2. I´m getting this:

```
root@ubuntu:~# [CODE]sudo change -
```l expired_user
sudo: change: command not found[/CODE]

@spynappels
1. I dont know, but if that was the case the provider of the script should have mentioned that (I´m having a discussion with them as well, regarding the script it self).
2. I don´t know how they run them. But since I´m running it as root it should not be any issue regarding permissions and stuff right? I have also tried to run it as "adminuser" both with and without sudo. But now I only use root (and all old cronjobs are of course removed)
If I can run it manually is an interesting question, what command do I use to run the file /var/www/module/foxfeedspro/LoadDataFromFeed.php ?

if you are using root you have to run 
```
sudo chage -l root
```
"CHAGE" NOT "CHANGE" (check the typo)

---

### Post by Hadaka on 2012-12-27
Hi, I've been bitten by this a time or 2, so thought why not
pass it along,


```
Although cron requires that each entry in a crontab end  in  a  newline    character,  neither the crontab command nor the cron daemon will detect    this error. Instead, the crontab will appear to load normally. However,    the  command  will  never  run.  The best choice is to ensure that your    crontab has a blank line at the end. 
```

sometimes its something simple.

---

### Post by fdrake on 2012-12-27
> **SmickSmack said:**
> I´ve placed an empty file named "cronlogfile" under /var/tmp/cronlogfile and tried:
```
0 * * * * /usr/bin/php /var/www/module/foxfeedspro/LoadDataFromFeed.php &> /var/tmp/cronlogfile
```

and

```
0 * * * * /usr/bin/php /var/www/module/foxfeedspro/LoadDataFromFeed.php&> /var/tmp/cronlogfile
``` (no space between)

But I get nothing written in the file. the time you are using is wrong [SIZE="4"][COLOR="Red"]_**do not use "0" in minutes but "*"**_[/COLOR][/SIZE]. Also remember that [COLOR="Red"][SIZE="4"]**_cron does not handle sec : you cannot use "*/30"_**[/SIZE][/COLOR]; it won't work

---

### Post by SmickSmack on 2012-12-28
Again, thank you all for your time. It´s really awesome.

@fdrake – I thought that the zero in “0 * * * *” was in what minute the script should run (in this case once at xx:00:00)? If I put “*” in the first value as well the script will update every minute and that´s not what I want (during testing it´s ok of course).

I also changed the password for root after running the things you proposed in an earlier post. I got “password must be changed” so I changed it.

@ Hadaka – Thanks for the tip, does not seem to change anything in my case tho.

@ Steeldriver – I tried your test as root and I got a file in tmp with a lot of text in it so it seems to work. I placed the file exactly like in your example. I also palaced both the result-file and the script-file in different places (in the file where the original php script is for instance) and it works everywhere.

@ Spynappels – Your php script also worked fine!

@ Everyone:

There must be something in my command line in cron or? What else can it be? I can run the php script manually and it works (but not as root)…

Now I have systematically tried to create cron job and manually run the php script for both users (adminuse (not sudo) & root) and have come to the conclusion that:
Adminuser: can run php script manually and can run cron job (touch test)
Root: can NOT run php script but can run cron job (touch test). I can however do both php tests given by Spynapple and fdrake.

Will the cronjob not work if I dont have setup e-mail, like sendmail or postfix (I have not configured it)? Is it dependent on what´s in the script?

It seems like adminuser is the owner of the script and/or that folder in some way, can it be like that and how do I give root the same privileges? It feels like root should have full access to do anything…

---

### Post by fdrake on 2012-12-28
> **SmickSmack said:**
> 

@fdrake &#8211; I thought that the zero in &#8220;0 * * * *&#8221; was in what minute the script should run (in this case once at xx:00:00)? If I put &#8220;*&#8221; in the first value as well the script will update every minute and that´s not what I want (during testing it´s ok of course).
well since we are debugging the script will be better to run it everymin than once an hour, for the moment.

---

### Post by spynappels on 2012-12-28
Can you share the actual update script so we can see if it tries to do something strange?

---

### Post by Cheesehead on 2012-12-28
> **SmickSmack said:**
> There must be something in my command line in cron or? What else can it be? I can run the php script manually and it works (but not as root)&#8230;

Now I have systematically tried to create cron job and manually run the php script for both users (adminuse (not sudo) & root) and have come to the conclusion that:
Adminuser: can run php script manually and can run cron job (touch test)
Root: can NOT run php script but can run cron job (touch test). I can however do both php tests given by Spynapple and fdrake.

If you can run the script as root in a terminal window, then it's not a mysterious 'problem with root.' That's an easy test.
 
The most likely answer is that some element of your php script requires a resource or environment variable that cron does not provide (Most common cron error #3).

For example, the script may require something from /usr/lib (not in cron's $PATH) without using a full path. Perhaps it uses a supporting application that requires an $DISPLAY or $XDG-* environment variable.

php will run the script in the same limited cron environment of the cronjob line, not the root login or user login environments. The same limitations apply to the script you are running: Full paths and/or exported variables.

The next step is to dive into your script:
- Look for subprocesses and commands within the script that don't have full paths.
- Look for subprocesses and commands that normally open a window or send a notification or require a user's .config file.
- Add debug statements to the output, so you can bisect or localize the failing line.
- Perhaps you can run php in some verbose or debug mode, and redirect the result to a logfile.


> **SmickSmack said:**
> Will the cronjob not work if I dont have setup e-mail, like sendmail or postfix (I have not configured it)? Is it dependent on what´s in the script?

The MTA message is simply cron telling you that it cannot e-mail you the fact of failure, and possibly the error message that was returned by the failed process. It answers the question "Why didn't cron send me an email when my job failed?" The lack of MTA is (almost) never the original cause of failure, but merely the proximate cause of the log entry.

In this case, we have already determined that the problem is not cron, not the cronjob, and not php. The failure is some instruction within your script, so the lack of MTA is not really a hindrance to debugging.


> **SmickSmack said:**
> It seems like adminuser is the owner of the script and/or that folder in some way, can it be like that and how do I give root the same privileges? It feels like root should have full access to do anything&#8230;

Think 'environment' more than 'permission'. Root has access to everything, or your system wouldn't boot properly. Root can indeed see and touch everything...but root is not omnicient. Cron's access to the user or root environment is ignorant of lots of things. Cron's environment doesn't know which display you use, nor which network device is working, you which e-mail client you use, nor lots of other things.

We can easily show you how to address those problems and tell cron what it needs to know...once we know more specifically what the script's problem is.

---

### Post by SmickSmack on 2012-12-29
Hi again,

Finally, it seems to work. I´ve had an close eye on the cron job for a day and now it´s working!

I cant tell you exactly what I did because I´ve tried so many things. But I think a great breakthrough was to change the expired password for root. I also did add a space after the command line like Hadaka wrote. Maybe any of those contributed perhaps.

I would like to give all of you who participated in this thread a big big thank you, both for sharing all of your knowledge and for your patience toward a newbie like me. I´m very greatful. If this is how the ubuntu community is like I will for sure use it on my home computer as well. But you probably want me to stay far away so I dont come with more stupid questions ;)

Hopefully this thread can be of use to others. I have for sure learned a great deal about ubuntu in general and cron in particular.

/Daniel

---

