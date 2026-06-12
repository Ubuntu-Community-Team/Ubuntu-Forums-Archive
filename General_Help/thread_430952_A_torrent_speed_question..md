---
title: "A torrent speed question."
date: 2007-05-02
forum: General Help
---

### Post by crimesaucer on 2007-05-02
The Microsoft Windows XP SP2 update, and a number of succeeding XP patch updates, install a system file - tcpip.sys - with settings that limit your computer's outgoing Internet connections.

In Windows with µTorrent, I had fixed this with lvllord's patch of the TCPIP.sys. I changed it form 10 to 50.

Then in µTorrent's Advanced Options, I had set the net.max_halfopen to 40, (80% of the number 50 which I had patched my TCPIP.sys to)

I also used a TCP/IP Optimizer, and set everything to my optimal settings for the maximum download speed (in kb/s).

Now in Windows my µTorrent had been super fast. 

...But I am tired of not using a bit torrent client in my xubuntu, so I was thinking about giving µTorrent in wine a try, or maybe a similar Linux program. I only want to do this if I can get things as fast or faster. 

So, I am still new to Linux and am wondering:

1.) If there is any limit on my xubuntu's outgoing Internet connections? 

2.) Is there any setting that I would have to change to allow more connections, like the way I had to patch the TCPIP.sys file in windows?  

3.) In windows I had installed a TCP/IP optimizer to adjust my computer to match my maximum download speed (in kb/s), and to optimize it to the new setting. Now is there a similar application needed in xubuntu/ubuntu to optimize my maximum download speeds (in kb/s) that my T1 cable connection offers?

4.) Are the settings in µTorrent able to be set when using wine? In Preferences... like Network Options, Advanced Options? Basically can I set µTorrent in the exact way that is in this guide: [http://forum.utorrent.com/viewtopic.php?id=3912&p=1](http://forum.utorrent.com/viewtopic.php?id=3912&p=1) while using µTorrent in wine?

5.) And my last question is this: Can anyone suggest a Linux bit torrent client that can be optimized in the way I have described, or even optimized better for working on a Linux system like the one I use, xubuntu Feisty?

Well, thanks to anyone that can help me with any of these questions.

---

### Post by blazercist on 2007-05-02
why would you use a non-native torrent client when there are so many native linux torrent clients that work perfectly fine without wine. azureus is my favorite but there are many many others.

My suggestion is to forget the "TCP" tweaks that you are accustomed to in windows they are not necessary in either windows or linux, especially linux.  The TCP tweaks only yeild a 5% difference on systems that are improperly configured to begin with and don't always manifest themselves as most of the time with a broadband connection you cannot download at max speed because people cant upload that fast.

---

### Post by felker2 on 2007-05-02
Ad 5: 

If you like to tweak (and it certainly looks like that), use Azureus: it has an enormous amount of parameters and features. And Azureus achieves fantastich results, *if* you have got enough memory.

Otherwise, try ktorrent 2.1.4 (not the 2.1 version on 7.04).

---

### Post by crimesaucer on 2007-05-02
Uhh...Azureus was so slow compared to utorrent with "the proper settings that you don't think are necessary", to the point of a single Azureus torrent taking a day and a half to download, compared to my utorrent taking an hour and a half. 

EDIT- after seeing felker2's post- I have to admit that was with very little optimization on the Azureus, so it might be an unfair comparison to a fully tweaked µTorrent. Maybe I'll give it a second try sometime and tweak with it more.

(and that was with the same exact torrent file, same good site, with the same amount of traffic in the same two day stretch of time of comparing the two, and with the same seeders. I also redid this test with other torrents to see if it was the same and I couldn't believe the difference. Not to mention that I always read people's descriptions of their download speeds and am amazed at how slow they usually are.)

And I don't like Azureus much compared to µTorrent. 

...Now with that out of the way...

I would totally, much rather use any good Linux bit torrent client if it can be optimized correctly, to be faster then just default regular settings. To be faster then my µTorrent on Windows Xp, which is what this post was about.

I mean, I can download 4 large files instead of 1 or 2, with peak speeds near 800kb/s (sometimes a lot more, and for large chunks of the files) and usually it's a steady 400-600 for all of them if they are a good torrent, 200-300 if it's slow.

I know it's fast because I read areas where people discuss there download speed (and yes it is relative to the Internet connection). 

For me, I can download and upload (seeded 100%) 6 large SLOW torrents in the time it used to take for 1 average torrent in default Azureus, just to download.  

In fact I would rather use any Linux bit torrent other than Azureus, and I don't want to use wine if I don't have too.

And I am trying to learn more about the settings available in Linux rather then "forget(ing) the "TCP" tweaks". Because I know on my system, that the correct settings for most ANYTHING, make it work better then just default settings and forgetting about something.

I may be no computer genius, but I can tell when something feels better, works better, or just is better, and I'm not scared to put effort into my computer to make it better. That's why I use xubuntu. So I can customize and optimize things to make my computer better, and because the ubuntu forums offer intelligent ways to fix things on your own with help from experts that give easy to understand directions and explanations. 

