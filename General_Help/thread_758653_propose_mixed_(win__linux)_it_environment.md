---
title: "propose mixed (win / linux) it environment"
date: 2008-04-18
forum: General Help
---

### Post by Linux&amp;Gsus on 2008-04-18
This might get a bit complicated. So, please bear with me.

I'm a full-time volunteer worker with a non-profit organization. Well, all staff are full-time volunteers, so some times we lack the expertise and/or man-power that might be helpful.
However, there are a lot of problems with the IT, which, luckily, doesn't affect me since I'm in an off-site office. But still “something” needs to happen at our main hub. The problem is that everyone in the IT department seems to favor Microsoft. Apparently because it is so “easy” to click everything together. I personally never worked with Windows server, so I can't tell whether that's true or not. But that was the answer I got when I asked why everything is Windows. And, of course, as an officially registered training center we get a rather huge discount from MS.

Applications that are used are Word, Excel, PowerPoint, Access, etc and, of course, MS Exchange server. Websites are also hosted on MS server and developed with ASP and a bit Flash stuff. However, I don't see that really everyone needs the 1% of features that might be missing in OpenOffice compared to MS Office. Here is where my idea comes in.
IMHO the most problems are due to a lack of server power. Most of the about 200 workstations are clients connected to the Windows servers. We have about 300 staff (not everyone is here at any given time) and about the same number of students that go through our various training courses, and we are growing. So, we have about 500-600 people going in and out each year from all parts of the world.

My idea would be to keep the Windows stuff for those who, sort of, rely on it and set up an LTSP for the rest. It don't know of anyone (skill and time wise) here who would be able to make something up to get the Access databases ported to something from the FOSS world. It's a quite a setup with Email, Calendar, Autotext, Staff & Student Database, etc. Autotext is actually quite important for some of the staff. It's quite an integrated setup, or in others words a “typical” MS lock-in.
A few are working a lot with Photoshop, Flash and Adobe Premier and the accounts department uses Quicken. Also applications are made with Adobe Acrobat so that it's possible to edit enter application details on the computer and print out the edited form. I don't know if there is something like that available for Linux. So, it's probably not possible to make a full switch.

But those who only use general email (without the need of using Autotext), a little bit of Word and Excel, a calendar, web browsing, etc, basically those who aren't locked in to a MS solution, could work with Linux just fine. That should be the majority.

Now, my problem is that I, even with my limited knowledge, probably know the most about Linux. Besides me there are max 5 others who have more or less ever touched it or even looked at Linux. So, I can't rely on too much help. I never made something with LTSP, so I have no clue what I walk myself into here.
Therefore I need to present a good concept and some good sources of information. I hope that some of you can help me out with some ideas.

So, here is my list of questions I have so far.

[LIST=1]
[*]Continue using the Exchange server or installing some sort of groupware on Linux? Why?
[*]Is there another application that can connect to Exchange other than Evolution? I don't think so but maybe someone knows more about it?
[*]What about the other way round. Can Outlook connect to a Linux based groupware or what other software is available on Windows to get something with email, calendar, tasks, etc going? And can that then still be used for those who rely on that Autotext stuff with Word and Outlook?
[*]Is the web interface of a groupware a good alternative or would it be better to use an app like Evolution or Kontact?
[*]Would user management be better on Windows or Linux? Is it actually possible to log in to Linux and Windows Terminal Server from one client or must a client be specific for either Linux or Windows?
[*]File sharing between the different platforms must be easily possible of course. In best case scenario the user wouldn't even need to know where the files are. Windows, Linux, where ever, as long as people can get what they need.
[*]What sort of hardware (32 vs 64 Bit, RAM, CPU, RAID, etc) would be required for an LTSP with about 200 clients. Also our goal is to have 500 staff. What would be a critical size to rather have 2 smaller servers instead of one big one. How hard or easy would it be to have some sort of load balancing in place?
Apps that would be used by probably almost everyone more or less at the same time are OpenOffice, something like Evolution or Kontact, Browser, PDF reader. Mainly office related stuff.
[*]How long would it take to set up an LTSP for someone who has never touched that before? Would you recommend to install the server version and add needed apps or just go for the “normal” Kubuntu install? I guess KDE would be easier for the people who are used to Windows. But I believe Gnome and KDE could co-exists so that people could choose what to use if they want to, right?
[*]At least for now the last question. Where do I find good info and a good install guide for LTSP? Honestly last time I looked the LTSP homepage it wasn't really appealing for the eye, which in fact isn't a good thing to present to others who might make the decision whether to dig deeper into this possible solution. Basically I'm looking for something easy to understand for newbies, fool proof, so to speak.
[/LIST]

