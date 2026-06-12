---
title: "Evolution mail"
date: 2008-07-09
forum: General Help
---

### Post by no-1-uno on 2008-07-09
Well I did it last nite I just pulled out the Ubuntu disc and said bye bye windblows. That said I can get on the net (obviously) I can receive mail but cannot send it. I have set it up the same way I did with outlook but no outgoing mail.

I am still trying to find my way around and need to try and load some of the programs which I used to use with windblows. I also looked for a firewall but really did know which one or how to install so a point in that direction would be appreciated also.

So new I sill have that new car smell

no-1-uno

---

### Post by pytheas22 on 2008-07-09
What kind of mail service do you have?  If it's something popular (gmail, Yahoo...) there are plenty of guides online to help you configure it for Evolution.  If it's a corporate or university mail account, you're more on your own.  But if you play around with the settings under the "Sending Email" tab in preferences, you might be able to figure it out.  Or better yet, ask your IT people what should go in each field...you need to know the address of their SMTP server, whether it requires authentication, if you need a secure connection and so on.  Also if they publish instructions for configuring Thunderbird (which you could use as an alternative to Evolution, by the way) or Outlook, those can give you a clue as to what you need to fill in in Evolution.

Linux has its own built-in firewall called iptables, but it comes turned off by default.  But you can install Firestarter, a nice front end for configuring iptables and turn your firewall on:
```

sudo apt-get install firestarter
```

If there's any other Windows software that you need, let us know what it is; in almost all cases there's either a Linux equivalent or a way to make it run on Linux.

---

### Post by no-1-uno on 2008-07-09
My mail server is a pop3/smtp from my server service. Douservers.

I will try and find the firewall program and turn it on if not maybe the Firestarter.

Is Thunderbird more like Outlook? I have used Outlook for many years and it is one of the few things I liked from MS.

Sorry for the questions, I have tried to look around the forum and find some answers but none so far. I did download Ubuntu Bible and I think Ubuntu or Linux for dummies.

Thanks for the help.

in my server docs it says for mac use challenge response md5 don't know if that helps or not. They have nothing on Linux.

---

### Post by pytheas22 on 2008-07-10
> My mail server is a pop3/smtp from my server service. Douservers.

Do they have instructions for configuring it for Thunderbird or Outlook.  If so, if you provide a link to them I'll take a look and try to figure out what you need to put in Evolution.

> I will try and find the firewall program and turn it on if not maybe the Firestarter.

Just to clarify: there's only one firewall program, iptables, and it comes built into Linux.  Firestarter is basically just an interface for turning it on and configuring it.  You can of course configure iptables from the command line if you want, but I wouldn't recommend it for beginners.  If you just want to block certain sites and services, Firestarter will work fine.
> 
Is Thunderbird more like Outlook? I have used Outlook for many years and it is one of the few things I liked from MS.

I've never really used Outlook so I don't know, but Thunderbird is a very popular multi-platform mail client made by Mozilla, the same people behind Firefox.  If all you need is email, Thunderbird will be great.  I don't think it includes the calendar features of Outlook, however; if you want those, you need to use Evolution.  But the advantage of Thunderbird is that because it's used by lots of people on Windows on OS X, it has better support by vendors than Evolution, which really only works on Linux (you can make it run on Windows, but it won't be pretty).
> 
in my server docs it says for mac use challenge response md5 don't know if that helps or not. They have nothing on Linux. 

I don't know what that means...maybe something about checksums?

---

### Post by Execute_Method on 2008-07-10
> 
Is Thunderbird more like Outlook? I have used Outlook for many years and it is one of the few things I liked from MS.


I love Thunderbird, I have been using it with my pop3/smtp accounts for about 8yrs, and I've only been running Ubuntu (no microshaft anything on my HD) for 4 months, although I'm not that new to linux.

Thunderbird has greater capability than outlook express and almost all the capabilities of outlook, but doesn't have Imap4 support (microsoft exchange), which evolution does.

However, since you are using a pop account exchange support doesn't matter. I say go for it! :KS

If you need any more help setting it up let us know :)

BTW from what I've seen you can use the setup instructions for outlook express to configure thunderbird. (for the most part)

---

### Post by Execute_Method on 2008-07-10
As far as the firewall goes, maybe a software firewall isn't really necessary. Are you using a router w/ built-in firewall? Even my $40 router will pass security tests for intrusion.

Do you need it for internal protection (ie. disallowing specific websites).

As well, linux is not prone to the same stuff windows is (ie. spyware, malware, nthmillion viruses, etc.)

If you want to check if you are "stealth" on the net or not try this site. It checks for ports that are open outside.

[http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2)

---

### Post by no-1-uno on 2008-07-10
I have been using the regular outlook for my e-mail for years with this server, not outlook express.

I have had to set up the mail several times and have had to set it up for others so that part is not the problem.

The in bound and outbound mail server is mail.supremecluster.com and it requires authentication.

I am receiving mail just fine. 

I had a problem once with having to change the access port do to an access provider (AT&T) problem. I do not see the ability to change ports in the settings or would have tried this already.

Thanks and I really appreciate your help with this as I so not want to ever go back to microlimp. 

