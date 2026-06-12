---
title: "How to work with bin files and install Synology Assistant"
date: 2013-10-11
forum: General Help
---

### Post by paullangdon678-1 on 2013-10-11
Hi,
I have two questions:
1) Can you open a bin file by double clicking on it or any other method outside the terminal? I have seen guidance says you can but if I double clik Ubuntu asks what programme I want to use?
2) When I do run in terminal for the bin file to install Synology Assistant I get:
psas@psas-BEUbuntu:~/Source/SynologyAssistant$ ./SynologyAssistant.bin
./SynologyAssistant.bin: error while loading shared libraries:  libqwt.so.5: cannot open shared object file: No such file or directory
Grateful for advice please.
Many thanks.

---

### Post by tgalati4 on 2013-10-11
Linux has two security precautions:

1.  Binary files must be marked as executable before they can be run:

```
sudo chmod +x SynologyAssistant.bin
```

2.  The file must be run with correct path designation:

```
sudo ./SynologyAssistant.bin
```

The dot is important because it prevents arbitrary execution of programs in the current directory--that is why you have to provide the dot.

Do you have the libqwt.so.5?  Perhaps it is looking for a Qt (graphics toolkit) library?

```
apt-cache search libqwt
```

You need to make sure you have all of the libraries (otherwise know as *dependencies*)  installed before you try to install the software.

The reason the file manager asks what application to open it is because it doesn't know how to handle a *.bin file.  You would normally run it from the terminal anyway so you can see any errors that pop up.

Installing this way is for advanced users, normally you would install through the software center or synaptic.

---

### Post by paullangdon678-1 on 2013-10-12
Thanks for the advice. I am fine with the command line instructions and can get the programme to execute if not successfully.

The specific library libqwt.so.5 is contained in the Linux download for Synology Assistant. In a folder named Libraries oddly enough. So taking the error message literally it is as if the programme cannot find it's own library.
I have asked synology support themselves about this and await their response.

I asked about the double click or opening of the bin file as I have seen guidance on the web giving this as a method for running bin file and posters have said it works. I cannot see how.

When you say installing in this way is for advance users are you referring to the terminal method? 
And is it possible to run a downloaded application through the software centre or synaptic and,if so, how?

That was interesting about the dot - so it is a 'security' measure aimed at making it harder to run programmes in error.

Thanks for your response really good. I am trying to fill in the gaps in my knowledge/understanding.

---

### Post by hodad on 2013-10-14
I have to admit that I'm a bit dense, but I've been trying to install SynologyAssistant on and off for an entire year. I can find all sorts of listings on how to help, but all of it is incomplete/doesn't work.   I tried again using your guidance above, and got to the same sticking point, i.e., SynologyAssistant wont run because it cant find the library libqwt.so.5 in it's own subdirectory.  Seems like their ought to be some kind of "path" command we can use to get it to recognize libqwt.so.5.  I really need to get this working, because I can't backup my drive...

---

### Post by paullangdon678-1 on 2013-10-16
Hodad,
Thanks I will let you know how I get on with Synology Support. It seems this is not one the forum can help with.
Although perhaps someone can fill in the gaps is my understanding above.

---

### Post by paullangdon678-1 on 2013-10-18
I asked about the double click or opening of the bin file as I have seen  guidance on the web giving this as a method for running bin file and  posters have said it works. I cannot see how.

And is it possible to run a downloaded application through the software centre or synaptic and,if so, how?

In answer to the above (poorly expressed question):

For advice on how to run bin and sh files:
[http://askubuntu.com/questions/121699/how-to-run-a-bin-file-without-using-terminal](http://askubuntu.com/questions/121699/how-to-run-a-bin-file-without-using-terminal)
[http://askubuntu.com/questions/122428/how-to-run-sh-file](http://askubuntu.com/questions/122428/how-to-run-sh-file)

---

### Post by hodad on 2013-10-22
Sorry for delay, but I got it (mostly) working after using instructions at :

[http://ubuntuforums.org/showthread.php?t=2180827](http://ubuntuforums.org/showthread.php?t=2180827)

Now Synology Assistant comes up, but can't find the Synology DS-112 (tried thru router, and directly through the ethernet port to each other). There's a message "Qstring argument missing" that is probably the cause...

See screenshot

---

### Post by hodad on 2013-10-28
Still no luck running Synology Assistant.  It comes up , but cant find the NAS.
Here's the full error message from when S.A. starts: 

QString::arg: Argument missing: Please make sure: 
1. Synology Assistant is not blocked by the firewall of your computer OS or anti-virus applications. 
2. Synology Server and your computer are both connected to the network. 
3. You have switched on the power of Synology Server., Synology Server
^C

---

### Post by hodad on 2013-10-28
The DS112 works fine on my windows pc, and I can ping it on the network from my linux box, so it's there, but not accessible (from the Linux box). I have the latest ver of DSM, but it won't find it under linux.

---

### Post by hodad on 2013-10-31
Success!  The last piece of the puzzle was Firestarter, which I thought was disabled, but was running in the background.  I guess you have to disable firestarter when you want to do backups, and then restart it afterwards.  I have a question in w Synology to see whether there's a better way.

---

### Post by paullangdon678-1 on 2013-12-01
Cool I was just coming back here to say I am still waiting on support. I have been asked to install teamviewer but this fails due to a dependency issue so I am getting nowhere.
I will take a look at the above and see if I can get going. Many thanks.

---

### Post by paullangdon678-1 on 2013-12-11
For completeness sake.I have it working no idea why.
 It just worked this morning.

---

