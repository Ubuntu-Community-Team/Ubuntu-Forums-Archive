---
title: "Here's a fun one for ya - getlive"
date: 2008-01-17
forum: General Help
---

### Post by Ripfox on 2008-01-17
Now this is WAYYY out of my understanding. I finally got Mail Notification 5.0 installed (built from source) and the reason was that it supports windows live hotmail now. But...it depends on something called "getlive" 

[http://sourceforge.net/projects/getlive](http://sourceforge.net/projects/getlive)

How do I install this thing? I dont see a way to compile it, or do you?

Help me learn!

:)

---

### Post by Ripfox on 2008-01-17
Oh btw here's the text that came with it (which I don't see how to install it :oops:)

---

### Post by eroica on 2008-01-17
have u tried using hotway: [http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html](http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html)

---

### Post by Ripfox on 2008-01-17
I have my Hotmail working perfectly through Swiftdove. I just want to get a (you guessed  it) Mail Notification when a webmail comes into my swiftdove inbox. BUT...Mail Notification 5.0 requires getlive to work with hotmail accounts. I don't use evolution, and the problem lies squarely with Mail Notification. :)

---

### Post by Ripfox on 2008-01-18
bump...I know it's alpha software :)

---

### Post by Ripfox on 2008-01-20
bummmpaaa

---

### Post by bollix47 on 2008-01-20
Don't know anything about Mail Notification 5 but I do use swiftdove and for my notifications I use [New Mail Icon]("http://moztraybiff.mozdev.org/releases.html").

Shows an envelope icon in the notification area when new mail arrives.

I too have a hotmail live account and get notified.

I use the [Webmail and Hotmail extensions]("http://forums.mozillazine.org/viewtopic.php?t=558335&highlight=") to check for hotmail and download to swiftdove.

---

### Post by Ripfox on 2008-01-20
I find that to be useless (no offense) since it closes when you close TB. :(

This new add on for Mail Notification would be ideal, but if no one here knows how to install the "getlive" dependency....:(

I have webmail working perfectly, as I said in previous posts.

---

### Post by Ni85 on 2008-02-01
hey there
i'm a total neewb, but i might help you in this, since i'm trying to get it working to download my hotmail mail on the pc with evolution.

first of all unpack it in a new folder (let's say home/username/.getlive) and install through synaptic "curl" and "procmail" or "postfix".
i found two ways to let it work, pretty much the same. the first one needs procmail, the second one postfix.

first method:
create in the folder where you have unpacked the tar file a new file (i'll call it from now on "fingercrossed" :) )
in this file you have to configure your settings. the manual in the unpacked file has under "usage" a list of the possible settings.
i did something like this:

UserName        = your mail user name before @
Password        = your mail password
Domain          = hotmail.com
#Proxy           = ProxyServer if you're behind one.
#ProxyAuth       = ProxyPassword if you're behind one with password. 
Downloaded      = Downloaded
FetchOnlyUnread = No
RetryLimit      = 2
CurlBin         = curl -k
Processor       = /usr/bin/procmail
Folder          = Inbox
MarkRead        = Yes
Delete          = No

save it.
run from terminal
```
$ cd home/yourusername/.getlive
$  ./GetLive.pl --config-file fingercrossed

```

you should start seeing your mails being downloaded (you can interrupt the download with ctrl + C) and find them afterwards in a file called as your user name in /var/mail
you have to do this manually every time you want to download your mail. (the french wiki mentioned below explains how to edit the crontab file to let these command run automatically every x minutes, haven't tried it yet)

the second setting is the one suggested by this french wiki
[http://doc.ubuntu-fr.org/tutoriel/hotmail_getlive_evolution](http://doc.ubuntu-fr.org/tutoriel/hotmail_getlive_evolution)

pretty much the same:
postfix instead of procmail, unpack it, run from terminal

```
gedit /home/username/.getlive/getlive.config
```

set it like this

UserName = your user before @
Password = your pass
Domain = hotmail.com 
Downloaded = /home/USERNAME/.getlive/downloaded 
Processor = /usr/sbin/sendmail -i yourubuntuusername
MarkRead = Yes
Delete = No

save it.
run from terminal
```
$ cd home/yourusername/.getlive
$  ./GetLive.pl --config-file getlive.config

```

same thing should happen and mails should be saved in /var/mail in the file with your user name.

i don't know in which way you wanna use getlive, but i'm trying to get my mail into evolution, and i can't get it right, even following the steps in the french tutorial! if anybody knew how to do it, please help!

hope this was useful! good luck

---

### Post by Ripfox on 2008-02-02
That's what i'm talkin' bout! Thanks man.

---

### Post by Ripfox on 2008-02-02
By the way, I don't use Evolution but the "webmail" extensions for Thunderbird work perfectly.

---

### Post by unclesam.xu on 2008-03-07
> **ripfox said:**
> That's what i'm talkin' bout! Thanks man.

Can you tell me how do you set it up with mail notification 5.0, I am facing same problem

thanks

---

