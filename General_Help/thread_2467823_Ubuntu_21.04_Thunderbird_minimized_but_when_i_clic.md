---
title: "Ubuntu 21.04 Thunderbird minimized but when i click on the icon it wont come back up"
date: 2021-10-08
forum: General Help
---

### Post by Kusho on 2021-10-08
I'm hoping this gets fixed in 21.10 but for some reason little dots appear next to the Thunderbird icon.  It seems that when there are 4 dots there and I minimize thunderbird...  when I want to use it again I will click the icon but nothing will happen.  All the other icons will launch their respective program but Thunderbird doesnt do anything when I click on it.  Sometimes if I click repeatedly it will come back open, but most likely it will just pull up Firefox or my File Folder.  When this happens the only way I can get Thunderbird to open back up is to reboot my system.  Any thoughts how to fix this or programmers can you fix it for Ubuntu 21.10.

Thanks

---

### Post by DuckHook on 2021-10-08
I have a few apps that behave in similar fashion on Focal (20.04). Have you tried cycling through your apps with <Alt> <Tab>?

BTW, it is rarely necessary to go all the way to a reboot. You can kill the T-bird process with the *kill* command. First, find the process using any of *top* or *ps*, then:```
kill -9 PID
```&#8230;where PID is the process ID identified from *top* or *ps*.

At most, a logout/login cycle should clear things up.

To chase down the problem, look at your logs. Also, try invoking T-Bird from the command line, which should allow you to see what is happening behind the scenes and give you some clues about what the possible problem might be.

---

### Post by Kusho on 2021-10-09
<Alt> <TAB> does nothing. <CTL> <TAB> cycles thru my different tab's in Firefox.  but <ALT> <TAB> doesnt do anything.

Tried both top and ps but couldnt make sense of what I was seeing.  Not enough to run kill -9 PID

I'll try just loging out then back in.  that would be faster than rebooting.
Did I mention I am still a newbe to Ubuntu.  I can run terminal commands if someone tells me what to type, but I dont have any of them memorized.  I'm mainly running Ubuntu on this pc because it shipped with Windows 10 but somewhere in there with the updates it quit working.  Now it just crashes if I run Windows 10.  I have tried reinstalling but as soon as it updates it becomes unusable.  I have been dual booting with Ubuntu but I dont see anymore why I am wasting all that HD space with Windows...  so with Ubuntu 21.10 I am going to delete all partitions and only install Ubuntu.  It has been nice to attempt to get used to Ubuntu but like I said I am not good at bash.

---

### Post by DuckHook on 2021-10-09
> **Kusho said:**
> <Alt> <TAB> does nothing. <CTL> <TAB> cycles thru my different tab's in Firefox.  but <ALT> <TAB> doesnt do anything.
Are you running Ubuntu and not one of its flavours? If vanilla Ubuntu, a sucession of <Alt> <Tab>s should cycle you through each of the apps you have up and running on your desktop. This will sometimes bring back up an app not accessible from the dock.
> Tried both top and ps but couldnt make sense of what I was seeing.  Not enough to run kill -9 PID
You need to research the proper use of *top* and *ps*. It's a topic that is too broad for a forum thread. My use of ps while running T-bird shows this:
```
duckhook@Zeus:~$ ps -ef | grep -i [t]hunderbird
duckhook   11795    7915  0 10:38 ?        00:02:00 /usr/lib/thunderbird/thunderbird
```
&#8230;so, in my case, the process ID of thunderbird on this occasion is 11795 (PIDs change on every login). Therefore:
```
duckhook@Zeus:~$ kill -9 11795
```&#8230;should successfully kill this instance of the app without the need to logout or reboot.
> I'll try just loging out then back in.  that would be faster than rebooting.
But killing the process would be faster still, and you wouldn't have to close down your other apps to do it.
> Did I mention I am still a newbe to Ubuntu.
No you didn't and I assumed you were a veteran, given the length of your forum membership.
> I can run terminal commands if someone tells me what to type, but I dont have any of them memorized.
A mistaken assumption persists that Linux fluency involves memorizing commands. I consider myself a power user, but I actually memorize very few commands. Progressively greying brain cells don't help me either. I use a combination of man pages and web searches to refamiliarize myself with the commands that I need on the few occasions that I need them. It does help to have a rough idea of the underlying use and logic of each command, but that is more to assess whether the advice I get from a web search passes basic sanity checks. Otherwise, I am in the same boat you are when using commands.
> It has been nice to attempt to get used to Ubuntu but like I said I am not good at bash.
I know of very few people who are "good at bash". Those forum gurus who are truly good at it elicit something approaching awe from me. It took me years to get to a level of comfort with the command line, but I am no longer in terror of it and can now make use of its power and flexibility.

