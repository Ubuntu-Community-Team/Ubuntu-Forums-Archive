---
title: "running teamviewer in firejail"
date: 2017-06-05
forum: General Help
---

### Post by rosika on 2017-06-05
Hello everybody,

is there a way of _running teamviewer in firejail_? Whenever I try to do this firejail complains about “teamviewer daemon not running”.


```
Child process initialized


Init…
XRandRWait: No value set. Using default.
XRandRWait: Started by user.
Checking setup…
Launching TeamViewer …
Starting network process (no daemon)
terminate called without an active exception
/opt/teamviewer/tv_bin/script/tvw_exec: Zeile 95: 113 Abgebrochen “$TV_BIN_DIR/teamviewerd” -n -f
Network process already started (or error)
Launching TeamViewer GUI …



```
Running teamviewer outside the sandbox works fine.

Greetings.
Rosika   :(

P.S.:
system: Linux/Lubuntu 16.04.2.LTS (64bit)

---

### Post by vasa1 on 2017-06-05
Hi,
Please edit your post to include the full command used and the version of Firejail. Thanks!

BTW, the developer doesn't seem optimistic: [https://github.com/netblue30/firejail/issues/825#issuecomment-251221645](https://github.com/netblue30/firejail/issues/825#issuecomment-251221645)> It cannot be sandboxed the normal way - the guy needs to become root and start daemons. That's bad, you are running a closed source executable as root!

---

### Post by rosika on 2017-06-05
Hi, 

sorry for the incomplete data.

The command I used was

```
firejail teamviewer 
```
But the same problem occurs with any command, like
```
firejail --private teamviewer
``` 
or

```
firejail --noprofile teamviewer
```

The firejail version is:  0.9.38.10-0ubuntu0.16.04.1 

Greetings.
Rosika

---

### Post by rosika on 2017-06-05
Hi,

thanks for the link. I read it through and it seems  there´s not a lot one can do about it at the moment.
That´s a real shame.

Does anyone know of another sandbox-technique which can run teamviewer?

Greetings.
Rosika

---

### Post by howefield on 2017-06-05
Seems that you won't be able to get this going, at least for the moment,

I'll give a vote to anydesk which I know you have rejected in a thread elsewhere but consider that it is produced by ex Teamviewer employees and is getting good reviews. It does seem to work with firejail and may be worth another look.

---

### Post by rosika on 2017-06-05
Hi howefield,

thanks for your reply.

> [...] [COLOR=#000000]anydesk which I know you have rejected in a thread elsewhere [...][/COLOR]

To tell the truth, I am not aware of having rejected anything and certainly not _anydesk. _ But perhaps I am mistaken and my memory abandoned me here :confused:.

And I must say _anydesk_ seems like good advice especially in view of the fact that it´s supposed to work with firejail.
I didn´t know that it is produced by [COLOR=#000000]ex Teamviewer employees . All the better.

So I think I´ll give it a try .

Thanks again for your help.

Greetings.
Rosika  [/COLOR]:)

---

### Post by vasa1 on 2017-06-05
> **rosika said:**
> ...
To tell the truth, I am not aware of having rejected anything and certainly not _anydesk. _ But perhaps I am mistaken and my memory abandoned me here :confused:.
...
Maybe [https://forum.ubuntuusers.de/topic/teamviewer-in-sandox-starten/](https://forum.ubuntuusers.de/topic/teamviewer-in-sandox-starten/)> 28. Februar 2017 17:31
Hi Mimosin,

danke für Deinen Vorschlag. Dieses Programm habe ich noch gar nicht gekannt. Scheint eine interessante Alternative zu teamviewer zu sein. Das Problem ist, den Leuten, denen ich im allgemeinen helfen möchte, kann ich gar nicht zumuten, von dem ihnen bekannten teamviewer abzuweichen und etwas anderes zu installieren. Die meisten sind schon damit überfordert.
Deshalb suche ich nach Alternativen einer Sandbox, in welcher ich teamviewer starten kann.

Dennoch vielen Dank für Deinen Hinweis.

Grüsse. Rosika

---

### Post by rosika on 2017-06-05
@vasa1 and howefield,

I sincerely have to apologize. I really didn´t recall having dealt with the possibility of using _anydesk _in another forum.
So both of you are perfectly right.

In view of the circumstances l´ll certainly give _anydesk_ a try combined with the hope to be able to convince my potential  help-seekers  to use
it as well ;).

So thanks again for your suggestion. I am very glad to have become a member of ubuntu forums as it seems to offer excellent help.

Best wishes
Rosika  :)

---

### Post by vasa1 on 2017-06-05
> **rosika said:**
> ...
is there a way of _running teamviewer in firejail_? Whenever I try to do this firejail complains about &#8220;teamviewer daemon not running&#8221;.
...
I came across this:> A minor stumbling hazard for web servers, databases, and other services 
is that their daemons immediately disappear into the background when launched. Firejail then 
believes that the program was terminated and takes down the sandbox and the service with it. To 
prevent this from happening, you need to resort to the following trick:```
firejail "/etc/init.d/sshd start && sleep inf"
```
to keep Firejail waiting, or running, infinitely after starting the daemon.
from [http://www.linux-magazine.com/Issues/2015/173/Firejail](http://www.linux-magazine.com/Issues/2015/173/Firejail)

I don't know what that means but it may be relevant. Given that the developer is relatively accessible on [firejail's github page]("https://github.com/netblue30/firejail/issues"), one could ask there before proceeding in view of the concern I linked to in an earlier post: [https://ubuntuforums.org/showthread.php?t=2363030&p=13653074#post13653074](https://ubuntuforums.org/showthread.php?t=2363030&p=13653074#post13653074)

---

### Post by rosika on 2017-06-06
Hi vasa1,

thanks a lot for the suggestion and the link. In the respective article they seem to deal  with all kinds of scenarios.
So at first I thought 
```
firejail "/etc/init.d/sshd start && sleep inf"
```
might be working but my terminal returns:

```
Reading profile /etc/firejail/generic.profile
Reading profile /etc/firejail/disable-mgmt.inc
Reading profile /etc/firejail/disable-secret.inc
Reading profile /etc/firejail/disable-common.inc


** Note: you can use --noprofile to disable generic.profile **


Parent pid 4335, child pid 4336


Child process initialized
/bin/bash: /etc/init.d/sshd: Datei oder Verzeichnis nicht gefunden



```
And indeed there is no file "**sshd" **within "**/etc/init.d/**".
Well, I could try contacting the developer but my guess is chances a pretty bad in view of what is said on  [https://github.com/netblue30/firejail/issues/825#issuecomment-251221645](https://github.com/netblue30/firejail/issues/825#issuecomment-251221645)  .

So perhaps I might resort to _anydesk _ after all .......

Thanks again for all the effort of yours.

Greetings.
Rosika  ;)

---

