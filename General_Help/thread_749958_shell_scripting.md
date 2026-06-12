---
title: "shell scripting"
date: 2008-04-09
forum: General Help
---

### Post by Mrwasab1 on 2008-04-09
I had no idea where else to put this, but here it goes...
im trying to write a script in ksh which displays a number of pagers, and when the user selects the pager, they then enter in a message and the message is sent to the pager...
works perfectly, its a simple thing...

now, the pagers have a character limit on them, so i wanted to limit the amount of text being inputed by the user.

how can i do this?
currently this is how im paging out

```

function pageout {
clear
echo
echo "Please enter the message to send to "$name""
echo "Message [Leave blank to quit]: \c"
read msg
	if [[ -n $msg ]] ; then
		echo "" | mailx -s "$msg" "$pager"
		clear
		echo
		echo "${flash}Page has been sent to $name.${norm}"
		sleep 2
	else
		echo "${flash}NO MESSAGE DETECTED. EXITING${norm}"
		sleep 3
	fi
}

```

---

### Post by johnl on 2008-04-09
you can use cut to limit input to a certain number of characters and/or truncate it.  Not familiar with ksh, but in bash I would do:


```

MESSAGE="whatever your message is"
CUT_MESSAGE=$(echo "$MESSAGE" | cut --characters=1-10)

if [ "$MESSAGE" != "$CUT_MESSAGE" ]; then
    echo "'$MESSAGE' is too long!"
    echo "truncating to '$CUT_MESSAGE'"
else
    echo "'$MESSAGE' is ok length."
fi

```

---

### Post by Mrwasab1 on 2008-04-09
hmm good point.
However i want to stop the user from writing more than what they are allowed.

Say the pager has a limit of 100 characters, if they send a message which is 150 and the important part of the message is in the last 50, then the message wont get through. if i use cut, i will be simply doing what the pager already does, and thats cut out the end of the message.

i want it to behave sort of like a text box in a web based form that stops your writing when you hit 100 characters so that the user knows they have to reword their message to fit.

---

### Post by sdennie on 2008-04-09
You could test the input message to see if it's over a certain number of characters (and then reprompt) with something like:

```

echo $MESSAGE | wc -m

```

That should return the number of characters the user has entered if the message is stored in $MESSAGE.

---

### Post by ghostdog74 on 2008-04-09
```

awk  'BEGIN{
    name="peter" #define your name here
    pager="root" #define pager here
    subject="test" #define subject here
    while (1){
        printf "%s %s: ", "Please enter the message to send to" , name 
        getline msg < "-"
        if ( length(msg) > 100 || length(msg) <=0 ) {
          print "message more than 100 chars or 0 length, pls try again"
          msg=""
          continue
        }else {
          cmd="mailx -s " subject " "pager
          print "echo "msg | cmd
          break
        }
    }
}' 

```

---

