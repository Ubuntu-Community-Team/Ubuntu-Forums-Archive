---
title: "Cron Command"
date: 2008-04-08
forum: General Help
---

### Post by chrisbish on 2008-04-08
I'm running Linux Mint and trying to use the cron command to switch off the computer at a specified time.
Running the command 

> /sbin/shutdown -P now

in the root terminal worked OK. However when I try using the time function of the cron command such as

> 05 18 * * *   root  /sbin/shutdown -P now

It dose not work.

I am using the program gnome-schedule.

Please help as I'm stuck now!

---

### Post by redbob on 2008-04-08
You could use the command 'halt', instead of shutdown. Try to put it:
> 05 18  * * *   sudo halt -p -f 

---

### Post by chrisbish on 2008-04-08
ok i will try that

thanks

---

### Post by ibuclaw on 2008-04-08
Also you can make a script and save as a file in your cron.daily folder
ie:
```
 sudo gedit /etc/cron.daily/shutdown.sh 
```

The script can be something like this
```

#!/bin/bash

gettime()
{
    export thetime=$(date)
    checktime $thetime
}

checktime()
{
    export thetime=$(echo $4 | sed -e "s/:/ /g")
    settime $thetime
    
    if [ $hour == $runhour ]
    then
	if [ $minute == $runminute ]
	then
	    endscript
	else
	    exit 1
	fi
    else
        exit 1
    fi
}

settime()
{
    hour="$1"
    minute="$2"
}

endscript()
{
    poweroff
}

### main logic ###
runhour="18"
runminute="5"
gettime

```
The reason why it's setup as so, so that it doesn't interfere with your other daily cronjobs.

Then open up the crontab file as root.

```
 sudo gedit /etc/crontab 
```
And add this to the list of cronjobs.
```
 05 18   * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily/shutdown.sh ) 
```

This can be heavily simplified, I know, but at least it can do the job!

Regards
Iain

---

### Post by chrisbish on 2008-04-08
@redboob

Thanks for your reply but it didn't seem to work.

@tinivole

I'll try using the script and I'll get back to you if it works.

---

### Post by chrisbish on 2008-04-08
> **tinivole said:**
> Also you can make a script and save as a file in your cron.daily folder
ie:
```
 sudo gedit /etc/cron.daily/shutdown.sh 
```

The script can be something like this
```

#!/bin/bash

gettime()
{
    export thetime=$(date)
    checktime $thetime
}

checktime()
{
    export thetime=$(echo $4 | sed -e "s/:/ /g")
    settime $thetime
    
    if [ $hour == $runhour ]
    then
	if [ $minute == $runminute ]
	then
	    endscript
	else
	    exit 1
	fi
    else
        exit 1
    fi
}

settime()
{
    hour="$1"
    minute="$2"
}

endscript()
{
    poweroff
}

### main logic ###
runhour="18"
runminute="5"
gettime

```
The reason why it's setup as so, so that it doesn't interfere with your other daily cronjobs.

Then open up the crontab file as root.

```
 sudo gedit /etc/crontab 
```
And add this to the list of cronjobs.
```
 05 18   * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily/shutdown.sh ) 
```

This can be heavily simplified, I know, but at least it can do the job!

Regards
Iain

I followed your instructions, and the cron job I entered in sudo gedit /etc/crontab  dosn't appear when I type  crontab -e.

---

### Post by ibuclaw on 2008-04-08
Ah, OK.
That be because it's a system cronjob, and not a user one.

Sorry, my fault. I should've taken that into account.

I suppose I should of really also asked, "do you want your PC to shutdown everyday at 18:05?"
Because, that's the time variable that I set in the script (ie: if you try the run the script at any other time, the script will exit without shutting down).


To make it a user one, remove the line that you put in the /etc/crontab file.

Run "crontab -e" and copy&paste it there.

Regards
Iain

---

### Post by pjkoczan on 2008-04-08
> **chrisbish said:**
> I'm running Linux Mint and trying to use the cron command to switch off the computer at a specified time.


FWIW, if you're just looking to do this as a one-off thing (say you want to shutdown today at 8 PM but tomorrow is something different), you should look at the "at" command.

