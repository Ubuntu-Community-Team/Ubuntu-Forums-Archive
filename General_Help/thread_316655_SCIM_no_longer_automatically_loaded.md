---
title: "SCIM no longer automatically loaded"
date: 2006-12-11
forum: General Help
---

### Post by rykel on 2006-12-11
Hi,

It used to be that I could just install Chinese Language Support in Dapper, and upon restarting the desktop, I would have a SCIM icon in the taskbar and an entry in the Session Manager Startup Programs list.

However, I CANNOT seem to do the same in Edgy.

Without SCIM in the list of startup programs in Edgy, I have no idea how to access the SCIM Pinyin input method, and this problem is frustrating.

Do you know how I can enable SCIM?

Thank you!

---

### Post by Sef on 2006-12-11
Put the cursor on the top bar, then right click, and select Add to Panel.  Go down to Utulities and select keyboard indicator.

---

### Post by rykel on 2006-12-11
> **Sef said:**
> Put the cursor on the top bar, then right click, and select Add to Panel.  Go down to Utulities and select keyboard indicator.

Hi,

Thanks, I tried that, but it is NOT what I want... the SCIM keyboard icon resides in the Notification Area, and in fact, if I recall correctly, there are TWO (2) keyboard icons placed there by SCIM... one icon for SCIM Setup, and another for choosing the input language.

Does everyone face this problem of the missing SCIM?

---

### Post by rykel on 2006-12-12
anyone?

or has all the old-time ubuntu SCIM users gone for christmas celebrations?  = )

---

### Post by inkbrush on 2006-12-24
Hey,
I am in the same place. I just switched from SuSE to Ubuntu. SCIM korean worked beautifully in SuSE, but I noticed that in Ubuntu, SCIM doesn't even load in the notification area tray. I tried messing with the SCIM setup in System-preferences, but no dice. I am guessing it's some kind of a bug.

---

### Post by rykel on 2006-12-24
> **inkbrush said:**
> Hey,
I am in the same place. I just switched from SuSE to Ubuntu. SCIM korean worked beautifully in SuSE, but I noticed that in Ubuntu, SCIM doesn't even load in the notification area tray. I tried messing with the SCIM setup in System-preferences, but no dice. I am guessing it's some kind of a bug.

Actually, in my humble opinion, I agree with you... SCIM just does not seem to work in Edgy Eft, AND nobody seems to know how to solve this problem around here... maybe the Chinese Ubuntu users are no longer hanging around this forum...

I believe that in order for SCIM to load itself in the Notification Area, you and I simply need to insert a line (perhaps something like, "scim-engine-pinyin") into the Startup Programs under System/Preferences/Session, which was what Ubuntu used to do automatically upon installing the Language Support.

I might revert to Dapper Drake if I still cannot get SCIM to work, since I NEED to input Chinese... sigh, going backwards is definitely not my idea of fun, but what can I do about it?   = P

---

### Post by FrankVdb on 2006-12-26
One of the (many) reasons why I returned to Dapper from Edgy was Scim not working properly. Edgy is not up to standard, especially not for a production machine.

---

### Post by polt on 2006-12-31
Okay, to get SCIM starting up in Edgy, all you have to do is go to System -> Preferences -> Sessions.  Under "Startup Programs" add a command that says "scim -d".  Restart, and it should be loading up.  That's the farthest I have come in getting it working though.

---

### Post by seshomaru samma on 2007-01-14
nope scim -d didn't work on a fresh install....
very strange...
one would expect scim to work flawlessly on edgy as it worked so well on dapper

i think it's back to dapper for me.

---

### Post by mhenriday on 2007-01-15
This is really strange ! I had no difficulty using **SCIM** in **Edgy** after upgrading from **Dapper** some three weeks ago, but after, for reasons not relevant to this discussion, finding it necessary to re-install Ubuntu (live CD to **Dapper** followed by an upgrade to **Edgy**) the day before yesterday, I'been unable to get the programme to function. When I try to adjust the **SCIM** settings by clicking on the keyboard icon in the top panel, nothing happens ; and when I go through **System&#8594;Settings&#8594;Settings for SCIM**, I get the customary «Starting settings for **SCIM**»icon on the bottom panel, but this latter disappears after a few seconds without my being able to make any adjustments. I've tried un-installing and re-installing **SCIM** through the **Package Manager**, but to no avail. Upon checking I see that I have a directory entitled **SCIM**, under ./etc, but aside from two text documents, it is empty ! And when I write «scim» in the command line on my console, I get the following response :

[INDENT]Smart Common Input Method 1.4.4

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
SCIM has exited abnormally.[/INDENT]

