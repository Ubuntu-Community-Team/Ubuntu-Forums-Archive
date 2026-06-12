---
title: "strange terminal message when using &quot;firejail thunderbird&quot;"
date: 2017-07-14
forum: General Help
---

### Post by rosika on 2017-07-14
Hi altogehter,


as of late my terminal produces a curious info message when I use thunderbird. I have to add that I start thunderbird within a sandbox (firejail) using the command


```
rosika@rosika-Lenovo-H520e ~> firejail thunderbird
Reading profile /etc/firejail/thunderbird.profile
Reading profile /etc/firejail/disable-mgmt.inc
Reading profile /etc/firejail/disable-secret.inc
Reading profile /etc/firejail/disable-devel.inc
Parent pid 6944, child pid 6945
Blacklist violations are logged to syslog

```

Until recently that worked fine.
But now I get the message (not always but rather often)


```
Error moving window, closing window
Error moving window, closing window
Error moving window, closing window
Error moving window, closing window
Error moving window, closing window
Error moving window, closing window
Error moving window, closing window
Error moving window, closing window
Error moving window, closing window
Error moving window, closing window
Error moving window, closing window
Error moving window, closing window
Error moving window, closing window
Error moving window, closing window
Error moving window, closing window



```That goes on endlessly.
Curious though that thunderbird itsfelf doesn´t show any unusual behaviour whatsoever. It just works well. Yet the terminal output got me worried.
And I don´t understand it because I didn´t move the window. Anyway what window? Thunderbird´s?
And it didn´t get closed either.


The thing is, I cannot tell whether that phenomenon is produced by firejail or by thunderbird but I strongly suspect thunderbird.


Can anyone help?


Thanks in advance.
Rosika  :confused:

---

### Post by rosika on 2017-07-15
[COLOR=#000000][FONT=Verdana]*****UPDATE*****[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I found out that the problem has nothing to do with firejail.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I ran thunderbird "normally" and it happened again.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]It seems it has something to do with the [/FONT][/COLOR][B]_junk-folder_.
[/B]After starting thunderbird it automatically scans for new e-mails. Amongst them there are some considered to be junk. Therefore thunderbird puts them in the junk-folder.

An that´s when the error-message is displayed.

Now I know the reason but why is that and what can I do about it?

Greetings.
Rosika

---

### Post by rosika on 2017-07-15
*****SOLUTION*****

[COLOR=#242729][FONT=Arial]In the meantime I filed a bug-report at 
[/FONT][/COLOR][https://bugzilla.mozilla.org/show_bug.cgi?id=1381220](https://bugzilla.mozilla.org/show_bug.cgi?id=1381220)
[COLOR=#242729][FONT=Arial]
Response:

 [/FONT][/COLOR]> looks like those messages are printed by one of your add-ons (possibly Mailbox Alert, but could be different one) try disabling your add-ons.[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]
It looks like the respective add-on was the culprit.

[/FONT][/COLOR]So it seems I´ve got to disable Mailbox Alert. It´s a shame though as I installed it for a reason. Thunderbird´s own mail-alert service worked rather unreliably.

Rosika  :(

---

### Post by vasa1 on 2017-07-15
[https://unix.stackexchange.com/questions/378633/strange-terminal-message-when-starting-thunderbird#comment673295_378633](https://unix.stackexchange.com/questions/378633/strange-terminal-message-when-starting-thunderbird#comment673295_378633) ;)

If that really fixes your issue you can mark this thread [SOLVED]: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