But if it's something you want to do everyday, cron works nicely.

As far as the question goes, have you tried setting root's crontab? For instance:

```
sudo crontab -u root
```

And then edit the crontab appropriately. I don't know if it will work for scheduling an automatic shutdown, but it's worth a shot.

---

### Post by unutbu on 2008-04-08
Hello, a few newbie questions:

1) Is the format for /etc/crontab different than the format for a user's crontab?
In particular, if I'm reading `man 5 crontab` correctly, isn't the sixth field for /etc/crontab the username, but for regular users there is no such field? If that's the case, and the OP wants to add the line to his user crontab, shouldn't the line be

```
05 18   * * *       test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily/shutdown.sh )
```

2) Don't you have to be root to shutdown/poweroff the machine? If that's so, then how can the script work if the OP is editing his user crontab rather than /etc/crontab?

3) Does it make sense to run a poweroff script as a normal user? Isn't tinivole's original post correct where he instructs the OP to edit /etc/crontab?

4) What is the point of  "test -x /usr/sbin/anacron" ? This checks if anacron exists and is executable right? But... so what? If it's there the test returns true and the script is run, but if it's not the test returns false and the script is still run. Please excuse me. I really don't understand bash very well.

5) While I'm at it, what does "run-parts --report" do? Where is the verbose output printed to? The man page was not very helpful.

Many thanks in advance!

---

### Post by pjkoczan on 2008-04-08
> **unutbu said:**
> Hello, a few newbie questions:

1) Is the format for /etc/crontab different than the format for a user's crontab?
In particular, if I'm reading `man 5 crontab` correctly, isn't the sixth field for /etc/crontab the username, but for regular users there is no such field? If that's the case, and the OP wants to add the line to his user crontab, shouldn't the line be

```
05 18   * * *       test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily/shutdown.sh )
```


It's slightly different. user crontabs live under /var/spool/cron/[username], and all jobs are run as [username] so there's really no need for the sixth name field under "user" crontabs.

I honestly don't know what the major differences are between /etc/crontab or the normal user crontabs. It appears to be "system" jobs vs. "user" jobs, but that distinction doesn't seem to be strongly enforced. I should also note that root can have a crontab under /var/spool/cron, so root cron jobs can go there, as well.

> 2) Don't you have to be root to shutdown/poweroff the machine? If that's so, then how can the script work if the OP is editing his user crontab rather than /etc/crontab?

Usually, but with recent power management stuff in hardware, the lines are blurred. I've been able to shutdown systems with user-level accounts when I shouldn't have.

I do think that the shutdown command does require root privileges, though.

> 3) Does it make sense to run a poweroff script as a normal user? Isn't tinivole's original post correct where he instructs the OP to edit /etc/crontab?

To me, it doesn't make sense to run shutdown as anything but root. However, to others, it may. One suggestion I gave was to edit root's crontab out in /var/spool/cron (via the crontab command), so shutdown would still be running as root. However, I'm not sure if it have the same effect as editing /etc/crontab, so caveat emptor.

> 4) What is the point of  "test -x /usr/sbin/anacron" ? This checks if anacron exists and is executable right? But... so what? If it's there the test returns true and the script is run, but if it's not the test returns false and the script is still run. Please excuse me. I really don't understand bash very well.

|| means "or", specifically a short-circuited or. It looks at the return code of the test command and decides whether or not to run the following command.

If the test succeeds, the return code is 0 (false), bash then has to execute the next part of the expression determine its truth value. If the test fails, the return code is not 0 (true), bash can assume the entire expression is true, and doesn't need to evaluate the second part of the expression.

It's a common bit of common programming "magic" in a lot of different languages (perl especially).

> 5) While I'm at it, what does "run-parts --report" do? Where is the verbose output printed to? The man page was not very helpful.

Many thanks in advance!

It's printed to stdout/stderr, but only names of scripts that produce output get printed.

---

### Post by ibuclaw on 2008-04-08
> **unutbu said:**
> Hello, a few newbie questions:
Many thanks in advance!

1) Yes, it appears so.

2) No, you don't. you can try it for yourself. Type in the word "poweroff" and your computer will turn off in some 4 seconds flat.
**shutdown** on the other hand I think **does** require root privileges.

