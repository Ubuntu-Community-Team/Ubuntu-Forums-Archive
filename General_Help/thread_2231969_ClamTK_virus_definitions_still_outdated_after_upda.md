---
title: "ClamTK virus definitions still outdated after update"
date: 2014-06-24
forum: General Help
---

### Post by John_Patrick_Mason on 2014-06-24
It's been over 24 hours, so I've decided to bump the thread as recommended here: [http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)
My question was: If the Software Updater updates all your programs such as ClamAV then how come after I used the Software Updater to manually update my system ClamTk still said that my virus definitions were outdated until I used the CLI?

---

### Post by John_Patrick_Mason on 2014-06-28
Could anybody please answer my question in the previous post? I'd really like to mark this thread as closed.

Mason

---

### Post by speartip on 2014-06-29
If I understand you correctly, the virus definitions are not updated by the software centre,
You have to update them manually by either using the gui or by running:
```
sudo freshclam
``` from the terminal.

---

### Post by John_Patrick_Mason on 2014-06-29
You understood me correctly. The thing is you can only update the GUI itself not the virus definitions through the GUI. I just find it strange that ClamTk would say that your virus definitions were outdated yet wouldn't allow you to get the latest virus definitions using its GUI. Does anybody have an answer?

---

### Post by Old_Grey_Wolf on 2014-06-29
In clamTK go to Advanced and run the AV wizard.

---

### Post by John_Patrick_Mason on 2014-06-29
I feel like an idiot, although to be fair a lot of people are asking the same question in the Ubuntu Sofware Center. To update my antivirus definitions I go to Advanced -> Rerun antivirus setup wizard, but even so you can only specify that you want your antivirus definitions to be automatically updated whenever you receive regular updates for your system, but it doesn't allow you to update the virus definitions whenever you want through the GUI. Could it be that Ubuntu hadn't packaged the latest antivirus definitions in their latest updates, which would explain why ClamTk still showed that my antivirus definitions were outdated even though I had gone to the Software Updater to manually update my system?

---

### Post by Old_Grey_Wolf on 2014-06-29
If you want something that works differently, you could try installing AVG for Linux from the AVG website. If I recall correctly it auto updates the signatures.

---

### Post by John_Patrick_Mason on 2014-06-29
AVG won't work. Check out this other thread I started: [http://ubuntuforums.org/showthread.php?t=2231021&page=2](http://ubuntuforums.org/showthread.php?t=2231021&page=2) The .deb file they have available for download can cause serious damage to your system. If the only sure way to get your virus definitions updated is to use the CLI, rather than hoping for the latest system updates to also update your antivirus definitions, then it kinda defeats the purpose of having a GUI for ClamAV.

---

### Post by speartip on 2014-06-30
> **John_Patrick_Mason said:**
>  If the only sure way to get your virus definitions updated is to use the CLI, rather than hoping for the latest system updates to also update your antivirus definitions, then it kinda defeats the purpose of having a GUI for ClamAV.

I agree, but the command line is fairly easy. Everytime I use clamav, I just update using the command in my last post, then run:
```
[COLOR=#000000][FONT=Ubuntu][SIZE=3]sudo clamscan -r --bell -i /[/SIZE][/FONT][/COLOR]*nameofdirectory*  
```

---

### Post by SeijiSensei on 2014-06-30
I just installed clamav from the repositories, and it downloaded and started the daemonized version of freshclam by default ("/usr/bin/freshclam -d --quiet").  The configuration file /etc/clamav/freshclam.conf has the "Checks 24" directive to tell freshclam to check once per hour.  

Perhaps ClamTK doesn't implement the same functionality?  If you enter the command "ps ax", do you see an entry for freshclam?

 I never use GUIs for things like ClamAV so I can't help with that.

---

### Post by monkeybrain20122 on 2014-06-30
Why do you think you may need an AV in the first place?

---

### Post by John_Patrick_Mason on 2014-06-30
> Why do you think you may need an AV in the first place?
To scan a Windows machine for malware as I have read that viruses can hide themselves even in Windows Safe Mode. And I did find something, which my antivirus in Windows missed.

---