Now, besides answers to many questions I need a good concept to present to the IT folks. What could I mention besides the obvious (MS license and software cost, viruses, etc)?

If you took the time to read that far maybe you have a few suggestions, ideas, answers websites to read through for me? That would be very much appreciated.
Thank you very much already.

Cheers,
Steve

---

### Post by mjziegle on 2008-04-18
I hate to be a downer and I'm all pro linux, but given your situation (volunteer) I think it would be best to stick with windows. A tremendous amount of effort and infrastructure has already been set up and you seem to only be considering capital costs and not the cost of both labor and good will (you users know windows)

Have you considered

1) Who is going to maintain the new linux servers? (All the windows people?)
2) Applications are king. Nothing else matters besides the end applications
3) Is anything really broken with your current setup that needs fixing

I'm in a large organization with a mixture of linux, solaris, and windows machines. We are slowly weening ourselves off windows servers but we have to have windows desktops for the applications and windows servers for some license servers. We have professional IT staff and it has taken us over 2 years to migrate over to unix based file and print servers. 

The biggest cost is going to be labor. It takes a long time for people who know what they're doing. We made the move for security reasons due to the nature of our operations knowing full well that it wasn't cost effective vs. windows. Active directory is sooo easy.

---

### Post by Tews on 2008-04-18
God Bless ya Steve, yer heart is in the right spot!! However, dont hold your breath while you wait for your IT dept to see the light.  As your company is an approved MS training Center and feeds from the MS trough, Im sure that there are contractual restrictions that severely restrict what type of programs they can run and still retrain their certification (typical blackmail tactics).  All you can do at this point is sit back and smile when the MS machine borks up..

---

### Post by Linux&amp;Gsus on 2008-04-18
> **mjziegle said:**
> I hate to be a downer and I'm all pro linux, but given your situation (volunteer) I think it would be best to stick with windows. A tremendous amount of effort and infrastructure has already been set up and you seem to only be considering capital costs and not the cost of both labor and good will (you users know windows)
Yes, I do consider the cost of labor. But in all aspects. I'm fully aware that it would not be a quick overnight thing to setup such a system. It takes it's time in planning, researching and of course doing it. However, there is also a cost of labor in keeping the current system running. Not to speak of the many times when most of the staff were halted because something crashed. Meaning the whole office is having a forced break. About every couple weeks I hear something about everything is unbearable slow, etc. Imagine at least half the people could continue working because they are on another system which ever that will be. I don't say that Linux will never break down....

> **mjziegle said:**
> Have you considered

1) Who is going to maintain the new linux servers? (All the windows people?)
2) Applications are king. Nothing else matters besides the end applications
3) Is anything really broken with your current setup that needs fixing
I do have considered some of these but for obvious reasons it would require some brainstorming and talking through with those in charge.
About point 1, the problem is probably not who is going to maintain these. I actually believe that it will cut down mix of OS versions. Due to the nature of our organisation we have some people working on their personal computers. That means we have almost all versions of Windows, starting from Win98 to Vista, in the wild plus a few people come with their Macs. The students internet cafe runs on WinNT with 6 clients for those who don't bring their own laptop.
Specifically about point 3, I just think of the uncountable times the registrars database broke with up to 1 weeks  data lost that needed to be re-entered. So, yes, things are broken and overstrained.

