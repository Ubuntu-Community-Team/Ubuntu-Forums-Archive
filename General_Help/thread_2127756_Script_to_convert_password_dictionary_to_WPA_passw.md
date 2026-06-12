---
title: "Script to convert password dictionary to WPA password dictionary"
date: 2013-03-21
forum: General Help
---

### Post by Stonecold1995 on 2013-03-21
I'm trying to test my Wi-Fi's security, but I only have a generic password dictionary.  WPA (the protocol I use) only supports 8-63 character passwords, so many passwords in the list are useless.  I don't want to download an entire new list, so I'm trying to make a script to convert it for me.  This is what I have so far:

```
#!/bin/bash

in="$1"
out=wpa_"$in"

if [ -z "$@" ]; then
    echo "Usage: ./dicconvert generic_dictionary.lst"
    exit 1
elif [ $# -lt 1 ]; then
    echo "Only one argument is required."
    exit 1
elif [ -e "$out" ]; then
    echo "Destination file already exists, it will not be overwritten."
    exit 1
elif [ ! -e "$in" ]; then
    echo "Source file '$in' does not exist."
    exit 1
fi

echo "Processing $in ($(stat -c %s $in) bytes), please wait."

original_num=0
converted_num=0

for p in $(cat "$in"); do
   len=$(expr length "$p")
   if [ "$(echo $p | awk {'print $1'})" != '#!comment:' ]; then
       ((original_num++))
       if [ $len -ge 8 -a $len -le 63 ]; then
           echo "$p" >> "$out"
           ((converted_num++))
       fi
   fi
done

echo "Done!  Saved to $out"
echo "Original dictionary size: $original_num passwords ($(stat -c %s $in) bytes)"
echo "Converted dictionary size: $converted_num passwords ($(stat -c %s $out bytes)"

exit 0
```

But I want to be able to preserve multiple word passwords.  What the script does now is treat anything with a space as another line, so the list:
```
#!comment: super short dictionary
password
mypass
two words
three word password
anotherpass
desu
```

Becomes
```
#!comment:
dictionary
password
password
anotherpass
```

But I want it to become
```
password
two words
three word password
anotherpass
```

How do I get the for loop to recognize newlines only and put the whole line into the variable "p" instead of each individual word?



Also, on another note, if I want to add a progress meter how would I go about doing that?  I know how to use "tput cup linenumber" (for an incrementing percentage meter), but I don't know how to use tput to *get* the current line number so I can use tput again to go back to the last line and update it as the percentage increases.  How do I do that?

---

### Post by sisco311 on 2013-03-21
Check out BashFAQ 001 and 031 (link in my signature). 

 You can get the length of the value of a parameter with the following expansion: ${#parameter}

EDIT: For the progress bar check out BashFAQ 044.

With dialog you can try something like:
```

dialog --gauge "Working..." 20 75 < <(
    n=$(wc -l < ./file); i=0
    while read -r line
    do
        sleep 1
        echo $((100*(++i)/n))
    done < ./file
)
```

EDIT2: ...and... error messages, warnings and input prompts shall be printed to stderr:
```

echo "Error..." >&2
echo "Warning..."  >&2
echo "Please enter something: " >&2; read something

```

---

