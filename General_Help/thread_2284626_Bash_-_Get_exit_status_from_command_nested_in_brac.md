---
title: "Bash - Get exit status from command nested in brackets"
date: 2015-06-30
forum: General Help
---

### Post by CaptainMark on 2015-06-30
```
fitcount=$(cp -vn /media/mark/GARMIN/Garmin/Activities/*fit /home/mark/Documents/gps\ files/fit/ | wc -l)
```
In this script snippet is it possible for me to get the exit status from the cp command? I want to launch into an if/else statement based on whether the copy succeeded or failed. (Just to clarify, I'm not considering zero files copied as being a failure)

Alternatively if someone can come up with a better way (but please lets keep it simple) to use the cp command and detect whether it succeeds or fails whilst still counting the number of copied files just let me know.

Regards
Mark

EDIT: I should also mention that both the source and destination directory for the cp command could well contain other files which will not be copied so simply counting the contents of the source first and then copying separately won't work.

---

### Post by nerdtron on 2015-07-01
Can't you revise the script and save the exit status of the cp command to a variable? the $? variable stores the exit status of the last command executed. exit status of $? of zero mean a command completed successfully, any other value of exit status means an error or interruption.

Example:
```

#!/bin/bash
cp -ap /source/files /destination/folder/
ext_stat=$?

if [ $ext_stat -eq 0 ]
then
command 1 here;
command 2 here;
else
echo cp command is not successful, exiting now
exit;
fi
```

---

### Post by CaptainMark on 2015-07-01
That wont work I'm afraid, the output of the cp command is being stored as the variable fitcount, so using $? after fitcount=$(somecommand) gives me the exit status of the variable creation (sorry I forget the correct word there) which will always be zero seen as the output from somecommand was successfully stored as $fitcount.

Your suggestion doesn't count the number of files successfully copied, which is pretty crucial I'm afraid.

Regards
Mark

---

### Post by nerdtron on 2015-07-01
Then try to create a log file for the cp command.

```

#verbose cp 
cp -av /some/source/* /destination/ > /tmp/cp_log.txt
#exit status
ext_cp=$?

#now the output of the cp command is on cp_log.txt and you can do what ever you want with it, like store it to another variable or count the number of copied files
#count copied files
wc -l /tmp/cp_log.txt

#put some additional commands here, or maybe if,then statements, whichever you may need

```

I hope you get my idea. This is another approach.

---

### Post by papibe on 2015-07-02
Hi CaptainMark.

I would personally do it differently. I would create a loop and check success for each file, while counting. That way I would know exactly which files weren't copied.

Having said that, the list variable PIPESTATUS holds the exit status of all commands inside a pipe.

You could do something like:
```
count_and_code=$(cp -vn /path/to/source/*files /path/to/destination/  | wc -l; echo "${PIPESTATUS[0]}")

cp_exit_code=$(tail -n 1 <<< "$count_and_code")

fitcount=$(head -n 1 <<< "$count_and_code")

```
Hope it helps. Let us know how that foes, and if you want to explore doing it with a loop.
Regards.

---

### Post by CaptainMark on 2015-07-02
Thanks for the suggestions, I've thought of another simple way would be to count the files in the destination both before and after the cp and save the difference to a variable afterwards. Many ways to skin a cat.

---