Upon **polt**'s advice, I added the command line «scim -d» in **System&#8594;Preferences&#8594;Sessions&#8594;Startup Programs**, but upon restarting my computer I was still unable to launch **SCIM**, and when I checked in the **Present Sessions** tab under **Sessions**, I found that instead of a cogwheel indicating that **SCIM** was running, the command «scim -d» was graced with a question mark....

Given that up to a couple of days ago, **SCIM **worked perfectly in my **Edgy** set-up, my conclusion is that one or more of the recent updates must have corrupted the programme to such a degree that it no longer functions. As I depend upon being able to use my Swedish keyboard to input Chinese and Japanese text , I sincerely hope one of the **Ubuntu** developers will take pity upon people like myself and correct this error as soon as possible....

Henri

---

### Post by ryukent on 2007-01-16
Have you tried putting a SCIM startup file in your XSession.d directory? This will assign SCIM as the input method. Sometimes it seems it gets attached only to particular locales. 

See the first part of my howto: [http://ubuntuforums.org/showthread.php?t=338991](http://ubuntuforums.org/showthread.php?t=338991)

---

### Post by mhenriday on 2007-01-16
Dear **ryû(&#40857; ?)kent**,

I followed the instructions on the page to which you provided a link with great interest and great hope, until I came to the following two commands :

[INDENT]mhenriday@mhenriday-desktop:~$ sudo im-switch -z sv_SE.UTF-8 -s scim-anthy
Password:
Error: no system wide configuration file "scim-anthy" exists.
Error: No action taken.
mhenriday@mhenriday-desktop:~$ sudo nautilus --browser

(nautilus:22970): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
ERROR: could not open init.scm (see errobj)

*backtrace*
>>(require "init.scm")
>>(*catch (quote errobj) (require "init.scm"))
>>(eq? (quote *init.scm-loaded*) (*catch (quote errobj) (require "init.scm")))

ERROR: unbound variable (errobj create-context)

*backtrace*
>>(create-context 0 (quote ()) (quote ()))

Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.4
[/INDENT]

after which the console simply hanged.

As you see, in the first case, no action was taken as no system-wide configuration file «scim-anthy» file, it was claimed, existed. In the second case, the failure may have been due to a plethora of causes, but for me the interesting thing was the message to the effect that «init.scim» could not be opened ; i e, the same problem («errorbj») of which I was informed earlier when I tried to get **SCIM** to open by simply writing «scim» as a command in the console (see my previous message). Could it be the case that a line in the **SCIM 1.4.4** application is missing ? This strikes me as quite odd as, as I mentioned above, **SCIM** worked perfectly for me until a couple of days ago. I've tried to counter this by downloading and installing **SCIM 1,4,5** from the [**SCIM **download page]("http://www.scim-im.org/downloads/scim_download"), but here again, unfortunately, I failed. Any suggestions ?...

Henri

PS When trying to open **SCIM** via the **System&#8594;Settings&#8594;SCIM Settings** route, I sometimes (not always) get a message to the effect that scim-helper-launcher closed unexpectedly. I am then asked to send in a bug report including the following file : «/var/crash/_usr_lib_scim-1.0_scim-helper-launcher.1000.crash». Hopefully this additional information may be of use in figuring out what is going wrong....

---

### Post by ryukent on 2007-01-17
Hmm... looks like you've got more serious issues. Actually I get the no scim-anthy error too, but I left it in my guide as it has helped other people. Try "sudo im-switch -z all_ALL -s scim". But to be honest, you shouldn't need this. I think you have some major conflict going on with your installation of scim. I guess a reinstall of edgy is out of the question? If you've added the details in the XSession.d directory, then scim is at least trying to run and failing...... I wish I could be of more help.

---

### Post by mhenriday on 2007-01-17
**Ryukent**, here's what happened when I followed your advice :
[INDENT]mhenriday@mhenriday-desktop:~$ sudo im-switch -z all_ALL -s scim
Password:
Allows "/etc/X11/xinit/xinput.d/scim" to provide "xinput-all_ALL".
[/INDENT]

But I haven't noticed any differences with regard to my problems with **SCIM** after performing the above. And indeed, I agree that I have, as you put it, «more serious issues» with my latest **Edgy** installation - I can no longer update applications or even open the updater ! I am advised to run the **Package Manager** or apt-get in a console to see what is wrong. The error message is as follows : "Error : Opening the cache (E: Type '"deb' is not known on line 37 in source list etc/apt/sources.list, E: The list of sources could not be read.)"

My guess is that (what I regard as) the extraneous «"» in «'"deb'» on line 37 is what is causing the problem. While I'm not entirely adverse to re-installing **Edgy** (I've done it several times), I should much prefer correcting line 37, in the event that doing so would suffice to resolve my problems. Unfortunately, **Linux** novice that I am, I haven't the slightest idea of how to do so. Have you any suggestions ? I should be grateful if, in that case, you could take them step-by-step, as you have done in your earlier instructions....

In the event, however, that this is not possible, I wonder if there is not a less cumbersome way to re-install **Edgy** than the one I use : re-installing **Dapper** from the live CD and then updating to **Edgy** from the net ? This takes me several hours, to which I have to add the time it takes to configure the system, download updates, etc, etc (losing my data is not a problem, as nearly everything is stored on the web, on such sites as **Gmail**, **Docs & Spreadsheets**, **del.icio.us**, etc, so that it can almost always be retrieved, even if this also takes a fair amount of time). Again, any suggestions are welcome !...

Henri

---

### Post by sso71 on 2007-01-25
I finally got it working. Here is what you should do after setting the language and installing the pingyin or other input method.

sudo touch /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 644 /etc/X11/Xsession.d/74custom-scim_startup

Best wishes to you all.

---

### Post by ncjones on 2007-02-03
Thanks for the solution, It worked a treat&#65281;

---

### Post by shanen on 2007-02-18
Actually, there is a fix for this, though I agree that Edgy Eft is not as good as Dapper Drake was... They need to focus on consistently getting better, not just being different on schedule.

The fix involves some environment tweaking, but only one or two commands. Unfortunately, I don't remember where I found it, and I'm looking for it again... Hopefully I can find it and add it here in just a minute or two...

Unfortunately, so far I can't find find it. This following link is related information, and probably works, but it isn't the good explanation that I found and used the last few times I fixed the Japanese input on Edgy Eft.

[https://wiki.ubuntu.com/InputMethods/SCIM/Setup](https://wiki.ubuntu.com/InputMethods/SCIM/Setup)

I can also say that using the following commands will fix it, but only for that window and it's descendents.

LANG='ja_JP.UTF-8' scim -d
export XMODIFIERS=@im=SCIM
export GTK_IM_MODULE=scim
export QT_IM_MODULE=scim

After you run those commands, you can start a new editor, such as gedit from that shell, and it will have normal Japanese capability. If I knew where to put it in my startup stuff, that would probably be one way to fix it, though a clumsy method.

However, the document I still can't find had a much better and more simple way to fix it. I think it actually came down to one missing command that had to be entered (assuming SCIM and Anthy had already been installed, though the document included those installation instructions).

I hope the next release is better in various ways than Edgy...

---

### Post by rykel on 2007-02-18
> **shanen said:**
> I think it actually came down to one missing command that had to be entered...

Thanks Shannen... I think the command you are looking for is this:

**[INDENT]$ im-switch -z en_SG.UTF-8 -s scim-pinyin[/INDENT]**

Of course, you should change "en_SG.UTF-8" and "scim-pinyin" to whichever locale and input engine you are using and planning to use.

However, my problem now on Dapper is not so much not being able to autostart SCIM, but rather, how to prevent SCIM from "hanging" my desktop and other minute problems. (eg. I cannot rename my folders whenever SCIM is running in the taskbar.)

Good to see a friend here!   :guitar:

---

### Post by Arjunanda on 2007-02-26
I am having the same problem, though I can use the gnome xkb tool for switching layouts. But SCIM is no longer using, though it used to work some time before. It must have some update that broke it down. I am using Dapper.

---

### Post by mhenriday on 2007-06-16
**Arjunanda**, almost four months have gone by since your message appeared on this thread ; I sincerely hope that you've been able to solve your **SCIM** problem in the meantime. If not, the best instructions I've hitherto seen are those that appear on the [**Ubuntu documentation page for SCIM**]("https://help.ubuntu.com/community/SCIM"), to which I always turn when in doubt. A brief synopsis follows :> The recommended method to set up SCIM input for all applications is using a command-line tool called im-switch (where im stands for Input Method, obviously :) ). Before that, you will have to know the name of the locale you're using. In a terminal (Applications>Accessories>Terminal) type :```
locale | grep LANG=
```The anwer would be something like```
LANG=en_GB.UTF-8
```where the relevant part is en_GB (en standing for English and GB for the country, here Great Britain). Another example could be fr_FR (fr for French and FR for France).

Now you just have to install an additional package called {{scim-qtimm}} and tell the system you want to use SCIM as the input method for your locale, using```
im-switch -z “your locale” -s scim
```In the above example, with an en_GB locale, you would type in the terminal :```
sudo apt-get install scim-qtimm
im-switch -z en_GB -s scim
```
Log out, then log in again. SCIM should be now the default input for all applications (go to Using SCIM to learn how to use it) **SCIM** automatically places a keyboard icon on your upper panel ; when you left-click it, a meny listing the languages and input choices you have made appears. A right-click allows you to modify the SCIM settings. If, after doing the above, you find that the icon does not respond to a left-click, type the following string into your terminal :```
scim -d
```. That should do the trick !...

Henri

---

