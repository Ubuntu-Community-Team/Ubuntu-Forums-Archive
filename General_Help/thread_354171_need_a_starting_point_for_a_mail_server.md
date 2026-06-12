---
title: "need a starting point for a mail server"
date: 2007-02-05
forum: General Help
---

### Post by nephish on 2007-02-05
lo there all.
i need a good starting point for the easiest email server i can install.
i need to be able to send and receive mail from mydomain.com ( local machine )
i have the mx records set up, i think they are good. my problem is where do i start ?

i have been through dozens of tutorials for dovecot, exim, postfix, courier. no telling how bad i have scrambled my os with config files. just cannot seem to make the pop one work. 

i don't care if it uses system users, or if it uses virtual users. I got apache set up, but this email thing is kicking my butt. Is there no simple install for all this ?

thanks for any tips. or links to a simple tutorials, i cant seem to find one, not an easy or recent one anyway. 

thanks all

---

### Post by llamakc on 2007-02-05
What POP server did you last try installing, and how are you testing it?

---

### Post by nephish on 2007-02-05
well, the box ( ubuntu edgy ) came with exim ( not sure which ) and 
i have a python script that i could just point to localhost and it worked. I was able to send mail to my Gmail account. Set up evolution and it seemed to work too. i think that i am ok with sending 
just being able to get anything was a problem. 

i think i spent the most time working with courior-pop 

i set it up in evolution using my [email]username@mydomain.com[/email]
also tried local host. 

for a while it could not even connect. then i found errors in the logs regarding no maildir. so i found that command and created a mail dir for my user. 

right now ( i think from all the tinkering ) i cannot even connect to the localhost pop server.

---

### Post by llamakc on 2007-02-05
Is the courier-pop daemon running?

Do (in a Terminal)

`ps aux | grep pop`

---

### Post by nephish on 2007-02-05
ok,. i got this

piv      23239  0.0  0.0   2800   760 pts/7    S+   17:13   0:00 grep pop

---

### Post by llamakc on 2007-02-05
Also, try telnetting to the POP port:

```

telnet yourdomain.com 110

 telnet localhost 110
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
+OK Hello there.
USER XXX
+OK Password required.
PASS XXXXXX
+OK logged in.
STAT
+OK 2 2433
LIST
+OK POP3 clients that break here, they violate STD53.
1 1178
2 1255
.
QUIT 
+OK Bye-bye.
Connection closed by foreign host.


```This way you'll know if POP access is working, and can figure out why it's not delivering next.

[FONT=Times New Roman][SIZE=3]  Commands that you can/must use are:

 **USER *userid***
This must be the first command after the connect. Supply your e-mail userid (not the full e-mail address). Example: USER john.smith

 **PASS *password***
This must be the next command after USER.  Supply your e-mail password.  The password may be case sensitive.

 The following commands may be used as needed:

 **STAT**
The response to this is: +OK #msgs #bytes Where #msgs is the number of messages in the mail box and #bytes is the total bytes used by all messages. Sample response: +OK 3 345910

  **LIST**
The response to this lists a line for each message with its number and size in bytes, ending with a period on a line by itself. Sample response:
 +OK 3 messages
 1 1205
 2 305
 3 344400
 .

 **QUIT**
This deletes any messages marked for deletion, and then logs you off of the mail server.  This is the last command to use.   This does not disconnect you from the ISP, just the mailbox.[/SIZE][/FONT]

---

### Post by llamakc on 2007-02-05
> **nephish said:**
> ok,. i got this

piv      23239  0.0  0.0   2800   760 pts/7    S+   17:13   0:00 grep pop

Okay, that's just YOUR search for the string "pop", so no pop daemon is running. Do you have one in /etc/init.d/?

How about this, the output of:

dpkg -l | grep pop

Mine says:

```

 dpkg -l | grep pop
ii  courier-pop                                0.53.2-3ubuntu1                      Courier Mail Server - POP3 server
ii  courier-pop-ssl                            0.53.2-3ubuntu1                      Courier Mail Server - POP3 over SSL
ii  libpoppler1                                0.5.4-0ubuntu4.1                     PDF rendering library
ii  libpoppler1-glib                           0.5.4-0ubuntu4.1                     PDF rendering library (GLib-based shared lib
ii  libpopt0                                   1.10-2                               lib for parsing cmdline parameters
ii  notification-daemon                        0.3.5-0ubuntu7                       a daemon that displays passive pop-up notifi
ii  poppler-utils                              0.5.4-0ubuntu4.1                     PDF utilitites (based on libpoppler)
ii  popularity-contest                         1.33ubuntu2                          Vote for your favourite packages automatical

```

Ignore the poppler ones, but see where I have courier-pop and courier-pop-ssl installed? Are those installed on your system yet?

---

### Post by nephish on 2007-02-05
ok this is what i got from telnet

telnet localhost 110
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
+OK Hello there.
USER xxx
+OK Password required.
PASS xxxxx
-ERR Login failed.

and this is the relevent out put of the dpkg -l

