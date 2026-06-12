---
title: "Cron job to replace file according to system date"
date: 2019-12-18
forum: General Help
---

### Post by erictherev on 2019-12-18
Hello all,

I am totally new to bash scripting and cron, so please forgive my lack of knowledge.

I am trying to create a cron job that will (most likely via a bash script) compare file names to the system date and replace a file with one that has today's date in the name. This needs to be a job that would run once daily indefinitely.

For instance, I have the following files:

1217.html
1218.html
1219.html
today.html

The system date today is 12/18, so the idea would be to overwrite today.html with 1218.html.

I need to not have the year in the file name, so I would not be able to name the files 12182019.html or 121819.html.

I am sure that this has been addressed in other threads, but I don't know how to word a search to get the results needed. Pointing me in the right direction as far as where to look for ideas on how to do this would be greatly appreciated.

---

### Post by Holger_Gehrke on 2019-12-18
```

mv $(date +%m%d).txt today.txt

```
The '$( ... )' is a command substitution; the command is executed and its standard output substituted for the $(...)-construct (see 'man bash' for the gory details). 'date +%m%d' prints the current date formatted as two digits for month followed by two digits for the day ('man date' for details and other formatting codes).

Holger

---

### Post by erictherev on 2019-12-18
> **Holger_Gehrke said:**
> ```

mv $(date +%m%d).txt today.txt

```
The '$( ... )' is a command substitution; the command is executed and its standard output substituted for the $(...)-construct (see 'man bash' for the gory details). 'date +%m%d' prints the current date formatted as two digits for month followed by two digits for the day ('man date' for details and other formatting codes).

Holger

Thanks for the reply, Holger_Gehrke.

