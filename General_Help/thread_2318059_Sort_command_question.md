---
title: "Sort command question"
date: 2016-03-22
forum: General Help
---

### Post by GrouchyGaijin on 2016-03-22
Hi Guys,


I was wondering about the sort command.
Is there a way I can use sort to arrange the tasks on this list by due date yet keep them grouped according to project?
I know I can set the --field-separator=: and then sort by the second column to put the dates in the correct order.  What I don't know is how to keep the projects grouped together.


That is can I go from this:


```

=====  Projects  =====

---  EAP  ---
Interviews due:2016-03-25 at 10:00
Interviews due:2016-03-29 at 10:00
Read the novel due:2016-03-27
Interviews due:2016-03-22
Interviews due:2016-03-23


---  KIDS  ---
Fritids due:2016-03-29
Fritids due:2016-04-01
Ledig due:2016-03-30
Ledig due:2016-03-31


---  Proofreading  ---
Eva Hämberg due:2016-04-04


---  Transcription  ---
Perman due:2016-03-28
Perman due:2016-03-29
Perman due:2016-04-01

```


To this:


```

=====  Projects  =====

---  EAP  ---
Interviews due:2016-03-22
Interviews due:2016-03-23
Interviews due:2016-03-25 at 10:00
Read the novel due:2016-03-27
Interviews due:2016-03-29 at 10:00

---  KIDS  ---
Fritids due:2016-03-29
Ledig due:2016-03-30
Ledig due:2016-03-31
Fritids due:2016-04-01

---  Proofreading  ---
Eva Hämberg due:2016-04-04

---  Transcription  ---
Perman due:2016-03-28
Perman due:2016-03-29
Perman due:2016-04-01

```

---

### Post by Edison_James on 2016-03-22
You will probably have better success with the ls command. See this link.
[http://www.linuxquestions.org/questions/linux-general-1/sort-files-from-command-line-4175571565/](http://www.linuxquestions.org/questions/linux-general-1/sort-files-from-command-line-4175571565/)

---

### Post by sandyd on 2016-03-22
Use this script
```

#!/bin/bash

## File to sort
FILE="test.txt"

TEXTBLOCK=()
while read text; do
  if [[ $text =~ ^---[" "].*[0-9A-Za-z].*[" "].*---$ ]]; then

        ## Sort if there are things to sort
        if [ ${#TEXTBLOCK[@]} -ne 0 ]; then
                ## Sort text
                sort -t: -k2 <(for x in "${TEXTBLOCK[@]}" ; do echo "$x" ; done)
                printf "\n"
        fi
        ## Empty array
        TEXTBLOCK=()
        echo $text
  else
        ## Append block to array if not null
        if [[ $text != "" ]]; then
                TEXTBLOCK+=("$text")
        fi
  fi
done <$FILE

## Last Block
sort -t: -k2 <(for x in "${TEXTBLOCK[@]}" ; do echo "$x" ; done)
```

Not optimized for speed/etc, just cobbled together.

Set the file path with the FILE variable at the top of the script

---

### Post by GrouchyGaijin on 2016-03-23
WOW - you are amazing - thank you so much.

---

