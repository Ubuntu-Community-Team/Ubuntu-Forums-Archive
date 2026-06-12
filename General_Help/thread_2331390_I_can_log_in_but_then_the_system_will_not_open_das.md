---
title: "I can log in but then the system will not open dash or launcher"
date: 2016-07-21
forum: General Help
---

### Post by Tom_Carr on 2016-07-21
I tried to install slimjet on my ubuntu 16.04 box.  The install did not work.  I shut down and then restarted.  The login screen came up and I entered my password.  The desktop came up but I can not open the dash or launcher.  I can right click on the screen and get the menu that lets me open terminal, create document, change desktop background and so on.

This is a system that has been working fine for a month.

What should I do?

---

### Post by trevor35 on 2016-07-22
I have a similar problem having used 16.04 xenial/xerus without problems for a good while. My system now starts up with a blank page and a password panel. After acceptance of the pw the only facility is the ability to right click the page and view a panel with options of New Folder/New Document/Open Terminal/Sort desktop icons by name/Align Desktop icons. The open terminal option is the only one which seems to provide a pathway to further progress.  I did notice from the script, when running dist-upgrade, that there appeared to be conflict between the existing system and the upgrade. Is there a command which allows me to check/restore my system?

---

### Post by Tom_Carr on 2016-07-22
Over 200 people have looked at this thread and no one has posted anything other than trevor35 saying he has the same problem.  I will wait another day, and if no response will assume the system is hosed and re-install.   I would like to understand what happened so it doesn't happen again.

Trevor, did it happen to you right after installing something new?  If so what?

It happened to me after a bad install of slimjet, but I wonder if the problem already existed and slimjet not installing was just a symptom, then when I rebooted the full problem appeared?

I tried to install the 32 bit version of slimjet on a 64 bit version of ubuntu.  I wonder if that could have caused a problem?

I can get into settings by doing a right click/Change desktop background.  The appearance screen comes up and I can then switch to all settings and open any of the settings screens.  So I am limited to settings and terminal.

---

### Post by howefield on 2016-07-22
> **Tom_Carr said:**
> Over 200 people have looked at this thread and no one has posted anything other than trevor35 saying he has the same problem.  I will wait another day, and if no response will assume the system is hosed and re-install.   I would like to understand what happened so it doesn't happen again.

No, 200 people have not looked at your thread. Other than you, exactly 6 people have viewed it.

> Trevor, did it happen to you right after installing something new?  If so what?

trevor35 would be better off starting his own thread for his issue which appears to be quite different to yours except on a superficial level.

> It happened to me after a bad install of slimjet, but I wonder if the problem already existed and slimjet not installing was just a symptom, then when I rebooted the full problem appeared?

I tried to install the 32 bit version of slimjet on a 64 bit version of ubuntu.  I wonder if that could have caused a problem?

You probably had your reasons for doing that, despite the slimjet website recommending the 64 bit version for 64 Linux installations.

> I can get into settings by doing a right click/Change desktop background.  The appearance screen comes up and I can then switch to all settings and open any of the settings screens.  So I am limited to settings and terminal.

Have you tried purging the application.

---

