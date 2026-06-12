---
title: "kill system call returning 0 for non-existent process ID instead of ESRCH?"
date: 2022-02-22
forum: General Help
---

### Post by erpo on 2022-02-22
**What I did:**

1. Added a stanza to .bashrc to start ssh-agent if it's not running:

[FONT=Courier New] # cache ssh passphrases
if [ -f ~/.ssh/agent.env ] ; then
    . ~/.ssh/agent.env > /dev/null
    if ! kill -0 $SSH_AGENT_PID > /dev/null 2>&1; then
        echo "Stale agent file found. Spawning new agent&#8230; "
        eval `ssh-agent | tee ~/.ssh/agent.env`
        ssh-add
    fi
else
    echo "Starting ssh-agent"
    eval `ssh-agent | tee ~/.ssh/agent.env`
    ssh-add
fi[/FONT]

2. Logged in, started a terminal, supplied my SSH key passphrase, and used SSH.
3. Restarted my PC.
4. Logged in and started a terminal.

**What I expected to happen:**
Since ~/.ssh/agent.env did exist and $SSH_AGENT_PID was not running, I expected to see the "Stale agent file found. Spawning new agent&#8230; " message followed by a prompt for my SSH key passphrase.

**What actually happened:**
I saw no special messages, and ssh-agent was not started.

**Other information that may be helpful:**
Upon further investigation, I discovered that ~/.ssh/agent.env had SSH_AGENT_PID set to 2315, and that [FONT=Courier New]kill -0 2315[/FONT] exits with status code 0 _even though no process with PID 2315 is running_:

[FONT=Courier New]anopolsky@IS01209:~$ ps -ejf|grep 2315
anopols+  866812  865683  866811  865683  0 11:12 pts/5    00:00:00 grep --color=auto 2315
anopolsky@IS01209:~$ ls /proc|grep 2315
anopolsky@IS01209:~$ kill -0 2315; echo $?
0[/FONT]

However, kill -0 for other nonexistent PIDs does give me the expected output:

[FONT=Courier New]anopolsky@IS01209:~$ ps -ejf|grep 123456
anopols+  867036  865683  867035  865683  0 11:13 pts/5    00:00:00 grep --color=auto 123456
anopolsky@IS01209:~$ ls /proc|grep 123456
anopolsky@IS01209:~$ kill -0 123456; echo $?
-bash: kill: (123456) - No such process
1[/FONT]

According to strace, kill is exhibiting this behavior because the kill() system call is returning 0 instead of ESRCH:

[FONT=Courier New]anopolsky@IS01209:~$ strace kill -0 2315 2>&1|grep ^kill
kill(2315, 0)                           = 0
anopolsky@IS01209:~$ strace kill -0 123456 2>&1|grep ^kill
kill(123456, 0)                         = -1 ESRCH (No such process)
[/FONT]

Any assistance explaining this behavior would be appreciated.

System Info:
[FONT=Courier New]anopolsky@IS01209:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.4 LTS
Release:        20.04
Codename:       focal
anopolsky@IS01209:~$ uname -a
Linux IS01209 5.13.0-30-generic #33~20.04.1-Ubuntu SMP Mon Feb 7 14:25:10 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
[/FONT]

---

### Post by MAFoElffen on 2022-02-24
Just from what I saw... I didn't run it to verify it works, but just by the conventions of Bash, look at your original nested "if" statement and how you tried to form your condition for it. Conditions have to be in a form that evaluates to true or false...

Look at my edits to your code
```

# cache ssh passphrases
if [ -f ~/.ssh/agent.env ]
then
    ~/.ssh/agent.env > /dev/null
    if [ ! $(kill -0 $SSH_AGENT_PID > /dev/null 2>&1) ]
    then
        echo "Stale agent file found. Spawning new agent… "
        eval `ssh-agent | tee ~/.ssh/agent.env`
        ssh-add
    fi
else
    echo "Starting ssh-agent"
    eval `ssh-agent | tee ~/.ssh/agent.env`
    ssh-add
fi

```
You can put in echo command within temporarily to use as DEBUG statements to see where the eval is going, and to test any values that change...

---

### Post by erpo on 2022-02-24
Thanks for taking a look.

The flow control in my original bash script is okay, and the square brackets are not necessary. To see why, run the following script:

```
#!/bin/bash

if ! bash -c "exit 0"
then
    echo "this message will not be printed"
else
    # the command provided as an argument to 'if' was told to exit
    # with status 0 (success), which was then inverted with the !
    # operator, so it will be considered false for the purposes of
    # flow control in this script.
    echo "this message will be printed"
fi

if ! bash -c "exit 1"
then
    # The command provided as an argument to 'if' was told to exit
    # with status 1 (failure), which was then inverted with the !
    # operator, so it will be considered true for the purposes of flow
    # control in this script.
    echo "this message will be printed"
else
    echo "this message will not be printed"
fi


```

The problem is that the kernel is responding to the [FONT=Courier New]kill(2315,0)[/FONT] system call with a return value of 0 when PID 2315 does not exist, which seems to violate the guarantees made in the system call documentation. From [FONT=Courier New]man 2 kill[/FONT]:
```

SYNOPSIS
       #include <sys/types.h>
       #include <signal.h>

       int kill(pid_t pid, int sig);

[...]

DESCRIPTION
       The kill() system call can be used to send any signal to any
       process group or process.

       If  pid  is positive, then signal sig is sent to the process
       with the ID specified by pid.

[...]

       If sig is 0, then no signal is sent, but existence and  per&#8208;
       mission  checks  are  still  performed;  this can be used to
       check for the existence of a process ID or process group  ID
       that the caller is permitted to signal.

[...]

RETURN VALUE
       On success (at least one signal was sent), zero is returned.
       On error, -1 is returned, and errno is set appropriately.

```

---

### Post by MAFoElffen on 2022-02-24
Then you are capturing the wrong thing...  It ran successfully and returned exit codes, but you did not capture the exit code of... For example:
```

if [ -f ~/.ssh/agent.env ]
then
    ~/.ssh/agent.env > /dev/null
    kill_it=$(kill -0 $SSH_AGENT_PID > /dev/null 2>&1)
    exit_code=$!

```
Then in your nested IF condition, it would evaluate if $exit_code is 0... Right?

---

### Post by erpo on 2022-02-25
This:

```
kill_it=$(kill -0 $SSH_AGENT_PID > /dev/null 2>&1)
```

would run [FONT=Courier New]kill -0 $SSH_AGENT_PID > /dev/null 2>&1[/FONT], take whatever it produces as output (which is nothing, because stdout and stderr are being redirected to /dev/null), and store that result in [FONT=Courier New]kill_it[/FONT].

This:

```
exit_code=$!
```

would take the PID of the most recently executed background command (as opposed to its exit code) and store it in [FONT=Courier New]exit_code[/FONT].

I just provided the bash script for context. The real problem I'm looking to solve is why the kill system call is returning 0 when I send signal 0 to a PID that does not exist.

---

### Post by MAFoElffen on 2022-02-26
Oh dang. LOL. You are right.

Hmmm. Thinking...

Different proposed solution, add these two lines just previous to your test condition...
```

pid_query=$(ps -aux | grep $SSH_AGENT_PID | grep -v 'grep')     # will return running process of the pid, or null
pid_boolean=$([ ! -z "$pid_query" ] && echo "0" || echo "1")            # test if result was empty/null; and set as boolean 0 is true, 1 is false

```
Then in your existing code, test the pseudo  boolean to see if the PID 'was' currently running.

Then you could kill if running, skip if not(?)

Just an idea.

---

