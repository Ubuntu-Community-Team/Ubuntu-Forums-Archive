---
title: "Bash script help - appending lines to files"
date: 2013-06-11
forum: General Help
---

### Post by gforster on 2013-06-11
**Background:** I have a bunch of filenames named username.sub in single letter directories under script_testing (first letter of username is the folder name). For every username.sub, I need to check if the line user.$username.contacts\t exists and, if not, append the line. I am having troubles with my code thus far. This should be a rather simple thing, I think. I am currently testing with 4 username.sub files in subdirectory "g." I have gone through many changes, this is how the script currently stands:

**Code:**
```
#!/bin/bash
Path_to_files=$Path_to_files$( find $HOME/script_testing/ -type d -printf ":%p" )
sub_files=$Path_to_files$( find . -type f *.sub)
FULLNAME="${sub_files##*/}"
username="${FULLNAME%%.*}"

if grep user.$username.Contacts $username.sub; then
    echo "Contacts already subscribed"
else
    echo "subscribing to contacts"
    echo -e "user.$username.Contacts\t" >> $username.sub
fi
```


**Debug output**:
```
++ find /home/user/script_testing/ -type d -printf :%p
+ Path_to_files=:/home/user/script_testing/:/home/user/script_testing/g
++ find . -type f g.sub '^*.sub'
find: paths must precede expression: g.sub
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]
+ sub_files=:/home/user/script_testing/:/home/user/script_testing/g
+ FULLNAME=g
+ username=g
+ grep user.g.Contacts g.sub
user.g.Contacts	
+ echo 'Contacts already subscribed'
Contacts already subscribed
```

**Questions**: 
1. Why is it using the folder name ("g" in this instance) instead of the username?
2. Why is it not appending to the file? If I hardcode everything, it works correctly for one file. I think I am missing something simple. 
3. If I were to get this working, how would I get it to do so for multiple subfolders? To clarify, there are 26 subfolders (one for each letter of the alphabet) containing multiple username.sub files (along with other files)

---

### Post by prodigy_ on 2013-06-11
```
#!/bin/bash

root_dir="/home/script_testing"

find $root_dir -type f -regex "${root_dir}/\([a-zA-Z]\)/\1.*\.sub" -print0 | \
	while read -r -d $'\0' full_name; do
		file_name=$(basename "$full_name")
		user_name="${file_name%%.*}"
		if grep "user.${user_name}.Contacts" "$full_name"; then
			echo "Contacts already subscribed"
		else
			echo "subscribing to contacts"
			echo -e "user.${user_name}.Contacts\t" >> "$full_name"
		fi
	done

```

---

### Post by HiImTye on 2013-06-11
> **gforster said:**
> **Questions**: 
1. Why is it using the folder name ("g" in this instance) instead of the username?
2. Why is it not appending to the file? If I hardcode everything, it works correctly for one file. I think I am missing something simple. 
3. If I were to get this working, how would I get it to do so for multiple subfolders? To clarify, there are 26 subfolders (one for each letter of the alphabet) containing multiple username.sub files (along with other files)

1.because you're using find and /home/user/script_testing/g is the last result. specify ```
-maxdepth
``` to prevent find from going too deep, however, it would be much simpler to just
```
#!/bin/bash
p=$HOME/script_testing
for d in $p/*; do
 # if this is a folder
 if [ -d "$d" ]; then
  # check its contents
  ls "$d"| while read -r f; do
   # if this is a file
   if [ -f "$f" ]; then
    # define variables
    F="${f##*/}"
    u="${F%%.*}"
    yes=$(grep "user.$u.Contacts" "$f")
    # if our file doesn't contain our string
    if [ -z "$yes"]; then
     # add it
     echo -e "user.$u.Contacts\t" >> "$f"
    fi
   fi
  done
 fi
done

