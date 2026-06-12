---
title: "[ubuntu] Some troubles with &quot;Startup Applications&quot;"
date: 2014-04-10
forum: General Help
---

### Post by Vaklin on 2014-04-10
Hi!
I have some issue wit the startup applications manager. I have added the string

xinput set-button-map $(/usr/bin/xinput list | /bin/grep 'Optical Mouse' | /bin/grep -o 'id=[0-9]\|id=[0-9][0-9]'| /usr/bin/cut -d '=' -f2) 3 2 1 

to swap mouse buttons when touchpad is still right hand oriented.

The command flow works flawless in a terminal (no sudo) but doesn't do the necessary in the "Startup applications".

I have tried with sh -c "......" and with raw command sequence with no success.
Any idea where to put this string to get it worked after restart, reboot, hibernate and log off/on?
Or, at least, please point me where to see the logon log? I'm new in Ubuntu.

---

### Post by papibe on 2014-04-10
Hi Vaklin. Welcome to the forum ):P

I'd recommend putting your code on a bash script:
```
#!/bin/bash
device_id="$(/usr/bin/xinput list | /bin/grep 'Optical Mouse' | /bin/grep -o 'id=[0-9]\|id=[0-9][0-9]'| /usr/bin/cut -d '=' -f2)"
/usr/bin/xinput set-button-map "$device_id" 3 2 1 
```
Then adding execute permission to the script:
```
chmod a+x /path/to/yourscript.sh
```
And finally adding your script to the Startup applications:
```
/path/to/yourscript.sh &> /path/to/log
```
Later check the log file to debug your script.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Vaklin on 2014-04-10
Thank you for the fast response.
I did my FirstScript.sh in my home directory /home/vaklin

Please explain the last sentence:  
/path/to/yourscript.sh &> /path/to/log

in accordance with my home directory.

And where is recommended to save the script?

---

### Post by papibe on 2014-04-10
> **Vaklin said:**
> Please explain the last sentence:  
/path/to/yourscript.sh &> /path/to/log
In your case you could use:
```
/home/vaklin/FirstScript.sh &> /home/vaklin/FirstScript.log
```
the key '&>' will redirect all output (including errors) to the file FirstScript.log, so in case anything goes wrong, you can take a look at the log.

Does that help?
Regards.

---

### Post by Vaklin on 2014-04-10
The script works fine. How to put it to the Last sartup sequence after the log on?
Or where to add to be executed surely?
In 
[h=2]"Startup Applications"[/h]no success.

---

### Post by papibe on 2014-04-10
I got a little confused.

Did you put that last line on your 'Startup applications'?

Did it work?

Could you post the content of the log after an unsuccessful attempt?

Regards.

---

### Post by Vaklin on 2014-04-10
Yes, I have put it in Startup Applications. No success as well as any other try to do this thing by this way,
Log is 0 bytes long due to no errors or something like this.
I'll try to clear my question.
1. Th script works fine.
2. When I use it in terminal everything is OK.
3. I'd like to put it in startup when I'm loging on.
4. Startup Applications doesn't help me.
5 Where to put the script to be sure it is the last one in startup? I'm afraid something rewrite my mouse buttons.

---

### Post by papibe on 2014-04-10
Let's try this: a pause of a certain amount of seconds so that the script is executed as late as possible:
```
#!/bin/bash
[COLOR="#FF0000"]**sleep 5s**[/COLOR]
device_id="$(/usr/bin/xinput list | /bin/grep 'Optical Mouse' | /bin/grep -o 'id=[0-9]\|id=[0-9][0-9]'| /usr/bin/cut -d '=' -f2)"
/usr/bin/xinput set-button-map "$device_id" 3 2 1
```

Then, edit the command on 'Startup application' so it looks like this:
```
/home/vaklin/FirstScript.sh &> /home/vaklin/FirstScript.log [COLOR="#FF0000"]**&**[/COLOR]
```
(the final '&' will send the execution of the script to the background so the initialization of the desktop environment is not stopped by the script).

Let us know if that works or not.
Regards.

---

### Post by Vaklin on 2014-04-10
Now works fine!
Thank's a lot.
BTW anyone can use the script just changing Optical mouse to your mouse with xinput list command search.

---

### Post by Vaklin on 2014-04-10
And last question. Where is suitable to put the scripts like this one. Any suggestion?

---

### Post by monkeybrain20122 on 2014-04-10
> **Vaklin said:**
> And last question. Where is suitable to put the scripts like this one. Any suggestion?

I made a directory called Scripts in my home for this kind of scripts.

---

### Post by papibe on 2014-04-10
:) Glad it's working for you!

When you have the chance, please mark the thread as solved ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how).

Regards.

P.S.: I personally put personal scripts in ~/bin (that would be /home/vaklin/bin):
```
cd ~
mkdir bin
mv -iv ./FirstScript.sh ./bin/
```
Don't forget to update the path to the script you put on 'Startup applications' to reflect the move.

---

