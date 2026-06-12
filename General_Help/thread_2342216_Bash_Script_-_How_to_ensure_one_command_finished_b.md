---
title: "Bash Script - How to ensure one command finished before next starts?"
date: 2016-11-04
forum: General Help
---

### Post by Alan5127 on 2016-11-04
Hi All,

I am pretty much a beginner with bash scripts.

I perform a few sets of tasks regularly, so I figured I would script them.

One example is, I regularly run the following commands (that I am now trying to put in a script) to make sure machines are fully up to date (not sure why the software updater misses things, but that's another question!)

```

#!/bin/bash
apt-get clean
cd /var/lib/apt
mv lists lists.old_`date '+%Y%m%d_%H%M'`
mkdir -p lists/partial
apt-get clean
apt-get update
apt-get upgrade
echo 'Completed'

```

I have been using general Google help plus this site:

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

but I cannot seem to work out how to be certain that one command finishes, before the next one starts?

I found references to using 'Sleep' or 'Wait' like this:

[http://forums.devshed.com/linux-help-33/shell-script-help-waiting-command-continuing-467642.html](http://forums.devshed.com/linux-help-33/shell-script-help-waiting-command-continuing-467642.html)

but neither seems to give me a general solution (or maybe I am not understanding).

Is it perhaps implicit, and hence there is no 'command' to ensure this?

Apologies if it is staring me in the face!

Thanks,

Alan.

---

### Post by jeremy31 on 2016-11-04
I think this may work
```
#!/bin/bash
apt-get clean && cd /var/lib/apt && mv lists lists.old_`date '+%Y%m%d_%H%M'` && mkdir -p lists/partial && apt-get clean && apt-get update && apt-get upgrade && echo 'Completed'
```

See [http://stackoverflow.com/questions/4510640/command-line-what-is-the-purpose-of](http://stackoverflow.com/questions/4510640/command-line-what-is-the-purpose-of)

---

### Post by steeldriver on 2016-11-04
It **is **implicit

Unless you explicitly put a command into the background (using a **single **& character), the shell will wait for it to complete before execution proceeds to the next command

It's only if you want to ensure that a command completes **successfully **(i.e. exits with status 0) that you need to chain it to the next command with the && logical operator

---

### Post by Alan5127 on 2016-11-04
Hi Guys,

Thank you both for your replies.

So, if I understand correctly, by default, the shell will wait until each command finishes before starting the next line.

However, finishing might include with some kind of error, so if I want to make sure that subsequent commands only execute when there were no issues prior, then I need to put them all on the one line, separated with 'space double-ampersand space'.

Is that correct?

For reference, is there any way to make the script easier to read by combining lines?

Not sure if this will make sense, but an example would be in, say, Microsoft Excel, if you use VBA, you can conjoin lines using the underscore character.  This helps makes complicated lines much easier to read for a human, but has no impact on the flow or execution of the code.

So, using that as an example, but accepting that the underscore character is not likely the actual way to do this (not least because underscores can be part of the script such in the mv command in this one), the script from jeremy31's post above would become something akin to:

```

#!/bin/bash
apt-get clean && _
    cd /var/lib/apt && _
    mv lists lists.old_`date '+%Y%m%d_%H%M'` && _
    mkdir -p lists/partial && _
    apt-get clean && _
    apt-get update && _
    apt-get upgrade
echo 'Completed'

```

Thanks,

Alan.

---

### Post by kpatz on 2016-11-04
You can write it on separate lines like this:
```
#!/bin/bash
apt-get clean && 
    cd /var/lib/apt && 
    mv lists lists.old_`date '+%Y%m%d_%H%M'` && 
    mkdir -p lists/partial && 
    apt-get clean && 
    apt-get update && 
    apt-get upgrade
echo 'Completed'
```

A cleaner way (in my opinion) is to do it like this:

```

#!/bin/bash
apt-get clean || exit 1
cd /var/lib/apt || exit 1
mv lists lists.old_`date '+%Y%m%d_%H%M'` || exit 1
mkdir -p lists/partial || exit 1
apt-get clean || exit 1
apt-get update || exit 1
apt-get upgrade || exit 1
echo 'Completed'
exit 0

```
This way you aren't chaining a bunch of commands together which can be confusing and difficult to read.  The command after a || operator executes only if the command prior was not successful (or returns a non-zero return code)--the opposite of &&.  The "exit 1" causes the script to exit at the point where something failed, and returns a 1 return code so a calling script will know if your script was successful.

It's also good convention to put "exit 0" at the end of your script to explicitly return a success return code, even though the shell will do this if you don't.

---

### Post by steeldriver on 2016-11-04
You *can *use \ as a line continuation character 

```

#!/bin/bash

echo "one" && \
sleep 2 && \
echo "two" && \
sleep 2 && \
echo "done."

```

However as kpatz has pointed out, it's not necessary in this case - see for example [How to tell bash that the line continues on the next line]("http://stackoverflow.com/a/35931689/4440445")

.

---

### Post by kevdog on 2016-11-04
All the posters post a variant that does work, however as someone pointed out above, all of it is superfluous unless you want to stop the command if one command fails.  So for example with all the && statements --- it really means in layman's terms -- if the previous command exits successfully (exit code = 0), then run the next command.  If the script your writing doesn't care if the prior command completed successfully or not, then there isn't really a need to chain the commands unless its by design.

---

### Post by Alan5127 on 2016-11-06
Hi All,

Thank you very much.

As always, I love that there are so many ways to achieve the same (or slightly different) thing.

Solved my problem perfectly.

Alan.

---

