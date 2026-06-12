---
title: "How to run some script during startup"
date: 2013-02-18
forum: General Help
---

### Post by sandeep913 on 2013-02-18
Hi. I need to launch one script during startup, but don't know what is the exact sequence to get this done like where to copy(rc*.d or /etc/init.d or /etc/init) my script, if needed how to give some special execution permissions etc. I tried copying one small script file with only an echo in /etc/rcS.d and got that print in /var/log/boot.log file. i could not make ,much progress after that.
Thanks in advance for any help.

---

### Post by Habitual on 2013-02-18
[http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up](http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up)

---

### Post by sandeep913 on 2013-02-19
Hi,
thanks for the reply. I created one .conf file(launch.conf) for my job (launch). i got that listing under initctl list command as : 
 
launch stop/waiting
 
But none of the task are done.
 
Also i need to get the output in console window. Is this possible to redirect all the output to one console window? Otherwise how to make sure whatever was written in script file executed successfully?

---

### Post by fdrake on 2013-02-19
> **sandeep913 said:**
> Hi,
thanks for the reply. I created one .conf file(launch.conf) for my job (launch). i got that listing under initctl list command as : 
 
launch stop/waiting
 
But none of the task are done.
 
Also i need to get the output in console window. Is this possible to redirect all the output to one console window? Otherwise how to make sure whatever was written in script file executed successfully?

place your script in your home : example: "~/myscript.sh"
in the startup application preference add a new start-up job: 
```
Name:My startuo script
Command:/usr/bin/gnome-terminal --tab -e "/bin/bash -c '/home/MYusername/myscript.sh; exec /bin/bash -i'"
Commants:My startup script
```
it should open the terminal and run the commands in the terminal and keeping the terminal open without exiting.

---

### Post by sandeep913 on 2013-02-19
Hi,
 
Thanks for the reply. I got the console up but my script require root priviledge. 
 
It gives : /bin/bash: /root/myscript: Permission denied
 
How can i run it with root priviledge without logging in as root. I need to first log in as root (using su and giving password - manually) then need to run rest of script. How can i do it with single script and not logging in as root.

---

### Post by fdrake on 2013-02-19
> **sandeep913 said:**
> Hi,
 
Thanks for the reply. I got the console up but my script require root priviledge. 
 
It gives : /bin/bash: /root/myscript: Permission denied
 
How can i run it with root priviledge without logging in as root. I need to first log in as root (using su and giving password - manually) then need to run rest of script. How can i do it with single script and not logging in as root.

NOTE/ADVICE: Keeping a terminal open with root priviledges is NOT ADVICED. you may have to go to the restroom and someone have full root access of you pc.
run this command, based on my previuos example

edit :
this is wrong, it wont work
[COLOR=Red]```

sudo chmod u+s /home/MyUsername/myscript.sh

```now the scrpt will have root priviledges of execution. Try it out and let me know.[/COLOR]

---

### Post by sudodus on 2013-02-19
You can also use crontab. See this link

[[COLOR="Red"]http://ubuntuforums.org/showpost.php?p=12510133&postcount=10[/COLOR]]("http://ubuntuforums.org/showpost.php?p=12510133&postcount=10")

but instead of @shutdown you want to run @reboot ;-)

so the line in crontab should contain

```
[COLOR="Red"]@reboot[/COLOR]   /full-path-to-command/command
```
(@reboot instead of 'minute hour dom month dow'). See more details in this link