dpkg -l | grep pop
ii  courier-pop                                0.53.2-3ubuntu1                      Courier Mail Server - POP3 server
rc  courier-pop-ssl                            0.53.2-3ubuntu1                      Courier Mail Server - POP3 over SSL

( there were other things but i know that they are not relevent, xchat, pdf viewer , etc..

thanks by the way

---

### Post by llamakc on 2007-02-05
Edit your post and put XXX's for your username, password please.

Next, lets purge all of your courier-pop files.

`sudo apt-get remove --purge courier-pop`

`sudo apt-get update`

`sudo apt-get install courier-pop`

But only do so AFTER you are certain there are no files leftover by courier-pop in /etc/courier, namely the files:

pop3d and pop3d.cnf

---

### Post by llamakc on 2007-02-05
Does your /etc/default/courier file look like this:

```

# This file is automatically generated by maintainer scripts.
# You may modifiy this file, but additional values and format
# modifications will not be preserved.
MAILDIR="Maildir"

```

and what happens when you restart the POP daemon:

```

sudo /etc/init.d/courier-pop restart

 * Stopping Courier POP3 server...                                       [ ok ] 
 * Starting Courier POP3 server...                                       [ ok ] 

```

---

### Post by chalex on 2007-02-05
You mentioned your MX records are set up.  Are you sure your ISP allows incoming traffic on port 25?

Try sending a mail from a different e-mail address, see if you get a bounce or an NDR.

---

### Post by nephish on 2007-02-05
ok, did the re-install
checked the /etc/default/courier and it does say
MAILDIR="Maildir"

restart gave me an ok

new telnet looks like this
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
+OK Hello there.
USER xxx
+OK Password required.
PASS xxxxx
-ERR Temporary problem, please try again later
Connection closed by foreign host.

---

### Post by llamakc on 2007-02-05
In your /etc/courier/pop3d file what's the value of POP3AUTH? Mine is on line 43.

---

### Post by nephish on 2007-02-05
i do not have a value in it, 
my line 43 says
POP3AUTH=""

---

### Post by llamakc on 2007-02-05
Are you running Firestarter or any other firewall(s)? Does your router (if you have one) allow packets to pass through to your machine?

What are your mail logs saying? Open two terminals and tail the mail log:

sudo tail -f /var/log/mail.log

and in the other one try connecting again, watching the log to see what happens.

---

### Post by llamakc on 2007-02-05
> **nephish said:**
> i do not have a value in it, 
my line 43 says
POP3AUTH=""

Mine has the same thing. Do you know if you are running Exim4 or Postfix?

---

### Post by nephish on 2007-02-05
i am running postfix,
our router is configured to allow mail thru 143 and 110
postfix is working, my python script is able to get mail to my gmail account.
i am not getting any bounces though trying to go from gmail back to my domain.

here is something weird, in the tutorial, there is a step by step of how to send an email thru a telnet session, that made it successful in the logs. when i try to point evolution to my username nad using localhost as the server, i cant connect, and nothing shows up in the logs. 

there is part of the account setup where i check what type of authentication i am using and there is an option to check supported types, that fails to connect to server localhost.

hope these clues help
and thanks

---

### Post by nephish on 2007-02-05
one more thing, i guess i scrambled my authdaemonrc file from /etc/courior because it was missing. i installed courier-pop on my home box here ( also ubuntu) and copied the authdaemonrc flle over to my work machine, restarted the /etc/init.d/courier-authdaemon and now i can log in thru telnet. 

however, i am still screwed up with evolution

---

### Post by llamakc on 2007-02-05
And you are using Maildir, correct? Do this: open a terminal and as your user type:

mail

If it says "No mail for USER" let me know. I'm wondering if mail is going to the mbox spool instead of your Maildir.

---

### Post by nephish on 2007-02-05
yes, no mail for user.
however if i go to ~/Maildir/new  there is some stuff in there

---

### Post by llamakc on 2007-02-05
Why not configure Evolution or whatever to look at that Maildir tree?

---

### Post by nephish on 2007-02-06
well, i am not so much interested in whether i use tbird or evolution. The real reason we need to be able to get email at this server is for another server that will send us machine updates by email. 

here is what i have working with courier-pop and postfix. sending mail is fine.
i can telnet mydomain.com 110 and log in from outside the lan. 
it also shows up in the logs when i do so. 
i can send and receive email from other machines on the lan using this mail server.
i cant seem to get a mail message from outside the lan to this box.
i have tried both [email]user@mail.mydomain.com[/email] ( how my mx record looks ), [email]user@my.ip.addr[/email]ess, and [email]user@mydomain.com[/email] (another mx record i have )

none of it gets through, no bounces, no undeliverable mail messages come back. Its like they just disappear..

anyway, thanks for all of your help on this, llamakc, you got me farther than i would have found myself without your help.

---

### Post by nephish on 2007-02-06
Hey there, i am up and running.
way cool. 

thanks for all of your help.
could not log in because authdaemon was not running.

thanks again for all of your config help

---

