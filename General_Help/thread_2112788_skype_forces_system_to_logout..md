---
title: "skype forces system to logout."
date: 2013-02-05
forum: General Help
---

### Post by Joao Lacerda on 2013-02-05
need help on this.
When I start Skype the system Ubuntu 12.10 automatically logout,
Can someone help on this?

the same happens with ubuntu one sync. when connect it also 
logout (USER) 

Thanks in advance.

---

### Post by Thee on 2013-02-05
Well thats weird. What happens when you run Skype from terminal?

---

### Post by Joao Lacerda on 2013-02-05
starting from terminal do the same thing, logout the user.

I have used it without problem yesterday and I do not have made any changes on the system, I really do not know how that is possible.
thank you for your time.

---

### Post by Thee on 2013-02-05
Does it display any error messages in the terminal?
Are you using the latest version of skype?

edit: does it crash when making normal calls or when using webcam? Or it logs you out as soon as you login to skype?

---

### Post by Joao Lacerda on 2013-02-06
when I start skype the system (USER) logout immediately,

What I do receive is a message, "crash report can not generate the reporter for a program that is not installed". 

I have reinstalled it and it still not working.

---

### Post by ankur1993 on 2013-02-06
go--->software center --->type search option---->Client for Skype VOIP and instant messaging service(skype)-------->click install option
:popcorn:

---

### Post by Joao Lacerda on 2013-02-06
the only [COLOR="Black"]**Voip Client**[/COLOR] that I have found on Ubuntu software center is this

Is that that you mean?

The problem is worse than I thought, the same happens with ubuntu one.

Can someone point me to some direction on this?

thank you.

---

### Post by rnerwein on 2013-02-06
> **Joao Lacerda said:**
> starting from terminal do the same thing, logout the user.

I have used it without problem yesterday and I do not have made any changes on the system, I really do not know how that is possible.
thank you for your time.
hi
sounds for me that in your login shell is on any point "set -e" is executed. this means that if anywhere an error occurs the whole procedure is cancelled.
you can try in at terminal: set -e and then type bla -> because this is an error the terminal will be closed.
cheers

---

### Post by scbingham on 2013-02-06
I too am having the exact same problem & also can't send error report as I get the same message.

Re installing OS Ubuntu 12.04.1 64bit & Skype 4.1.0.20 makes no difference.

I'm at a loss.

---

### Post by rnerwein on 2013-02-06
> **scbingham said:**
> I too am having the exact same problem & also can't send error report as I get the same message.

Re installing OS Ubuntu 12.04.1 64bit & Skype 4.1.0.20 makes no difference.

I'm at a loss.
hi
are you guys running skype as an autostart program ??
if yes - remove it from the autostart and run it from a terminal.
cheers

---

### Post by scbingham on 2013-02-06
rnerwein, not to my knowledge. How would I check?

If I check for any skype processes with ps, there are none, so I guess not.

At the moment I can start skype from terminal or from the Unity task bar & I get my list of contacts. Unfortunately no one is online so I'm unable to try to invoke a conversation & hence create a crash.

---

### Post by sabersong on 2013-02-06
Seems I'm having this problem as well. It worked yesterday. Today it crashes.

The crash happens when I use video calling, either answering or initiating a call. My most recent attempt while Skype was on autostart connected for a few seconds, but the incoming video was badly pixelated, and then the I got logged out again.

I made one attempt with Skype manually started, and that didn't log me out, but the video was badly pixelated, and almost unrecognizable.

HP 2000 DX416 Laptop
2x AMD E-300 APU
Ubuntu 12.10 with KDE
AMD Radeon 6310 with Proprietary Drivers & Catalyst
Broadcom 4313 Wireless Adapter

---

### Post by Joao Lacerda on 2013-02-06
first thank you all for your time.
For me it make no difference if I start it from terminal or from dash lens, what is strange that it have worked for many days without problem, I have re-installed it and the system do not gave any message that the program was already installed on the system.

I do not even know where to start searching for solution, on this.

Friends, really many thanks. maybe we will find the reason why it happens.

---

### Post by Thee on 2013-02-06
Try renaming .Skype directory and see what happens. Its where all the Skype settings are stored, maybe something got messed up and hopefully it fixes itself when its newly created. If it doesn't work, just rename it back.

```

mv .Skype .Skype-backup

```

Or manually rename it with a file manager.

---

### Post by Joao Lacerda on 2013-02-07
Friend, 
I do not use the auto start, and I also tried to start it from terminal, but it does not help the problem.

---

### Post by Joao Lacerda on 2013-02-09
Friends,

That has solved the problem for me,

sudo apt-get autoremove --purge skype-bin:i386

and installing this one:

skype-ubuntu-precise_4.1.0.20-1_amd64.deb

Thank you for those who have interact with this problem,

---

### Post by scbingham on 2013-02-09
Thanks for putting that up, installing that version seems to have worked for me too :-)

---

