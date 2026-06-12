---
title: "Command/script to open a terminal window run multiple commands and print outputs"
date: 2021-11-06
forum: General Help
---

### Post by jazahalka on 2021-11-06
Hi, this should be a very trivial question. Please how could I create a command or a script, which would open a terminal window, run a few commands printing their outputs in the terminal and then it would just wait. Thank you very much for any suggestions.

---

### Post by TheFu on 2021-11-06
> **jazahalka said:**
> Hi, this should be a very trivial question. Please how could I create a command or a script, which would open a terminal window, run a few commands printing their outputs in the terminal and then it would just wait. Thank you very much for any suggestions.

What have you created so far?  If you can type it into a terminal to get the result you want, then you can put those commands into a script and get similar outcomes if the environment is similar.  There are a few caveats, but those aren't too important for beginner-level scripts.

To open a terminal, run the terminal program.  Every terminal program I've seen will happily run a command, if that is passed as an option. The option will be dependent on which terminal program you choose to use.
The outputs from commands go to the window they are launched inside automatically.

There are lots of different way to handle this, but usually it is easiest to put the commands into a file - call it a script - chmod +x that file and pass the full-path to the file location as an argument into the terminal. Simple.  There must be 1,000 examples on the internet just like that and probably 500K example bash script to run a few commands.

If you can type it, then it can be scripted. If really is that simple.

---

### Post by jazahalka on 2021-11-07
I am dumb, thank you very much.

---

### Post by TheFu on 2021-11-07
> **jazahalka said:**
> I am dumb, thank you very much.

What commands, exactly, do you want to run?

---

