---
title: "Newbie to Linux from Windows 7 - external monitor display issues"
date: 2017-11-22
forum: General Help
---

### Post by frappe792 on 2017-11-22
Hi all,

I have decided to make the jump into Linux because I have always been intrigued reading so many wonderful things about it. I have come from Windows 7 which I found to be the best yet but I took the plunge anyway. 

OK so I installed the latest version 17.10. Installation and initial setup went well I am operating and using this Toshiba laptop for posting in this forum.

With Windows 7 I had a habit of keeping the laptop lid closed and connected to either HDMI or both HDMI and VGA at the same time. Has always worked perfectly on Windows 7.  could do whatever I wanted and at the end of a session I would use the shortcut to put the PC to sleep. Come back press any button and boom everything restored back to normal.

Right now as I am typing, the laptop lid is closed and I have had to setup the monitors in display manually and then I have applied those settings. Shutting down, rebooting, unplugging seems to do whatever it then wants to do and I have to go through the same steps again manually to setup the monitors.

What is going on? On windows 7 I would have to go through this setup once only and it would remember that every-time. I haven't installed any graphics drivers or anything since installing Ubuntu because I have read I shouldn't have to, but it's honestly quite frustrating on day 1 where I can't even get the operating system to detect and remember monitor configurations.

I know it's going to be a steep learning curve, but that's learning curve is much harder trying to do from a small screen. An uncomfortable first experience.

What I would like is this

Monitor A = Laptop Screen
Monitor B = HDMI
Monitor C = VGA


If A lid is closed = screen off always
If B is plugged in, then display B
If C is plugged in, then display C
If B & C are plugged in, then display both B & C in last saved position
if A lid is open, B is plugged in, C is unplugged  = display A & B in last saved position
if A lid is open, B is plugged in, C is plugged in  = display B & C in last saved position

basically any connection/disconnection of a display device or laptop lid opening or closing, it should trigger an event to run the rules above.

But this is not happening. If anyone can help, I would appreciate it very much.

---

### Post by frappe792 on 2017-11-23
Hi all,

I am wondering why I haven't received any guidance, have I posted this in the wrong section?

---

### Post by Autodave on 2017-11-23
You are in the correct section: no problem there. I am just not sure how many people here have ever even thought of what you want to do, let alone done it. I have played with computers for over 30 years and never attempted more than 2 monitors at one time.

Keep in mind too, that everyone here is a volunteer: no paid employees. And, it is a holiday when a lot of folks are traveling or having company.

---

### Post by frappe792 on 2017-11-23
> **Autodave said:**
> never attempted more than 2 monitors at one time.

Sorry, I am not trying to be pushy at all. Before I downloaded and installed Ubuntu I was aware that it was a community driven OS. I knew there would be a learning curve and reading all over the web I was assured there would be plenty of help in these forums - I can see alot of members online at once which is a great thing. 

I have not asked for more 2 screens at a time, but either 1 or 2 screens on and based on the various configurations above. My immediate thinking is that if my Windows 7 could do this out of the box, then it probably wouldn't be too much mucking around to tweak for that in Ubuntu.

BTW what holiday are you talking about?

---

### Post by mastablasta on 2017-11-24
> **frappe792 said:**
> 
BTW what holiday are you talking about?

probably Thanksgiving in USA.

Anyway, i tried to smell for your GPU chip, but came up with nothing :)

