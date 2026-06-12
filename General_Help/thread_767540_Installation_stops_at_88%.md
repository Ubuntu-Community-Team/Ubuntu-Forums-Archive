---
title: "Installation stops at 88%"
date: 2008-04-25
forum: General Help
---

### Post by verroitn on 2008-04-25
Hello,

I'm new to the linux word and I've tried to install ubuntu using wubi but I'm facing a problem: the installation failed at 88% during the import documents and settings. The installation was done in verbose mode and you will find the log to this post. (I used the command *sudo sh /custom-installation/hooks/failure-command.sh* after the error).

I could make the installation on a wirtualbox machine and the liveCD is working fine but not with wubi.

Tell me if you have enough informations and if you want me to post something in launchpad.

Thanks in advance.

PS: I found a similar topic on the [french ubuntu forum]("http://forum.ubuntu-fr.org/viewtopic.php?pid=1659066") with no answer (yet) but nothing in the wubi forum.

---

### Post by verroitn on 2008-04-25
Hello,

I took the latest wubi installer in the website and tried installing with no more success. Nevertheless, here is the log file.

I'm also facing the time shift of two hours but this was already identified as a bug so I won't focuse on it (ony one bug at a time !)

---

### Post by ago on 2008-04-26
Please open a bug report here: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bugs](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bugs)

---

### Post by Nikell on 2008-04-26
After the Fragmented Swap Space problem were resolved, I got this problem too.

At 88% percent, while doing the "importing documents and settings..." just after the "configuring keyboard..." I get an error message box:

"The installation failed. Logs have been saved in : 
C:\ubuntuinstallation-logs.zip

Blabla about password in verbose mode

The system wll now reboot" 

I've found that this is an already known bug in the Wubi 7.10 release. There : [http://ubuntuforums.org/showthread.php?t=624263#post3846533]("http://ubuntuforums.org/showthread.php?t=624263#post3846533")

And instead of opening a new bug report, should we not reopen this one : [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/106643](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/106643)?

And there are my logs :

---

### Post by ago on 2008-04-26
Probably [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/195905](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/195905) is more appropriate

It seems there is a problem when accented chars are used in the windows name

---

### Post by verroitn on 2008-04-26
Concerning the accented chars, I have two window users : "Nico" and "Invit**é**". It may be the reason. I will search how to rename or delete the "Invité" account as I don't use it anymore.

I will post my logs on launchpad 195905.

---

### Post by ago on 2008-04-26
There might be accents in the Windows OS name itself.
Also what other operating systems do you have on your machine?

---

### Post by verroitn on 2008-04-26
Windows XP is the only operating system installed. It came with my computer during purchase (Dell Dimension 8300)

Can you explain me how to find the Windows OS name so I can provide it to you ?

---

### Post by ago on 2008-04-26
This is from Nikell log for instance

Apr 26 18:35:42 ubuntu 20microsoft: result: /dev/sda1:Microsoft Windows XP dition familiale:Windows:chain

"E'"

---

### Post by verroitn on 2008-04-26
ok, I understand. I have the same OS as Nikell : "Windows XP édition familiale" with an accented char.

Tell me if you want me to perform some tests, I will try to help.

---

### Post by duanra on 2008-04-26
Joining forces with you, verroitn !

(quote from my previous thread)
[INDENT]"Well, it looks like Wubi people don't like French-speaking people ;) !

I know that both my computers are "Windows XP **_É_**dition familiale".

