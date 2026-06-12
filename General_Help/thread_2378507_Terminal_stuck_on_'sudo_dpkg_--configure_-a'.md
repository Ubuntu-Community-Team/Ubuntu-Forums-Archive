---
title: "Terminal stuck on 'sudo dpkg --configure -a'"
date: 2017-11-23
forum: General Help
---

### Post by firefightertcfd on 2017-11-23
Hello,

I am very sorry please be patient as I am somewhat new to linux but am loving it so far. However, I have run into a snag and can't seem to find a resolution for it anywhere online.

Now when trying to install any software using 'sudo apt-get'... doesn't particularly matter what it is it tells me that it cannot be installed and that I need to manually run 'sudo dpkg --configure -a' in order to fix the issue. However when I do ht process gets stuck on setting up colplot. I have attached a screenshot of this.

So far I have tried resolving the issue by clearing out the /var/lib/dpkg/updates folder and running the command again as suggested on another forum post but that did not help as the 'sudo dpkg --configure -a' command just tries to set up colplot all over again.

I have also tied 'sudo apt-get -f' which also did not help.

If there is anything that I can do to help you better diagnose the problem please let me know. Like I said I am fairly new and am still learning. I come from Windows so this is all new to me.

---

### Post by firefightertcfd on 2017-11-23
Oh I am sorry by the way I am running Ubuntu Budgie on 16.04

---

### Post by firefightertcfd on 2017-11-23
Here is a screenshot of the message when I try to run 'apt-get' commands.

---

### Post by firefightertcfd on 2017-11-23
Nevermind, I managers to solve my problem. :-) I'm learning!!!! I booted the system into recovery mode and ran [COLOR=#111111][FONT=Consolas]sudo dpkg --purge --force-all colplot and it cleared up the issue. All is well.
[/FONT][/COLOR]

---

### Post by Bashing-om on 2017-11-23
firefightertcfd; Welcome to the forum .

Let's see what we can work out - to isolate the problem .
Post back - Between code Tags -
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
that maintains formatting and allows copy/paste operations for information exchange

 the outputs Of terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt -f install
dpkg -l colplot

```

[INDENT][INDENT]a tale gets told
[/INDENT][/INDENT]

---

### Post by firefightertcfd on 2017-11-23
I appreciate you writing to help. I solved my own problem and all seems to be good now, I already posted above what I did to solve it.. Again thank you!

---

### Post by Bashing-om on 2017-11-23
firefightertcfd; Great .

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]you do good work[/INDENT][/INDENT]

---