### Post by John_Patrick_Mason on 2014-06-30
I didn't have to install ClamAV since it was already included in the Ubuntu install. The only thing I did was install a GUI for ClamAV. It's really just a question; I'm just trying to learn more about how Ubuntu works. I thought that when you got regular updates that these would also update the virus definitions for ClamAV, being a program that was already installed, in addition to updating the other programs on your computer, so I was just surprised that when ClamTk* said my virus definitions were outdated I just thought that I could open the Software Updater to also update these. I guess not. That was really my question.
> If you enter the command "ps ax", do you see an entry for freshclam?
Yes I do, not sure what it all means but I see:
```
 
PID   TTY   STAT TIME COMMAND
1158 ?        Ss     2:06 /usr/bin/freshclam -d --quiet

```
Thanks SeijiSensei for taking the time to installing it yourself.

Mason

---

### Post by monkeybrain20122 on 2014-07-01
> **John_Patrick_Mason said:**
> To scan a Windows machine for malware as I have read that viruses can hide themselves even in Windows Safe Mode. And I did find something, which my antivirus in Windows missed.

ClamAV is a pretty poor AV, I wouldn't bother with it. Better find a good one on your Windows end.

---

### Post by SeijiSensei on 2014-07-01
> **John_Patrick_Mason said:**
> ```
 
PID   TTY   STAT TIME COMMAND
1158 ?        Ss     2:06 /usr/bin/freshclam -d --quiet

```

ClamAV should be updating itself regularly then without any intervention from you.  What servers are you using for updates?  (See /etc/clamav/freshclam.conf for that.)  As a American I'll often use db.jp.clamav.net or db.de.clamav.net to use servers in timezones ahead or behind me.

---

### Post by maglin2 on 2014-07-01
If under clamtk you click advanced/rerun setup wizard, then tick manual under av signature options, then go to help/check for updates, then tick signature updates, then click the check for updates box beneath it should update.

---

### Post by John_Patrick_Mason on 2014-07-01
> What servers are you using for updates?  (See /etc/clamav/freshclam.conf  for that.)  As a American I'll often use db.jp.clamav.net or  db.de.clamav.net to use servers in timezones ahead or behind me.
I think I'm under:
```

DNSDatabaseInfo current.cvd.clamav.net
DatabaseMirror db.local.clamav.net
DatabaseMirror database.clamav.net

```
> ClamAV should be updating itself regularly then without any intervention from you.
Mmm,  not sure what happened, at least when I installed ClamTk I didn't have  the latest virus definitions. Maybe I just didn't wait long enough for  it to update itself or something. Glad it works for you right off the bat under Kubuntu though.
Thanks for your help          SeijiSensei.
> If under clamtk you click advanced/rerun setup wizard, then tick  manual under av signature options, then go to help/check for updates,  then tick signature updates, then click the check for updates box  beneath it should update.
I'll try this from now on. For some  reason I was thinking that when I clicked manual that I would have to  use the CLI, which I don't mind to use, but I'd like to learn how to use  both the GUI and the CLI in case I someday have to show someone who's  new to Linux how to scan their Windows partition for viruses and  malware. Or I could use speartip's CLI command:
```
sudo freshclam
```
And then:
```
sudo clamscan -r --bell -i /nameofdirectory
```
which I find much simpler.
> ClamAV is a pretty poor AV, I wouldn't bother with it. Better find a good one on your Windows end.
I have AVG, one of the best AV software there is. I also have another program called Malwarebytes to scan for malware, which many recommend, since AV software cannot catch everything. If I remember correctly I think I ran an AVG scan in Windows (not in Safe Mode), which found nothing. I didn't run Malwarebytes though, so there's a possibility that it could have caught something had I done so. I then rebooted and ran ClamAV under Linux, which found yontoosetup.exe, which stores information about your browsing habits, as well as a lot of false positives, which is not a good thing for ClamAV to do. At first, I was reluctant to install ClamTk under Linux to scan my Windows partition, preferring the more popular AV programs such as Avast or AVG, but unfortunately you can no longer install those safely without causing damage to your system.

---

### Post by maglin2 on 2014-07-02
I think you will get more fps using GUI scan than CLI scan. PUA can be disabled with CLI.

---

### Post by John_Patrick_Mason on 2014-07-07
Well, I guess this thread as been solved. So long as ClamTk will update itself every hour it doesn't really matter if I didn't have updated virus definitions when I installed it.

Thanks everyone for your help.

---