We have an older PC at home with "XP Professional" but I prefer to leave it apart from all this mess for now (I'm not even sure that it has the minimum requirements ;) )"[/INDENT]

Well, now the question is (maybe for 'ago') : what do we do now ?
Is there a way to get around this bug ?
Can I install Ubuntu in another language or will the bug appear all the same ?

Can I help in any way (just don't make me test beta versions) ?

Thanks
Duanra

PS : my user name on Windows begins with a capital letter : coult it be a problem too ?

---

### Post by Nikell on 2008-04-26
And indeed, it seems that some other french speaking people on ubuntu-fr.org have the same problem.  

Counting verroitn, duanra and myself, we are 12 frenchspeaking with this bug. And I didn't searched all the posts on ubuntu-fr, but checked only 3 threads about bugs in installation with Wubi :)

What i don't understand is why there's in the French web-press and blogosphere so much people talking about Wubi... They might have not tried to use it, or they have an English Windows... but its still strange.

---

### Post by verroitn on 2008-04-26
A dedicated question concerning launchpad bug follow-up

do you think we shall create a dedicated bug on launchpad concerning this topic or continue using the existing one : [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/195905](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/195905)

---

### Post by ago on 2008-04-26
The workaround might be to disable migration-assistant in preseed.cfg before rebooting.
I will ask m-a dev for confirmation.

Note that you will have to uninstall/reinstall/edit preseed.

---

### Post by ago on 2008-04-26
> **verroitn said:**
> A dedicated question concerning launchpad bug follow-up

do you think we shall create a dedicated bug on launchpad concerning this topic or continue using the existing one : [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/195905](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/195905)

I think that a separate bug would be better, since the original bug issue was about spaces in the username which was fixed. Please move the logs to the new bug and add a reference in the old one! It will be addressed speedily.

---

### Post by verroitn on 2008-04-26
I will try this immediatly and keep you informed.

---

### Post by verroitn on 2008-04-26
I've created a new bug reference:
[https://bugs.launchpad.net/wubi/+bug/222690](https://bugs.launchpad.net/wubi/+bug/222690)

---

### Post by verroitn on 2008-04-26
Ago,

can you confirm me the modifications I've done in the file preseed.cfg: 

Before modification
```
## MIGRATION-ASSISTANT
#UserFolder=/Documents and Settings/nico
d-i anna/choose_modules multiselect migration-assistant
d-i migration-assistant/partitions multiselect Windows XP Professional (/dev/MADEVICE)
d-i migration-assistant/MADEVICE/users multiselect nico
d-i migration-assistant/MADEVICE/nico/items multiselect AIM Triton, Internet Explorer, Yahoo, MSN, Opera, Firefox, Wallpaper, User Picture, Outlook Express, Gaim
# d-i migration-assistant/MADEVICE/hostuser/items multiselect My Documents, Internet Explorer
d-i migration-assistant/MADEVICE/nico/user string nico
# d-i migration-assistant/new-user/linuser/password password xyz
# d-i migration-assistant/new-user/linuser/password-again password xyz
# d-i migration-assistant/new-user/linuser/fullname string fullusername
# d-i migration-assistant/new-user/linuser/administrator boolean true
```

After modification:
```
## MIGRATION-ASSISTANT
#UserFolder=/Documents and Settings/nico
#d-i anna/choose_modules multiselect migration-assistant
#d-i migration-assistant/partitions multiselect Windows XP Professional (/dev/MADEVICE)
#d-i migration-assistant/MADEVICE/users multiselect nico
#d-i migration-assistant/MADEVICE/nico/items multiselect AIM Triton, Internet Explorer, Yahoo, MSN, Opera, Firefox, Wallpaper, User Picture, Outlook Express, Gaim
# d-i migration-assistant/MADEVICE/hostuser/items multiselect My Documents, Internet Explorer
#d-i migration-assistant/MADEVICE/nico/user string nico
# d-i migration-assistant/new-user/linuser/password password xyz
# d-i migration-assistant/new-user/linuser/password-again password xyz
# d-i migration-assistant/new-user/linuser/fullname string fullusername
# d-i migration-assistant/new-user/linuser/administrator boolean true
```

Are there other modifications to perform ?


############################
Result of the test: Failed with the modifications described in this post. Same error at the same 88% :(

---

### Post by duanra on 2008-04-26
I posted my installation logs and preseed.cfg file to the new bug reference created by verroitn.

I hope to still be useful and I'm eager to hear for any solution / fix /patch clearly described and guaranteed "NO-risk".

Thanks
Duanra

---

### Post by ago on 2008-04-26
I have informed m-a dev, we will let you know about a workaround soon.

---

### Post by Nikell on 2008-04-26
Since I was bored, and since I don't care about my PC, I did the workaround commenting the lines in preseed.cfg, just as verroitn said.

And, well, it worked :] I'm writting that in Fx3b5 in Ubuntu 8.04.
Is a little laggy sometimes, but my pc ever was laggy.

I still didn't saw if Windows was still working, but who cares, huh ?

Ah, and one difference between verroitn and me. I plugged my computer on a RJ45 cable to make a backup of some files... and by that, I were connected to internet... (before that I was on wifi, with a WPA encryption, so no chance it could had connected), and before the 88% the installer struck for a while doing some apt-get configuration, same thing to the time setting thingie.

Hope it may help.

Wubi rules!

---

### Post by verroitn on 2008-04-27
Hello,

It's good to see that a workaround is close. You are right about connection on the internet during installation (for Ago: we've tried to make a little poll in the french forum to see what were the common points for the ones that were having problems but it didn't show any obvious points yet).

concerning my computer, I'm not sure I will make the test with a direct connection as it took me some time before having my local wifi network configured correctly.

Let's hope Ago will find a good general workaround.

---

### Post by Zakhafr on 2008-04-27
I'm also interested if you fix it.

I've posted in the same thread Verroitn posted on the French forum, we have apparently the same bug.

Only difference my install fails at 83% (not 88%) but same step.
I've tried both
- Kubuntu 
- Kubuntu remix, same bug.
- Ubuntu doesn't install at all with Wubi, it tries to read past the CD length (someone posted this bug as well [http://ubuntuforums.org/showthread.php?t=706167&highlight=wubi]("http://ubuntuforums.org/showthread.php?t=706167&highlight=wubi")).
I have verified the CD with MD5, and to avoid read errors from CD I did it again with iso mounted in Daemon Tools, still tries to read past the CD end !

Also the bug with time. It sets the computer clock to UTC+2 which is the current time in Paris, instead of setting it to UTC and applying the time-zone (CEST). So back in windows, I have to set the clock back -2 hours.

The uninstall works correctly (fortunately !).

---

### Post by ago on 2008-04-28
I talked to Evan, a proper fix is in the making.

The fix will appear in Daily ISOs in coming days, this means that you will need to use a new version of Wubi with a new ISO (both will become the "default" in July when 8.04.1 is released). I will let you know once everything is ready. 

For the impatients, you may want to edit C:\ubuntu\install\custom-installation\preseed.cfg so that it looks like: 

```
d-i anna/choose_modules multiselect migration-assistant
d-i migration-assistant/partitions multiselect 
d-i migration-assistant/MADEVICE/users multiselect hostuser
d-i migration-assistant/MADEVICE/hostuser/items multiselect AIM Triton, Internet Explorer, Yahoo, MSN, Opera, Firefox, Wallpaper, User Picture, Outlook Express, Gaim
d-i migration-assistant/MADEVICE/hostuser/user string linuser
```

Basically in the second line above after multiselect you need a few whitespaces and nothing else (which should mean: we do not select any partition!). Thanks to Evand for the tip! 

Apologies for the troubles.

---

### Post by verroitn on 2008-04-28
Hello,

good to see that a workaround is really close :cool:. Thanks a lot for your quick actions. I will keep you informed about the result of the test.

One question: does it mean that you removed some functionality with this workaround or just a bug corrected ?

---

### Post by ago on 2008-04-28
The workaround above disables migration-assistant which is the program that imports your settings and files from Windows. Once that is fixed in the ISO, there will be no need to edit the preseed file since you will be able to use m-a as usual.

---

### Post by verroitn on 2008-04-28
ok, I will wait for the new ISO + new wubi to make the test. Unless you want me to check something tonight (after I will be away until sunday). just tell me.

---

### Post by ago on 2008-04-28
Check the workaround above maybe, since I had no chance to do so myself. It involves: uninstalling, running wubi, and editing preseed.cfg before rebooting.

---

### Post by verroitn on 2008-04-28
ok, I will make the test tonight.

one comment concerning the workaround in the ISO. Will the workaround disable the migration assistant (as defined in you previous post) or is it something else?
If so, don't you think it's a regression ?

Nevertheless, I prefer a wubi that works without migration than a wubi that doesn't work at all ! ;)

---

### Post by ago on 2008-04-28
The preseed.cfg edit above is the workaround and it disables m-a.

But the ISO fix, is not going to be a "workaround", it will fix the problem at the root, so that m-a can be used normally.

---

### Post by verroitn on 2008-04-28
wonderfull, wubi rocks !

---

### Post by verroitn on 2008-04-28
Hello,

for information, I'm writting you this mesasge from ubuntu 8.04 on firefox! the workaround is working perfectly. Let's wait now for the official bug correction.

:) :) :) :) :) :)