```
might want to double check it (I'm on my tablet) but it should be fine
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Vaphell on 2013-06-11
why would you want to use unreliable *ls "$d" | while read f* when you can use the same trick as with d -  *for f in "$d"/** ?
how about *for f in "$p"/*/** ?

---

### Post by HiImTye on 2013-06-11
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
 considered switching it to the second but didn't feel like editing it beyond correcting tablet typing issues

why is ```
ls | while read
```unreliable? I googled but no beans

---

### Post by Vaphell on 2013-06-11
[http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

---

### Post by HiImTye on 2013-06-11
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
so it's only an issue if you use weird filenames? good to keep in mind, but given the formatting implied in post#1 it isn't an issue

---

### Post by Vaphell on 2013-06-11
ugly non-kosher shortcuts reinforce bad, potentially dangerous habits and not always you have processed filenames under full control. Let's you run some malformed script that creates a lot of garbage files everywhere due to a simple typo. How would you clean up these files with non-printable chars all over the place with *ls* that is unable to reproduce their names correctly?

When it comes to filenames the order would be as follows: 100% rock solid native globs, then 100% rock solid find -print0 + while read -d $'\0', then dirty hacks if there is absolutely no other choice. If you do the right thing right off the bat, you don't have to fix anything when it comes to more complicated inputs and it's not like you need to write an additional page of code to get proper solution.

---

### Post by HiImTye on 2013-06-11
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
I don't know how prevalent newlines are in filenames, but it stands to reason that if they were as common as you make them out to be, everyone would have a filesystem completely destroyed by ```
ls | while read
```sounds like a linux boogeyman to me

---

### Post by Lars Noodén on 2013-06-12
I'd defer to Vaphell's experience there.  In general it's always best to learn the right way when starting something new so that there is less to unlearn along the way.  It's really hard to unlearn bad habits like relying on ls once they get set.  So it's less work not to go down that path in the first place.  

If you need anecdotal support, I've gotten stung more than a few times in the distant past by (mis-)using **ls** in place of globbing.  Mostly it was caused by spaces in the file names and paths.

---

### Post by gforster on 2013-06-12
Thank you all for the help. And the discussion does help. I agree in learning it the right way. I also understand hacking something together quickly on a tablet. 

Dangerous question: given the above solution, what would be the ideal way to check for and append mutliple lines? Another if statement? Or elif?

---

### Post by Vaphell on 2013-06-12
You can't depend on filenames not having any crappy characters because they are impossible to create via GUI. A script with a subtle typo or wrong base assumptions can create them, eg create filename directly from grep some output assuming only 1 result, but there is an oddball chance you get 2 matches - voila, you've just created a newlined file.
Long story short in extX filesystems all characters except \0 and / are legit. Work with that and you will NEVER fail.

If you have
a\nb
a
b
in case you wanted to do something like *ls a* | while read d; rm -rf "$d"; done*
you would delete b too. Sounds like a fat fail to me

Attitude of 99.9% is good enough wouldn't get you far in the programming field. Dealing with almost impossible corner cases is its daily bread because once you or your users use the program enough times they are bound to hit some of them.

---

### Post by gforster on 2013-06-12
Nevermind, it looks like I got it. Well, at least it is working. Any glaring errors?

```
#!/bin/bash
p=$HOME/script_testing
for d in $p/*; do
 # if this is a folder
 if [ -d "$d" ]; then
  # check its contents
  for f in "$p"/*/* ? ; do
   # if this is a file
   if [ -f "$f" ]; then
    # define variables
    F="${f##*/}"
    u="${F%%.*}"
    cont=$(grep "user.$u.Contacts" "$f")
    cal=$(grep "user.$u.Calendar" "$f")
    # if our file doesn't contain Contacts subscription
    if [ -z "$cont" ]; then
     # add Contacts subscription
     echo -e "user.$u.Contacts\t" >> "$f"
    #fi
    # if our file doesn't contain Calendar subscription
    elif [ -z "$cal" ]; then
     # add Calendar subscription
     echo -e "user.$u.Calendar\t" >> "$f"
    fi
   fi
  done
 fi
 done
```

---

### Post by Vaphell on 2013-06-12
what was your script supposed to do exactly?
find sub files and do something based on their name?

either way if you want to find files 2 levels deep you can use right off the bat

```
for f in "$root_dir"/*/*.sub
```

you don't have to check if the intermediary is a dir, it can't be anything else.

in other words this is superfluous
```
for d in $p/*; do
 # if this is a folder
 if [ -d "$d" ]; then
```

---

### Post by gforster on 2013-06-12
very cool. Thanks so much. soon, I will be able to do this on my own without assistance. Though, I do have another unrelated problem I will likely be asking for help with soon.

---

