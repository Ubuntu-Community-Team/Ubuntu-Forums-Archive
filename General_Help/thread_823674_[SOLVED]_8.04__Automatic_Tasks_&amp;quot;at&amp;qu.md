---
title: "[SOLVED] 8.04  Automatic Tasks &amp;quot;at&amp;quot; ??"
date: 2008-06-09
forum: General Help
---

### Post by thelugnut on 2008-06-09
I am having much difficulty with 'at'.
I can open the terminal and type in the at command all right.
But I never see the command I entered, executed.
I also can not seem to get atrm x, to work.
atq does show the queue list.

The man for 'at' seems to be quite outdated. There are some options listed that are not recognized by the terminal.

I googled, trying to find some information but nothing popped up of any interest.

I did a search on this site and again, nothing of interest.

Is this program obsolete? Am I playing with a long dead toy?:confused:

Cheers and beers!

---

### Post by ibuclaw on 2008-06-09
What sort of commands are you trying to run?

The problem that most people have with **cron** and **at** is the fact that they forget that these services are running in the background, and therefore schedules to open up program X won't executed as expected.

To run applications on the Xserver, use "**DISPLAY=:0.0**"
ie:
```
DISPLAY=:0.0 gcalctool
```

A way of showing whether or not it "**works**" would be to run this:
```

at 1830
touch /tmp/test.at
echo "Hello World" >> /tmp/test.at

```
To end the input of scheduled commands, press "**Ctrl+D**".

Then at 6:30pm, a new file will be created inside the /tmp folder with the message "Hello World".


Another way you can try it is by just echoing words.
```

at 1830
echo "test test"
echo "All echoed output gets sent to your mailbox"

```
Then type in **mail** after 6:30pm and a new letter will be in your inbox.
[PHP]
$ mail
"/var/mail/iain": 1 message 1 new
>N   1 Iain Buc&#322;aw       Mon Jun  9 18:24  15/514   Output from your job       1
& 
[/PHP]

Regards
Iain

---

### Post by geirha on 2008-06-09
Never used at before, but it seems to be working for me. Are you maybe trying to run a graphical application? If so, that won't work unless you set the DISPLAY variable to a running xserver. If you only have one user that logs in graphically on your computer, then it will probably work just fine to use DISPLAY=:0.0. I.e. 
```
$ at now +1min << EOF
> DISPLAY=:0.0 xeyes
> EOF
```

Also, if the at-command fails to run, it will send you a mail using a local mailsystem. I suggest you install the [mailx](apt:mailx) package, then run "mail" in a terminal to read those mails.

EDIT: tinivole beat me to it!

---

### Post by ibuclaw on 2008-06-09
lol.

Ah, but you see. I wasn't aware of that "DISPLAY=:0.0" command either.

So I guess we both win ;)

Here are some more tasks you can try out in the safety of your home.

**Send 5 Clicks to your speakers:**
```

at 1900
for i in 1 2 3 4 5; do echo >/dev/dsp1; done
<Ctrl+D>

```
**Update your "locate" database:**
```

at 1900
DISPLAY=:0.0 gksu updatedb
<Ctrl+D>

```
**You're own alarm clock**
```

at 1900
mplayer "/path/to/file.mp3"
<Ctrl+D>

```
Regards
Iain

---

### Post by thelugnut on 2008-06-09
Hey, we all be winners. I didn't know any of that stuff. 

Can't thank you all enough for the answers.

I'm trying to cycle through some of the available things in Ubuntu and snagged on this one. No longer snagged though.

Again, thanks to all.

---