---

### Post by duanra on 2008-04-28
That's good news. At least, we know now for sure where the bug hides !

Now as you said,

> **verroitn said:**
> 

Let's wait now for the official bug correction.



Duanra

---

### Post by verroitn on 2008-04-28
for information, somes updates are required by Evan Andrea concerning this bug. I won't be able to give feedbacks until next sunday (vacations...8) ). So if somebody can make the test, it will ease the bug fixing.

[https://bugs.launchpad.net/wubi/+bug/222690](https://bugs.launchpad.net/wubi/+bug/222690)

> Evan Dandrea wrote 3 hours ago: 

Could someone who is experiencing this problem please try the install again, switch to one of the virtual terminals when it is starting up (ctrl-alt-f2), run `sudo nano /usr/lib/ubiquity/migration-assistant/ma-apply` and stick set -x on the second line, then attach the logs as per usual when the installation fails.

Thanks very much!
> Evan Dandrea  wrote 3 hours ago:

To clarify, you can switch to one of the VTs when you first see the installer window. You should have some time to do this as the code you're modifying executes after the file copy procedure, and that will take a little while.

---

### Post by ago on 2008-04-28
When you help Evan, please note that you do NOT have to edit preseed.cfg, that would disable M-A, while Evan requires more logs once that fails.

---

### Post by trueblue53 on 2008-04-28
Hi,

I'm at a loss what to do next. I'm stuck with 14 brandnew 'Dell Inspiron Latitude D531' laptops that I'm taking with me to Senegal on May 6th. About fourteen hours ago, I started what I thought would be an easy job... installing Ubuntu v8.04 with the latest Wubi, on a NTFS drive (shared with Windows XP). The laptops will be used to help Senegalese kids get used to 'Open Source' software. Ah well... in those past fourteen hours, I guess I've run into Murphy more than a hundred times. At least, so it feels. Installing Ubuntu v8.04 with Wubi is impossible for me, it breaks off at around 80%, not unlike some of the other users around here. I even tried a 'dedicated' install with Ubuntu 8.04, bypassing Wubi, but then the wireless ends up broken (Dell Wireless 1390). I haven't got around to that one yet... :(

Is there anyone out there that knows more about this 'Wubi' problem?  Like I said, the stakes are high for me.

An exerpt from the end of user.log:

Apr 29 18:36:04 ubuntu ubiquity[8990]: RuntimeError: Install failed with exit code 1
Apr 29 18:36:04 ubuntu ubiquity[8990]: Traceback (most recent call last):
Apr 29 18:36:04 ubuntu ubiquity[8990]:   File "/usr/share/ubiquity/install.py", line 1911, in <module>
Apr 29 18:36:04 ubuntu ubiquity[8990]:     install.run()
Apr 29 18:36:04 ubuntu ubiquity[8990]:   File "/usr/share/ubiquity/install.py", line 405, in run
Apr 29 18:36:04 ubuntu ubiquity[8990]:     self.configure_ma()
Apr 29 18:36:04 ubuntu ubiquity[8990]:   File "/usr/share/ubiquity/install.py", line 1101, in configure_ma
Apr 29 18:36:04 ubuntu ubiquity[8990]:     raise InstallStepError("MigrationAssistantApply failed with code %d" % ret)
Apr 29 18:36:04 ubuntu ubiquity[8990]: InstallStepError: MigrationAssistantApply failed with code 1
Apr 29 18:36:04 ubuntu ubiquity[8990]: 

I've tried to adjust the 'preseed.cfg' file per some of the comments here:

d-i anna/choose_modules multiselect migration-assistant
d-i migration-assistant/partitions multiselect   
d-i migration-assistant/MADEVICE/users multiselect SatangJabang
d-i migration-assistant/MADEVICE/SatangJabang/items multiselect AIM Triton, Internet Explorer, Yahoo, MSN, Opera, Firefox, Wallpaper, User Picture, Outlook Express, Gaim
d-i migration-assistant/MADEVICE/SatangJabang/user string linux

As you can see, in the first line, I added a couple of spaces ('  '). The main Linux user in the Wubi install window I called 'linux'.

Does anyone have more information on this one? Is there any info I can add that will help you crack this one? Do tell, thanks in advance.

regards,
Erik Coolen,
The Netherlands

---

### Post by ago on 2008-04-28
Not sure if it make a difference but add more spaces to the second line. Anyway if you can do a dedicated partition installation go that route. If you have networking problems there the same is going to happen in Wubi.

---

### Post by trueblue53 on 2008-04-29
Hi Ago,

Thanks for your comment. The 'Wubi Way' would be ideal for us so I'm still very much hoping for a solution. Not sure what to do next.

regards,
erik

---

### Post by ago on 2008-04-29
Try a clean installation. Uninstall, run chkdsk /r on target drive, defragment, run wubi, edit preseed, reboot and install.

---

### Post by duanra on 2008-04-29
I see, Ago, that you linked "our" bug with 8.04.1 release, due to July. Is this good or bad news ?

Any idea when an official workaround will be proposed ?

I mean, not a fix in the installer, just a way to have it working correctly. Because it seems the "comments" method and the "spaces" method do not work with everybody.

Thanks

Duanra

---

### Post by ago on 2008-04-29
The official ISO cannot be released before July, but daily ISOs will be available way before that, in fact the day after the fix is committed, and I will upload a new Wubi that will use such ISOs by default... The earlier you guys can provide Evan with debugging data, the earlier it will be fixed ;)

