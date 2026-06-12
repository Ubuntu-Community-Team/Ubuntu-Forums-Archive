---
title: "running sudo from the gnome-terminal on startup"
date: 2018-08-07
forum: General Help
---

### Post by Robbyx on 2018-08-07
Is there a way of causing the following command line to run without stopping for sudo's password (the command must be run as root otherwise it will not work )?

The whole line is put into the start applications:

gnome-terminal  --command="sudo /usr/local/xxx.ac/bin/run_ubuntu.sh"

---

### Post by DuckHook on 2018-08-07
The usual way to run commands or a script with root privileges at startup is to define it as a systemd service and add it to the systemd.service subsystem. Instructions: [https://linuxconfig.org/how-to-automatically-execute-shell-script-at-startup-boot-on-systemd-linux](https://linuxconfig.org/how-to-automatically-execute-shell-script-at-startup-boot-on-systemd-linux)

What you are trying to do (a root level startup app at GUI login) is highly discouraged. There is a way to do it using *sudoers*, but it is beyond my pay grade and risks breaking Ubuntu security.

---

### Post by Robbyx on 2018-08-07
Thank you. I will leave the command as is and enter the password manually. This I assume is not breaking ubuntu security and it is a lot less hassle than trying to  avoid entering the password at startup.

---

### Post by springshades on 2018-08-08
You add a line to /etc/sudoers that looks like this:

```
myusername ALL=(root) NOPASSWD: /usr/local/xxx.ac/bin/run_ubuntu.sh
```

And then... this is REALLY important. You have to make sure that run_ubuntu.sh is owned by root:root. If you don't do that, ANYONE who has write access to the file will be able to execute ANYTHING as root. You need to make sure that this is a safe command because other users will also be able to execute this file as well (as root) unless you do some more stuff.

When you run the command, get rid of the sudo. It's not necessary to run as root in this case and it will still ask for your password.

```
 gnome-terminal --command="/usr/local/xxx.ac/bin/run_ubuntu.sh"
```

Are you absolutely sure that this needs to run in a terminal? Does it ask for user input or something? If not, the standard way is to just let this execute and terminate in the background. And in that case, letting it run as a service is the more standard method.

---

### Post by Robbyx on 2018-08-08
It is now working very well. Thank you.

Just to make sure I have it right:

the .sh file is owned by Root and group is Root. Access control  is View: anyone; change control: only owner; execute: anyone

The file that .sh runs looks to me like a gui in that there is a slider button for on/ off, drop down menus for location, protocol and port, radio buttons for preferences , advanced and news.

---

### Post by springshades on 2018-08-08
Yes. You have the file permissions set correctly. The only thing you'll need to remember for security is that the GUI has root access permanently, and all users can execute it. As long as you think that is safe, you're good to go.

If you're worried about other users being able to execute the command, you can fix that by: (1) creating a new group, (2) adding yourself and the file to the new group, and (3) changing the execute permission of the file to be owner and group (not everyone). However, that's probably not necessary unless it's something like a shared server with users that you don't know.

---

### Post by Robbyx on 2018-08-08
Thank you very much for sorting out this problem with the .sh file. It is a pleasure to see it working well. I do  not 
need to worry about others using the same file.

---

### Post by HermanAB on 2018-08-09
You can also use setuid root on the network utilities, so that ordinary mortals can run them without having to resort to sudo.

---

### Post by Robbyx on 2018-08-11
I wish to move the window to the 5th workspace on startup. I wrote this bash.  "wmctrl -r XXX.AC -t 4" works from the command line, but when it is in  startup apps,  it does not work. I guessed it might be that it is running before XXX.AC is loaded so I added the wait command into the script, but still no joy. What do I need to alter?

#!/bin/bash
# xxx.ac workspace move sript on startup
# to show open windows in linux
# wmctrl -l|awk '{$3=""; $2=""; $1=""; print $0}'  
# shows XXX.AC ie in caps
# move XXX.AC to workspace 4 (windows start at 0)
wait $1
# wait or wait $1 does not allow XXX.AC to be moved 
wmctrl -r XXX.AC -t 4

---

### Post by Robbyx on 2018-08-29
> **springshades said:**
> Yes. You have the file permissions set correctly. The only thing you'll need to remember for security is that the GUI has root access permanently, and all users can execute it. As long as you think that is safe, you're good to go.

If you're worried about other users being able to execute the command, you can fix that by: (1) creating a new group, (2) adding yourself and the file to the new group, and (3) changing the execute permission of the file to be owner and group (not everyone). However, that's probably not necessary unless it's something like a shared server with users that you don't know.

I have had to reviset this topic because I have just upgraded to  18.04 but it did not work well so I had to do a reformat install.

Having followed the advice in this topic, when I now login I get the following request to enter my password again at this point:

localuser:root being added to access control list
id:1000 this script must be run as root
  try gksu + run_ubuntu.sh
[sudo] password for robins: 

When I enter password here, the xxx.ac script runs as before. 

Can I change something so I do not need to enter my password once when I login and again when the script is run?

[I][B]I solved the problem by changing the sudoers line from:
myusername ALL=(root) NOPASSWD: /usr/local/xxx.ac/bin/run_ubuntu.sh

To 

robin ALL=(root) NOPASSWD: /usr/local/xxx.ac/bin/run_ubuntu.sh[/B]
[/I]

I note that gksu is not in the repositories for 18.04.

---

