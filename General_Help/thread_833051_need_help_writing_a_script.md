---
title: "need help writing a script"
date: 2008-06-18
forum: General Help
---

### Post by dexter.deepak on 2008-06-18
i had a manual install of tomcat6 and i need help mking a script which stops,starts ,restarts and checks status of tomcat.
i managed to make simple script to start and stop tomcat but have difficulty in the latter two.
can someone help ?

---

### Post by bodhi.zazen on 2008-06-18
You can test if tomcat is running with :

```
if ! (ps -C tomcat > /dev/null) ; then
 ... put commands here (ie restart tomcat)
fi
```

---

### Post by dexter.deepak on 2008-06-18
thanks a lot ...but could  you explain the meaning of 
ps -C tomcat > /dev/null)

what does it do ??

and i want seperate scripts to have restart and for checking status of tomcat!!

---

### Post by bodhi.zazen on 2008-06-18
ps checks running processes. To list all running processes use :

```
ps aux
```

The -C if a flag and tells ps to list that command.

see man ps

> /dev/null re-directs the output

( ) runs the command in a sub shell and return a value (success or failure) which is then tested by the if ...

the ! negates the test

if ! (ps -C tomcat) == is "ture" if tomcat is not running
if (ps -C tomcat) == is true" if tomcat is running

so basically you are asking "if tomcat is not running ... then ..."

if you write separate start / stop / restart scritps, just call them

START=/path/to/start_tomcat
STOP=/path/to/stop_tomcat

while ...
if ! (ps -C tomcat > /dev/null); then
  $START
fi
sleep 30
done

put that fragment in a while loop or ...

HTH ...

---

### Post by dexter.deepak on 2008-06-18
why redirect that stuff?? :confused:

if ! (ps -C tomcat > /dev/null) :

what i can understand here is that the () would contain the value of pc -C tomcat > /dev/null ....that is the return value of "whether the output of pc -C tomcat has been successfully redirected to /dev/null"
that is the () would contain the return value of the redirection and not of the ps command :confused:

please tell me if i am wrong ...

---

### Post by omrsafetyo on 2008-06-18
Nope.  You are redirecting the output from the ps command..

e.g.
$ ps -eaf | grep whoami
000nkula 240300 296728   0 14:16:17 pts/168  0:00 grep whoami
$ ps -eaf | grep whoami > /dev/null
$

If you do not redirect the output, then the results of the ps will be displayed to the terminal.  You don't want this, because you want it to be silent.

Either way, the if command will be able to read the return status of the command (true if it returned results, false if the ps command returned nothing)

for instance - if instead of
$ ps -eaf | grep whoami
000nkula 240300 296728   0 14:16:17 pts/168  0:00 grep whoami

I say

$ ps -eaf | grep whoami | grep -v grep

This returns nothing.  Whether or not I output this to /dev/null, the return status is 0 (false).

The return status of this:
$ ps -eaf | grep whoami
000nkula 240300 296728   0 14:16:17 pts/168  0:00 grep whoami

Is anything other than 0 and therefore true - regarless of where the output is directed.

To think of it this way, the redirect ( > ) only changes where the results are displayed.  Standard output is the monitor/console.  By redirecting, you are sending it elsewhere (/dev/null).

From here, you just need to wrap your code into a while loop that cannot be satisfied (while 1=1 or etc.) with a sleep x at the end.  Then you run your command at start up, and it will check your service and restart it every x seconds.

I hope it helps!

---

### Post by bodhi.zazen on 2008-06-18
lol

Try it as a fragment on the command line and see what happens :)
[INDENT]Best way to learn , really
[/INDENT]Basically, in a nut shell, you do not want the output of the command "ps -C tomcat" you want to know if tomcat is running.

If tomcat is running , the command ps -C tomcat completes with no error (exit 0)

If tomcat is not running, the command exits with an error (exit 1)

But ps -C returns things we do not want and using pipes in tests gets complex, in a nut shell the return value will be that of the last command and may not be 0 or 1 (see bash error messages for the gory details).

I ran the command in a sub shell ( ) to get around this.

Run (with tomcat stopped and running):

```
`ps -C tomcat` ; echo $? #this echos the exit status
if `ps -C tomcat`; then : ; fi 
`ps -C tomcat > /dev/null` ; echo $?
if `ps -C tomcat > /dev/null`; then : ; fi 
(ps -C tomcat > /dev/null) ; echo $?
if (ps -C tomcat > /dev/null); then : ; fi
```Note the command : == do nothing (just running the command through the test)

I think those snipits will be educational, of course there may be better of different ways of "skinning the tomcat".

---