---

### Post by duanra on 2008-04-30
Well, that's good news, then ! :)

I just hope the test I did for Evan was correct, because the "stick set -x on the second line" was not a very clear instruction for us French-speaking, as Zakhafr rightly said.

Duanra

---

### Post by Zakhafr on 2008-04-30
Although "stick" is in the [Globish dictionary]("http://www.jpn-globish.com/file/1500motsGlobish.pdf"), it was indeed not so obvious. If some more experiments are to be done I'm ready to do them as well.

To be clear, it would be just fine to say how the ma-apply file has to look like after modification.

Just a few suggestions:
- could you add a "flush" instruction to be sure the log file is written to NTFS when the installer encounters an error. It is annoying to do a test that lasts for 30 minutes, and have no log at the end!
- if you could make Wubi work from a network mounted drive (ISO ou CD mounted on another machine and accessed as Share Folder or Network drive) it would be "nice to have". I saw a post from someone that had to install 14 PC for a charity association, I'm pretty sure it would have helped him. I'm not a Window's specialist programmer, but isn't it just NOT assuming you are reading a CD-ROM, but just reading regular files on the Windows part of Wubi.

---

### Post by ago on 2008-04-30
sudo nano /usr/lib/ubiquity/migration-assistant/ma-apply

The first few lines should look like this: 

