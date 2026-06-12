---
title: "FireFox is always closing using Breezy Badger"
date: 2007-05-18
forum: General Help
---

### Post by cjax1 on 2007-05-18
Hi.

I just dug out my old Toshiba Satellite 1555CDS laptop. I had to replace the hard drive. It used to have a 4 Gb drive. Now it has an 80Gb drive. It used to dual boot Win98SE and Breezy. The Win98 configuration CD thinks it's on the wrong machine now and won't install. Doesn't matter. It is now an Ubuntu only machine. Love it. But because it only has 128 Mb memory, (evidently that's the maximum amount that can be installed, besides, I'm not about to spend any more money on that old thing) I unfortunately can't run any newer Ubuntu version than Breezy on that thing. I can't even install Xubuntu because it loads at such a low resolution I can't even see some of the buttons at the bottom of the windows. Every thing's too big. At least I can install Breezy. After it's installed I have to jump through hoops to get the monitor's native 800X600 resolution. I'm just trying to save this old laptop and hopefully use it a while longer.

Anyway, I've never had trouble with FireFox on Breezy on that machine until now. The last time I used it was last summer before the HD crash. Now FireFox has a nasty habit of closing. One example is when I go to my Yahoo page it loads every time. When I click on the Mail link FireFox closes immediately. Once in a while it works but usually doesn't. It's not just with Yahoo, it's anytime I surf the web for anything. The first page always loads but when I click any links, presto, it's closed. It seems to work a little better if I open links up in new windows but not all the time. For the most part I just can't use the web on that machine. Last night I cleared all the cookies and everything else in FireFox. Then I could not even sign back into my Yahoo. It keeps closing. Tonight it's a little better but not much. At least I got signed in to Yahoo. So I had this bright idea. I installed the latest FireFox 2.0.0.3 using a script I found on this forum a while back hoping that would solve the problem. But I still have the same problem. It's no better and no worse. So, maybe it's not FireFox after all. So far I have had no other problems with the OS. I did reinstall once already and did a disc check. Didn't help at all.

I hope someone can help me fix this. I really want to keep using Ubuntu on that old thing. Puppy Linux will work. The latest Puppy version supports those cards. Even in a live session I can get wireless going. I may have to go with that. Mepis will install but it's slow on that thing (I forget what version) and it evidently doesn't support pcmcia wireless cards even though it has the drivers installed for that card out of the box. I installed Symphony 2005/2006 but I can not find how to install any wireless anything. Feather Linux and DSL doesn't work.

Please help. I need Ubuntu on that thing or I may experience withdrawal symptoms. :) I can't imagine it's because of the new HD. Maybe it's because I can no longer get updates for Breezy? Also is there a way to update Breezy at all? Should I learn how to install a newer kernel version?

Thanks anyone for considering my question. Or questions.

---

### Post by roffy on 2007-05-18
I have been having probelms with Firefox doing that with Feisty and on numerous XP machines. It's started a couple updates ago, not quite sure why though.

---

### Post by yopnono on 2007-05-18
Try to disable all of your add-ons for the firefox.

---

### Post by cjax1 on 2007-05-18
Thanks for the reply. The only add-ons in FireFox 2.0.0.3 are DOM Inspector and Talkback which came with 2.0.0.3. I disabled both to no avail. I've also tried disabling Java and Java script.

When I reopen FF it asks me if I want to start a new session or restore session. I went to Tools - Error Console. Here's just a few of the errors listed if this make any sense.

