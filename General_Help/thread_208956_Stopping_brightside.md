---
title: "Stopping brightside?"
date: 2006-07-04
forum: General Help
---

### Post by Xzallion on 2006-07-04
I have a program installed called brightside that lets me switch virtual desktops by having the mouse at the edge of the screen for a second.  I start it in a terminal by typing ```
brightside
```

I want to know how I can stop this from running, as I like it running for some things and don't like it running for others.

---

### Post by frodon on 2006-07-04
Get the PID (the number of the process) of  brightside : ```
ps -aef | grep -i brightside
```Then run a kill command on the process number : ```
kill -9 process_number
```If you need to do it often paste here the output of the "ps -aef | grep -i brightside" command when brightside is active and i will write you a small toggle_script.

---

### Post by Xzallion on 2006-07-04
Okay, I did the first command and got this ```
kenneth@Xzallion-Ubuntu:~$ ps -aef | grep -i brightside
kenneth   7695     1  0 09:01 ?        00:00:03 brightside --sm-client-id 117f00 0101000115202531800000051540016 --screen 0
kenneth  10045 10024  0 10:07 pts/0    00:00:00 grep -i brightside

```
I feel a little stupid, but which one of those numbers would be the process number?

---

### Post by frodon on 2006-07-04
To kill brightside in this case the command is : ```
kill -9 7695
```Tell me if you wish a toggle script, i have enough informations now to write it.

---

### Post by Xzallion on 2006-07-04
A toggle script would be nice.  And thanks for all the help frodon, I really appreciate it.

---

### Post by frodon on 2006-07-05
Here is the toggle script.

1- create a new file under /usr/bin/ called toggle_brightside.bash : ```
sudo gedit /usr/bin/toggle_brightside.bash
```
2- paste that in the file : ```
#!/bin/bash 
a=`ps -aef | grep -i brightside | awk ' {if ($8 == "brightside"){printf "2"}} '` 
if [[ $a = "" ]] 
then 
     brightside & 
else 
     kill -9 `ps -aef | grep -i brightside | awk ' {if ($8 == "brightside"){printf $2}} '` 
fi
```
3- make the file executable : ```
sudo chmod +x /usr/bin/toggle_brightside.bash
```
4- create a launcher on your task bar or the desktop and put the full path of the script as command. Now each time you click on the icon it start/kill brightside.

---

### Post by Xzallion on 2006-07-05
I followed your directions exactly frodon, but the script doesn't seem to work.  Maybe its something I did with the launcher? The launcher command is /usr/bin/toggle_brightside.bash and its type is application, should the type be something else?  I also do not have the checkmark marked for it to run in terminal.  should that be checked?

---

### Post by frodon on 2006-07-05
There's no need to run the script in a terminal and from what you said your launcher seems ok.
You can run the script in the terminal if you want.

Maybe i made a mistake in the script.
When brightside is active this command : ```
ps -aef | grep -i brightside | awk ' {if ($8 == "brightside"){printf "2"}} '
```
should return "2"
and this one : ```
ps -aef | grep -i brightside | awk ' {if ($8 == "brightside"){printf $2}} '
```should return the number of the process

If it's not the case the problem is there.

I'm waiting your feedback

---

### Post by Xzallion on 2006-07-05
I set it to run in terminal for now, to see what its doing.  But when i run the launcher, it opens a terminal, and the terminal closes before it displays anything, and it doesn't affect brightside at all.  I thought maybe I had to start brightside for the toggle to work, so I started brightside up, and it still has no effect on it. :(

---

### Post by frodon on 2006-07-05
Could you tell me the result of the 2 commands i gave you in my previous post when brightside is active ?

---

### Post by Xzallion on 2006-07-05
okay brighside is running, and heres what its giving me.
```

kenneth@Xzallion-Ubuntu:~$ ps -aef | grep -i brightside | awk ' {if ($8 == "brightside"){printf "2"}} '
kenneth@Xzallion-Ubuntu:~$ ps -aef | grep -i brightside | awk ' {if ($8 == "brightside"){printf $2}} ''
6997
kenneth@Xzallion-Ubuntu:~$

```

---

### Post by frodon on 2006-07-05
Really weird the second command return the expected result but not the first, there should be a typo somewhere.
Check what you pasted in the toglle_brightside file.

If it stlill don't work i'll install brightside and test the script on my own computer because it's difficult to debug it that way.