```

#!/bin/sh  

set -x
. /usr/share/debconf/confmodule
. /usr/share/migration-assistant/ma-script-utils  
...

```

I.E. replace "set -e" with "set -x"

After you have done that, save the changes, then you can get back to the installation window pressing alt+F7 (might be anything from alt+F8 to alt+F12, sorry but do not remember on top of my head).

---

### Post by ago on 2008-04-30
In fact no need to replace set -e you can have both set -e and set -x together. This seems to be the block creating troubles (made it stand-alone so that it can be tested by itself):

#!/bin/sh
for line in `os-prober`; do  
echo "$line"  
loc=$(expr match "$line" '\(.*\):.*:.*:.*')
echo "$loc"  
done

---

### Post by duanra on 2008-04-30
OK : then I did well and Evan already has at least 1 correct "modified" installation-logs.

I'm about to do the same trick with my other computer (the desktop this time)

Glad to hear that the "trouble block" has been found !

Duanra

---

### Post by ago on 2008-04-30
in ma-apply before 

loc=$(expr match "$line" '\(.*\):.*:.*:.*')

try to add the following line (watch the spaces)

line=$(echo "$line" | tr -cs 'a-zA-Z0-9\_\-\(\)\;\.\:\+\=\n\ \[\]' '+')

---

### Post by duanra on 2008-04-30
> **ago said:**
> in ma-apply before 

loc=$(expr match "$line" '\(.*\):.*:.*:.*')

try to add the following line (watch the spaces)

line=$(echo "$line" | tr -cs 'a-zA-Z0-9\_\-\(\)\;\.\:\+\=\n\ \[\]' '+')

Is this an "official" workaround from Evan (or you) or a new test ?

---

### Post by ago on 2008-04-30
test at this stage

---

### Post by Zakhafr on 2008-04-30
It goes further, but I don't know really if it works. It produced an unusable Kubuntu with a corrupted Apt Database.

It's probably due to the "no-flush" bug. At the end of the install, I have no message at all and everything is stuck. I assume it gives no message and tries to reboot which does never happen on my laptop !

So I'm now trying again with my "Ctrl-Alt-F1" trick before it tries to reboot to flush writes to NTFS partition and keep you posted... and before that, I'm running a CHKDSK /R to be sure the database corruption does not come from bad sector on the disk.

...unless of course, corrupted Apt database is a known bug!
I'll search for it if it happens again.

---

