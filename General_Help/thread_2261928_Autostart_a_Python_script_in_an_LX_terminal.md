---
title: "Autostart a Python script in an LX terminal"
date: 2015-01-22
forum: General Help
---

### Post by John_White on 2015-01-22
I have a python script which extracts continuous data from an  incoming serial string and inserts the fields into an Sql database.
  The python script can be run manually from an LX terminal and works successfully **whilst the terminal remains open**.   This is easily tested by examining an associated web site where a PHP  script is used to extract the data from the data base and display it in a  HTML page.
  I have tried a number of techniques to have the Python script  executed automatically on restart.  The closest I have got is for the  terminal to open momentarily, start to run the python script **and then close**.   I have tried delaying the opening on the terminal for a number of  seconds to ensure there is no clash with the desktop or other  applications starting, without luck.  
  The techniques that have been tried include:
  
[LIST=1]
[*]Creating a .desktop file in ~/.config/autostart to start the python  script in an LX terminal.   I have also tried delaying the start of the  .desktop file via an .sh script with a 10 sec delay (sleep 10). 
[*]Starting the Python script using the @reboot command in a cron job. 
[*]Using Upstart with a .config file in /etc/init. 
[*]Modifying the /etc/rc.local file to run the Python script. 
[/LIST]
  I don't believe this is a permissions issue as the /usr/bin/python  ~/user/file.py command and .desktop file can be run manually OK.
  **Any help will be greatly appreciated.**
  The environment is an UDOO Quad SBC running Ubuntu on the ARM  processor, with the embedded Arduino Due capturing sensor data and  transferring the string of data to the ARM processor.

---

### Post by Joseph_Tortorello on 2015-01-25
A couple quick questions:
1. Does the script need to run in a LXTerminal, or would it be OK to run in the background
2. What commands did you use in the methods that you described?

---

### Post by Holger_Gehrke on 2015-01-25
> **John_White said:**
> 
  
[LIST=1]
[*]Creating a .desktop file in ~/.config/autostart to start the python  script in an LX terminal.   I have also tried delaying the start of the  .desktop file via an .sh script with a 10 sec delay (sleep 10).
[/LIST]
 
You could change the "Exec" line to something like 'Exec=sh -c "script;read"' and set 'Terminal=true'. That way the terminal stays open until you hit enter and if there are any error messages you could actually read them.

---

### Post by John_White on 2015-02-11
Thanks for your help but I had already tried the techniques suggested by others without luck.  Actually, I have decided to SOLVE this problem using the Supervisor tool because it provides the following advantages:
1.  Will autostart the python script and restart if required.
2.  Will enable the script to be stopped and started under control when required.  I have found this to be really quite useful and have a cron job running once per day to stop the python script (from loading data into the sql db), dump the db into a file for archiving, truncate the database and then start the python script again.  This has been tested and works satisfactorily.

---

### Post by ian-weisser on 2015-02-11
Both Upstart and systemd have a socket-bridge that will start any application you like (including a Python script) when an inbound stream appears on a specific socket. Terribly handy.
All in the background.
The application should terminate when complete - the socket-bridge will start a new instance for the next stream.
Does not require any login, autostart, cronjob or any other initiator.

---

