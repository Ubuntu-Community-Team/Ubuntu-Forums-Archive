---
title: "General information needed"
date: 2004-11-15
forum: General Help
---

### Post by ITLogic() on 2004-11-15
Hello. I have posted a few questuins here so far and have been very happy with this community!

As I read other posts, FAQ's and HOW-TO's, things keep coming up that I don't understand. Being completely new to any distro of Linux, I am beginning to find myself lost in tid bits of information. My first question is, and this is probably pretty lame, what version of the Linux kernel does Ubuntu use?

I am getting the idea that no matter what disto you use, there are common comands generic to all distro's depending on the kernel being used. Is that correct?

If so, can someone recommend a book, or even better, a basic on-line tutorial of the common generic commands of the kernel? For instance, I read about using the reprobe command when installing new hardware. Is that a generic command, or is that specific to Ubuntu?  :roll: 

Thanks for any help in getting me started.  :wink:

---

### Post by TravisNewman on 2004-11-15
[QUOTE=ITLogic()]Hello. I have posted a few questuins here so far and have been very happy with this community!

As I read other posts, FAQ's and HOW-TO's, things keep coming up that I don't understand. Being completely new to any distro of Linux, I am beginning to find myself lost in tid bits of information. My first question is, and this is probably pretty lame, what version of the Linux kernel does Ubuntu use?

I am getting the idea that no matter what disto you use, there are common comands generic to all distro's depending on the kernel being used. Is that correct?

If so, can someone recommend a book, or even better, a basic on-line tutorial of the common generic commands of the kernel? For instance, I read about using the reprobe command when installing new hardware. Is that a generic command, or is that specific to Ubuntu?  :roll: 

Thanks for any help in getting me started.  :wink:[/QUOTE]
 I think the Warty kernel is 2.6.8.1

Regardless of the kernel, there are common commands generic to all distro's. Each new kernel that isn't just a bugfix release will enable more functionality, so new commands or new command line parameters for existing commands may be written.

As far as books go, I'd suggest the O'Reilly books. They have a wealth of information in them, and they're organized and written very well.

For online, I frequently use [www.google.com/linux](www.google.com/linux) to search for specific questions. The documentation on linux.org is pretty good for a generic intro that will be pretty much the same no matter what distro you're on: [http://www.linux.org/docs/index.html](http://www.linux.org/docs/index.html)

---

### Post by ITLogic() on 2004-11-15
Thanks, I'll check those out. I saw the reference to the O'Riely book, but I have used them before for somthing else and thought it was average. But, perhaps it was just the topic.

---

### Post by TravisNewman on 2004-11-15
[QUOTE=ITLogic()]Thanks, I'll check those out. I saw the reference to the O'Riely book, but I have used them before for somthing else and thought it was average. But, perhaps it was just the topic.[/QUOTE]
 There are hundreds of books on linux if the O'Reilly books don't impress you. Just go to your local bookstore and check out the Geek books. You should be able to find something that you think can tickle your fancy.

---

### Post by mortiferus on 2004-11-15
To find out what kernel you run, you kan use this command (in a terminal):
uname -r
When we are at it, try to run man uname. Then you see the manual for the command uname. If you read it you wil se that you can run for example 
uname -a
to show more information. To quit the manual just type q. Most terminal commands have a man page. 
The thing all linux distros have in common is the kernel, linux. And then they seperate eachother by what other software they include and how they set it all up. But almost all (if not all) distros come with a sertan "basic package" that is the same. F.eks ls to show files, mkdir to create dir, touch to create a emty file, cat to view and grep to extract sertan information from a text(and several others). (to my knowledge) Most of these tools are created by the GNU project. That, and so that we should never forget about the freedom, is the reason that many people mean that linux distros should be called GNU/Linux. 
The cool thing is that much of this stuff, the basic terminal tools, have not changed much. So if you read a 5 year old book, most (if not all) of the commands will work as expected. 
If you are interested in some reading I would recoment [this](http://linux-newbie.sunsite.dk/) site.

---

### Post by zenwhen on 2004-11-15
Compile your own kernel. Make it support all of your hardware. Make it perfect. 

If you can do that, you will probably have a much greater understanding of and apreciation for Linux and OSS in general. 

Everyone should run their own kernel at least once. There are tons of guides out there on the net. Pick one that looks nice to you, and go for it.

---

### Post by HungSquirrel on 2004-11-15
Eh, well, get to know Linux a bit before you do that.  ;)

---

### Post by jwb on 2004-11-15
It sounds kinda silly, but if' you're just starting off..... get a copy of the "Linux for Dummies" series. It's pretty generic and actually covers stuff very well.

A little more advanced is "Linux Administration: A Beginner's Guide" by Steve Shah. (ISBN: 0072122293). It's not Ubuntu specific, but most of what goes on from the command line is the same or very similar across all Linuxes. (Linux's? Linuxii?)

Of course, you can get most of what you need simply by going to Google and searching. Careful though- even idiots can get their stuff on the web.

Which begs the question- am I an idiot giving you bad advice, a friend giving good advice, or an evil genius knowingly giving bad advice for humorous effect?

Mwahahahahahahahahahaha!

;-)

---

### Post by ITLogic() on 2004-11-16
Hey thanks for all the help! I found this:

[http://www.tldp.org/LDP/intro-linux/html/index.html](http://www.tldp.org/LDP/intro-linux/html/index.html)

at linux.org. I haven'r really got into it yet, but it supposedly has review questions at the end of each chapter. I like those kinds of learning material. I am also setting up another computer with FreeBSD. I hope I'm not byting off more than I can chew, but I'm going to try to learn and understand both systems.

I like the compiling my own kernel idea. I'm not really sure what it means yet, but it sounds good!  :grin:  

Whatever resources I use to get me up to speed, I must say, this board is number 1. Thanks to all you guys and gals for all the help. You will be hearing from me again.  :wink:

---

### Post by Marauder1 on 2004-11-16
But dont forget to share what you learned
and help others on this forum.

---

### Post by HungSquirrel on 2004-11-16
>  I hope I'm not **byting** off more than I can chew
If that was supposed to be a pun...

GROOOOOOOOOOAAAAANNNNNNNNNN!  :-p

---

### Post by ITLogic() on 2004-11-16
LOL!  :mrgreen: 

Yes it was a pun, a lame one, but one the less.  :oops:

---

