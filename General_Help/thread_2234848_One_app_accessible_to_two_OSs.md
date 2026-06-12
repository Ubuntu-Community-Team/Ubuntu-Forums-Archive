---
title: "One app accessible to two OSs?"
date: 2014-07-17
forum: General Help
---

### Post by Mike_Walsh on 2014-07-17
Afternoon, all.

Just as a matter of curiosity; when running two OSs in dual-boot config, is it possible to set up apps on a separate partition, so that ONE installation of a given program is available to, and seen by, both OSs?

I know this can be done with data files, but I don't know if it's possible to do so with apps and programs. Would it make it easier with both OSs being members of the Ubuntu family?

I Skype quite a bit with relatives abroad; and I do tend to move from one OS to the other, as the mood takes me. It's a bit disconcerting to find chunks of your chat conversation missing, because you were on the other OS at the time!

Anybody have any ideas about this one? I can't be the first person to have considered this...


Regards,

Mike.

---

### Post by lukeiamyourfather on 2014-07-17
It's probably storing logs of the conversations in your home folder since that's the only location it would have access to when running as a non-root user. So you wouldn't necessarily be sharing applications between installs but rather your home directory. You could make a symbolic link to the other home directory assuming the permissions and users are the same between them. Or you could setup a dedicated partition as a home directory that all installations use.

---

### Post by |{urse on 2014-07-17
It's possible using portable apps, but with registered applications you will run into dependency nightmares unless both OSes are distributions of the same kernel. You would need to (a very small example) Say, you have Mint and Ubuntu and Debian all sharing the same home partition, the slightest package update on Mint that was held back or decided against in Ubuntu would then render your program possibly broken on Ubuntu but possibly not Debian. You can probably see from that example how disastrous that sort of thing ends up being for daily use. 

There's always portable apps! But what you're proposing (as many others have) is inviting entropy.

[http://portablelinuxapps.org/](http://portablelinuxapps.org/)

---

### Post by tgalati4 on 2014-07-17
Change your computing habits to use all cloud-based services.  For instance I use googletalk instead of skype and my chat logs show up in any computer, tablet or smartphone.  Trying to get identical application behavior across Windows and Linux might be difficult. Skype seems to lag in version/capability in Linux.

Perhaps there is a script to backup/email your Skype logs to another service such as Evernote--then they would be available.

Let me google that for you:

[http://superuser.com/questions/67133/how-do-i-export-the-history-of-skype](http://superuser.com/questions/67133/how-do-i-export-the-history-of-skype)

[http://askubuntu.com/questions/149214/copy-skype-chat-history-to-text-files](http://askubuntu.com/questions/149214/copy-skype-chat-history-to-text-files)

---

### Post by Mike_Walsh on 2014-07-17
Thanks everybody for your replies.

[COLOR=#ff0000]lukeiamyourfather[/COLOR]: You're probably right about the chat logs being stored in the home folder; like you, I don't see where else they COULD go. I'll ask you this, if you know how to do it; how do I set up a /home partition, and how do you set up the permissions, etc?

[COLOR=#ff0000]|{urse[/COLOR]: You've got me there. I'm not even sure what you mean by 'portable apps'.....

[COLOR=#ff0000]tgalati4[/COLOR]: Googletalk, huh? Is it cross-compatible with Skype? I mean, if I start to use that, can my relatives remain on Skype, and still be able to talk to me?

I get what you mean by cloud-based computing. Even now, I'm still amazed at being able to log into Chrome on ANY computer, and hey presto! there's all my favourites, bookmarks, et al... And for somebody who can trace his computing roots back to the days of the Commodore 64, the Sinclair ZX 81, and the TRS-80, that's QUITE something, I can tell you!

BTW, the two OSs in question, if you look at my signature, are the first two...Ubuntu 14.04, and Xubuntu 14.04. As far as I can tell, they're both running the 3.13.0-30 kernel. The only place I run ANY Microsoft stuff is XP, under Virtualbox on Ubuntu!


Regards,

Mike.

---

### Post by |{urse on 2014-07-17
Portable in the sense that they run independently as a single file existing in a shared Home directory between operating systems. This won't help you in regards to mswindows, of course.

---

### Post by tgalati4 on 2014-07-17
gtalk chat sessions will show up across devices--just like Chrome bookmarks.  I don't use Skype anymore, so I can't comment on how to connect gtalk and Skype.  I presume you can't.  Get your friends to use gtalk on Chrome and that might solve your problem.  The ones that don't want to change, you don't want to talk to anyway.

---

### Post by Kirkx on 2014-07-18
> Mike_Walsh: [COLOR=#ff0000]|{urse[/COLOR]: You've got me there. I'm not even sure what you mean by 'portable apps'.....
"Portable apps" are usually very small programs that you extract from a .zip or similar package. They can be extracted to any directory of your choice and that's it, there is nothing to install. You can place them on a dedicated partition which is shared between different distros. Here is an example of a small app like that, Hashcalc, sitting in my custom "pap" partition (pap = portable applications) :

[http://i.imgur.com/l2NCh5u.png](http://i.imgur.com/l2NCh5u.png)

[http://i.imgur.com/A7wORXA.png](http://i.imgur.com/A7wORXA.png)

[http://i.imgur.com/VnfOgIF.png](http://i.imgur.com/VnfOgIF.png)

Of course this is not going to help you with Skype, which is much more complex program and has files installed all over the filesystem (I'm guessing here, I don't have Skype installed).

---

### Post by Mike_Walsh on 2014-07-18
Well, thanks everybody for your responses.

It's given me a few things to chew on! To be frank, I think I've probably put this in the wrong forum anyway (shoulda gone in 'General Chat', I reckon); it was more of a '"What if..?" question, really.

I'll mark it as solved, anyhow!

Cheers, guys.


Regards,

Mike.

---

### Post by lukeiamyourfather on 2014-07-18
Why not just install Ubuntu and then install the different interfaces. No need to have multiple installs like you're doing now.

---

### Post by Mike_Walsh on 2014-07-18
Hiya.

Oh, it's not a case of having multiple installs and making life awkward; believe it or not, I LIKE dual-, and even on occasion triple-booting my system.....and just generally 'playing around' with them.

I had over 10 years of using a laptop with an Intel 'Celery Stick', 128 MEGAbytes of RAM (!), and a 20 Gb hard drive. Since January, I've had a system with an Athlon 64, 3 GIGAbytes of RAM.....and a 500 Gb hard drive; still pretty tame by today's standards, but it's SO much more to play with than I'd ever been used to. Unless I upgrade, although I have 4 memory slots, I'm still limited to a max of 4 Gb RAM anyway, by virtue of it being DDR1.....1 Gb sticks are the largest you can get.

Despite using the things for over 30-odd years, it's only during the last year or so that I've really got into the 'techie' side of things, and generally upgrading or improving where I can. My goal, in the next couple of years, is to build my own system.....when I feel I've amassed sufficient expertise. I'm stuck with the integrated graphics at the moment (which are actually quite good for what I want), since the single PCIe x16 bus on the mobo is faulty, with a number of damaged connectors.....and it's only 1.0a standard, to boot!

Damn near impossible finding a card for a bus that old, even if it WAS still working!!

Regards,

Mike.

---

### Post by at_first_light on 2014-07-18
In theory I suppose if you compiled your applications from source to be run from a seperate partition you could then launch them on either OS. I'm not sure how dependencies would factor into that, but I assume if you installed all the dependencies on both operating systems before compiling it might work? I'm thinking out loud here...and haven't done much compiling from source so I'm hardly a useful resource on the topic; perhaps someone else can shed light on this idea?

---

