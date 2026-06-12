---
title: "crontab"
date: 2008-05-24
forum: General Help
---

### Post by frenchface on 2008-05-24
I have Ubuntu Server 8.04LTS (Hardy Heron). I have several perl scripts that I need to automatically run daily, each script needs to run a on different hour and their are a total of 24 scripts. THey are all located in /var/www/cgi-bin/ All of the scripts work print to a .txt if i manually run them. I created a crontab called auto which is in the same directory as all the other files. when I type crontab -l this is what is shows me

0 0 * * * 0.pl
0 1 * * * 1.pl
0 2 * * * 2.pl
0 3 * * * 3.pl
0 4 * * * 4.pl
0 5 * * * 5.pl
0 6 * * * 6.pl
0 7 * * * 7.pl
0 8 * * * 8.pl
0 9 * * * 9.pl
0 10 * * * 10.pl
0 11 * * * 11.pl
0 12 * * * 12.pl
0 13 * * * 13.pl
0 14 * * * 14.pl
0 15 * * * 15.pl
0 16 * * * 16.pl
0 17 * * * 17.pl
0 18 * * * 18.pl
0 19 * * * 19.pl
0 20 * * * 20.pl
0 21 * * * 21.pl
0 22 * * * 22.pl
0 23 * * * 23.pl

so i believe that means that they are registered with the cron stuff. 
anyone have any ideas on what the problem might be? 

thanks

---

### Post by drs305 on 2008-05-24
Is /var/www/cgi-bin/ in your path? If not, add a path statment at the top of the crontab file (PATH= add this to the end of your path  :/var/www/cgi-bin/ ).

If that doesn't work you might want to post one of the pl files.

---

### Post by frenchface on 2008-05-24
ok i changed all of the paths and now they all look like this

0 0 * * * /var/www/cgi-bin/0.pl


also here is the perl script that it needs to run, i do knwo for sure that teh script works


my $url = 'http://en19.tribalwars.net/map/tribe.txt';
use LWP::Simple;
my $content = get $url;
open W,">0.txt";
@array=split(/,/, $content);
$n=1;
$j=4;
do
{
         print W  "@array[$n] @array[$j]\n";
         $n=$n+5;
         $j=$j+5;
}
while ($n<=$#array);
close W;

---

### Post by drs305 on 2008-05-24
I don't use perl but I am pretty sure you need to designate the path to perl at the beginning of the file. If you do a search for crontab and perl you can probably find an answer if no one comes to your assistance here.

---

### Post by frenchface on 2008-05-24
do you mean like #!/usr/bin/perl ??

---

### Post by frenchface on 2008-05-24
do you mean #!usr/lib/perl?

---

### Post by Bruce M. on 2008-05-24
> **frenchface said:**
> do you mean #!usr/lib/perl?

That's right. - without the ? though  :)

---

### Post by frenchface on 2008-05-24
i added that to all the scripts i'll see if it stars to work

---

### Post by ibuclaw on 2008-05-24
First line should look like this:
```

#!/usr/bin/perl

```
And also. Sorry if this sounds odd...

But are all the scripts identical?
If so, why not just have one script put inside the "**/etc/cron.hourly**" folder? (Or at the very least have one script that is ran hourly).

Regards
Iain

---

### Post by frenchface on 2008-05-24
no they are not identically. otherwise that would have made it alot easier

---

### Post by frenchface on 2008-05-24
also it is still nto running, that is unless the server clock is wrong, can someone tell me how to see what time it is and possibly change the time? also give me any other things to look for to why it isnt working

---

### Post by ibuclaw on 2008-05-24
> **frenchface said:**
> no they are not identically. otherwise that would have made it alot easier

Ah, Ok. I understand.
Although, I am a lazy person, so I'd just through it all into one script anyway. :D

---

### Post by frenchface on 2008-05-24
well how would i go about changing the time?

---

### Post by ibuclaw on 2008-05-24
OK, change subject. I think I've spotted a possible line that may be wrong.
[QUOTE=frenchface]open W,">0.txt";[/QUOTE]
Where do you expect the text files to be saved?

Try altering it to something like:
```
open W, ">/home/frenchface/cron/output/0.txt";
```
Ideally, a place where you have write access is a good start.

Iain

---

### Post by frenchface on 2008-05-24
well the txt files are being saved in /var/www/cgi-bin/ which is the same place that all the files are in. Now i know that the scripts them self do work because if I type perl 0.pl then the script executes properly

---

### Post by drs305 on 2008-05-24
> **frenchface said:**
> well the txt files are being saved in /var/www/cgi-bin/ which is the same place that all the files are in. Now i know that the scripts them self do work because if I type perl 0.pl then the script executes properly

Did you make the change as suggested by tinivole in post #14? The files are being written to /var/www/cgi-bin/ if you still have the line
```
open W,">0.txt";
```

Change the text after ">"  to a path to a folder you have write privileges to. See tinivole's example.

---

### Post by frenchface on 2008-05-24
ok it is not working.


do i not have write privalges to all the folders? what if i change the permissions of the folder is that what i need to do?

---

### Post by ibuclaw on 2008-05-24
> **frenchface said:**
> ok it is not working.

do i not have write privalges to all the folders? what if i change the permissions of the folder is that what i need to do?
[EDIT]

Try modding the lines to something like this:
```
0 * * * *   cd /var/www/cgi-bin/ && perl 0.pl
```

Then type in:
```
sudo chown $USERNAME:$USERNAME /var/www/cgi-bin
```

Regards
Iain

---

### Post by frenchface on 2008-05-24
ok i did it, i'll let you knwo if it works or not

---

### Post by frenchface on 2008-05-24
what idd the command do that you had me type in?

---

### Post by ibuclaw on 2008-05-24
> **frenchface said:**
> what idd the command do that you had me type in?

> **tinivole said:**
> 
```
0 * * * *   cd /var/www/cgi-bin/ && perl 0.pl
```

Change Directory to the location of the perl scripts.
If successful (return code 0, directory exists) then run the script given.


> **tinivole said:**
> 
Then type in:
```
sudo chown $USERNAME:$USERNAME /var/www/cgi-bin
```

Change the ownership and group ownership of the /var/www/cgi-bin directory (just the parent layer, not the subdirectories) from (what I presume must be) root to your username.

Hopefully, the files will be saved now.

Regards
Iain

---

### Post by frenchface on 2008-05-24
i dont know if this is the problem but there is no root user, as in no one can log in as a root user, but there is a sudo command that i user, i'm a noob so i dont know if that would do anything or not, just throwing out a thought

---

### Post by frenchface on 2008-05-24
it is still not working, to run the script manually i have to tyep perl 0.pl so do we need to put perl 0.pl in the crontab?

---

### Post by frenchface on 2008-05-25
does the crontab have an error log that i can look at?

---

### Post by frenchface on 2008-05-25
i believe it is now working, i dont remember what i did for sure, but i believe it is now working, thakns for everyoenes help

---

