---
title: "Need a few Ubuntu apps similar to Windows programs"
date: 2008-06-19
forum: General Help
---

### Post by gobbles414 on 2008-06-19
Hi all,

Although I prefer the Ubuntu OS, I have been spending a lot of time recently using my Vista desktop for work. I'm just curious to learn if some of my favorite Windows programs have Ubuntu equivalents (with GUI). Here's a list:

**[CCleaner]("http://www.ccleaner.com/")**
A privacy & maintenance utility, similar to OnyX in Mac OS X...

**[Recuva]("http://www.recuva.com/")**
A recovery & secure delete utility...

**[Any Video Converter Free Version]("http://www.any-video-converter.com/products/for_video_free/")**
Transcodes some files that VLC cannot...

**[Windows Live Messenger]("http://get.live.com/messenger/overview")**
I need to audio/video chat with friends & clients who are on Windows Live network.

PS: I'd also like to find an "always-on" antivirus program for Ubuntu that can successfully interface with Evolution -- without the need for a customized kernel. I'm currently using Linux version of Avast; the Linux version is "on-demand" only.

---

### Post by VMC on 2008-06-19
> **gobbles414 said:**
> Hi all,

Although I prefer the Ubuntu OS, I have been spending a lot of time recently using my Vista desktop for work. I'm just curious to learn if some of my favorite Windows programs have Ubuntu equivalents (with GUI). Here's a list:

**[CCleaner]("http://www.ccleaner.com/")**
A privacy & maintenance utility, similar to OnyX in Mac OS X...

**[Recuva]("http://www.recuva.com/")**
A recovery & secure delete utility...


**[Any Video Converter Free Version]("http://www.any-video-converter.com/products/for_video_free/")**
Transcodes some files that VLC cannot...

**[Windows Live Messenger]("http://get.live.com/messenger/overview")**
I need to audio/video chat with friends & clients who are on Windows Live network.

Recuva try = sudo apt-get install secure-delete
Windows Live Messenger = Use Pidgin
Video convertor = Use VLC for Linux

---

### Post by Anzan on 2008-06-19
Good list.

And you don't really need CCleaner in Linux. (I remember Crap Cleaner fondly as it really helped make Windows useable.)

---

### Post by dmsuperman on 2008-06-19
You don't really need antivirus...I don't think I've ever heard of a successful linux virus.

As far as video converter...if you aren't afraid of commandline install mencoder.

---

