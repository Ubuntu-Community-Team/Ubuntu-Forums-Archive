---
title: "problem with scheduling a reminder using &quot;at&quot; command"
date: 2006-11-01
forum: General Help
---

### Post by ssalman on 2006-11-01
Hi,

I'm trying to schedule a reminder message at a specific time using the "at" command. Below is my syntax

```
echo "~/remindeme.sh" | at now + 5 min
```where ~/remindeme.sh contains:
```
#!/bin/bash
zenity --info --text "reminder text"
```But this does not work. when testing the remindeme.sh script using cli it works, but not when scheduled using at... is there something I'm missing.

please help! Thanks:)

---

### Post by bsussman on 2006-11-01
what happens?  error messages?  nothing??

if you run:

```
mail
```

do you see any messages?

what is the state of your /etc/at.allow and /etc/at.deny files.

```
man at
```to read more

I assume that after running at, if there are no error messages, that

```
atq
```shows the job pending

---

### Post by jmacak on 2006-11-01
Hi

Also, you might want to include the full path to zenity in your script just in case the path from "at" is different.

---

### Post by bsussman on 2006-11-01
> **jmacak said:**
> Hi

Also, you might want to include the full path to zenity in your script just in case the path from "at" is different.


From
```
bos@Dillon:/var/lib$ man at
```> The working directory, the environment (except  for the  variables TERM, DISPLAY and _) and the umask are retained from the time of invocation.

---

### Post by chalex on 2006-11-01
So I put the command you want to execute into a file called command_for_at:
```

zenity --info --text "reminder text"

```

I also made a shell script called testing.sh:
```

#!/bin/sh
zenity --info --text "reminder text"

```

Testing these:
```

$source command_for_at

```
or
```

$./testing.sh

```
shows that both give the desired result.


Then I ran ```

at now + 5 min < command_for_at

```
or
```

at now + 5 min < "./testing.sh"

```
neither of those produced the desired result.

---

### Post by bsussman on 2006-11-01
The problem may be that zenity does not have a tty when it runs so it might not work.

Please divide the problem by producing and verifying that some simple script, say an ls command or 'date>tstfile' can be made to run through at.

I installed zenity and replicated.

the mail message to me is 'This option is not available. Please see --help for all possible usages.'   for a zenity script that properly produces a popup when run from the command line.  I think my first comment may be right - zenity needs an environment that the batch exec cannot produce.

Did you check for mail as I asked above?

---

### Post by chalex on 2006-11-01
You can also see the actual script that will run by typing ```
at -c <jobnumber>
```
or something like ```

at -c `atq | awk '{ print $1 }'`
```

There's a more fundamental issue here; take the following script:```

#!/bin/sh
cd /tmp

```

What happens when this script is run?  Why?

---

### Post by bsussman on 2006-11-01
> **chalex said:**
> There's a more fundamental issue here; take the following script:```

#!/bin/sh
cd /tmp

```What happens when this script is run?  Why?
```

bos@Dillon:~/bin$ at now + 1 min < ceedee
warning: commands will be executed using /bin/sh
job 5 at Wed Nov  1 19:57:00 2006

``````
bos@Dillon:~/bin$ cat ceedee
 #!/bin/sh
cd /tmp
pwd>>ceedeelog
ls>>ceedeelog
```After 1 min: ```


bos@Dillon:~/bin$ cat /tmp/ceedeelog
/tmp                    <--- output of pwd
0567181028        <---- start of ls output
ceedeelog
gconfd-bos
gnome-system-monitor.bos.1103390844
icdsoft ltd demand.doc
kde-bos
ksocket-bos
magazine101.pdf
mysql5.pid
mysql5.sock
orbit-bos
OSL_PIPE_1000_SingleOfficeIPC_680-352b4d00
ssh-xHEvjI5809
zman3uFLNM
zman6mG2q7
bos@Dillon:~/bin$                
```

Just as I might have expected.

I don't understand your question.

---

### Post by bsussman on 2006-11-01
This worked:
```
bos@Dillon:~/bin$ at now + 1 min < zeni
warning: commands will be executed using /bin/sh
job 6 at Wed Nov  1 20:21:00 2006
``````
export DISPLAY=:0.0
zenity   --question --title "Alert"  --text "Microsoft Windows has been found"
```The at manpage documents that DISPLAY is not set - you gotta set it yerself.

If you use multiple x Displays, you may have a problem :), but most ppl don't.  Multiple workspaces work but it seems that the popup appears on the workspace that I submitted the at job from.  There may be a workspace variable to control this behavior.  BTW - I am running kde so YMMV

---

### Post by ssalman on 2006-11-02
> **bsussman said:**
> The at manpage documents that DISPLAY is not set - you gotta set it yerself.

That did the trick, Thanks bussman and other people who tried to help! :-D

---

### Post by bsussman on 2006-11-02
> **ssalman said:**
> That did the trick,:-D


Cool :KS

---