I encourage you to keep at it. It will doubtfully ever be "second nature" to you, but it can become a supremely powerful tool that you can find your way around with a little bit of web searching and referencing. If you want a good intro/reference e-book on the command line, click on the link in my sig: *A Great CLI Guide*

---

### Post by Kusho on 2021-10-09
> **DuckHook said:**
> Are you running Ubuntu and not one of its flavours? If vanilla Ubuntu, a sucession of <Alt> <Tab>s should cycle you through each of the apps you have up and running on your desktop. This will sometimes bring back up an app not accessible from the dock.



Ubuntu 21.04 regular release.  Nothing special.  When I click Alt the File menu pops up or dissapears.  but when I hold alt and hit TAB nothing happens.  Also tried holding TAB and pressing ALT.  again nothing.  I even tried both ALT keys.  I will try to see why that is, but no it's just Ubuntu.  nothing else.

[https://askubuntu.com/questions/1349544/alttab-stops-working-after-a-while-in-ubuntu-21-04](https://askubuntu.com/questions/1349544/alttab-stops-working-after-a-while-in-ubuntu-21-04)

Did what this post said and ALT - TAB works again.
Stil not a fix for Thunerbird but should be good this way.  Curious if there is any reason not to use XORG instead of Wayland.

---

### Post by Kusho on 2021-10-09
[https://askubuntu.com/questions/1349544/alttab-stops-working-after-a-while-in-ubuntu-21-04](https://askubuntu.com/questions/1349544/alttab-stops-working-after-a-while-in-ubuntu-21-04)

---

### Post by DuckHook on 2021-10-10
> **Kusho said:**
> Ubuntu 21.04 regular release.  Nothing special.  When I click Alt the File menu pops up or dissapears.  but when I hold alt and hit TAB nothing happens.  Also tried holding TAB and pressing ALT.  again nothing.  I even tried both ALT keys.  I will try to see why that is, but no it's just Ubuntu.  nothing else.

[https://askubuntu.com/questions/1349544/alttab-stops-working-after-a-while-in-ubuntu-21-04](https://askubuntu.com/questions/1349544/alttab-stops-working-after-a-while-in-ubuntu-21-04)

Did what this post said and ALT - TAB works again.
Stil not a fix for Thunerbird but should be good this way.  Curious if there is any reason not to use XORG instead of Wayland.

You are far more resourceful than you let on. ;)

Congrats on your successful research. I'm afraid I can't really help much with your specific issue. Note that I am running Focal and not 21.04, so am not that familiar with it. Bugs and reversions are more common in standard releases, so I would recommend sticking to LTS. You may have no problem with T-Bird running in Focal, in which case, you may wish to consider installing that instead. I would then recommend that you stick with LTS releases henceforth. The next LTS (22.04) is just a few months away.

Re Xorg vs Wayland: Xorg is no longer being actively developed, although I believe that it is still being maintained. However, any maintenance would take the form of security fixes only (no bug fixes, no new features, no accommodation of new HW), so no matter how you slice it, Xorg is living on borrowed time. Ultimately, the whole Ubuntu ecosystem will have to move on to Wayland.

I don't think that continuing to use Xorg is a big concern (yet). Just be aware that it was never designed as a secure display server, so you are at more risk than Wayland, but it's debatable if this is a significant exposure for the typical user.

---