There is one program I use from Black obelisk for writing a book that may be windows only.  So far in searching the Linux programs I have not found any thing comparable. I would rather change to a Linux program if possible but I have been reading up a little about Wine for running windows programs.

---

### Post by pytheas22 on 2008-07-11
I should have asked for this before, but maybe if you post a screenshot of your sending mail configuration screen (I'll post mine as an example of what I'm referring to), it would give a better idea of what you might need to change to get it to work.  Also, do you get any error messages when you try to send mail, and if so what exactly do they say?

> There is one program I use from Black obelisk for writing a book that may be windows only. So far in searching the Linux programs I have not found any thing comparable. I would rather change to a Linux program if possible but I have been reading up a little about Wine for running windows programs.

What is the name of the program and what exactly does it do?  Would OpenOffice work?  It has some advanced features for organizing and formatting long documents like book manuscripts; you just need to learn to use them.  I've written multi-chapter, 100+ page documents in it and it and have never been disappointed.

Otherwise, wine is pretty good these days at running most Windows software.  And you can also run Windows inside a virtual machine if necessary for those programs that you just can't get around--it's sad to use Windows even in a virtualized environment, but I think a lot of us end up doing it from time to time.

---

### Post by no-1-uno on 2008-07-11
I am not getting any error messages just a timed out one after a long time of it trying to send the message.

I have attached the screenshot.

Is there a way to change which port evo is using?