So I'm sorry to rant, and I don't mean to be negative, but I just was asking for 5 expert answers and the explanations of those 5 questions.

---

### Post by crimesaucer on 2007-05-02
> **felker2 said:**
> Ad 5: 

If you like to tweak (and it certainly looks like that), use Azureus: it has an enormous amount of parameters and features. And Azureus achieves fantastich results, *if* you have got enough memory.

Otherwise, try ktorrent 2.1.4 (not the 2.1 version on 7.04).

And thank you felker for your answers to #5, I have heard a lot of mixed views on Azureus from µTorrent users. I guess I was just hoping for a bit torrent client similar to µTorrent that can be set to download and upload very fast for my T1 cable hook up, and then modified easily when I move, so as to adjust to a slower connection. I like things precise, so it doesn't get bottlenecked, and so it flows perfectly for the maximum download speeds.

---

### Post by brharri1 on 2007-05-02
For me I spent much more time tweaking Azureus than I did utorrent, and utorrent is much faster. I have no clue why. I did not like azureus much because of the slower speed, the enormous memory usage, and the fact that I constantly had java problems with it.

---

### Post by crimesaucer on 2007-05-02
Thanks for the info, and did you use µTorrent in wine? And if so, is µTorrent in wine able to use the µTorrent's Advanced Options and settings (like in question #4). Like the net.max_halfopen?

---

### Post by kelvin spratt on 2007-05-02
crimesaucer azureus is far superior to utorrent infact so are most apllications when set up correctly
i've used them all you are limited by your conection and by running the correct upload download ratio 
have your upload settings to high you kill the download speed theirare a lot of myths about uttorent
but one thing is true it is not a trustworthy client any more since selling out what information are they collecting about you i would recommend as above ktorrent as above download from there site

---

### Post by crimesaucer on 2007-05-02
This guide covers everything to an exact science: [http://forum.utorrent.com/viewtopic.php?id=3912&p=1](http://forum.utorrent.com/viewtopic.php?id=3912&p=1)

It was stickied in the µTorrent forum for over a year, and on digg.com and slashdot, most people agreed that it was correct, and made µTorrent very, very, fast, and faster then a fully optimized Azureus.

I would argue the statement about Azureus being better then µTorrent. I've been a happy µTorrent user for over a year now, I know how to properly set all of my settings correctly both in the client and using patches and a TCP/IP optimizer. I know my ratios, if you want, you can check them in that guide that I linked.

But this isn't a post about people's favorite, but more of a post to answer questions #1, #2, and #3. And also the wine question #4.

Question #5, about Linux bit torrent clients, is more about advanced options and hopefully answered with a link to preferred clients and their guides for total optimization of all the settings.

Thanks though.


P.S.- I still use the stable beta version right before they "sold out to the man" because I was happy with it and, well, I didn't want things to change. So I don't have the one that people were scared about. 

Also, with Protocol Encryption enabled, and no address listed, and no reason to fear, since I don't download torrents that would get me into trouble, I'm not too worried about it and haven't received any complaint letters from my ISP.

---

### Post by crimesaucer on 2007-05-02
I'm sorry to *bump* my thread, but I'm really hoping someone can explain questions #1, #2, and #3. I can figure out the others on my own.

---

### Post by zvacet on 2007-05-02
If I understood correctly TCP/IP Optimizer is exe file,so if you can run utorrent with wine maybe will be possible to run TCP/IP Optimizer as well.I don´t know I´m not an expert and this is just sugestion.

---

### Post by crimesaucer on 2007-05-02
My hope is to learn if I can open my Linux xubuntu up to as many connections as I had patched in my Windows Xp, or find out if it's already open to that many (50 in the TCPIP.sys after I had patched it), and then hopefully add a Linux program that is similar to the TCP/IP optimizer to optimize my ISP's T1 LAN, and then use a native Linux bit torrent client that I can set to the best possible settings, using advanced settings, similar to µTorrent and that guide I have linked earlier.

But thanks, I'll still look into the wine compatibility issues of a TCP/IP optimizer, but if I'm going to go through all of that, then it would be as easy to just use my dual booted Xp, where everything is already done.

I'm just wondering if there are already applications built into Linux, or settings that I can do in terminal or elsewhere, that are like the TCP/IP optimizer, and if there are restrictions like the TCPIP.sys file in Windows that limits the connections to 10.

And yes, I know this isn't Windows so that's why I'm asking if these sort of tweaks for the TCPIP were only needed in Windows and not Linux, or are there some other tweaks needed in Linux that make using a torrent that much faster.

---

### Post by crimesaucer on 2007-05-13
So can anybody tell me about the ports for bit torrent on ubuntu.

or answer any of these three questions:

1.) If there is any limit on my xubuntu's outgoing Internet connections?

2.) Is there any setting that I would have to change to allow more connections, like the way I had to patch the TCPIP.sys file in windows?