> **mjziegle said:**
> I'm in a large organization with a mixture of linux, solaris, and windows machines. We are slowly weening ourselves off windows servers but we have to have windows desktops for the applications and windows servers for some license servers. We have professional IT staff and it has taken us over 2 years to migrate over to unix based file and print servers. 

The biggest cost is going to be labor. It takes a long time for people who know what they're doing. We made the move for security reasons due to the nature of our operations knowing full well that it wasn't cost effective vs. windows. Active directory is sooo easy.
Thanks for your honest answer. I prefer someone tells me to stay with Windows instead of promising me heaven but it'll be far from it.

Cheers,
Steve

---

### Post by seeker1458 on 2008-04-18
1) What version of Exchange server are you using? 2003/2007?
2)Thunderbird...[http://www.downloadsquad.com/2007/03/30/howto-thunderbird-and-ms-exchange-server/](http://www.downloadsquad.com/2007/03/30/howto-thunderbird-and-ms-exchange-server/)
3)Outlook Express/Outlook 2003/Outlook 2007?
    a)[http://www.geocities.com/mailsoftware42/](http://www.geocities.com/mailsoftware42/)
4)Some stuff HAS TO HAVE IE to run.  I would Test with firefox, opera, shirra is nice on OSX but still needs some work. Personally I like having an application instead of using something like OWA.
5)User managment would probably be easer with AD. Likewise open makes it super easy to joing ubuntu to an Active Directory Domain. Yes you can RDP into a windows box using terminal services. Vice versa is true using a VNC client. I use TightVNC, its a super lightweight version.
6)Even if the non windows machine is not part of the same domain, it can access smb shares. All the user would need to know are the credentials for a AD user. The machine does not need to be part of AD, bc the user is the only thing being authenticated.

As for the rest google is a god send.  In your MS Office suite you should be able to export you dictionary file (with your auto text entries) and import into open office.  I havn't tried it, but Im sure its possible.  Also as far as presenting making the move.  It will obviously be a pretty big intial cost to get things moving, but run the numbers on how much  you would save in licensing fees along....say for the next ten years.

---

### Post by Linux&amp;Gsus on 2008-04-18
> **Tews said:**
> God Bless ya Steve, yer heart is in the right spot!!
He surely does, thank you... ;) O:)


 > **Tews said:**
> However, dont hold your breath while you wait for your IT dept to see the light.  As your company is an approved MS training Center and feeds from the MS trough, Im sure that there are contractual restrictions that severely restrict what type of programs they can run and still retrain their certification (typical blackmail tactics).  All you can do at this point is sit back and smile when the MS machine borks up..
That is a good point. I mean I really want to get our IT department get excited about the idea instead of throwing something on them and then run away. But this could be a show stopper.

Anyways, I'm still open for suggestions. Because I'm personally not satisfied with the fact that I can sit back and smile while most of my co-workers are stalled and potentially loose some work they did. Say 100 people saved their documents 5 min before a crash, that's a lot of time wasted. Plus the time to wait for everything working properly again.

Well, I don't quite want to give up on that one...

Cheers,
Steve

---

### Post by Linux&amp;Gsus on 2008-04-18
> **seeker1458 said:**
> 1) What version of Exchange server are you using? 2003/2007?
I believe it's 2003.

As for the rest, thanks. I'll read through the links tomorrow, it's getting kinda late here.

Cheers,
Steve

---

### Post by seeker1458 on 2008-04-18
I manage an Exchange 2007 server and it hasn't caused any problems.  So from a stability and ease of use stand point, its fine.  It was in place when I came here so Im not sure on the licensing fees or ttl.  Again just compare some of the free mail servers, and if you see something you like/need in Exchange, just keep it.

---

