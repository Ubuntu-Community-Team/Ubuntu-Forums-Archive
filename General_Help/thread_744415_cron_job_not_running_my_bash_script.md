---
title: "cron job not running my bash script"
date: 2008-04-03
forum: General Help
---

### Post by Rizla on 2008-04-03
**This post could be related to an Ubuntu bug filed at**: 4 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				i have a shell script call myip.sh

i added an entry in my crontab to run the script but its not working..

when i go into my crontab via crontab -e

i see my entry

06 16 * * * /home/myuser/sh myip.sh

ive been editing the time to run a test that is a little in advance of the current time, just to test it out, but nothings happening.

for example, i had wanted that job to run at 4:06pm, but nothing happened at 4:06  any ideas?

---

### Post by ibuclaw on 2008-04-03
> **Rizla said:**
> [b]
06 16 * * * /home/myuser/**sh myip.sh**


That'll be your problem.

the cron job doesn't execute "sh myip.sh" once you enter in the folder location.
Instead it tries to run a file that isn't there (/home/myuser/sh) and uses the latter (myip.sh) as an argument for the non-existent file.

try it without the "sh"

```
 06 16 * * * /home/myuser/myip.sh 
```

That should give you the result you want.

Regards
Iain

---

### Post by Rizla on 2008-04-03
**This post could be related to an Ubuntu bug filed at**: Well, quasi good news.  I've managed to put together a script that does what I need it to do.  The problem is that its a little quirky and not very clean. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **tinivole said:**
> That'll be your problem.

the cron job doesn't execute "sh myip.sh" once you enter in the folder location.
Instead it tries to run a file that isn't there (/home/myuser/sh) and uses the latter (myip.sh) as an argument for the non-existent file.

try it without the "sh"

```
 06 16 * * * /home/myuser/myip.sh 
```

That should give you the result you want.

Regards
Iain

just updated it literally minutes ago to

28 16 * * * /home/myuser/myip.sh

and still not getting the results back..  Anything else I could be messing up on?

---

### Post by ibuclaw on 2008-04-03
What is it that you are trying to do?

What are you expecting to happen?

Regards
Iain

---

### Post by Rizla on 2008-04-03
**This post could be related to an Ubuntu bug filed at**: Well, quasi good news.  I've managed to put together a script that does what I need it to do.  The problem is that its a little quirky and not very clean. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **tinivole said:**
> That'll be your problem.

the cron job doesn't execute "sh myip.sh" once you enter in the folder location.
Instead it tries to run a file that isn't there (/home/myuser/sh) and uses the latter (myip.sh) as an argument for the non-existent file.

try it without the "sh"

```
 06 16 * * * /home/myuser/myip.sh 
```

That should give you the result you want.

Regards
Iain

Here's myip.sh

#!/bin/sh
clear
rm index.html
wget [http://canyouseeme.org](http://canyouseeme.org)
egrep -o '([[:digit:]]{1,3}\.){3}[[:digit:]]{1,3}' index.html >>DHCPaddresslist.txt
egrep -o '([[:digit:]]{1,3}\.){3}[[:digit:]]{1,3}' index.html >>emailheader.txt
ssmtp [email]someonesemail@server.com[/email] < emailheader.txt

do you think theres a problem with the ssmtp argument via cron?  it works when i just run the myip.sh from CLI

---

### Post by Waappu on 2008-04-03
Hi

Do you have execute permission for file.
```
chmod a+x /home/myuser/myip.sh
```
gives all permission to execute

---

### Post by drs305 on 2008-04-03
Nevermind, I just saw a line saying it works in terminal....

---

### Post by Rizla on 2008-04-03
**This post could be related to an Ubuntu bug filed at**: Well, quasi good news.  I've managed to put together a script that does what I need it to do.  The problem is that its a little quirky and not very clean. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **drs305 said:**
> Nevermind, I just saw a line saying it works in terminal....

script works in terminal and sends me an email successfully.

I just noticed after checking the files that the script edits.  Its defnintly running the script, but the email isnt being sent....  can cron send email via ssmtp without special privileges?

---

### Post by ibuclaw on 2008-04-03
Well, I may have different software installed to you, cos all I'm getting is:
```
 ssmtp: Cannot open mail:25 
```

But, other than that, it seems like good code to me.
Try what **Waappu** says first.

If your still getting difficulties.
Try setting it 10/15 minutes from now, reboot your PC. 
Then wait for it to supposedly run.

Regards
Iain

---

### Post by Rizla on 2008-04-03
**This post could be related to an Ubuntu bug filed at**: > **WW said:**
> Take a look at the egrep man page: [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				[QUOTE=tinivole;4645978]Well, I may have different software installed to you, cos all I'm getting is:
```
 ssmtp: Cannot open mail:25 
```

But, other than that, it seems like good code to me.
Try what **Waappu** says first.

If your still getting difficulties.
Try setting it 10/15 minutes from now, reboot your PC. 
Then wait for it to supposedly run.

Regards
Iain

I did what wapuu suggested, it seems the cron job is running successfully becasue i see the edits in the files, but I just wish the last operation would work to send the email.

---

### Post by Rizla on 2008-04-03
**This post could be related to an Ubuntu bug filed at**: [QUOTE=WW;4645841]Take a look at the egrep man page: [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				to add further mystery to the equation, i looked at my mail log and I see all the SUCCESSFUL outgoing email.  I never recieved them in my outlook inbox.  I get them when i just run the script from command line.

How weird is this??

---

### Post by ibuclaw on 2008-04-03
I've just had a small look round.

It seems that ssmtp is abandonware (isn't maintained anymore.)

Perhaps trying something a little more up-to-date:

Such as:
[B] o msmtp
 o postfix
 o sendmail[/B]

Regards
Iain

Hmm... Yes, It is weird :)

---

### Post by Rizla on 2008-04-03
**This post could be related to an Ubuntu bug filed at**: > **WW said:**
> Take a look at the egrep man page: [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				[QUOTE=tinivole;4646062]I've just had a small look round.

It seems that ssmtp is abandonware (isn't maintained anymore.)

Perhaps trying something a little more up-to-date:

Such as:
[B] o msmtp
 o postfix
 o sendmail[/B]

Regards
Iain

Hmm... Yes, It is weird :)

i like ssmtp becuase its really light weight.  Turns out though, i modified it to sendmail and it still sends the emails properly via the command line, but when not through the damn cron job.  AAARG!

---

### Post by ibuclaw on 2008-04-03
shrink...

This post was nullified.

---

### Post by ghostdog74 on 2008-04-03
make sure your cron daemon is running..

---

### Post by Rizla on 2008-04-04
**This post could be related to an Ubuntu bug filed at**: > **WW said:**
> Take a look at the egrep man page: [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				[QUOTE=tinivole;4646425]Hi, I've just had a small play about (sorry I took so long)

But maybe your answer is to **NOT** use a cronjob. But to incorporate a script that does nothing until a designated time:

Here is my concept
[PHP]
#!/bin/bash

startloop()
{
# Run function gettime.
    gettime
}

gettime()
{
# Gets the time, then runs waitfortime with the time as the argument.
    export thetime=$(date)
    waitfortime $thetime
}

waitfortime()
{
# Removes the colons in the time and separates the hour and minute numbers.
    export thetime=$(echo $4 | sed -e "s/:/ /g")
    settime $thetime

# Simply, if the hour isn't 22 and the minute isn't 40 (as set below)
# Then we go a full circle back to gettime.
# Else, we go to endloop.
    if [ $hour == $runhour ]
    then
	if [ $minute == $runminute ]
	then
	    endloop
	else
	    gettime
	fi
    else
	gettime
    fi
}

settime()
{
# sets current time to the appropriate strings
    hour="$1"
    minute="$2"
}

endloop()
{
# What to execute once the time is right.
    echo "FINISHED"
    exit
}

### main logic ###
runhour="22"
runminute="40"
startloop
[/PHP]

I've given it a few runs, and** it appears to not take up any memory whatsoever to run.**
Though a few more tests are needed first.

To give it a cronjob type of personality.
Edit the **endloop** function to something like this:
[PHP]
endloop()
{
    echo "RUNNING SCRIPT"
    ### Your Script Here ###
    wait 60
    startloop
}
[/PHP]

So the script is neverending.
Unless you insert a virtual lock file into the equation.
ie:
[PHP] touch /home/username/.myscript.lock [/PHP]
creates an empty file.
[PHP]
checklock()
{
    if [ -f /home/username/.myscript.lock ]
    then
        run-next-function
    else
        exit
    fi
}
[/PHP]
checks that the file is still there. If not, the script ends.

And lastly, to have it run everytime you login.
Add something like this to **/etc/gdm/PreSession/Default** before "**exit 0**"
[PHP] sh /path/to/script [/PHP]
and this goes in the **/etc/gdm/PostSession/Default** before "**exit 0**"
[PHP] rm -f /path/to/lockfile [/PHP]


