---
title: "Procmail not starting bash script."
date: 2014-07-15
forum: General Help
---

### Post by rnappr on 2014-07-15
I have a bash script I was given which I am using for work. Its a simple  script. Basically I get emails for work which I have to accept the job  by clicking a link within the email. So the bash basically just curls to  the link i need to accept so that these jobs can get accepted  automatically.
 
So I know that fetchmail is set up right because I am able to get my  gmail no probs. When I check my procmail log I see all the subjects of  the email but it does not start the script?? I have read on some site  that when the script start you should see on the procmail log that the  script was executed. I do no see this.
 
Before starting I have done this;
chmod 600 ~/.fetchmailrc
chmod 600 ~/.procmailrc
chmod 755 myscript.sh
 
Im thinking so far that it has to be something wrong in the .procmailrc, this is what I have..

```

SHELL=/bin/sh
PATH=/bin:/usr/bin:/opt/local/bin
MAILDIR=/home/username
LOGFILE=.procmail.log

:0
* ^From:.*sender*
* ^To:.xxxxxxxx at gmail dot com
| /bin/sh /home/username/myscript.sh

```

Also do I have to chmod evertime I am going to run the script?

do you see anything I am missing? Anything stick out in my .procmailrc? I am a total noob at linux and am learning as I go so if you think of anything I could have missed even entry level please let me know.. 
 

thanks!

---

### Post by rnappr on 2014-07-16
I was thinking could it be where the .procmailrc file is located? Where do you guys have your .procmailrc file located? mine is at /home/username/.procmailrc

---

### Post by SeijiSensei on 2014-07-16
Try testing the script from the command line.

Save a copy of a message that meets your filter requirements and should have been processed as a file.  Then run
```
$ /home/username/myscript.sh < /path/to/the/saved/message
```

Does it run properly?

Where the .procmailrc file should reside depends in part on how you have your mail server set up?  I use good-old mbox folders so having .procmailrc in my home directory works properly.  However if you're using something like Postfix with Maildir and perhaps even "virtual domains" then the location may be very different.  I'm afraid I can't help with that.

Does the script start like this?
```

#!/bin/sh

```
or
```

#!/bin/bash

```

If so, you don't need the /bin/sh in the procmailrc recipe.

---

### Post by rnappr on 2014-07-16
hey SeijiSensei thanks for taking your time to help me out..

well strange enough I checked the script and it does not start with #!/bin/sh or #!/bin/bash 

Not sure why it does not start that way. Should I make it the first line? Im a little confused because I read that "The first line of the script is important. This is a special clue given to the shell indicating what program is used to interpret the script. In this case, it is /bin/bash." But then it goes to say that "Everything that appears after a "#" symbol is ignored by bash."

So if the first line has to be #!/bin/bash to tell the shell what program to use why does it start with a # which is ignored by bash?

---

### Post by rnappr on 2014-07-16
ok i think i have fixed this by changing the .procmailrc file as I am at least now seeing it execute my script in the procmail-log. I will have to wait until tomorrow to get an email from my job to test.

thanks for your help I will report back.

---

### Post by SeijiSensei on 2014-07-16
The "hash-bang" sequence at the very top of a script is a convention to identify the program to interpret the script's commands.  In all other instances in bash, the hash character denotes the start of a comment.

Scripts that are written in a shell language like bash normally begin with the sequences I gave above.  I prefer to use "#!/bin/bash" for bash scripts because "/bin/sh" can point to a different command interpreter.  On Ubuntu /bin/sh points to /bin/dash, and I'm uncertain about how the two shells differ.  So I specify /bin/bash to be sure.

Scripts can be written in many languages so the hash-bang entry need not be just a shell.  For instance, scripts written in Perl usually begin with 
```
#!/usr/bin/perl
```

When you save an email message for testing, make sure you save it with all the headers.  They should start with
```
Return-Path: <someone@example.com>
```.  That will ensure you pass the same text to the script from the command prompt as you do in procmail.

---

### Post by rnappr on 2014-07-17
> **SeijiSensei said:**
> Try testing the script from the command line.

Save a copy of a message that meets your filter requirements and should have been processed as a file.  Then run
```
$ /home/username/myscript.sh < /path/to/the/saved/message
```

Does it run properly?
i did this test and got /home/username/myscript.sh: line 15: [: -gt: unary operator expected

the script did run and did what I needed it to do. 

Also I had one of the filters wrong in my recipe which is why I assume it wasnt running the script.

Two questions, will the error on line 15 be a problem for my script? also this script was able to run without the #!/bin/bash shebang. should I just include it to practice better script writing? Well I guess I should it wouldnt hurt I suppose. Well I answered my own question but do u think the error in line 15 is a serious problem?

thanks for all your help!

---

### Post by SeijiSensei on 2014-07-18
Remember that bash uses space as a delimiter.  The syntax
```
if [$X = 1]
```
is not valid.  Both "[" and "]" are operators and require spaces around them:
```
if [ $X = 1 ]
```
will work.  Check your line 15 to make sure there are the proper spaces.

If the script worked as expected, then perhaps the message you used for testing did not trip the if condition.  Try it with a message that would meet that condition; what happens then?

---

