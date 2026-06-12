---
title: "what is '&gt; in terminal???"
date: 2008-02-24
forum: General Help
---

### Post by UnCola on 2008-02-24
What does '> mean in the terminal? 

I keep getting this and cannot proceed except by restarting the terminal, as it does not respond to commands or inputs.

Or is it a mysql command - I am logged into the mysql terminal in the terminal in ubuntu, but after getting '> I can't sign out of the mysql terminal using quit or \q or any other command that I can find.   Earlier commands that end with '> if copied and pasted without '> just recreate it and will not run.  Baffling, any help welcome.

---

### Post by steveneddy on 2008-02-24
It looks like you are logged in to a remote server and it is waiting for you to input a command.

---

### Post by rapiscan on 2008-02-24
Type 'exit' to log out of the mysql command line interface.

EDIT: Actually, I just tried and 'quit' also gets me out of mysql, so I'm not sure that you are inside of mysql if 'quit' doesn't work.  Perhaps it's version dependent?

EDIT #2: If you type 'help' and hit enter, it should provide information about your current interface.  The Bash shell will print out the version and the commands that you can use, mysql will also do the same.

---

### Post by UnCola on 2008-02-24
> **rapiscan said:**
> Type 'exit' to log out of the mysql command line interface.

EDIT: Actually, I just tried and 'quit' also gets me out of mysql, so I'm not sure that you are inside of mysql if 'quit' doesn't work.  Perhaps it's version dependent?

EDIT #2: If you type 'help' and hit enter, it should provide information about your current interface.  The Bash shell will print out the version and the commands that you can use, mysql will also do the same.

Hi thanks for the answers.  I am logged in locally.  When all is well once you have logged into mysql you get this:

mysql>

asking you to enter a command, and if you have forgotten the semicolon you get 

>

prompting you to enter a semicolon to end the command

and yes no problems then logging out of mysql


BUT what I am getting after a command is this:


                    '>

ie an indent, an apostrophe, a >
and no matter what command I type after that nothing happens, nor does it respond to typing a semicolon and pressing return.  ?????

---

### Post by spupy on 2008-02-24
Try pressing Control+D

---

### Post by WakkiTabakki on 2008-02-24
Yup, it's because you've type an opening quotation sign but haven't ended it... Same thing happens in the terminal.
Try ending the quote or hit Ctrl-C to break out.

/N

---

### Post by UnCola on 2008-02-24
Hi Control C worked, gives message   'Aborted' and exits mysql, thanks.

typing a ' and return gets me this:

-> 

after which I can type commands again, thanks.

---

