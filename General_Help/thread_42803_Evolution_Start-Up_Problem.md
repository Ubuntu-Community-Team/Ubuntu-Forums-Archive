---
title: "Evolution Start-Up Problem"
date: 2005-06-19
forum: General Help
---

### Post by xalphas on 2005-06-19
Hi everybody, 

I've made a fresh install of Hoary. I clicked the evolution icon and just follow the steps to set my account up. At the end i finished my account setup and no window comes up. 

When i look at my running processes i can see that evolution is running and below it "netstat" looks as zombie. 

And when i call the program from terminal i get this output and it stays like this with no window popup. 

```
xalphas@ubuntu:~$ evolution
es menu class init
adding hook target 'source'
``` 

I've been searching for this issue for 2 weeks around google and evolution sites. Finally i found that it can be conflicted with evolution-exchange. i apt-get remove evolution-exchange with dependency ubuntu-desktop. Then tried to run evolution again it opens but freezes. 

I already deleted ./evolution folder in my home directory but again no success. So i have no data as mail or organize in evolution now. I am open to any fix this problem. I just want to use it but by default having problems with it. 

Any help would be good. 

Thx.

---

### Post by blind0wl on 2005-06-20
Might be worth opening up a couple more repositories and getting a later version of it...or if you have them all ready, maybe go back to a stable version.  What version is it currently?

---

### Post by xalphas on 2005-06-20
Default Version comes with stable Hoary 5.04 Cd. Evolution 2.2.

I think of using Breezy repos to upgrade. Is it worth or safe to do this? or Is there a fix for my problem? 

Thx.

---

### Post by blind0wl on 2005-06-20
Can you try opening evolution offline?  Have a poke around evolution --help, there should be an --offline option.  Ive heard this help other users who couldnt open evolution all the way.  Otherwise try just opening the calendar portion of it with ```
evolution -c calendar
``` and see if that makes a difference.

It might be worth looking through [http://lists.ximian.com/archives/public/evolution/](http://lists.ximian.com/archives/public/evolution/) 
for a solution also.

Regards

Blindy

---

### Post by xalphas on 2005-06-20
Thx @Blindy

I am at work now. I will try your suggestions when i get home.

---

### Post by xalphas on 2005-06-20
When i type 

evolution -c calendar

it gives the same error like:
```

xalphas@ubuntu:~$ evolution
es menu class init
adding hook target 'source'
```

Any other solution?

---

### Post by blind0wl on 2005-06-20
Did you try the offline option?

```
evolution --offline
```

---

### Post by xalphas on 2005-06-21
it is the same. No change. Doesn't start up. This is the only thing that doesn't work in Hoary. Maybe i am lucky but i want to use it.

---

### Post by blind0wl on 2005-06-21
Another thing to try is to delete or backup your gconf evolution settings (id just delete them) in ~/.gconf/apps/evolution.  This will remove the evolution settings, where ~/.evolution is the data.

[I]"However, before messing around with any file in the GConf dir, be sure to close the GConf daemon, as it holds this data in memory.
'gconftool-2 --shutdown' is the command these days, not sure about your
version. See 'gconftool-2 --help' for available options."[/I]

[guenther](http://lists.ximian.com/archives/public/evolution/2005-June/043737.html)

Cheers

Blindy

---

### Post by xalphas on 2005-06-22
@Blindy thx for support. It was a good advice. When i deleted evolution folder with gconf disabled, Evolution Setup Wizard comes up. That's good. 

It reminds me after fresh install scene. Same process and i fill my details for mail setup. But when i come to end it gives the same error again. I don't know why this is like this. Especially after a fresh install. I search for this and look for answers. But especially nobody has this problem with evolution. 

Anyway again thx for help. Will have to search a little about this. 

Regards.

---

### Post by blind0wl on 2005-06-22
So its up and running?  Excellent...this is the point Id bury my head in the sand and hope it didnt do it again!   :grin: 

Cheers

Blindy

---

### Post by xalphas on 2005-06-23
> But when i come to end it gives the same error again 

No it is not buddy. Sorry.

---

### Post by ions on 2005-07-05
Did you find a fix for this xalphas?  

All of a sudden today Evolution has started with this nonsense!  This is not a new install.

```
$ evolution
es menu class init
lsmith@Linux:~ $

```

Same thing with evolution-2.2.  Only thing I've done is started using VNC.

---

### Post by ions on 2005-07-05
Oh, this could be related, I get this error on startup in an Error dialogue box:

```
The Application "evolution-alarm-notify" has quit unexpectedly.

You can inform the developers of what happened to help them fix it.  Or you can restart the application right now.

```

There's a Close button and a Inform Developers button.  No button to restart and of course I checked these possibilities:

```
lsmith@Linux:~ $ evolution-alarm-notify
 bash: evolution-alarm-notify: command not found
lsmith@Linux:~ $ sudo apt-get install evolution-alarm-notify
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package evolution-alarm-notify

```

---

### Post by ions on 2005-07-05
I have now removed evolution and re-installed it.  The es menu class init error remains.

---

### Post by ions on 2005-07-05
Anyone?

Losing an email app is kinda a critical problem for some....

---

### Post by ions on 2005-07-05
The only thing different between the last time I had Evolution working, just over 12 hours ago, is that I got VNC runnins as per this thread: [http://www.ubuntuforums.org/showthread.php?t=42941&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=42941&page=1&pp=10)

Could they be related?  I can't see how but....

---

### Post by ions on 2005-07-05
I submitted a bug: [https://bugzilla.ubuntu.com/show_bug.cgi?id=12432](https://bugzilla.ubuntu.com/show_bug.cgi?id=12432)

---