### Post by editrix on 2008-06-20
Try here: [http://www.osalt.com/](http://www.osalt.com/)

---

### Post by gobbles414 on 2008-06-20
Thank you all for your ideas. I'll attempt to address each of them in my reply; I'm sure that I'll expose some of my ignorance. Here we go...

> Recuva try = sudo apt-get install secure-delete
Windows Live Messenger = Use Pidgin
Video convertor = Use VLC for Linux
I'll try the secure-delete suggestion. But two things... First, I'd also like to have the ability to recover lost files -- on my digital camera's memory card, for example. Can you suggest a good file recovery program? Second, I assume that I'd have to install Ubuntu on a partition without journaling in order for secure-erase to permanently delete files. Is that correct?

I'd like to have the ability to audio/video chat with friends who are on the Windows Live network. According to the Pidgin website, "As part of Google's Summer of Code 2008, a voice and video project has been accepted. The plans are to first implement and stabilize voice and video on XMPP (making adding GTalk trivial) and then continuing onto the other protocols." In other words, it could be a long time before anyone will be able to audio/video chat over the WL network using Pidgin. I've also tried Mercury Messenger 1.9, Kopete, AMSN, and Gizmo5, all without success.

I love VLC. However, there are some video files that it simply refuses to transcode. Also, I sometimes want to transcode short clips from long video files. But VLC requires start & end times to be input in seconds. At least for me, it will not accept the hh:mm:ss format. And when transcoding some files, even properly formatted times are ignored! Am I doing something incorrectly?

> And you don't really need CCleaner in Linux. (I remember Crap Cleaner fondly as it really helped make Windows useable.) I would like a CCleaner/OnyX type program for Ubuntu because I value my privacy as well as the performance of my system. I estimate that my Vista computer's performance has increased by at least 10% since I've started running CCleaner on a regular basis. I've witnessed similar results after using OnyX on Macs. Incidentally, does anyone know if CCleaner deletes/clears the NTFS journal in Windows? What about OnyX and the HFS+ file-system...?

> You don't really need antivirus... I don't think I've ever heard of a successful linux virus. I'm not afraid of getting a Linux virus. As you say, that's 99.9% impossible. I simply don't want to become a carrier of a Windows virus. I'll be using my Ubuntu computer to send emails, attachments, and files to friends & clients. I'd rather not infect their computers.

> As far as video converter... if you aren't afraid of commandline install mencoder. I'd much rather use a GUI than a command line interface. Is there a good MEncoder front-end available?

> Try here: [http://www.osalt.com/](http://www.osalt.com/) Thanks for the link. I'll check it out.

---

### Post by daleus on 2008-06-20
> **Anzan said:**
> Good list.

And you don't really need CCleaner in Linux.


In firefox, push Ctrl + Shift + Delete and hit enter to clean firefox out.

There isn't anything else CCleaner does that applies to Linux

---

### Post by danwood76 on 2008-06-20
> **gobbles414 said:**
> 
I love VLC. However, there are some video files that it simply refuses to transcode. Also, I sometimes want to transcode short clips from long video files. But VLC requires start & end times to be input in seconds. At least for me, it will not accept the hh:mm:ss format. And when transcoding some files, even properly formatted times are ignored! Am I doing something incorrectly?


[AviDemux2]("http://www.getdeb.net/app/Avidemux") will transcode video files, it probably uses the same codecs as your win alternative.
I've found it gives better quality video compared to the windows one I used to use.

Video and Voice and chat to windows is only available on skype at the moment, I think.
Convince them to use skype :)

---

### Post by gobbles414 on 2008-06-20
> In firefox, push Ctrl + Shift + Delete and hit enter to clean firefox out. There isn't anything else CCleaner does that applies to Linux. Thanks for the advice, but it's incorrect. CCleaner does a lot more than just clearing Firefox data. For example, it also clears the system's thumbnail cache. I don't like having to dig in half-a-dozen different directories to clear out such files in Linux.

> AviDemux2 will transcode video files, it probably uses the same codecs as your win alternative. I've found it gives better quality video compared to the windows one I used to use. I definitely try AviDemux2. Thanks!

> Video and Voice and chat to windows is only available on skype at the moment, I think. Convince them to use skype. Easier said than done, sadly. :(

---

### Post by gobbles414 on 2008-06-24
I'm interested in some additional alternatives. Any ideas?

---

### Post by Taxman415a on 2008-06-24
ClamAV I think will cover the antivirus front, but I think there are others. I don't know specific solutions for what you're looking for but a good general method is to open synaptic and try various search terms. virus or antivirus will find what you want there, recovery or file recovery should find some utilities there, etc. You're not always going to find GUI tools. That there are so many good ones that are free software now is a growing thing, but sometimes you just have to adjust without them.  As far as Windows messenger, that's just an unfortunate case of lock in and that's how those things go.

---

### Post by gobbles414 on 2008-06-26
> ClamAV I think will cover the antivirus front... A year or two ago, I tried using ClamAV in Ubuntu. I couldn't get it to integrate with Evolution, and it didn't detect all of the Eicar test files that I used in testing. But perhaps ClamAV is worth another look.

> You're not always going to find GUI tools. True... But a boy can dream, can't he? :biggrin:

> As far as Windows messenger, that's just an unfortunate case of lock in and that's how those things go. From what I've read, it's partially a case of Microsoft not opening the Windows Live network to outside developers. But the open source community has proven that it's capable of crafting solutions to these kinds of problems when it wants to do so (e.g. breaking DVD encryption). So IMHO, the WLM audio/video problem is also the fault of a vocal group of open source developers who've lost touch with reality. These developers believe that non-Windows user will be able to convince all of his/her friends & family & business contacts to switch from WLM to an alternative service. I'm sorry, but it just doesn't work that way in the real world. A friend of mine whom I've helped to switch to Ubuntu has to run Windows XP in a virtual machine only to audio chat with her relatives via WLM. These relatives live in another country than she does, so it really saves her a lot of money to use the computer instead of a telephone.

Incidentally, the speed at which Pidgin and other WLM-compatible clients execute file transfers is WAY TOO SLOW!

---

### Post by danwood76 on 2008-06-26
> **gobbles414 said:**
> 
Incidentally, the speed at which Pidgin and other WLM-compatible clients execute file transfers is WAY TOO SLOW!

In Amsn if you setup port forwarding properly the file transfers at insane speeds.
It doesnt use the MSN servers like the rest, the only problem is its built on Tcl/Tk.

---

### Post by Taxman415a on 2008-06-26
> A year or two ago, I tried using ClamAV in Ubuntu. I couldn't get it to integrate with Evolution, and it didn't detect all of the Eicar test files that I used in testing. But perhaps ClamAV is worth another look.
Yeah, try this link: [http://ubuntuforums.org/showthread.php?t=84423](http://ubuntuforums.org/showthread.php?t=84423) or try in the forum again if you can't get it working.

 > True... But a boy can dream, can't he? :biggrin:
But of course! I did find some command line tools that will fit the file recovery part of the bill you were looking for. They are some of the packages that [http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/) uses for their iso. The packages are listed here: [http://ubuntu-rescue-remix.org/Software](http://ubuntu-rescue-remix.org/Software)
Try looking up the man pages or documentation for those and I think you'll find some of them very useful. Maybe you can be the one that integrates them into a nice GUI package. ;)

 > From what I've read, it's partially a case of Microsoft not opening the Windows Live network to outside developers. But the open source community has proven that it's capable of crafting solutions to these kinds of problems when it wants to do so (e.g. breaking DVD encryption). So IMHO, the WLM audio/video problem is also the fault of a vocal group of open source developers who've lost touch with reality. These developers believe that non-Windows user will be able to convince all of his/her friends & family & business contacts to switch from WLM to an alternative service. I'm sorry, but it just doesn't work that way in the real world. A friend of mine whom I've helped to switch to Ubuntu has to run Windows XP in a virtual machine only to audio chat with her relatives via WLM. These relatives live in another country than she does, so it really saves her a lot of money to use the computer instead of a telephone.
No, it's really not like that. There's no (or few) vocal developers like that, there just is a lack of any motivated enough to tackle to problem of reverse engineering Microsofts protocols again and again every time they change them. The vocal people are typically not the developers. :) That's how free software works. If a tool doesn't exist it's because no one has yet gotten motivated enough to write it. I'm ok with that, I just try to focus on what is there, find alternatives, and use emulation or wine where I have to. I find that gets less and less every day. Whenever I get frustrated I try to stop and think that it's pretty darn cool that anybody decided to release any of the stuff I use everyday for free. And on top of that it's really good stuff.

---

### Post by VMC on 2008-06-26
> **Taxman415a said:**
>  
No, it's really not like that. There's no (or few) vocal developers like that, there just is a lack of any motivated enough to tackle to problem of reverse engineering Microsofts protocols again and again every time they change them. The vocal people are typically not the developers. :) That's how free software works. If a tool doesn't exist it's because no one has yet gotten motivated enough to write it. I'm ok with that, I just try to focus on what is there, find alternatives, and use emulation or wine where I have to. I find that gets less and less every day. Whenever I get frustrated I try to stop and think that it's pretty darn cool that anybody decided to release any of the stuff I use everyday for free. And on top of that it's really good stuff.

When I decided to leave Windows, surprisingly I found a solution in every case.
As Henry Ford said “If you think you can or you think you can’t, Your Right”
Remember, the Universe always says "Yes" to us. Either you can or, your right, you can't. That has been my view of live.

I have found a solution to every program that Windows has in Linux. I think the Kiss of Death  is dual booting. When I stopped doing that and only booted into Linux I was then forced to find answers - or was I then willing to find them :)

Backup on topic, you can use shell scripts to remove almost all you temp files that CCLEANER did in Windows. Remember that stands for Crap Cleaner. And you don't have to deal with the Windows Registry anymore.

---

### Post by der_joachim on 2008-06-26
As for a CCleaner alternative (I really love that little program :)), KDE4 has a little utility called Kleansweep that cleans a lot of KDE-related cruft, like the konqueror cache and various KDE-related temporary files. I do not know whether such a thing exists for other desktop environments.