[COLOR="DarkRed"]Warning: Error in parsing value for property 'font'.  Declaration dropped.
Source File: [http://my.yahoo.com/](http://my.yahoo.com/)
Line: 17

Warning: Error in parsing value for property 'font'.  Declaration dropped.
Source File: [http://my.yahoo.com/](http://my.yahoo.com/)
Line: 19

Warning: Expected color but found '#'.  Error in parsing value for property 'background-color'.  Declaration dropped.
Source File: [http://my.yahoo.com/](http://my.yahoo.com/)
Line: 60

Warning: Error in parsing value for property 'cursor'.  Declaration dropped
Line: 3

Warning: Error in parsing value for property 'font'.  Declaration dropped.
Line: 5

Warning: Error in parsing value for property 'cursor'.  Declaration dropped.
Line: 15

Warning: Error in parsing value for property 'cursor'.  Declaration dropped.
Line: 50[/COLOR]

I have FF 2.0.0.3 on this newer machine in XP and 6.0.6 Dapper Drake and when I check Error console in both it has a long list of errors too but FF is working normally.

Like I mentioned above I'm kind of doubting it is FireFox since the original version that came with Breezy Badger did the same thing. Could it be that this was a known bug in Breezy but Breezy is no longer supported and I can't get updates for it now to fix it. It's too bad Dapper won't run on that old machine. If anyone has any clue what this might be and how to fix it or update it I would greatly appreciate it.

Thanks.

---

### Post by cjax1 on 2007-05-21
I just wanted to bring this up once more. I still haven't been able to figure out what's wrong. Are there any system files that I could modify? I came across one suggestion by someone saying firefox was crashing on pages with flash content to add the line "export XLIB_SKIP_ARGB_VISUALS=1" (without quotes) to /usr/lib'mozilla-firefox/firefox. Didn't help. I also found a similar file at /usr/bin/firefox and tried adding that line to it. Didn't help. Just so you know I have no clue how those files work and how to edit them. All I know is someone said add a line and I tried it and it didn't work. So I went back and deleted that line and re-saved the file.

I'm going to find out how to uninstall flash and try it then. But I'm pretty sure it was crashing even before flash was installed.

Besides firefox crashes even on pages with no flash content. This is driving me crazy. I have had Breezy on that laptop before, I installed Breezy a few times because I was always trying different distros and didn't have much room on the old 4Gb drive dual booting with Win98. I always came back to Breezy. I don't recall ever having this problem before with the default Breezy install. But then I usually downloaded and installed the system updates fairly soon after the install but they don't seem to be available anymore. The only difference now is the laptop has a brand new 80 Gb hard drive. I am dual booting now with Puppy. Puppy works great on that old machine, but it's Puppy. Nothing against Puppy but by design it's not as polished as Ubuntu. But I guess that's by design in order to keep Puppy very small.

I want very much to keep Ubuntu on that machine. All I use it for mostly is to surf the web and check email. And to experiment with now and then. If Puppy was the only thing that ran on that old thing then fine but I know Breezy runs good on it, I just need to fix the problem with FireFox crashing.

Please if anyone can offer any suggestions on any thing to edit or if there may be some other part of the system that needs an update to address this issue (and how to do it since Ubuntu evidently quit putting out updates for Breezy :( ) I'd really appreciate it.

Thanks again.

---

### Post by yopnono on 2007-05-21
1, Create a new profile for firefox.
2, Download the official firefox from mozilla.

---

### Post by cjax1 on 2007-05-22
Thanks yopnono for your replies. Sorry it took so long to get back. I tried a new profile like you suggested but the problem still persisted. I never knew about creating a new profile. I see where that could eliminate any possible causes with any add-ons or preferences I had saved before. Plus I was reading about it on the Mozilla web site.

However, it might be something with Flashplayer after all. I started searching more stuff and poking around and I was in the /home/.mozilla/plugins directory and there was two files that had to do with flash, flashplayer.xpt and libflashplayer.so.

I sent them to the trash. Now so far Firefox is working. Flash isn't but Firefox is. So far. It hasn't crashed yet. Before, I couldn't usually get past the first one or two pages. 4 or 5 if I was real lucky.

I'll have to look into reinstalling flash later when I'm more awake tomorrow. I'm going to keep using it a little while tonight to make sure it's OK but I think that's it. If it keeps working I'll reinstall flash and post back here tomorrow and hopefully mark this solved.


Thanks again.

---

### Post by cjax1 on 2007-05-22
Hi,

I am very very happy to say Firefox is working fine now. If there is a problem with installing flash I'll start a new thread.

Thanks.

---

### Post by chip-maker on 2008-01-25
I am new to linux/Ubuntu. I was having the same problem and found away around it.
If you're having a problem with fire fox closing unexpectedly what you can do is run a flash player application for example youtube. Click on any clip but don't use the serch option first. If you serch first it will quit and go back to desk top. Once the clip is playing go to Yahoo or any other site you want and go to work/or have fun.
Hope this helps.
I use an old computor Pentium 3 with 128 ram for net stuff. The machine is much faster and doesn't work so hard as when I had Xp. The open office is great and I am recomending Ubuntu to all my friends. Thanks so much to the providers.
Chuck

---

