---
title: "Please assist with shell script - Issues with Grep? Any help appreciated"
date: 2015-11-09
forum: General Help
---

### Post by deadline527gmail. on 2015-11-09
So I have a shell script which does quite a bit, and everything works perfectly except for one single part. I am trying to grep out information from today and yesterday from a log file that has two or so months worth of data in it. I am able to grep it without issue using just the shell, but in the script, it refuses to work. What I am trying to accomplish is below:

cat native_stderr_wsf* | grep -A30 --group-separator= 'timestamp="Nov 09'

This command has no issues outputting exactly what I am looking for. 

Followed by the function in the script I am having issues with. Problem lines are highlighted. The issue is with the grep statements reading the $todays_day as a file name, instead of as part of the search string within the command. I am unsure if this is due to the way I used escape sequences, or if its due to the blank space in between the variables. The group separator is blank intentionally after the equals sign, since I want it to be a blank line in between each group. Either way, its driving me crazy, lol. 

Any help would be appreciated.


Function below:```

split_stderr_Log(){

while read line

do

   HOST_NAME="$(echo $line | awk '{ print $1 }')"

   LOG_FILE_DIR="$(echo $line | awk '{ print $2 }')"

   todays_month="$(date +%b)"

   todays_day="$(date +%d)"

   yesterdays_day="$(date --date='yesterday' '+%d')"

   yesterdays_month="$(date --date='yesterday' '+%b')"


   if [[ $line == *"wsfpp1"* ]]

   then

      jvm_name="$(echo $line | awk -F'/' '{ print $4 }')"

   else

      jvm_name="$(echo $line | awk -F'/' '{ print $3 }')"

   fi


   if [[ $line == *"wsfpp1"* ]]

   then

   while read line

   do

      file_name="$(echo $line | awk -F'/' '{ print $6 }')"

[COLOR=#ff0000]      cat $LOG_FILE_DEST/$HOST_NAME/$jvm_name/$file_name | grep -A30 --group-separator=  \'timestamp=\"$todays_month $todays_day\' >> $LOG_FILE_DEST/$HOST_NAME/$jvm_name/stderr_today_$jvm_name[/COLOR]
[COLOR=#ff0000]
[/COLOR][COLOR=#ff0000]      cat $LOG_FILE_DEST/$HOST_NAME/$jvm_name/$file_name | grep -A30 --group-separator=  \'timestamp=\"$yesterdays_month $yesterdays_day\' >> $LOG_FILE_DEST/$HOST_NAME/$jvm_name/stderr_today_$jvm_name[/COLOR]

   done < ./test_files/combine_list_stderr_$jvm_name 

   echo "File: $LOG_FILE_DEST/$HOST_NAME/$jvm_name/stderr_today_$jvm_name now contains $todays_month $todays_day and $yesterdays_month $yesterdays_day log output..."

   fi

done < $SERVER_LIST

}
```

---

### Post by deadline527gmail. on 2015-11-09
Ok so I fixed the grep issue. 

I just passed the command as a variable, which seems to be easier.

I also figured out an issue with the outer loops. Basically, there is a list formatted like:

server /directory/name
server2 /directory/name

The script checks to see if *wsfpp1* exists in the line, because if so, it means it needs to pull websphere logs instead of Pega logs. 

The script isn't looping though. It runs the if statement on the first line - but doesn't continue to the second line.

Any ideas?

---

### Post by deadline527gmail. on 2015-11-09
Ok so loop is fixed. Was an issue with a character in the grep command. 

But now, still no luck with grep. Here is the output from bash -xv regarding it:

++ date +%d
+ todays_day=09
++ date --date=yesterday +%d
+ yesterdays_day=08
++ date --date=yesterday +%b
+ yesterdays_month=Nov
++ grep -A30 --group-separator= 'timestamp="Nov' 09
grep: 09: No such file or directory


Trying to make it so it doesn't read the day as a file - it should all be one string up until after the date.

---

### Post by TheFu on 2015-11-09
cat isn't needed. grep can read from a file directly.  It can glob filenames too. Save an extra process. fgrep may be 10x faster, if speed matters.

Always quote/sanitize directories and filenames.  Quoting is often enough:
    "$LOG_FILE_DEST/$HOST_NAME/$jvm_name/$file_name"
if you know these don't have any single/double quotes.

Build the regex and store in a variable, then use that in the grep.

By the time a script gets this complicated, I would switch to a cleaner language.  Perl, python, ruby....  awk.

---

### Post by deadline527gmail. on 2015-11-09
The issue is the regex. I'm not sure how to escape the whitespace where its not read as a separator but part of the string I'm searching for. 

And yes, its stupid complicated for a shell script, but honestly, I don't know other languages too well so just going with what I know and am comfortable with. 

I'll make sure I sanitize the directories, and remove the cats - but the issue still remains with grep. I even put the date into a single variable instead of two separate variables, such as "date +%b' '%d", but its still reading the day as a filename and not as part of the string.

Any help would be awesome if you could provide me the correct regex. I always hated regex but the more I script, the more I realize I need to learn it.

---

### Post by deadline527gmail. on 2015-11-09
Here is the newer version, with what I tried to do with passing the date as a single variable. Also changed grep to a command variable and still no luck due to whitespace:



