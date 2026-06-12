---
title: "aMsn closing at startup"
date: 2008-06-09
forum: General Help
---

### Post by scope on 2008-06-09
Hi, I'm having a big problem with amsn since this morning (yesterday it was working ok). 

Whenever I open it and click on sign in or language, the window closes and the icon disappears from the tray. Wish8.5 also disappears from the system monitor.

If I execute it from terminal I just get this message:
Fallo de segmentación ("Segment fault" in english maybe?)

Any help?

btw I'm using hardy

Thanks

---

### Post by y-lee on 2008-06-09
How did you install aMSN?

Segment fault is a serious error so my advise would to try to uninstall it and then reinstall it.

---

### Post by scope on 2008-06-09
i installed it through synaptic but anyways, I have:
Uninstalled it partially (keeping configuration files), re-installed it from synaptic. 
Nothing.
Uninstalled it again completely (deleting configuration files) and reinstalled from synaptic.
Nothing.
Uninstalled it from add/remove programs and reinstalled it.
Nothing.

I read somewhere that sometimes this is caused by a faulty font or codification. I change the codification to UTF-8 and the font a couple of times and nothing. Also I tried a command to refresh the fonts or something like that (fcache -v... I dont remember). And still no results.

I'm trying "emesene" and i'm liking it but It would be too bad to loose some of the amsn features forever :(

---

### Post by y-lee on 2008-06-09
Hmmm

My advice would be to uninsatll and downlaod the source code and compile it by hand. If it still gives the same error do the below: 

> **Q: How do I capture bug report information from a segmentation fault? (LINUX)**

**A:**Make sure amsn was compiled with debugging symbols, if you installed it using a binary package, you should probably download from source and recompile it. To enable debugging symbols, configure it with :

```
./configure --enable-debug
```

If you're unable to compile it, then you can still send us information without the debugging symbols.

Once it is compiled/installed, go to the directory where you have installed aMSN (example: /usr/share/amsn or /home/yourusername/amsn-0.95/) type:


```
$ gdb --args wish amsn
(gdb) run
then when it segfaults
type bt
bt full
```


You will then receive the bug report information. Please send this information to: [email]amsn-devel@lists.sourceforge.net[/email]

From: [aMSN web site]("http://amsn.sourceforge.net/wiki/tiki-index.php?page=Frequently+Asked+Questions")




If you can do this you might also post the debug information here. May be some messed up library you have installed.

---

### Post by scope on 2008-06-09
thanks for the reply. I compiled it from source with ./configure --enable-debug and it works now almost correctly.
And I say almost because as soon as I log in I get a bug window which asks me to send the report. The bug seems to be related with TK. Before that amsn asked me to download the tls package, which I have downloaded from synaptic.

I ran amsn with the gdb as you told me but if I type bt when the bug window appears, nothing happens. And after closing amsn the terminal says that the program exited normally :S

So, it works now but everytime i start it I get the tk message.

Again, thanks for your interest

---

### Post by scope on 2008-06-09
thanks for the reply. I compiled it from source with ./configure --enable-debug and it works now almost correctly.
And I say almost because as soon as I log in I get a bug window which asks me to send the report. The bug seems to be related with TK. Before that amsn asked me to download the tls package, which I have downloaded from synaptic.

I ran amsn with the gdb as you told me but if I type bt when the bug window appears, nothing happens. And after closing amsn the terminal says that the program exited normally :S

So, it works now but everytime i start it I get the tk message.

Again, thanks for your interest

---

### Post by y-lee on 2008-06-09
Hmm interesting

Try going to the directory  you compiled aMSN from and uninstall the program by running

```
sudo make uninstall
```

Now recompile it without the -enable-debug thing. That should get rid of the bug window, :lolflag:

Also e-mail the aMSN team and tell them of your problem and send them a link to this thread. Might help them fix the problem or figure out the issue.

Just be aware that by compiling from source you will have to manually update the program yourself. A minor problem tho if this makes it work.

---

### Post by scope on 2008-06-09
Okay I will do it. Thanks! I think I'll use the manually compiled one until a new update is available on the repositories.

---

