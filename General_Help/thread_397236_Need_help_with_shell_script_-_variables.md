---
title: "Need help with shell script - variables"
date: 2007-03-30
forum: General Help
---

### Post by Syock on 2007-03-30
I don't know if I might have installed something that broke my installation, but here goes a brief explanation of my problem:

- My system doesn't execute the resume.d routine properly, so I have trouble in several things, for example, beryl-manager not restarting after a resume from suspend.
- After I did some research, I found out that beryl-manager didn't restart because a key variable, WASBERYLRUNNING didn`t have a positive value, even though one of the scripts in suspend.d folder toggles the value if beryl was found to be running.
- Among other consequences are network interface not reconfigured properly (failure in retrieving address from DHCP)

I did a simple test which involved running a script which runs another two different scripts, which I shall name foo.sh and bar.sh (in the same folder as the main script)
```
#!/bin/sh
./foo.sh
./bar.sh
```
while foo.sh and bar.sh have these lines respectively
```
#!/bin/sh
TESTVAR="Hello and goodbye world"
echo $TESTVAR
```
```
#!/bin/sh
echo "Now on to bar.sh"
echo $TESTVAR
```

I expected the second script to display the message defined in the first script, but nothing came out.
What could be the problem here?
Someone mentioned something about dash was being used instead of bash, what does that mean?

---

### Post by fanatik on 2007-03-30
Well when you run the foo script it creates a subshell, all variables are local to that, it exits and the variables disappear. so when you run bar.sh it doesn't know about $TESTVAR in it's own subshell.

You can overcome this in a number of ways, export the variable from the main script:

#!/bin/sh
export TESTVAR="test"
./foo.sh
./bar.sh

or pass the variables into the scripts (more complicated). There's a good reference on bash scripting [here]("http://tldp.org/LDP/abs/html/").

hope this helps.

James.

---

### Post by Syock on 2007-03-30
From your explanation, I understood that the variable defined in foo.sh is local and unaccessible by bar.sh.

But if that is the case, why don't the scripts in /etc/acpi/suspend.d/ and /etc/acpi/resume.d/ use export for its variables? For example, /etc/acpi/suspend.d/55-down-interfaces.sh is supposed to save the list of current working network interfaces so that /etc/acpi/resume.d/62-ifup.sh can reenable them when the computer wakes up. But after putting some debugging logs, I found out that the value isn't stored, making the script useless.

Weird thing is, before I reinstalled Ubuntu 6.10, my PC used to resume and manage to reconnect to the internet appropriately. It was Compiz back then, and the Compiz restart script also had no problem.
I need to know how the scripts can serve their purpose, though trying to understand advanced bash scripting might be a good idea too.

---

### Post by juicemansam on 2007-04-02
> **Syock said:**
> From your explanation, I understood that the variable defined in foo.sh is local and unaccessible by bar.sh.

But if that is the case, why don't the scripts in /etc/acpi/suspend.d/ and /etc/acpi/resume.d/ use export for its variables? For example, /etc/acpi/suspend.d/55-down-interfaces.sh is supposed to save the list of current working network interfaces so that /etc/acpi/resume.d/62-ifup.sh can reenable them when the computer wakes up. But after putting some debugging logs, I found out that the value isn't stored, making the script useless.

Weird thing is, before I reinstalled Ubuntu 6.10, my PC used to resume and manage to reconnect to the internet appropriately. It was Compiz back then, and the Compiz restart script also had no problem.
I need to know how the scripts can serve their purpose, though trying to understand advanced bash scripting might be a good idea too.

Fanatik's explantion of the variables and sub-shells is correct. I'll try to further expand on the topic. The top most variables exist in the environment, such as those you find when typing *env*. Those variables have been exported through the system login scripts, and are available to all scripts run by a shell running with that environment. Now inside a script, you can add your own variables, such as TESTVAR, but as Fanatik mentioned, it will only exist inside that sub-shell. Also, the way you're testing/running your script is calling external scripts, which like Fanatik mentioned, creates sub-shells. You can however, import the external script, with the "source" or '.' command, which wouldn't create a sub-shell, but instead expand your script. Here's how your script would look importing an external script:
```
#!/bin/sh
. ./foo.sh
source ./bar.sh
```
```
#!/bin/sh
TESTVAR="Hello and goodbye world"
echo $TESTVAR
```
```
#!/bin/sh
echo "Now on to bar.sh"
echo $TESTVAR
```

That's the way most system scripts work. You might notice that the source command doesn't work, but the . does. Right now I'm confused about that because they're pretty much the same command. But I left it in the example because it might work elsewhere. Other's might point out if it's called wrong as well.

OK, I've gone and confused myself, but I hope I cleared it up a bit. Also try *help* in the bash prompt, that'll give you a list of all built-in commands, ie *help source*, *help .*, *help for*, etc.

Just a quick note about the resume/suspend.d scripts. They don't actually save a list of interfaces. What the scripts are doing is finding available interfaces, creating a list (INTERFACES) and shutting each interface down, or bring it up (via the *for* built-in bash command). The variable name in both scripts just happens to have the same name, but in reality they're unrelated. The only way for that variable to be in common would be for it to be in settings script, such as those in /etc/default or similar.

---