Have a look at this: [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

we need to know the GPU.

windows uses windows drivers, linux uses linux driver. if your GPU manufacturer made poor drivers (or maybe not even made any at all), then you get what you are getting. it has nothing to do with the OS.

For example i have Fujitsu at work loaded with Win10. the OS itself is not bad, but obviously the Fujitsu manufacturer made bad Win 10 drivers. so i am getting similar issues than you when i dock the laptop after having presentation in conference room for example - screens get all mixed up. the windows Intel drivers app has even a save option but is happily ignored by OS and intel app itself, and simply ignores the existence of second monitor. but enough about my Win 10 issues.


a short workaround (if you just need to set it all up again) would be to create a short script and just run it instead of doing same setup routine over and over. the ideal would be that manufacturer made drivers properly and provided a setup utility (if necessary), but as you can see this is not always the case. so we often resort to solutions that are not ideal but they work just fine.

---

### Post by HermanAB on 2017-11-24
Note that Linux has a zoo of different desktop systems.  In my experience, KDE handles external monitors better than any other, so that is the one I use at work, where I need the laptop to work in various conference rooms with different projectors and screens without hassle and KDE does that admirably.  With any other DE, I always have to configure things manually, which quickly becomes a PITA.

---

### Post by frappe792 on 2017-11-24
> **HermanAB said:**
> KDE does that admirably


Hey thanks for that, I'd be keen to try it out.

Can you point me in the right direction so I can try out the kde version. I don't truly understand it, do I have to wipe my disk and install kubuntu operating system from scratch?

HI Mastablasta, 

thanks for your response

lspci | grep VGA returns

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)






I'd be keen to try the KDE version as per post by Herman, if that fails for me maybe a script will have to do.

Ok well here goes, I have been able to follow some steps I found online and now I have Kubuntu running (without re-installing another operating system haha)

Herman you are spot on, KDE does do that admirably - instant detection of which monitors are connected and does exactly what I want (like windows 7 did)

But I have to say I prefer the interface of the gnome desktop... looks much better. Why does linux have to frustrate the hell out of me, why can't the gnome version do what kde does when it comes to monitors. Clearly it's an operating system issue and absolutely nothing to do with my drivers!

...continued, I won't bother going back to gnome, kubuntu has a million more settings built in to tweak the appearance which I have done. So I will stick with that.
A moderator may close this topic if required. I wouldn't call it a solution however, more of a work around. I still think that ubuntu gnome 17.10 should be able to do that out of the box, who wouldn't want that?

---

### Post by HermanAB on 2017-11-24
The developers of the different DEs have different priorities.   I usually have two or three different DEs installed on my machines and select the one I want at login.  To me, KDE is best for business use when I have to run between meetings and do presentations.  For engineering use, I prefer XFCE, since it uses less resources and therefore my tools run faster.  I tried Gnome many times in the past and it still feels immature, so I don't use it much, while IceWM, Blackbox, WM and the like are too simple and painful to use.

So, to each his own.  Linux is about choice!

---

### Post by frappe792 on 2017-11-25
> **HermanAB said:**
> 

So, to each his own.  Linux is about choice!

I can see that, I guess it's a great thing :)

---

### Post by mastablasta on 2017-11-27
> **frappe792 said:**
> ...continued, I won't bother going back to gnome, kubuntu has a million more settings built in to tweak the appearance which I have done. So I will stick with that.
A moderator may close this topic if required. I wouldn't call it a solution however, more of a work around. I still think that ubuntu gnome 17.10 should be able to do that out of the box, who wouldn't want that?


there are different philosophies behind the desktops. KDE has settings in GUI for example. for that reason all their applications have many settings available in GUI. these can be helpful to "power users" but can overwhelm those that just want to use the PC and have a desire for simplicity (want things present and not bother with extra setting up). in other words some users can be overwhelmed with all the options. 

on the other hand Gnome aims for simplicity, ease of use. so while a Gnome distro has same features available many are hidden or not accessible via GUI. this enables the users to just do the task they want to do without fiddling with options. gnome is also made with one monitor in mind. this seems quite obvious to me. it was different with the old Gnome 2 (now Mate). Gnome 3 came out when touch, mobile and convergence was all the rage. hence the big icons and full screen menues. KDE on the other hand stayed focused on traditional desktop but at the same time they also developed a touch version.

a good comparison is k3b and brasero app. one complex with many options laid out immediately, the other does what is expected with minimum extras instantly visible.

desktop is just one of the OS layers. and in linux it is easy to change it. KDE then for example has 2 menues the kick off and the classic one: [https://forum.kde.org/viewtopic.php?f=289&t=131179](https://forum.kde.org/viewtopic.php?f=289&t=131179)

---

### Post by frappe792 on 2017-11-27
Thank you mastablasta, That's very good information for a newbie. It's really helpful :)

---