I Hope that I have given you a lot to think about.

It seems like a relevant fix/work-around for the setbacks of cronjob, plus it** should have better integration with your system**. (Not to forget, it may actually work for a change :) )

Regards
Iain

Wow, thanks for taking the time to write that out, but instead of coming up with a work around I want to make sure I dont have an issue that i'm over looking.  The script works fine when executed from the CLI, but in cron the script still runs, downloads the file, greps, appends output to file, but does not send the email.  I looked at the mail log and it shows that it was sent, but i dont get it.

I have no idea from a troubleshooting perspective where the gotcha is.  Hopefully its something simple i'm over looking.  Does cron need any special permissions to email?

---

### Post by ibuclaw on 2008-04-04
This post is meantioned below...

---

### Post by Rizla on 2008-04-05
> **tinivole said:**
> OK, I've been thumping my head for the past hour or so.

Then it came to me to not look at what you have, but what you don't...

Okay, this is what we have at the moment
[PHP]  06 16 * * * /home/myuser/myip.sh [/PHP]

Now lets examine a cronjob from **/etc/crontab**
[PHP] 25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ) [/PHP]
AHHH!!!

All may be clear now...

OK, for a fully blown version of perhaps what your cronjob should look like.
[PHP] 06 16 * * * **username** test -x /usr/sbin/anacron || ( cd / && run-parts --report /home/**username**/myip.sh )[/PHP]
But this can be slimmed down.
[PHP]  06 16 * * * **username** cd / && run-parts --report /home/**username**/myip.sh[/PHP]
And this will probably work in the same manner too.
[PHP]  06 16 * * * **username** /home/**username**/myip.sh[/PHP]
Try those as templates, one of them (if not all) should be bound to work.
sorry for the generally long time to get here.

Regards
Iain

should i try those in my crontab -e or the actual /etc/crontab file?

in crontab -e it doesnt specify a user.  Also i take it the **...** were just formatting input put in by the web browser right?  Not something I should put in the contab file

---

### Post by ibuclaw on 2008-04-05
yeah, the (b) (/b) was just web formatting gone wrong:lolflag:

give it a try.

erm, try it on both.

first **crontab -e**,
then the **/etc/crontab** file.

I should of posted it this way
```
 06 16 * * * **username** /home/**username**/myip.sh 
```

And try it with anacron and run-parts working the script too.

It's got to be answer. I just can't see it being anything else.

Regards

---

### Post by Rizla on 2008-04-08
i've been a little busy the past couple days and havent been able to try the other two option, but i got to it today.  Still no luck..  same issue.  Script runs, but no email sent.

---

### Post by Rizla on 2008-06-05
Not sure if it will help anyone, but I got it to work awhile ago.  i basically had to take the send mail command out of the shell script and just create a new crontab entry to send the email.  Works well.  I've been recieving emails everyday since i've fixed it.  Man, i'm really in love with linux now.. 

got some new books on shell scripting, on bash itself, a pocket refrence guide, a squid proxy server book, next i need a good reg ex book to round me out.

---

