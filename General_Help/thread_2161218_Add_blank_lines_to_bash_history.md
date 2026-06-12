---
title: "Add blank lines to bash history"
date: 2013-07-09
forum: General Help
---

### Post by hwttdz on 2013-07-09
I realize this is a weird request, but I was wondering if it might be possible to add blank lines to the bash history?  I.e. I want !! to be the no-op. Scanning about I can't seem to figure out how to do this.

---

### Post by llamabr on 2013-07-09
> **hwttdz said:**
> I.e. I want !! to be the no-op. Scanning about I can't seem to figure out how to do this.
I read this twice, and I'm still not sure what you're asking.

---

### Post by VMC on 2013-07-09
I'm guessing you want '!!' to run " " or when you type "!!" then a blank line to appear?!

What is the outcome of all this. What are you trying to accomplish?

---

### Post by bejiitas_wrath on 2013-07-09
You can add the line** unset HISTFILE** to your .bashrc and then entries destined for the .bash_history file will not be written. That is all I can come up with.

---

### Post by hwttdz on 2013-07-09
I still need the history, I'd just like blanks in there, closer to what vmc is describing. I've made a sort of custom history, where the command, directory in which it was run and time at which it was last run are all maintained. However if you run, say ls, then just press enter a few times !! is still ls (which trips me up a bit), even more odd is that !! in a new terminal is the last line in the history, when I might have expected it to be blank. Essentially what I want is what I typed at the last prompt, even if it's empty.

---

### Post by CaptainMark on 2013-07-11
So what you're saying, (I think) is that if you just hit return at a blank terminal prompt, you want a blank line to be printed to .bash_history?
Why?

---

### Post by hwttdz on 2013-07-11
Because the alternative is that the last line of the history reflects something other than what was typed last at the prompt.  I want to get what was typed last at the prompt because it will make history management more useful to me.  

Here's a relevant block from my .bashrc
```
PROMPT_COMMAND='thiscommand=`fc -ln -1 | perl -pe "s/^\s+//"`
if [[ "$thiscommand" != "" ]]; then
    pwd > ~/.tmp_command
    echo "$thiscommand" >> ~/.tmp_command
    mv ~/.tmp_command ~/.history/`md5sum ~/.tmp_command | cut -c 1-32`
fi'
```

The catch is "$thiscommand" is not always the last thing that was run.  If I happen to leave a terminal up for a few days and then press enter in it before I run something else, whatever that last command I ran will get put into my ~/.history directory, even though it did not in fact run again.  I think this solution is interesting in general, because it allows me to keep lots of history, but only one copy of each command per directory.  And also tells me when the last time a command was run.  There are some other conveniences like being able to delete history more than 1 month old "find ~/.history -mtime +30 -delete", knowing which directory a command was run in...

---