[[COLOR="Red"]http://www.pantz.org/software/cron/croninfo.html[/COLOR]]("http://www.pantz.org/software/cron/croninfo.html")

---

### Post by fdrake on 2013-02-19
> **sudodus said:**
> You can also use crontab. See this link

[[COLOR="Red"]http://ubuntuforums.org/showpost.php?p=12510133&postcount=10[/COLOR]]("http://ubuntuforums.org/showpost.php?p=12510133&postcount=10")

but instead of @shutdown you want to run @reboot ;-)

so the line in crontab should contain

```
[COLOR="Red"]@reboot[/COLOR]   /full-path-to-command/command
```
(@reboot instead of 'minute hour dom month dow'). See more details in this link

[[COLOR="Red"]http://www.pantz.org/software/cron/croninfo.html[/COLOR]]("http://www.pantz.org/software/cron/croninfo.html")

that's would be valid if the user did not need to see the output of the script in the terminal after login (at least that is what it looks like s/he wants)
> 
Also i need to get the output in console window. Is this possible to redirect all the output to one console window? Otherwise how to make sure whatever was written in script file executed successfully?


---

### Post by sudodus on 2013-02-19
> **fdrake said:**
> that's would be valid if the user did not need to see the output of the script in the terminal after login (at least that is what it looks like s/he wants)
I see your point, it will be executed too early (before the user's desktop environment is ready), and does not work like that. I suggest a work-around in a new post.

---

### Post by sandeep913 on 2013-02-19
Hi fdrake, 
I tried that option but it asks for some password i gave that and it didn't do anything. 
One more clarification, this way the script gets executed after logging in or it starts even before logging in, Because i need to get the script executed even if nobody logs in.
And redirecting to console is something for getting the debug prints.

---

### Post by MG&amp;TL on 2013-02-19
Maybe you could redirect the script to a file, then analyse that once logged in?

---

### Post by fdrake on 2013-02-19
> **sandeep913 said:**
> Hi fdrake, 
I tried that option but it asks for some password i gave that and it didn't do anything. 
One more clarification, this way the script gets executed after logging in or it starts even before logging in, Because i need to get the script executed even if nobody logs in.
And redirecting to console is something for getting the debug prints.

I edited my post because this method does not work anymore. For security reasons linux does not have this kind of feature anymore.
See below for possible workaround or try the sudodus's suggestion.

[http://superuser.com/questions/440363/can-i-make-a-script-always-execute-as-root](http://superuser.com/questions/440363/can-i-make-a-script-always-execute-as-root)


> One more clarification, this way the script gets executed after logging in or it starts even before logging in, Because i need to get the script executed even if nobody logs in.
And redirecting to console is something for getting the debug prints.

my methods makes the script work when the user logs in only. you will need to use cron instead like sudodus suggested. If you want you can also print out the output to a log file, and check the log when you are logged automatically or not.

---

### Post by sudodus on 2013-02-19
> **sandeep913 said:**
> Hi fdrake, 
I tried that option but it asks for some password i gave that and it didn't do anything. 
One more clarification, this way the script gets executed after logging in or it starts even before logging in, Because i need to get the script executed even if nobody logs in.
And redirecting to console is something for getting the debug prints.
I checked my suggestion with crontab and xterm. It does not work @reboot, because it will be executed before log in. So I have this suggestion instead:

1. Run your script with ```
crontab -e 
```and enter the command line
```
@reboot  /path-to-command/command  >> /tmp/command.log
```

where command can be a shell-script or program with parameters. Redirect (and append) the output to a file in a directory that will always be available. I suggest /tmp (select suitable file name), and I think [COLOR="Red"]the redirection should be directly from the commands inside a shell-script[/COLOR].

2. When logging in, you can read that file, either with a file viewer or with tail if you expect there to be continuous output to the file.

```
less /tmp/command.log
```
or
```
tail -f /tmp/command.log
```

This viewing of the file can be auto-started, if you like.

---

### Post by sandeep913 on 2013-02-19
I am not sure but this @reboot option works only when the system is rebooted and not when system is started after a shutdown. I haven't tried it though.

---

### Post by sudodus on 2013-02-19
> **sandeep913 said:**
> I am not sure but this @reboot option works only when the system is rebooted and not when system is started after a shutdown. I haven't tried it though.
It starts the task at cold boot after shutdown as well as after reboot. The name is a little misleading.

---

### Post by sandeep913 on 2013-02-19
> **sudodus said:**
> I checked my suggestion with crontab and xterm. It does not work @reboot, because it will be executed before log in. So I have this suggestion instead:
 
1. Run your script with ```
crontab -e 
```and enter the command line
```
@reboot  /path-to-command/command  >> /tmp/command.log
```
 
where command can be a shell-script or program with parameters. Redirect (and append) the output to a file in a directory that will always be available. I suggest /tmp (select suitable file name), and I think the redirection should be directly from the commands inside a shell-script.
 
2. When logging in, you can read that file, either with a file viewer or with tail if you expect there to be continuous output to the file.
 
```
less /tmp/command.log
```
or
```
tail -f /tmp/command.log
```
 
This viewing of the file can be auto-started, if you like.
 
I tried your suggestion 
 
i gave 
#crontab -e
and added 
 
@reboot /home/work/myscript >> /home/work/out.txt

then restarted the sytem. out.txt was created but was empty
 
the script file contains one echo.and other operation gives the prints.
 
Please correct me if i am making some mistakes.

---

### Post by sudodus on 2013-02-19
You can test that it works like this
```
crontab -e
```
(select nano) add this line to the end of the edited file
```
@reboot              /bin/date +"\%H:\%M">>/tmp/time-at-reboot.txt
```
Write to file and exit the editor.

After poweroff + boot or reboot, check that the current 'hour:minute' at boot was written with cat, less or tail, e.g.
```
tail -f /tmp/time-at-reboot.txt
```

Exit from tail -f with ***ctrl + c***

---

### Post by sandeep913 on 2013-02-19
Just for the clarification, whatever job i am running using script requires the root priviledge i.e previouesly when i used to run it manually i used to log in as root and then used to execute all those commands. Will this method not get affected by requirement of root priviledge?
I asked this because date command doesn't require root priviledge so it might work. I haven't tried it though.

---

### Post by sudodus on 2013-02-19
> **sandeep913 said:**
> I tried your suggestion 
 
i gave 
#crontab -e
and added 
 
@reboot /home/work/myscript >> /home/work/out.txt

then restarted the sytem. out.txt was created but was empty
 
the script file contains one echo.and other operation gives the prints.
 
Please correct me if i am making some mistakes.
When you have a script file, you need to redirect from the command(s) inside it.

/bin/echo "this or that" >> /home/work/out.txt
/full-path/other-operation >> /home/work/out.txt

This way out.txt will accumulate all the time. If you want it to restart at each boot, you can start with the following command (inside the script file, but before the other commands)
/bin/echo -n "Boot at " > /home/work/out.txt
/bin/date +"%H:%M" >> /home/work/out.txt

Notice that it is only one > sign in the first command, which writes at the beginning of the file (overwrites an old file), while >> writes at the end of the file (appending lines).

---

### Post by fdrake on 2013-02-19
> **sandeep913 said:**
> Just for the clarification, whatever job i am running using script requires the root priviledge i.e previouesly when i used to run it manually i used to log in as root and then used to execute all those commands. Will this method not get affected by requirement of root priviledge?
I asked this because date command doesn't require root priviledge so it might work. I haven't tried it though.

if the script doesn't run because of root privileges run again the commands that sudodus told you but change the first one to this:
```

sudo crontab -u root -e

```

---

### Post by sudodus on 2013-02-19
> **sandeep913 said:**
> Just for the clarification, whatever job i am running using script requires the root priviledge i.e previouesly when i used to run it manually i used to log in as root and then used to execute all those commands. Will this method not get affected by requirement of root priviledge?
I asked this because date command doesn't require root priviledge so it might work. I haven't tried it though.
When the jobs require root privileges, you must use root's crontab, not the user's crontab (these are two files, that are used by ***cron*** independent of each other).

```
sudo crontab -e
```

---

### Post by rnerwein on 2013-02-19
> **sandeep913 said:**
> Hi. I need to launch one script during startup, but don't know what is the exact sequence to get this done like where to copy(rc*.d or /etc/init.d or /etc/init) my script, if needed how to give some special execution permissions etc. I tried copying one small script file with only an echo in /etc/rcS.d and got that print in /var/log/boot.log file. i could not make ,much progress after that.
Thanks in advance for any help.
hi
just post the content of your script even the ls -l your_script (the output of ls) of your script to end this puzzle.
ciao

---

