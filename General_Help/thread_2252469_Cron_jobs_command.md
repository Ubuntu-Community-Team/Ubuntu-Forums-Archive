---
title: "Cron jobs command"
date: 2014-11-12
forum: General Help
---

### Post by pcknights2 on 2014-11-12
Hi guys,
I have an issue with Cron jobs
I have a php script in a page for sanity sake lets say [http://www.testemail.co.uk](http://www.testemail.co.uk)
When I visit the page with a browser it send an email to a specific email.

Now I want to set Cron to run this page every hour but I dont know how
I tried the command below but it didn't sent the email. I know that the URL is working because if i visit it from a browser it send the email.
0 * * * * wget [http://www.testemail.co.uk](http://www.testemail.co.uk)

Any help will be much appreciated.

---

### Post by TheFu on 2014-11-12
There is no PATH set - use the full-path-to-every-command.  Cron doesn't have any environment. Know it, love it. That means you must setup any environment you'd like each task to have.

Also, using the @hourly alias might be a good idea, though not necessary.

---

### Post by etescartz on 2014-11-12
First of all the whole point of this eludes me.
And secondly why don't you telnet on the web service port in you using cronjob ?  telnet "sitename" 80

Also consider using "curl" instead of "wget" or even a command line web browser like [these]("https://askubuntu.com/questions/29540/browsing-the-internet-from-the-command-line").

---

### Post by SeijiSensei on 2014-11-12
Why not run the script locally so you can use "php /path/to/the/script" in cron rather than executing it on a remote site?

---

### Post by pcknights2 on 2014-11-12
ok[**[COLOR=#000000] etescartz [/COLOR]**]("http://ubuntuforums.org/member.php?u=1141045")The scenario in my case is not exactly like that I have made it simpler, in order to find a solution.
I am noob both to ubuntu and cron job so I am asking for some help.
I just want to set the cron jobs to open the url every hour.
This can be done right?

---

### Post by pcknights2 on 2014-11-12
The script is on a specific website [**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195")

---

### Post by pcknights2 on 2014-11-12
TheFu can you please provide more details what path do you mean?

---

### Post by pcknights2 on 2014-11-12
if i use instead the following command will make any difference?
0 * * * * wget -O /dev/null "[http://www.testemail.co.uk](http://www.testemail.co.uk)"

---

### Post by TheFu on 2014-11-12
> **pcknights2 said:**
> if i use instead the following command will make any difference?
0 * * * * wget -O /dev/null "[http://www.testemail.co.uk](http://www.testemail.co.uk)"

No - that will not help.
PATH - is the list of directories where commands are searched. Under cron, there is no PATH unless you set it. It is a best practice to assume no environment in any non-interactive work, thus specifying the exact, full, path to every command is needed. Every OS works this way - all of them from MVS to DOS to Windows to UNIX to Linux.

Where is wget on the file system?  which wget on my system says: ```
$ which wget
/usr/bin/wget
```

So ```

0 * * * * /usr/bin/wget -O /dev/null http://www.testemail.co.uk
```
is what I'd use (though I'd really create a script file and call it.  Plus know there isn't any default CWD, so ... if you do want to store anything you'll need to fully specify any output locations too.

Scripting 101 stuff.  You are at the stage where [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) that book will help. Skim the first 100 pages and flip through the rest of the book so you know where to look for information later. It will save hours, days, weeks, months of frustration over stuff like this.

---

### Post by btindie on 2014-11-12
use
```
0 * * * * /usr/bin/curl "http://www.testemail.co.uk" >/dev/null
```

---

### Post by pcknights2 on 2014-11-12
Thanks for all your help 
I am on it to try it now

---

### Post by pcknights2 on 2014-11-13
Ok Mates,
What I Did
1) crontab -e
2)Enter
3)After the lines with the # I added a new line
50 * * * * /usr/bin/wget -0 /dev/null [http://www.testemail.co.uk](http://www.testemail.co.uk)
This was set yesterday on 17:30
It didnt work no email was send
TheFu I did $ which wget and returned /usr/bin/wget

Any other has any other suggestions that I can try?

---

### Post by pcknights2 on 2014-11-13
Any other has any other suggestions that I can try?

---

### Post by TheFu on 2014-11-13
Why should email be sent?  Have you setup an MTA to work too?  If so, then it should work fine.  What do the log files show?

BTW, the suggestion to use curl isn't bad - generally curl is used much more in crontabs than wget. I've never used wget inside a crontab like this - always put this stuff into a script and call the script in crontabs.

---

### Post by pcknights2 on 2014-11-13
What the page [http://www.testemail.co.uk](http://www.testemail.co.uk) do is to send a specific email
If I simple visit the URL in my browser it does send the email
I am trying curl right now I will have results in7 min I have set it for 9:35
I will let you know how it goes

---

### Post by pcknights2 on 2014-11-13
[**[COLOR=#000000]btindie[/COLOR]**]("http://ubuntuforums.org/member.php?u=876590") You Curl seems to works
Thanks I will keep testing during the day

---