---

### Post by gobbles414 on 2008-06-30
> In Amsn if you setup port forwarding properly the file transfers at insane speeds. It doesnt use the MSN servers like the rest, the only problem is its built on Tcl/Tk. Thanks. So these insane speeds will work AMSN to AMSN and AMSN to WLM, correct? If so, it sounds promising.

> Yeah, try this link: [http://ubuntuforums.org/showthread.php?t=84423](http://ubuntuforums.org/showthread.php?t=84423) or try in the forum again if you can't get [ClamAV] working. Thanks. That thread is old enough that I probably read it when I tried to install ClamAV in Ubuntu a couple of years ago. But, I guess it can't hurt to try again.

> I did find some command line tools that will fit the file recovery part of the bill you were looking for... Thanks, I'll try that if I'm unable to locate a GUI-based tool with similar functionality.

> No, it's really not like that. There's no (or few) vocal developers like that, there just is a lack of any motivated enough to tackle to problem of reverse engineering Microsofts protocols again and again every time they change them. The vocal people are typically not the developers. That's how free software works. If a tool doesn't exist it's because no one has yet gotten motivated enough to write it. I'm ok with that, I just try to focus on what is there, find alternatives, and use emulation or wine where I have to. I find that gets less and less every day. Whenever I get frustrated I try to stop and think that it's pretty darn cool that anybody decided to release any of the stuff I use everyday for free. And on top of that it's really good stuff. I 100% agree that we Ubuntu users are getting a lot of functionality cost-free; and I'm thankful to the open source community for all of it. But a few minutes of searching in these forums makes it clear to me that a significant portion of open source developers/gurus live in an imaginary world where command line is the best possible user interface for everyone, and only idiots need access to closed source technologies like WLM. On a positive note, I notice that Wine is getting better-and-better all the time. So I'll test some Windows-based alternatives to WLM, like Trillian or Yahoo. Then I'll report back. 

> I have found a solution to every program that Windows has in Linux...

Backup on topic, you can use shell scripts to remove almost all you temp files that CCLEANER did in Windows. Remember that stands for Crap Cleaner. And you don't have to deal with the Windows Registry anymore. I welcome any recommendations that you have for shell scripts that would be helpful to me. I'm not a programmer. And I'm sure that there are dozens of places where data that I'd like to delete are hiding in Ubuntu. So again, I'd appreciate your advice on how to begin. Regarding your comment that you have found a solution in Linux to everything that you'd been doing in Windows, I congratulate you. You've certainly had better success that I have had in that department! :D

> As for a CCleaner alternative (I really love that little program ), KDE4 has a little utility called Kleansweep that cleans a lot of KDE-related cruft, like the konqueror cache and various KDE-related temporary files. I do not know whether such a thing exists for other desktop environments. Unfortunately, I'm using the GNOME version of Ubuntu. So I don't think that Kleansweep will work properly for me, will it?

---

### Post by der_joachim on 2008-07-01
> 
 Unfortunately, I'm using the GNOME version of Ubuntu. So I don't think that Kleansweep will work properly for me, will it?

Alas. It's KDE specific.

---

### Post by manfer on 2008-07-01
aMSN has webcam support at least since half an year, or maybe a year. I tried it in Windows and Mac and works perfectly. I haven't used it in linux, so I don't know if it works on linux (but amsn has that functionality so if not webcam available in linux the problem must be different from that one of the use of WLM protocol. They know how to deal with it because works on windows and mac)

----------------------------------------------
I 100% agree that we Ubuntu users are getting a lot of functionality cost-free; and I'm thankful to the open source community for all of it. But a few minutes of searching in these forums makes it clear to me that a significant portion of open source developers/gurus live in an imaginary world where command line is the best possible user interface for everyone, and only idiots need access to closed source technologies like WLM. On a positive note, I notice that Wine is getting better-and-better all the time. So I'll test some Windows-based alternatives to WLM, like Trillian or Yahoo. Then I'll report back.
----------------------------------------------

I don't think any of those you call gurus would say you are an idiot if you don't want to use the command-line. One can use it, one can not, it is our own decision.

I'm a recent user of linux (though I had just tried it many times in the past) and at first I always tried to find a GUI application for what I wanted to do (that's how we are used to work, is what we do on windows platforms). But when you give command-line a chance and you start to learn and use it too, you realize it worths the effort. I suggest you to learn how command-line works too, the same as you learn how to use applications. You would be impressed for what you can do with it many times.