### Post by Zakhafr on 2008-05-01
1st try : (post above) corrupted APT database - Kubuntu unusable [but it booted in "graphical" KDE mode].
------------
CHKDSK /r
Defrag offline (for locked files)
Defrag
------------
2nd try : with Ctrl-Alt-F1 "trick" : Kubuntu boots in "konsole" mode.
3rd try : let it run : Kubuntu boots in "konsole".

So basically, Ubiquity says what it is doing. At the end it says it is removing some packages, then the progression windows disappears and I have only one window left on the screen, a blank window with a title "Ubiquity" (this windows is there since the begining, and in top of it there is the "progression window" during install)
At this point my PC is completely stuck. Keyboard and mouse do not respond. I waited for 10 minutes in case some loooooong operation would be running, but nothing changes.

I don't know what Ubiquity is suppose to do at the point I describe, but I assume it tries to reboot the system which does not happen on my computer.
So the only option I have left is to manually switch off the computer.

As rebooting does not happen, or something blocks before it tries rebooting, I suppose things are not totally or correctly written to NTFS partition. That's a guess because when I tried to help with the current bug, most of the time I had no log file when I came back to windows.

For the log file, it seems that switching to a console with ctrl-alt-F2 before the 88% error worked, but it seems to be useless for the complete install.

So now I'll try with
Wubi-8.0.4-rev505.exe
that I just downloaded

As instructed, I copied in the same directory as this new Wubi :
kubuntu-8.04-desktop-i386.iso