```

split_stderr_Log(){
while read line
do
   HOST_NAME="$(echo $line | awk '{ print $1 }')"
   LOG_FILE_DIR="$(echo $line | awk '{ print $2 }')"
   today="$(date +%b' '%d)"
   yesterday="$(date --date='yesterday' +%b' '%d)"
  
   if [[ $line == *"wsfpp1"* ]]
   then
      jvm_name="$(echo $line | awk -F'/' '{ print $4 }')"
   else
      jvm_name="$(echo $line | awk -F'/' '{ print $3 }')"
   fi

   if [[ $line == *"wsfpp1"* ]]
   then
   while read line
   do
      file_name="$(echo $line | awk -F'/' '{ print $6 }')"
      grep_split_today="$(grep -A30 --group-separator= 'timestamp='\"$today)"
      grep_split_yesterday="$(grep -A30 --group-separator= 'timestamp='\"$yesterday)"

      cat $LOG_FILE_DEST/$HOST_NAME/$jvm_name/$file_name | $grep_split_yesterday >> $LOG_FILE_DEST/$HOST_NAME/$jvm_name/stderr_today_$jvm_name
      cat $LOG_FILE_DEST/$HOST_NAME/$jvm_name/$file_name | $grep_split_today >> $LOG_FILE_DEST/$HOST_NAME/$jvm_name/stderr_today_$jvm_name
   done < ./test_files/combine_list_stderr_$jvm_name 
   echo "File: $LOG_FILE_DEST/$HOST_NAME/$jvm_name/stderr_today_$jvm_name now contains $today and $yesterday log output..."
   fi
done < $SERVER_LIST
}



```

---

### Post by deadline527gmail. on 2015-11-10
Got grep working. Now just having an issue with it not looping. I'll figure this out eventually I'm sure, lol. If someone wants to help though, more than welcome :)

```

split_stderr_Log(){
while read line
do
   HOST_NAME="$(echo $line | awk '{ print $1 }')"
   LOG_FILE_DIR="$(echo $line | awk '{ print $2 }')"
   todays_month="$(date +%b)"
   todays_day="$(date +%d)"
   yesterdays_day="$(date --date='yesterday' '+%d')"
   yesterdays_month="$(date --date='yesterday' '+%b')"
   if [[ $line == *"wsfpp1"* ]]
   then
      jvm_name="$(echo $line | awk -F'/' '{ print $4 }')"
   else
      jvm_name="$(echo $line | awk -F'/' '{ print $3 }')"
   fi
   if [[ $line == *"wsfpp1"* ]]
   then
   while read line
   do
      file_name="$(echo $line | awk -F'/' '{ print $6 }')"
      grep_split_today="$(grep -A30 --group-separator= timestamp=.$todays_month\\s$todays_day)"
      grep_split_yesterday="$(grep -A30 --group-separator= timestamp=.$yesterdays_month\\s$yesterdays_day)"
      echo $file_name
      grep -A30 --group-separator= timestamp=.$todays_month\\s$todays_day $LOG_FILE_DEST/$HOST_NAME/$jvm_name/$file_name > $LOG_FILE_DEST/$HOST_NAME/$jvm_name/stderr_today_$jvm_name
      grep -A30 --group-separator= timestamp=.$yesterdays_month\\s$yesterdays_day $LOG_FILE_DEST/$HOST_NAME/$jvm_name/$file_name >> $LOG_FILE_DEST/$HOST_NAME/$jvm_name/stderr_today_$jvm_name
   done < ./test_files/combine_list_stderr_$jvm_name
   echo "File: $LOG_FILE_DEST/$HOST_NAME/$jvm_name/stderr_today_$jvm_name now contains logs from yesterday and today..."
   fi
done < $SERVER_LIST
}

```

---

### Post by deadline527gmail. on 2015-11-10
Success!!

 Everything works the way it should now :) Loop issue was due to my two grep command variables. Removed them and all working good. Not sure what in them was stopping the loop, but I'm happy. haha.

Removed some login/server info, but here is what it does in total:

 ```

 [*****@***** ~]$ bash -xv ./gather_gc.sh ***** test-list ./logs/ 2> output.txt
 ---------------------------------------------------------------------
 -                    Gather PEGA Alert / JVM Logs                     -
 ---------------------------------------------------------------------
+++ Clearing old files before starting...
+++ Gathering data...
+++ Downloading files...
 Host: ***** - JVM: wspdev2 - Modified: Nov 9 02:28 -- File: PegaRULES-ALERT-2015-Nov-06.log.201511090228.*****.gz...
 Host: ***** - JVM: wspdev2 - Modified: Nov 9 22:28 -- File: PegaRULES-ALERT-2015-Nov-06.log...
 Host: ***** - JVM: wsfpp1*****wspdev2Server - Modified: Nov 9 02:23 -- File: native_stderr.log.201511090223.*****.gz...
 Host: ***** - JVM: wsfpp1*****wspdev2Server - Modified: Nov 9 22:27 -- File: native_stderr.log...

+++ Combining Pega ALERTS into single files per JVM...
PegaRULES-ALERT-2015-Nov-06.log
PegaRULES-ALERT-2015-Nov-06.log.201511090228.*****
File: ./logs/*****/wspdev2/pega_alerts_wspdev2 has been created..

+++ Combining native_stderr logs into single files per JVM...
native_stderr.log
native_stderr.log.201511090223.*****
File: ./logs/*****/wsfpp1*****wspdev2Server/native_stderr_wsfpp1*****wspdev2Server has been created..

+++ Extracting yesterdays and todays data from native_stderr log file for each JVM...
File: ./logs/*****/wsfpp1*****wspdev2Server/stderr_today_wsfpp1*****wspdev2Server now contains logs from yesterday and today...

---------------------------------------------------------------------
-                               DONE                                -
---------------------------------------------------------------------

```

---