I am assuming I would put this code in a bash script and then execute the code via cron, much as I could run a batch script from the Windows task scheduler. Is there a way to specify that if the file for today's date doesn't exist then it should be left as-is? (i.e. there is no file for today, so yesterday's file is left as today.html)

---

### Post by erictherev on 2019-12-18
Just to clarify, this is intended to be for a web page that will have "on this day..." type content, hence the need to update it daily.

---

### Post by TheFu on 2019-12-18
I won't answer this homework question, but .... 
[https://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](https://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html)

 Holger_Gehrke hit on the date part and looking at the manpage for date.
```
$ date "+%F"
```
There are other format control options which can be interesting.  Put them together, if you like.  Using yymmdd-hhMM is very helpful for sorting.

As for using cron, add this to your crontab as a cheat sheet:
```

# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  *  /full/path/to/command to be executed
# *  *  *  *  *  /full/path/to/command --arg1 --arg2 file1 file2 2>&1
# m h  dom mon dow   command
```
There are how-to guides for doing **crontab -e** or videos.  If you get stuck, post what you have.  Be certain to never assume the PATH is set the way you expect and realize that cron doesn't setup much of any environment.  It is definitely NOT the same as an interactive  login environment.

---

### Post by erictherev on 2019-12-18
> **TheFu said:**
> I won't answer this homework question, but .... 
[https://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](https://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html)

 Holger_Gehrke hit on the date part and looking at the manpage for date.
```
$ date "+%F"
```
There are other format control options which can be interesting.  Put them together, if you like.  Using yymmdd-hhMM is very helpful for sorting.

As for using cron, add this to your crontab as a cheat sheet:
```

# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  *  /full/path/to/command to be executed
# *  *  *  *  *  /full/path/to/command --arg1 --arg2 file1 file2 2>&1
# m h  dom mon dow   command
```
There are how-to guides for doing **crontab -e** or videos.  If you get stuck, post what you have.  Be certain to never assume the PATH is set the way you expect and realize that cron doesn't setup much of any environment.  It is definitely NOT the same as an interactive  login environment.

Thanks for the reply, TheFu.

This isn't exactly a homework assignment. This is for a website I am designing for myself and the church I am working on founding. I will definitely be saving the link to that beginners guide.

As to the date format in the filename, because this is going to be run daily with content repeating annually, I can't do more than the month and day in the file names, but I will be looking over that reference material. Everything I learn about this will be that much more I know...

---

### Post by TheFu on 2019-12-18
> **erictherev said:**
>  I am assuming I would put this code in a bash script and then execute the code via cron, much as I could run a batch script from the Windows task scheduler. Is there a way to specify that if the file for today's date doesn't exist then it should be left as-is? (i.e. there is no file for today, so yesterday's file is left as today.html)

Cron is 1000x lighter than Windows Task Scheduler.   In Windows, creating a new process is extremely heavy. On Unix-like systems, creating a new process is very quick and lite.

Bash can check for all sorts of things about files.  Use the beginning bash scripting guide link to see those tests.  There is a command called 'test' which has a manpage that explains each. Those tests can be used in the bash/sh "if" statements to help decide, but if you run the job only once a day at 11:59p or 12:01a, and only once a day, then there shouldn't be any need to test stuff.  In anacron, there is a @daily method or if you use the  /etc/cron.daily/ directory, then you don't have fine control over the start time.

If you set the job to run at 11:59p, you might want to sleep for 55 seconds before running the move to get closer to midnight.  crontab entries are only possible in 1 minute accuracy, hence the need to control the delay inside your script.  But really, doing this at midnight is probably fine for a small website.

There is an ABSG too, which has more real-world examples.  Google that with "bash ABSG" to find it.

---

### Post by SeijiSensei on 2019-12-18
Create an entry in /etc/crontab by running this command at a terminal prompt.

```
echo "1 0 * * * username mv -f /full/path/to/$(date +%m%d).txt /full/path/to/today.txt"  | sudo tee -a /etc/crontab
```
This will add a procedure to cron that will run Holger's command on the first minute after midnight each day.  (See TheFu's post above.)  The command will be run as user "username" so make sure that user has full permissions on each dated file and also today.txt. Include the full paths for both files starting from the root ("/").

If you want to keep the dated files, you should use "cp" instead of "mv" in this command. That will copy, say, 1219.txt to today.txt and keep the original. The '"mv" ("move") command "forcibly" (-f) renames the dated file as today.txt and keeps no other copy.

This method avoids creating a script to run this single-line command. In fact, you can string commands together in crontab by using the semicolon (";"). I only do that if I have maybe two or three commands. After that creating a script makes more sense.

If these files are being created automatically, I'd use a different time specification in crontab.  If the files are created a 4 am, use something like "2 4 * * * [etc.]" so the renaming of today.txt happens a couple of minutes later.

---

### Post by Impavidus on 2019-12-18
> **Holger_Gehrke said:**
> ```

mv $(date +%m%d).txt today.txt

```

is incompatible with this:
> **erictherev said:**
> 
As to the date format in the filename, because this is going to be run daily with content repeating annually, I can't do more than the month and day in the file names, but I will be looking over that reference material. Everything I learn about this will be that much more I know...
By using mv you remove the old today.html and rename the 1218.html to today.html, so there will no longer be a 1218.html and your 1217.html you renamed yesterday won't come back. In other words, after a year, all your mmdd.html files will be gone.

May I suggest this?```

# Find today's date
today=$(date +%m%d)

# Test for the existence of the file
if [ -e "/path/to/$today.html" ]
then
    # Update the symbolic link to today's file. Use -f to overwrite the link to yesterday's file
    ln -sf "/path/to/$today.html" "/path/to/today.html"
fi
```Instead of copying the file, this will only update a symbolic link. If you really want to copy the file (just in case somebody modifies 1219.html on 19 December), you can use cp instead (no -sf required).

---

### Post by erictherev on 2019-12-18
The other side of this, which I have figured out, is backing up the files I am modifying in Windows using a batch file, and having said batch file work on multiple systems/user accounts. Here's what I have for the windows backup:

```
@echo off
ECHO It is recommended that you rename any existing backups to prevent overwriting.
ECHO.
SET /P V=This will overwrite any existing backups. Type YES to confirm:
ECHO.

mkdir Backup
IF %V%==YES copy *.html %userprofile%\Documents\Test\Backup
```

The reason for the timing of making the backup directory is to give me a chance to rename an existing backup directory if needed. Until I type YES, nothing has been changed and I can simply close the command prompt window if I don't want to run the backup.

---