---

### Post by Xzallion on 2006-07-05
It was a weird glitch in the terminal on the output, but it erased the first commands output when I entered the second, so let me try again.
```
kenneth@Xzallion-Ubuntu:~$ ps -aef | grep -i brightside | awk ' {if ($8 == "brightside"){printf "2"}} '
2
kenneth@Xzallion-Ubuntu:~$ ps -aef | grep -i brightside | awk ' {if ($8 == "brightside"){printf $2}} '
6997
kenneth@Xzallion-Ubuntu:~$
```
I slightly edited that, cause it was displaying the output like this 2kenneth@Xzallion-Ubuntu:~$ and this 6997kenneth@Xzallion-Ubuntu:~$

The script seems be doing what you told it to, but it still isn't affecting brightside.

---

### Post by frodon on 2006-07-05
Ok it's perfect, i would say that the script works (execpt if you(or me) made a typo pasting it).

Try to run it in the terminal just to see if the launcher is the problem, type in a terminal : ```
/usr/bin/toggle_brightside.bash
```

---

### Post by Xzallion on 2006-07-05
Hmmmm still doesn't affect it.  odd.  I don't know anything about bash so I can't tell if theres any problem with the code, but I triple checked what I pasted into the file, theres no errors there.

---

### Post by frodon on 2006-07-05
LOL

And here is the frodon's typo !!!!!! :

line 5 of the script should be *brightside &*  instead of *brighside &*, i forgot a "t".

Shame on me lol

---

### Post by Xzallion on 2006-07-05
lol we both missed it.  I was just comparing it to what you pasted, not checking for a typo in what you typed lol.  But for some reason it still isn't working :(
I tried running it from the terminal, and from the launcher I had, neither one stopped brightside.

---

### Post by frodon on 2006-07-05
It don't kill brightside but does it start it ?
Anyway if it don't kill brightside it should be because the command "ps -aef | grep -i brightside | awk ' {if ($8 == "brightside"){printf $2}} '" don't return the good process number, you can check that.

---

### Post by Xzallion on 2006-07-05
```
kenneth@Xzallion-Ubuntu:~$ ps -aef | grep -i brightside | awk ' {if ($8 == "brightside"){printf $2}} '
8716kenneth@Xzallion-Ubuntu:~$

```
How would I just kill it from the terminal so I can test to see if that script starts brightside?

---

### Post by frodon on 2006-07-05
Hehe, you forgot the post #2

ps -aef | grep -i brightside to get the process number then "kill -9 process_number"

BTW, you can also use the system monitor.

I hate when a script don't work :twisted:

---

### Post by Xzallion on 2006-07-05
```
kenneth@Xzallion-Ubuntu:~$ ps -aef | grep -i brightside | awk ' {if ($8 == "brightside"){printf $2}} '
8716kenneth@Xzallion-Ubuntu:~$ kill -9 8716
kenneth@Xzallion-Ubuntu:~$ ps -aef | grep -i brightside | awk ' {if ($8 == "brightside"){printf $2}} '
9218kenneth@Xzallion-Ubuntu:~$ kill -9 9218
kenneth@Xzallion-Ubuntu:~$

```
I tried that, and it didn't kill brightside, and i decided to double check and it had a new process number, so I tried to kill that, still didn't stop it. :(
I tried to kill and end the brightside process from the system monitor, and It didn't work there either.

The only way I know to stop it is to reboot, since I don't have it set to run at startup.

---

### Post by frodon on 2006-07-05
Really, it seems more serious if you can't kill the process as a simple user, does it work with root rights at least ?
The kill command will be "sudo kill -9 process_number", this must work i don't see why you would not be able to kill a process.

---

### Post by Xzallion on 2006-07-05
even the sudo kill -9 process_number command didn't work :(

---

### Post by Uisel on 2006-11-05
hey there!
could you solve the problem.cause i got the same and would like to know how to stop brightside.thanx for answers

---

### Post by UBCToad on 2007-12-16
Yeah, this seems like a tricky bugger.
Try this:
$ which brightside
/usr/bin/brightside
$ sudo chmod a-x /usr/bin/brightside
$ start-stop-daemon --stop --name brightside -v
Stopped brightside (pid 22284).
$ ps -A | grep brightside
$ sudo chmod a+x /usr/bin/brightside

Alternatively you can use the previously discussed kill -9 command to stop brightside.  That should work as well.

---