### Post by Tom_Carr on 2016-07-22
> [COLOR=#000000]No, 200 people have not looked at your thread. Other than you, exactly 6 people have viewed it.[/COLOR]

Thanks [RIGHT]for the correction on that. I didn't understand. When I do "Quick Links/Find all my threads" it says "views 235".  How do I get the correct info?[/RIGHT]

> [COLOR=#000000]Have you tried purging the application.[/COLOR]

How do I do that?

---

### Post by howefield on 2016-07-22
> **Tom_Carr said:**
> Thanks for the correction on that. I didn't understand. When I do "Quick Links/Find all my threads" it says "views 235".  How do I get the correct info?

You don't, it is only the total views that you can see, which includes a multitude of various search spiders, bots and guests. You are now up to 10 forums members who have viewed your thread :) 

> How do I do that?

Well, you have access to a terminal so..

```
sudo apt purge nameofpackage
```

Although to be honest, I'd not think this will solve your issue it's worth a try.

Did you do anything else during that session, like updates ?

---

### Post by tomrbland on 2016-07-22
I literally just had this issue. Here is how I fixed it. I'll post the entire process but the TL;DR is: 
```
export DISPLAY=:0   
sudo dconf reset -f /org/compiz/
setsid unity
```

My situation was like this: 
Goes to login page. I can login. Then screen displays my background. Notifications pop up such as &#8220;connected to wi-fi&#8221;, and I have a mouse. I can right click and open terminal so I can open graphical programs etc.  But there is no launcher etc.

My first step was:
```
apt-get install --reinstall ubuntu-desktop
apt-get install unity
```

That didn&#8217;t help

Similar problems on google point towards graphics drivers. I&#8217;m pretty sure this isn&#8217;t the issue here considering graphical programs run.

Anyway the output of```
lspci | grep vga
``` is ```
Intel Corporation Broadwell-U Integrated Graphics (rev 09)
```


So I tried:
```
sudo apt-get install --reinstall xserver-xorg-video-intel
```

Then after some serious time on google I found a suggestion that did this:
```
export DISPLAY=:0   
sudo dconf reset -f /org/compiz/
setsid unity
```

I really don't know why that worked and what went wrong with my system. If anyone could explain to me what that set of commands does I'd be very greatful. Graphics in Ubuntu is not my strong point!

HTH

TL;DR: 
```
export DISPLAY=:0   
sudo dconf reset -f /org/compiz/
setsid unity
```

---

### Post by Tom_Carr on 2016-07-22
> export DISPLAY=:0   
sudo dconf reset -f /org/compiz/
setsid unity

When I got to 
> setsid unity
it responded
> setsid: failed to execute unity:  No such file or directory

Also I purged slimjet,  That didn't help

> [COLOR=#000000]You don't, it is only the total views that you can see, which includes a multitude of various search spiders, bots and guests. You are now up to 10 forums members who have viewed your thread [/COLOR]

If I can only see the total views, how do you know that only 10 forum members have read this?  Is that something only admins can see?

---

### Post by mc4man on 2016-07-22
> **Tom_Carr said:**
> I tried to install slimjet on my ubuntu 16.04 box.  The install did not work.  I shut down and then restarted.  The login screen came up and I entered my password.  The desktop came up but I can not open the dash or launcher. 

Just to clarify  - 
Does this mean you see the launcher but it doesn't respond or is it not there at all?

What does this show?
```
apt-cache policy unity compiz
```

Also - how did you try to install slimjet?, the Ubuntu/Debian package from here installed with no issue for me
[http://www.slimjet.com/en/dlpage.php](http://www.slimjet.com/en/dlpage.php)

---

### Post by Tom_Carr on 2016-07-22
The launcher is not there at all
Code:
> apt-cache policy unity compiz
It says 
> unity: installed(none)
compiz: installed:1:0.9.12.2+16 .....

It said more than that of course.  Normally I would copy and paste the terminal output but I can't do that now.  Tell me if I gave you enough info.

---

### Post by mc4man on 2016-07-22
For starters install unity
```
sudo apt install unity
```
Then reboot & see what happens, if still no go then try that previous command  set from tomrbland

---

### Post by howefield on 2016-07-23
> **Tom_Carr said:**
> Also I purged slimjet,  That didn't help

Yep, didn't think it would. I'd think installing slimjet was coincidental to you having the issue. But it was worth trying.

> If I can only see the total views, how do you know that only 10 forum members have read this?  Is that something only admins can see?

Afraid so.

PS. Just a general comment as you mentioned reinstalling earlier in the thread. If you do end up going that route, consider imaging your disk/partition with something like Clonezilla. That way anytime you hit a problem like this you have a choice of learning through fixing it or simply re-imaging and being back in business. Combined with having your Data folders (Documents, Music, Pictures, ect, ect) on a separate drive/partition so the image won't "age" so much is good insurance. YMMV.

---

### Post by Tom_Carr on 2016-07-23
> [COLOR=#000000]PS. Just a general comment as you mentioned reinstalling earlier in the thread. If you do end up going that route, consider imaging your disk/partition with something like Clonezilla. That way anytime you hit a problem like this you have a choice of learning through fixing it or simply re-imaging and being back in business.  [/COLOR]

I really want to learn to do that.  Should I start a seperate Clonezilla topic, or can we talk about it here?

By the way, it is working now, which I will describe in the next post.

---

### Post by Tom_Carr on 2016-07-23
It is working :p
Thanks everyone for your help.

I did

sudo apt install unity
rebooted, and it was not fixed
Then did
 
export DISPLAY=:0   
sudo dconf reset -f /org/compiz/
setsid unity
and it worked fine.

Thanks again.

---

### Post by QDR06VV9 on 2016-07-23
> **Tom_Carr said:**
> I really want to learn to do that.  Should I start a seperate Clonezilla topic, or can we talk about it here?

By the way, it is working now, which I will describe in the next post.

Yes Please start another thread for Clonezilla and glad to hear you got sorted out.
Kind Regards

---

### Post by Tom_Carr on 2016-07-23
I am marking this as solved.
How do you do a code tag?

---

### Post by wildmanne39 on 2016-07-23
Look in my signature and click on code tag and it will show you how.
Thanks

---

### Post by howefield on 2016-07-24
> **Tom_Carr said:**
> I really want to learn to do that.  Should I start a seperate Clonezilla topic, or can we talk about it here?

Yes, as runrickus suggests, a different topic generally means a different thread is best.

FWIW, there are a few ways to get Clonezilla up and running, you can burn the iso image to cd, install Clonezilla into a Live Ubuntu USB stick that has been created with persistance or my preference which is a dedicated USB stick, I use Clonezilla at least a couple of times a week, so a dedicated stick is worth having, the basic steps to create are...

1. Download Clonezilla zip file : currently I use clonezilla-live-20160627-xenial-amd64.zip
2. Unzip and extract all files to the USB drive.
3. Open a terminal and cd /media/hugh/Clonezilla/utils/linux/ && sudo bash makeboot.sh /dev/sdb1 

Your path will be different to the above and I can't stress enough that you want to ensure that you have the path to the USB correct, but once you have the USB stick made, I'd suggest watching a few youtube howto's to get the general idea of how it works and then any specific questions, post a new thread here in the forums.

---