3.) In windows I had installed a TCP/IP optimizer to adjust my computer to match my maximum download speed (in kb/s), and to optimize it to the new setting. Now is there a similar application needed in xubuntu/ubuntu to optimize my maximum download speeds (in kb/s) that my T1 cable connection offers?

---

### Post by entropic_existence on 2007-08-16
In case you come back to this thread my advice is don't use WINE when native is available because you won't get the same results with the program as you had running under windows. You'll use far more system resources than you need because you are running it through an emulator and this will impact download speeds.

I personally use ktorrent for my torrents and have found it to be much better than Azureus, although some of that may just be because I hate running a Java app for this sort of thing, the footprint always seems much bigger. With ktorrent there are several options for udnp to do automatic port forwarding and there is an option that increases the number of sources you can download from simultaneously. 

As for tweaking of any settings to increase the number of connections, etc I really have no idea. Most of the tweaking I do for my internet connection I do on my router end and not on my linux box.

---

### Post by crimesaucer on 2007-08-16
Well, I installed the Linux bit torrent client called "Deluge", and I set the settings to the exact same as my µTorrent settings and gave it a test.

Using Deluge to download a large torrent, it gave me top speeds of 324KiB/s and an average speed of 180KiB/s-260KiB/s...(and I use Firestarter as my firewall if that matters at all?).

Using µTorrent 1.6 build 474, on my Windows partition, I was able to get top speeds of the same exact torrent all the way to 750kbps...and the average speed was 350kbps-500kbps.


...Now, I like Deluge, and I think it was very easy to use, and it worked good, I just think it could be made to be faster if I knew what to do. I'm sure there is a way to open up more ports, and make it faster...I was wondering if this would make it faster: [http://ubuntuforums.org/showthread.php?t=331161&highlight=Torrent+ports](http://ubuntuforums.org/showthread.php?t=331161&highlight=Torrent+ports)


...or if I should configure something else. It would be nice to not have to use my Windows partition but for now I'll stick with µTorrent on xp....(I guess it doesn't matter because I usually run a torrent when I'm asleep.)

---

### Post by Hallvor on 2007-08-16
You have to open the ports in Iptables. Firestarter is basically a gui for Iptables, and the howto you pointed to is opening up ports using the command line.  Not having open ports (being firewalled) will have a drastic negative effect on download speed. There is no need for any other tweaks, like the hack in Windows XP to allow more connections.

All in all, p2p works much better (both upload and download) for me in Ubuntu than under Windows. Maximim speed for me has been some 1500 kB/s in Ubuntu using BitTornado, but only 300-400 kB/s in Windows. I can also upload faster. And I don`t have to reboot nearly as often. :)

---

### Post by crimesaucer on 2007-08-16
> **Hallvor said:**
> You have to open the ports in Iptables. Firestarter is basically a gui for Iptables, and the howto you pointed to is opening up ports using the command line.  Not having open ports (being firewalled) will have a drastic negative effect on download speed. There is no need for any other tweaks, like the hack in Windows XP to allow more connections.

All in all, p2p works much better (both upload and download) for me in Ubuntu than under Windows. Maximim speed for me has been some 1500 kB/s in Ubuntu using BitTornado, but only 300-400 kB/s in Windows. I can also upload faster. And I don`t have to reboot nearly as often. :)

Cool, thank you for the info...should I use different port numbers, rather than the default torrent ports of: 6881-6889?

---

### Post by Hallvor on 2007-08-16
> **crimesaucer said:**
> Cool, thank you for the info...should I use different port numbers, rather than the default torrent ports of: 6881-6889?

Yes, that may be a good idea, but it may also work just fine. Some ISPs give traffic on known standard p2p ports very low priority for some strange reason.. :)

---

### Post by crimesaucer on 2007-08-16
> **Hallvor said:**
> Yes, that may be a good idea, but it may also work just fine. Some ISPs give traffic on known standard p2p ports very low priority for some strange reason.. :)

Is there a suggested port number(s) to replace them with, or will any random port number be cool? And should I open them up with that command, and then close them afterwards for security...or is it ok to leave it open?

---

### Post by Hallvor on 2007-08-16
> **crimesaucer said:**
> Is there a suggested port number(s) to replace them with, or will any random port number be cool? And should I open them up with that command, and then close them afterwards for security...or is it ok to leave it open?

It should be above 10000 and avoid other standard p2p ports, so just pick one. 10001 should do just fine, 10002, etc.

I am not a security expert, but I keep three open ports on my computer 24/7 since I run p2p applications 24/7. It is a little safer to close them afterwards, but I can`t give you a good answer as to how much (or little) an open port or two compromises your security.

---

### Post by crimesaucer on 2007-08-16
Thank you for all of your help, hopefully this will bring me one step closer to a Windows free computer....all I need is a new music device that can work with Linux, like the Cowon mp3 player.

Thanks again for the info,
-c.

---

### Post by Hallvor on 2007-08-17
Glad to help, and good luck.

---