The program is Liquid story binder XE and you can download a 30 day trial copy at     [http://www.blackobelisksoftware.com/download.html]("http://www.blackobelisksoftware.com/download.html") it says it is for windose and has no dnl for Linux.

I has all kinds of items to help authors, timelines, notes, dossiers, story boards etc and I have about 25 chapters finished on a new Sci-fi I am working on.

I do not know anything about virtualized environments and so far  have not been able to open any of my program rar files anyway. Dumb question will winzip work in Ubuntu?

Thanks again for all your help.

Also what do you mean by bump the thread?

I suffer from thread newbiness.

---

### Post by pytheas22 on 2008-07-11
Thanks for the picture, but actually could you post another of the "Sending Email" tab of the config window, please?  That's the one that's really important to see.

> 
Is there a way to change which port evo is using?

From this [thread]("http://ubuntuforums.org/showthread.php?t=127852"), it sounds like you just append the port number you want to use to the address of your SMTP server.  See if that helps.

> so far have not been able to open any of my program rar files anyway. Dumb question will winzip work in Ubuntu?

You don't need winzip; Ubuntu comes with an archive manager that can deal with virtually every kind of archive file except .rar.  I think it doesn't support .rar because it's not a free/open-source format and Ubuntu doesn't like that.  However, you can easily install a nice GUI to open .rar files:
```

sudo apt-get install unrar rar xarchiver
```

Then under Applications>Accessories you will have a program called Xarchiver that can open .rar files (or you can do it from the command-line with the program "unrar").
> 
I do not know anything about virtualized environments

It's pretty easy to install Windows inside a virtual machine on Ubuntu.  I use VirtualBox--it's in the repositories--but you can also use VMware, qemu or xen (not sure how stable xen is right now; the last I checked it was still being developed).  All of them are available for no cost.  Once you install them, you basically just put your Windows install CD in the drive, tell the virtual machine to boot to it and install Windows as if it were a real computer.  Virtualization wastes a lot of resources, but since Windows XP is seven years old, it will fly in a virtual machine on a modern computer.
> 
Also what do you mean by bump the thread?

I just mean to make a new post in the thread so that it comes back to the top of my subscribed list.  I've been realizing lately that sometimes I lose track of threads and forget to respond.

---

### Post by pytheas22 on 2008-07-11
Also I just downloaded the demo of that liquid story program and it seems to install and run great in wine.  I didn't try out all of the features, and of course the full version won't necessarily work as well as the demo, but it looks good for you.  So I'd recommend installing wine:
```

sudo apt-get install wine
```

and giving your program a try in it.

---

### Post by no-1-uno on 2008-07-11
I thought I was attaching the sending tab sorry.

here it is this time.

I far as the port issue I do not see an option to change it or even tell what it is.

I have tried all of the different configuration possibilities on the sending mail page and still it just sets there for ever doing nothing. No movement on the progress bar or anything.

I think I found the unrar and installed it but I do not see it in the applications. DO you have to restart or anything to finish the installs?


I think rather than do th virtual think I will just make a windows machine if I cannot get some of the progs I use to work. I really don't want to as I do most everything on my laptop a Dell Latitude D610.

The Liquid Story binder is the full version it just stops after 30 days of actual use.

Is ther a anti virus program like Avast? I dnl progs and things all the time and do not want infect my machine. The Avast pro works great in windows as it even scans the dnls before you even open them.

I really want to say a BIG THANK YOU for all of you time and help. You are sure making the learning curve time a whole lot quicker and easier.

Thanks again

Todd

---

### Post by no-1-uno on 2008-07-11
Oh I forgot I even tried the search for supported types and it timed out.

If you want I can set you up a test email account so you can try it out.

It is real easy since I have my own server.

---

### Post by Salomonis on 2008-07-12
I'm having trouble getting evolution to send mail using smtp for gmail.  I've looked at many solutions online, all have the same results and that is it times out.  pop works in less than a second.  I turned Deluge off to make sure it wasn't a bandwidth problem which it wasn't.  Any help would be great.

---

### Post by Salomonis on 2008-07-12
Funny how I always find the solution after I post the problem.
Pop was on SSL while smtp wasn't.  both should be SSL

---

### Post by no-1-uno on 2008-07-12
Mine does not use a ssl on either.

Thanks anyways glad your works

---

### Post by dcstar on 2008-07-12
> **no-1-uno said:**
> Mine does not use a ssl on either.

Thanks anyways glad your works

Open a terminal:

```
telnet smtp-server-name 25
```

If you get a response, then the network connection is ok and the app is probably the problem, if you don't then something is blocking the traffic.

---

### Post by no-1-uno on 2008-07-12
Thanks for the point I tried it and get this response

```
tojo@ubuntu:~$ telnet smtp-server-name 25
telnet: could not resolve smtp-server-name/25: Name or service not known
tojo@ubuntu:~$ telnet smtp-server-mail.supremecluster.com 25
telnet: could not resolve smtp-server-mail.supremecluster.com/25: Name or service not known
```

I tried it with the name of my server also, did not know if it made any difference.

---

### Post by pytheas22 on 2008-07-12
> I far as the port issue I do not see an option to change it or even tell what it is.

To change the port being used to send mail, you have to append it to the mail server's address.  In other words, if you want to use port 5000 to send mail, then in the box labelled "Server," enter: ```
mail.supremecluster.com:5000
```

See if that helps.  You may need to restart Evolution for the change to take effect.

> 
I think I found the unrar and installed it but I do not see it in the applications. DO you have to restart or anything to finish the installs?

You don't need to restart.  Look under the Applications>Applications menu for "Xarchiver," or open a terminal and type:
```

xarchiver
```

If the program doesn't start, then try installing it again:
```

sudo apt-get install xarchiver
``` 

> Is ther a anti virus program like Avast? I dnl progs and things all the time and do not want infect my machine. The Avast pro works great in windows as it even scans the dnls before you even open them.


You don't need antivirus software on Linux, as there are virtually no exploits against it (one of the benefits of having a tiny market share is that no one bothers to attack you).  If you want you can install Clam AntiVirus to scan for malware, but really that's designed for Linux servers that are serving Windows machines--it scans for Windows viruses and removes them so that they don't get passed on to the Windows machines.  A Windows virus could reside on a Linux machine, but it can't do anything to it.

---

### Post by pytheas22 on 2008-07-12
> If you want I can set you up a test email account so you can try it out.


If you want to do that, I'll see if I can figure it out.  Also, let me know which port you think you need to use to send mail.

---

### Post by no-1-uno on 2008-07-12
I found out what it was. It was the port issue.

I had to enter    mail.supremecluster.com:2525

Works just fine now thanks for all of the help on that one.




Question: I did the synaptic thing for the unrar and I still cannot open a rar file. I also do not see it in the applications or anywhere else. THis is the biggie number 2 as almost all of my backups and programs are in rar form. (rare form LOL) I tried restarting the machine and that made no difference is there something else I should be doing?

Thanks

---

### Post by pytheas22 on 2008-07-13
Just type at a command line:

sudo apt-get install unrar xarchiver rar

Then unless you get error messages, you should have a program called Xarchiver under Applications>Accessories.  Is it really not there?  The only reason that it would not be installing is if you don't have all of the repositories enabled; to make sure they are all enabled, go to System>Administration>Software Sources and check the boxes under the "Ubuntu Software" tab to enable all repositories.

There's also a command-line utility for unextracting .rar files that should be installed by the commands above.  If you type:

```
unrar
```

in a terminal, what does it say?

---

### Post by dcstar on 2008-07-13
> **no-1-uno said:**
> Thanks for the point I tried it and get this response

```
tojo@ubuntu:~$ telnet smtp-server-name 25
telnet: could not resolve smtp-server-name/25: Name or service not known
tojo@ubuntu:~$ telnet smtp-server-mail.supremecluster.com 25
telnet: could not resolve smtp-server-mail.supremecluster.com/25: Name or service not known
```

I tried it with the name of my server also, did not know if it made any difference.

"smtp-server-name" is supposed to be replaced by the **exact** name **you** are using for your SMTP server. Post those results.

---

### Post by no-1-uno on 2008-07-13
> **pytheas22 said:**
> Just type at a command line:

sudo apt-get install unrar xarchiver rar

Then unless you get error messages, you should have a program called Xarchiver under Applications>Accessories.  Is it really not there?  The only reason that it would not be installing is if you don't have all of the repositories enabled; to make sure they are all enabled, go to System>Administration>Software Sources and check the boxes under the "Ubuntu Software" tab to enable all repositories.

There's also a command-line utility for unextracting .rar files that should be installed by the commands above.  If you type:

```
unrar
```

in a terminal, what does it say?


The software sources were not checked I just thought I was installing. Once again Mucho thanks

---