3) Having it in the system crontab is more convenient. I find that it intergrates well with the system. 

4) Have you looked up anacron? I prefer to use it as it easier to handle. As it doesn't treat your PC like it is constantly on. ie: If you were to boot up your PC at 18:04 in this example, then 1 minute later, because of the cronjob, it would power-down unexpectedly to the user.

You can tweak anacron  to work more sensibly than that. So that wouldn't happen.

5) run-parts is another neat little tool to run scripts for you. Report doesn't do much, if all goes well, but you get a nice mail through your mbox if it doesn't execute as planned. (At least, that's what I find when I include it in).

try it for yourself. Type in **mail** in the terminal and see what you get.

Regards
Iain

---

### Post by unutbu on 2008-04-08
Many thanks for the information, pjkoczan and tinivole!
I'm more confused than ever!

Pjkoczan, please forgive me if I am wrong, but I am going to try to interpret the spirit of what you wrote instead of what you wrote: Did you mean to say:
> 
If the test **fails**  the return code is 0 (false), bash then has to execute the next part of the expression determine its truth value. If the test **succeeds**, the return code is not 0 (true), bash can assume the entire expression is true, and doesn't need to evaluate the second part of the expression.

But if that's true, then look at what
```

test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily/shutdown.sh )

```
is going to do. On a normal Ubuntu system, /usr/sbin/anacron is present and executable, so the test returns true. 'True' satisfies the || operator, so the second half is not executed. How is that a good thing? The shutdown script will not be executed by cron. I suppose testing for the presence of anacron is really trying to determine if /etc/init.d/anacron is being run. (Let's assume that works, though it sounds iffy to me.)

If I understand correctly, the purpose of anacron is to catch up on cron jobs that weren't run at their scheduled times because the machine was off. Does this mean if the user happened to shut off the machine before 18:05, then the next time he boots up anacron will run the scripts in /etc/cron.daily and promptly shutdown his machine? That doesn't sound good. Oops -- the shutdown script checks what time it is, so it is safe to run at any time. Nevertheless, given that execution of the shutdown script is left up to anacron, the question becomes will anacron run shutdown.sh at exactly 18:05? I don't see why it would.

And one more thing: poweroff may not work for the OP if run as a normal user:
```

22:22:21 cyrano@farmer:~% poweroff
poweroff: Need to be root
```

I wonder why this works for tinivole but not for me.

---

### Post by redbob on 2008-04-08
It's exactly that! I forgot to mention it, because I thought it has been understood. Crontab must be open by root, otherwise it will not execute this sched. Just type 
> sudo crontab -e
insert this line
> 05 18 * * * sudo halt -p -f
Save the file then it will work. In my machines it works like a charm.

---

### Post by pjkoczan on 2008-04-09
> **unutbu said:**
> Pjkoczan, please forgive me if I am wrong, but I am going to try to interpret the spirit of what you wrote instead of what you wrote: Did you mean to say:

No, I meant exactly what I said, the spirit is the same as the letter in this case. Most programs return 0 if they succeed and non-zero if they fail for some reason (as a matter of convention). Then you can use the non-zero code to try to figure out what went wrong. The || operator will then work as I described it.

I admit that it's a little hard to get your head around at first glance and it helps to know some programming to truly understand it.

---

### Post by unutbu on 2008-04-09
pjkoczan, thanks for the response. Okay, so I should believe, as you originally wrote:

> If the test succeeds, the return code is 0 (false)...

But if that is true, then the following script should print "test returned false" because /usr/sbin/anacron exists and is executable on my system:

```
if [ -x /usr/sbin/anacron ]; then
echo "test returned true"
else
echo "test returned false"
fi
```

But in fact,
23:20:49 cyrano@farmer:~% test.sh
test returned true

---

### Post by chrisbish on 2008-04-09
> **tinivole said:**
> Ah, OK.
That be because it's a system cronjob, and not a user one.

Sorry, my fault. I should've taken that into account.

I suppose I should of really also asked, "do you want your PC to shutdown everyday at 18:05?"
Because, that's the time variable that I set in the script (ie: if you try the run the script at any other time, the script will exit without shutting down).


To make it a user one, remove the line that you put in the /etc/crontab file.

Run "crontab -e" and copy&paste it there.

Regards
Iain

I do want it to shut down everyday.

---

### Post by redbob on 2008-04-09
Chrisbish:

you must know that each user you create in your system has got its own crontab file. If you insert this shutdown command in your account or in anyelse, that user must be logged to execute this command. If you open crontab with "sudo crontab -e", it will be executed by root, it means you will not be logged to execute this command. Other difficulty to insert system commands in user crontab is that if someone is logged in the computer, the system will not execute the command because there is this open account. Sudo will enforce shutdown not regarding whether is logged or not.

---

### Post by pjkoczan on 2008-04-09
> **unutbu said:**
> But if that is true, then the following script should print "test returned false" because /usr/sbin/anacron exists and is executable on my system:

But in fact,
23:20:49 cyrano@farmer:~% test.sh
test returned true

There is a big difference between testing the truth value of an expression in an if statement and interpreting the return code of a program. The latter, you can determine by examining the value of the variable $?

For instance,

```

[koczan@ator] ~ $ ls -l /usr/sbin/anacron
-rwxr-xr-x 1 root root 27904 Dec 18  2006 /usr/sbin/anacron*
[koczan@ator] ~ $ ls -l .bashrc
-rw-r----- 1 koczan koczan 2931 Mar 10 15:31 .bashrc
[koczan@ator] ~ $ test -x /usr/sbin/anacron
[koczan@ator] ~ $ echo $?
0
[koczan@ator] ~ $ test -x .bashrc
[koczan@ator] ~ $ echo $?
1

```

So, what I described is what it's doing. Why the user decided to put that entry in the crontab that way I'm not exactly sure. You'd have to ask them.

---

### Post by unutbu on 2008-04-09
chrisbish,
Have you found the solution you were looking for?
I've tried redbob's. His solution is far simpler and it works... except for one thing: the halt command knocks your computer out like a light -- no chance for any running process to exit gracefully. When you reboot you'll see a couple orphaned inodes in your dmesg.

I think this slight modification of redbob's method fixes that problem:
```

sudo crontab -e
```

Add the line
 
```
05 18 * * * /sbin/shutdown -P now
```

sudo is not necessary in the crontab line because this is root's crontab.

---

### Post by unutbu on 2008-04-09
pjkoczan, thank you for explaining to me something which I find very unintuitive about bash. If I understand correctly, test returns 0 when the test succeeds.
The bash 'if' operator executes the 'then' commands when an 'if' test returns 0. So as far as 'if' is concerned, zero is true. But the || operator interprets 0 as false and therefore has to go on and execute the second half.

Do I finally have it right?

---

### Post by unutbu on 2008-04-09
Uh oh. Confusion city! 

```
#!/bin/bash
[ -x /usr/sbin/anacron ] || echo "return val = $?. Printing anacron line"
[ -x ~/.bashrc ] || echo "return val = $?. Printing bashrc line"

```

20:18:50 cyrano@farmer:~% test.sh
return val = 1. Printing bashrc line

There must be something wrong with your original statement, pjkoczan:
> 
"If the test succeeds, the return code is 0 (false), bash then has to execute the next part of the expression determine its truth value."

[ -x /usr/sbin/anacron ] succeeds, and the return code is 0. I agree. But the test.sh script does not print "Printing anacron line", so || must interpret that 0 as true, not false, and the next part of the expression was not executed.
> 
"If the test fails, the return code is not 0 (true), bash can assume the entire expression is true, and doesn't need to evaluate the second part of the expression.

[ -x ~/.bashrc ] fails, and the return code is not 0. I agree. But the test.sh script does print "Printing bashrc line", so || must interpret the non-zero value as false, and hence is force to execute the next part of the expression.

So for the record, I think the correct statement must be

> 
If the first test succeeds, then the return code is 0 (true) and the || operator can assume the entire expression is true, and doesn't need to evaluate the second part of the expression. If the first test fails, then the return code is not 0 (false) and the || operator then has to execute the next part of the expression to determine its truth value. 


---

### Post by pjkoczan on 2008-04-09
> **unutbu said:**
> pjkoczan, thank you for explaining to me something which I find very unintuitive about bash. If I understand correctly, test returns 0 when the test succeeds.
The bash 'if' operator executes the 'then' commands when an 'if' test returns 0. So as far as 'if' is concerned, zero is true. But the || operator interprets 0 as false and therefore has to go on and execute the second half.

Do I finally have it right?

Almost (we're so very close). There's one key difference...

"test -x /usr/sbin/anacron" means that you're actually running a program, apart from bash. The return value is the *external program's* return code, not necessarily the truth value of the arguments.

"if [ -x /usr/sbin/anacron ]; ..." means that bash is trying to interpret an expression natively, within bash (since -x [file] can be interpreted by bash). This is part of the bash programming language, and bash isn't running a program.

If you think about it and know a little bit of C programming, it makes sense. Certainly, though, it can be a source of confusion. Unfortunately, I can't think of any quick and easy analogies to illustrate my point.

---

### Post by redbob on 2008-04-09
Wow, ubutnu!
I liked your suggestion. Really shutdown is more graceful than halt. I already changed my crontab commands. 

Chrisbish and pjkoczan:

What a salad you're doing! Sincerelly, do you want to shutdown a machine or "deactivate" a bomb?
:popcorn:

---

### Post by chrisbish on 2008-04-10
Thanks to you guys for responding.
I got it to work in the end buy using

> sudo gedit ~/.bashrc

and adding to the end of the script:

> shutdown -h 23:00

This works fine and is a simple command.

I have another problem now which is to do with starting up. I'm using the bios power management option , Resume on Alarm. With this I can set the start up time but if I allow Linex Mint to boot up past the countdown display stage, the the bios resume command does not work the next time the PC is powered down. The motherboard is a Foxconn 520A with Award bios. I've carried out the same test on a borrowed Asrock board with American Megatrends bios. This worked fine.

Does anyone know if Award bios is not compatible with Linux?
Is there anything I can do to get the Award bios to work?
What do people find is a good bios  for Linux?

---

### Post by ibuclaw on 2008-04-10
Hi. I'm glad that you've found an answer that suits you.

As for your question, I believe that you should really open up a new thread to ask it, as you will get a better answer.

But on the topic on BIOS, I suppose I don't really take much notice. But now I come to think of it. When I started Linux, I had a WinFast (Leadtek) BIOS, and I had a lot of trouble getting things to run smoothly, in the end I found a loving home with Debian Etch, as it was the only OS that worked to the efficiency to meet my needs.
And I have had a love for all things Debian since.

But that motherboard has since outlived its time by the better amount of 2/3 years (thanks to Linux), and I've since bought a new motherboard (well... cheap motherboard, first manufacturered in 2005).
And, though I may have taken things for granted, or thought it as proof as my expanding knowledge to keep up and maintain the Linux Operating System. I have definitely noticed an overall improved and smoother usage with interaction between hardware and software. Thus I have expanded onto many OS' that I once couldn't work with.

Oddly enough it is too an American Megatrends motherboard, but this may seem as no surprise in context with what you say.

Maybe American Trends make better motherboards for Linux, maybe it's just coincidence. I'm not really in the know to say.

What I do know, is that new, fresh off the market motherboards generally have less compatibility with Linux as manufacturers don't build them with Linux compatibility in mind. Thus it takes around 6 months to  year to develop the code to get them working to a usable level.

As for certain types of motherboards working better than others... It may certainly seem as a possibility, as there are few vendors who develop open hardware/release their datasheets of the hardware (afterall, staying ahead of the competition is quite obviously harder if the competition can see what you're made of).
And as reverse engineering every motherboard in existance would be a needlessly slow process, not to forget to mention the lack of developers to carry out the task. As with everything else in Linux, the answer is once again, "varied".

Though, check your BIOS settings, just to be sure. Make sure every setting is setup right. As there could be a flaw within it.

But back at hand, open a new thread. You'll get a better answer. People will read the title "Cron Command" and will think that you're still asking a question on that topic, thus people with knowledge of cronjobs will reply.

A new thread with a relevant title will attract the right attention.

Regards
Iain

---