---

### Post by billgoldberg on 2008-07-01
About the video converter:

The easiest and best on is winff.

Winff is a gui frontend for ffmpeg.

But in order to install the full version of ffmpeg you'll need to add the medibuntu repo.

So these are the commands to get winff, fully working on your computer.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install ffmpeg
```

and then install this file:

[http://winff.googlecode.com/files/winff-0.42-i386.deb](http://winff.googlecode.com/files/winff-0.42-i386.deb)

The program will be located in "applications -> sound & video -> winff".

The GUI is very easy to use.

---

### Post by gobbles414 on 2008-07-01
> Alas. It's KDE specific. Yes, I once tried installing Kleansweep in GNOME Ubuntu. It installed and even ran, but too many of the tools are KDE specific. How much effort do you think that it would take for programmers to port this program over to GNOME? I'd be really interested in such functionality.

> aMSN has webcam support at least since half an year, or maybe a year. I tried it in Windows and Mac and works perfectly. I haven't used it in linux, so I don't know if it works on linux (but amsn has that functionality so if not webcam available in linux the problem must be different from that one of the use of WLM protocol. They know how to deal with it because works on windows and mac) I'm not sure that I see the point in using a webcam if there's not any audio to accompany it. I know that aMSN has "voice clips". But that is certainly not the same as full audio chat support. My understanding is that full audio chat support is on the to-do lists of most major WLM-compatible Linux chat clients. But this state of affairs has not changed in a couple of years at least.

> I don't think any of those you call gurus would say you are an idiot if you don't want to use the command-line. One can use it, one can not, it is our own decision. You'd be surprised how many Linux gurus/programmers insist on the superiority of the command line. I encourage you to search the web, go on an open source related IRC channel, or just take an honest look at some of the threads in the Ubuntu Forums. And the command line is not the only arena in which gurus/programmers are out of touch.

I remember going on an Evolution-related IRC channel sometime in 2007. I asked if it was possible to have my contacts sorted alphabetically by last name when I pressed the *TO* button in a new message. Many Windows-based email programs offer this functionality. At least at that time when I asked the question, such functionality was unavailable in Evolution. But instead of the gurus/programmers just politely stating that what I wanted to do was impossible, I was subjected to responses like, "Why in the hell would you want to sort that way," and "Why can't you just use the search tool?"

> I'm a recent user of linux (though I had just tried it many times in the past) and at first I always tried to find a GUI application for what I wanted to do (that's how we are used to work, is what we do on windows platforms). But when you give command-line a chance and you start to learn and use it too, you realize it worths the effort. I suggest you to learn how command-line works too, the same as you learn how to use applications. You would be impressed for what you can do with it many times. I know how to use the command line; it is indeed a very powerful tool. Nevertheless, I prefer to use GUI front-ends whenever possible.

> The easiest and best on is winff... Winff is a gui frontend for ffmpeg. Thanks for that idea! I notice that there's also an AMD64 .deb package. This is great news for me, since I've been experimenting with 64-bit Ubuntu. So far, all of the essentials I had been concerned about (e.g. Flash Player) seem to work well.

---

### Post by ladr0n on 2008-07-01
> **gobbles414 said:**
> You'd be surprised how many Linux gurus/programmers insist on the superiority of the command line. I encourage you to search the web, go on an open source related IRC channel, or just take an honest look at some of the threads in the Ubuntu Forums. And the command line is not the only arena in which gurus/programmers are out of touch.

    TBH, you're being pretty presumptive.  Programmers don't insist on the general superiority of the command line (or anything else, for that matter).  However, they do dislike wasting their time, and they typically write applications they will use.  
    There are some things (advanced filesystem tools being one example) that most programmers won't bother writing a GUI for, because the GUI will not add any additional functionality to the program.  There are other things (reverse engineering a constantly changing protocol like Microsoft's MSN being one example) that a programmer would consider a waste of time, because since Microsoft does change their standards so often, even the best reverse engineering job would have to be redone fairly often, and that's just annoying.  
    If you think that having a programmer spend the time to do those things would be beneficial to you and others, you could always hire one to do so (there are plenty of sites where you can post jobs for freelance programmers to take up) or even start working on it yourself.  Who knows, perhaps if you start it, someone else will help you finish it :).  It is not because they are living in some sort of fantasy world that open source programmers tend not to tackle certain problems, it is simply that there are other problems they see as being more worthy of their time.

---

### Post by manfer on 2008-07-01
Permit me a joke... maybe if microsoft ports his "free" windows live messenger to all other systems or just open it !!. Mhhhh, wait, that is for sure beyond reality. ;) Wait, wait, they have ported it to MAC... mhhhhhh, can you guess what is not available on mac version? VoIP ;)

Sorry my mistake about aMSN, yes, webcam and voice clips are not VoIP which was what you were looking for. Thanks for the correction.

I guess another thing to consider is that many programmers involved in open source free software won't expend their code effort in a proprietary technology and would try to code an open source free alternative. There's a lot of VoIP open source free alternatives under development. Even a lot of those people won't suggest you to use a proprietary free solution, like skype. And I don't think that could be said being out of reality. It is only another point of view. As much people tends to involve and use open source free solutions, more and better ones for all of us.

---

### Post by gobbles414 on 2008-07-02
**ladr0n:** Perhaps I am being too critical of open source gurus/programmers. After all, it's not wise to bite the hand that feeds me!:) But as a non-programmer, I just get frustrated when I witness a SMALL MINORITY of gurus/programmers giving phony/rude answers to reasonable questions from users (e.g. the IRC chat about Evolution mentioned above).

Also, I don't understand why a priority hasn't been given to getting Windows Live Messenger working in Wine. I am convinced that MOST open source gurus/developers have the best interests of the community at heart. And FULL compatibility with WLM in Ubuntu is one of if not *the* most requested feature in these forums. Relatively speaking, shouldn't it be rather simple to get WLM working in Wine? After all, Wine is a VERY advanced compatibility layer nowadays.

**manfer:** I agree on how lame it is that Microsoft still refuses to release an un-neutered version of its Messenger software for Mac OS X.

To address one of your other statements, when an open source guru/developer says to me, "You don't need this functionality," they're usually speaking code for "Open source cannot do this yet." But as you correctly observe, open source is getting more popular all the time. And as a result of the subsequent increased interest on the part of gurus/programmers, open source software continues to improve at a rapid pace.

---

### Post by Fevrin on 2009-01-05
> **gobbles414 said:**
> Yes, I once tried installing Kleansweep in GNOME Ubuntu. It installed and even ran, but too many of the tools are KDE specific. How much effort do you think that it would take for programmers to port this program over to GNOME? I'd be really interested in such functionality.

I've personally had success using Kleansweep in GNOME.  However, you may also be interested in FSLint, which is a GNOME version (with a slightly different set of capabilities).  You can even use both, if you find it necessary to do so.

If you wish to remove only thumbnails and you use Nautilus as your file manager, you can simply delete the ~/.thumbnails directory (or selectively delete files within that directory).

---

### Post by cb951303 on 2009-01-05
If you're looking for a good transcoder GUI: [http://handbrake.fr/](http://handbrake.fr/)

---