But apparently it is not the correct file, and Wubi tries to download from [http://cdimages.ubuntu.com](http://cdimages.ubuntu.com) and fails at the moment. I'm presuming it's busy. I'll retry (last try before abandonning the idea of using kubuntu on this PC) later.



**Question is** : should I open a new launchpad bug for _"Ubiquity stuck and not rebooting"_ ?



So, sorry, I can't confirm the fix although it seems to go pass the "migration-assistant". I let to Duanra or Verroitn to confirm that fix is OK.

---

### Post by ago on 2008-05-01
Let's wait for a fix from Evan first, it would be confusing to have bug reports about trial fixes. Your help is much appreciated though!

---

### Post by Zakhafr on 2008-05-01
The tries were done with the "official" Wubi released one week ago, and official Kubuntu iso.

I just patched it according to your advise, adding the instruction :

line=$( echo ....

If I manage to connect to htpp://releases.ubuntu.com or [http://cdimages.ubuntu.com](http://cdimages.ubuntu.com) to download the iso Wubi-505 wants, I'll give it a try and let you know.

Otherwise I'll leave my fellow french Ubnuteros take it from here.


Next week I'll exchange my current laptop with a brand new one, and I'll have another try. That's because the new laptop comes with Vista, and as I'm used to XP and I've got to move to a new interface, I thing it's the right moment to get used to Kubuntu instead!

Wubi is the ideal to have a try and decide if it's good for me or not... once it will work!
If I decide to go on with Ubuntu I might install it "regularly" aftewards as the configuration I'll run is ideal for that with two physical drives.

I plan to keep Vista just for games, as at the moment it's no so easy using Wine for that.

*Keep up the good job !*

---

### Post by ago on 2008-05-01
The ISOs for 505 are not yet ready :) 
They will come up in the next days
You can use 503 or 501

---

### Post by Zakhafr on 2008-05-01
Yes I just realized that tracing it with Wireshark.

It's trying to retrieve :

[http://releases.ubuntu.com/kubuntu/](http://releases.ubuntu.com/kubuntu/)**8.04.01**/MD5SUMS-metalink.gpg

and trying the same on

[http://cdimage.ubuntu.com](http://cdimage.ubuntu.com)

... but there is no such **8.04.01** directory and it gets a 404 :(

So I'll get a try with 503

---

### Post by ago on 2008-05-01
Hopefully it is 8.04.1 instead of 01...

---

### Post by Zakhafr on 2008-05-01
Yes could be... sorry I copied it manually and now Wireshark is closed and trying Kubuntu 1014th install on the other PC ;)

---

### Post by Zakhafr on 2008-05-01
Ok, so same bug with Wubi-rev503.

- System stuck at the end of ubiquity install
- No reboot
- Had to manual shutdown
- Kubuntu booting to console-tty mode
- No install-log.zip written to c:\ubuntu

I'll be filing this bug in the launchpad in case it helps.
It would be quite difficult to guess where it comes from without any intall-log I'm sorry.

I'll set the priority to medium as I don't really need Kubuntu on this laptop. I was just trying it to get used to the install process. Next week I'll try Kubuntu on the new laptop and hope I'll be luckier, and this one is going to be reformatted with it's original Windows XP before I give it back.


Duanra, Verroitn, it's up to you guys to continue here :)

---

### Post by ago on 2008-05-01
Comment out: 

ubiquity ubiquity/reboot boolean true

in c:\ubuntu\install\custom-installation\preseed.cfg

you should be able to avoid the automatic reboot. You can use

sudo sh /custom-installation/hooks/failure-command.sh

Anyway, there should be no need. If the installation was successful all the logs will be under /var/log/installer

---

### Post by Zakhafr on 2008-05-01
Ok I'll try that, because Verbose mode indicated in the Launchpad did the same thing (and worse). I was stuck at the end, and no way I could do Ctrl-Alt-F2 to type the "failure-command.sh".

---

### Post by Zakhafr on 2008-05-01
And now it works !

Thanks Ago.

It should definitely have been a "flush" problem with the reboot not working.

After I typed the command:
sudo sh /custom-installation/hooks/failure-command.sh

I got bunch of text saying that it was saving intallation-log, then I got:
(...)
The system will now reboot.
kdialog: cannot connect to X server
+ reboot

And from here the system was stuck again.
But thanks to the "write-log" it must have flushed everything pending and now I have a working Kubuntu.

I'll add this information to the ticket on "Ubiquity is stuck at the end of installer", with your workaround, the ticket is closed for me.


Oh, and by the way, that **validates the modification** of ma-apply:
line=$(echo "$line" | tr -cs 'a-zA-Z0-9\_\-\(\)\;\.\:\+\=\n\ \[\]' '+')

... at leat for my PC.

Many thanks.

---

### Post by Zakhafr on 2008-05-01
[https://bugs.launchpad.net/wubi/+bug/225250]("https://bugs.launchpad.net/wubi/+bug/225250")

Is so "workaround-ed" or you could move to "suggestion": do not automatic reboot (as you do under Windows) but instead display the success dialog, with an option to reboot. Reboot when the user hits "Reboot" button.

It would give user a chance to "flush" with the failure-command.sh manual command.

That might be equivalent to simply consider the standard option is ubiquity/reboot commented out by default.
Those who want a "full automatic unattended" install can uncomment it.

As far as I am concerned, I was a bit frustrated to have no dialog box saying if it succeeded or not... but that is my own opinion ;)


Last thing:

**Cosmetic bug**: the gauge in Ubiquity does not change after 83% (for Kubuntu, and 88% presumably on Ubuntu), that is under "normal" installation mode. With "verbose" the gauge is correctly updated.

---

### Post by duanra on 2008-05-01
GOOD NEWS !!!

I'm writing from........ Ubuntu with Firefox 3.0b5 !!!

The installation went well and correctly WITH the "patch" line=$(echo blablabla), and Ubuntu seems to be working fine (for now, at any rate).

So, that's 1 PC out of the problem.
I haven't tried with my laptop yet, but maybe you want some more debugging and I can wait to install Wubi on it ?

What do you want me to do now, captain ô captain ?!  ;)

Duanra
PS : finally, it's quite "fun" to help debugging open software, after all :D

---

### Post by Zakhafr on 2008-05-01
Yes ;)

And my Wubi install lasted for only a few hours.
I had a crash in Wine trying to use Bridge Base Online, had to reboot "manually" the system, and the C:\ubuntu\disks was corrupted. What a pity!

I think for the validation of the ma-apply, Duanra, you should just try to install it to your laptop adding the:
line=$(echo ...

That would validate the fix works with another type of PC/Windows.

As for the stability of the Wubi-NTFS Driver there should be certainly improvement to be done although I know NTFS can be broken if you "manually" restart a PC.

---

### Post by ago on 2008-05-01
Well a proper proper fix is going to be slightly trickier but we have enough information for the time being! :) 

I will let you know once the ISOs are ready so you can play with those directly.

---

### Post by verroitn on 2008-05-04
well, it seems that a lot of things were tested while I was in vacations. Just tell me if something still needs to be done.

At least, it's good to hear that you are on a good way to fix this nasty bug.

---

### Post by ago on 2008-05-04
The fix has to be approved then we will have the first ISOs

---

### Post by verroitn on 2008-05-14
Hello,

the bug in launchpad is marked as "fix committed". Can you explain us how to test it if it is available somewhere ? Thanks in advance.

[https://bugs.launchpad.net/ubuntu/+source/migration-assistant/+bug/222690]("https://bugs.launchpad.net/ubuntu/+source/migration-assistant/+bug/222690")

---

### Post by ago on 2008-05-14
Hi verroitn,

You will have to wait until you see "fix released", then it will take 12-24h for it to appear in new ISOs.

---

### Post by verroitn on 2008-05-25
Hello Ago,

for information another workaround was discovered in the [french forum]("http://forum.ubuntu-fr.org/viewtopic.php?id=206247&p=3"). It requires a simple modification of the windows Boot.ini file. You just remove the nasty "é" and it's done, everything is working fine.

Example of a boot.ini file modified:
```
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP edition familiale" /noexecute=optin /fastdetect
```

I've not tested the workaround but according to two users, it seems to work fine.

---

### Post by ago on 2008-05-26
Thanks verrotin, we do now have a proper fix (although not released yet). But the above workaround is well suited for users in the meantime, since it is simpler to apply. Feel free to edit the WubiGuide and add it in there.

---

### Post by verroitn on 2008-05-27
for information, I've just modified the wubiguide with the new workaround.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by verroitn on 2008-06-02
Hello,

in launchpad, the bug has now the tag "Verification needed". Nevertheless, the only file available is a file describing the code modifications. Can you explain us how to perform this modification and validate the change ? 

[https://bugs.launchpad.net/wubi/+bug/222690]("https://bugs.launchpad.net/wubi/+bug/222690")

thanks in advance

---

### Post by verroitn on 2008-06-13
Hello Ago,

the solution is available but I have a question before downloading :

there is a link into [launchpad]("https://bugs.launchpad.net/wubi/+bug/222690/comments/22") to an alternate version including the bug solution. Nevertheless, I thought that wubi was not working with alternate *(from documentation : The ISO must be an 8.04 CD Desktop ISO. DVD ISO and Alternate ISO will not work. *). What do you think of this ?

thanks in advance

---

### Post by ago on 2008-06-13
verroitn,

for wubi testing you need to use the 8.04.1 Live CD with this version of wubi [http://wubi-installer.org/devel/minefield/Wubi-8.04.1-rev502.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04.1-rev502.exe)

It is better to let wubi download the ISO, copying the ISO on the same folder does not work at the moment.

---

### Post by verroitn on 2008-06-14
Hello,

I've just made the try and it wasn't successfull. Here is what I've done:

[LIST]
[*]download the latest wubi version using this link : [http://wubi-installer.org/devel/minefield/Wubi-8.04.1-rev502.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04.1-rev502.exe)
[*] wait until download is complete
[*] restart
[*] do a normal installation
[*] message : "Busybox v1.1.3 (Debian 1:1.1.3-5ubuntu(2) built in shell (cst). Enter "help" for a list of built-in commands. (initranfo)
[*]then nothing...
[/LIST]

any ideas ?

---

### Post by ago on 2008-06-16
Yes there was a file missing from the latest ISO for another bug. I have sent the patch a couple of days ago'. Should hopefully be in soon.

---

### Post by verroitn on 2008-06-23
Hello,

do you know if the ISO are available now or if we shall wait a little more?

thanks

---

### Post by ago on 2008-06-23
Yes, they are available, see the sticky thread about Wubi 8.04.1, please try it out and let me know.

---

### Post by ago on 2008-06-24
Verrotin did you test with wubi 8.04.1?

If so please comment into LP222690

---

### Post by verroitn on 2008-06-24
Hello Ago,

no yet any test with the pre-release (except the one that failed last time). I've downloaded the ISO and the lastest wubi version yesterday but I won't be home until thursday night. Normally, I will give you some news this WE at last.

I've posted a mail today in the french forum stating that the new 8.04.1 pre-release was available so they can make some tests also.

I will keep you informed asap.

What are the deadlines for 8.04.1 ?

---

### Post by ago on 2008-06-24
We need the end of the world to push something in now...
The above is already in but confirmation that it works is required

note that if you pre-downloaded an ISO, you will have to run wubi with --skipmd5check since wubi checks the md5 of the LATEST daily ISO. Also note that at the moment there is a known bug that does not allow wubi to work when the ISO is burned/mounted as a CD, you have to use the ISO directly.

---

### Post by verroitn on 2008-06-24
Hello,

I'm writting this mail from ubuntu 8.04.1 :D... The bug is fixed correctly. Thanks for all the work. I will update launchpad with this information and spread the news in the french forum.

---

### Post by ago on 2008-06-24
thank you verrotin

---

