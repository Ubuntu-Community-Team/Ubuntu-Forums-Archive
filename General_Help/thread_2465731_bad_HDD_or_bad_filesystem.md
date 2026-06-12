---
title: "bad HDD or bad filesystem?"
date: 2021-08-10
forum: General Help
---

### Post by Timothy Taylor on 2021-08-10
My desktop system has been temperamental since upgrading to 20.04.  Recently the system has started freezing, with mouse & keyboard locked. Streaming video freezes, audio continues to play, but there's no control. The only way out is to switch off my PC. 
On the next boot, diagnostics report "orphaned inodes" etc.  If I try recovery mode start-up, fsck is not allowed to unmount volumes prior to checking.
I see from the system summary :
> LVM State, Physical volumes: Not OK (Bad)

Does that mean I need a new HDD or would a re-format and re-install do the trick?
Any easier ways round this?

---

### Post by Paddy Landau on 2021-08-10
> **Timothy Taylor said:**
> On the next boot, diagnostics report "orphaned inodes" etc.
That's normal when a system shuts down without a chance to flush the cache to disk. I would be surprised if you didn't get this error under the circumstances. It simply means that the system is repairing your disk's file system.
> **Timothy Taylor said:**
> The only way out is to switch off my PC.
There is usually a way to force the system to shut down cleanly. It disables your desktop manager and goes directly to the kernel (I think) to do its work. Called [REISUB]("https://en.wikipedia.org/wiki/Magic_SysRq_key#Uses") (think BUSIER backwards), it goes like this (make a paper note for next time you need it):

[LIST=1]
[*]Alt+PrintScreen+R (Gives the base system direct access to your keyboard.)
[*]Alt+PrintScreen+E (Asks all programs and systems nicely to shut down. Wait a few seconds after doing this, to give them time to do shut down.)
[*]Alt+PrintScreen+I (Rudely kills all programs and systems that didn't manage to shut down in the previous step.)
[*]Alt+PrintScreen+S (Flush the cache to disk, to do its best to prevent data loss.)
[*]Alt+PrintScreen+U (Make all disks read-only, again to try to prevent data loss.)
[*]Alt+PrintScreen+B (Immediately reboot.)
[/LIST]
Remember REISUB for every time your Linux system hangs or otherwise prevents you from doing anything useful.
> **Timothy Taylor said:**
> Does that mean I need a new HDD or would a re-format and re-install do the trick?
It's impossible to say from the information given. What makes you suspect the disk — is it old? You might be right, given a quick perusal of an [internet search]("https://www.google.com/search?q=%22LVM+State%2C+Physical+volumes%3A+Not+OK+%28Bad%29%22").

If your disk supports [SMART]("https://en.wikipedia.org/wiki/S.M.A.R.T."), you can see its diagnostics. Open Disks (gnome-disks). Open its hamburger menu (the vertical ellipsis at the top right) and select *SMART Data & Self-Tests*. If this is greyed out, your disk doesn't support SMART; otherwise, check the diagnostics for a serious problem.

Something else that you can do is to look at the journal. After you have recovered, open a terminal and view the journal with the following command.
```
journalctl --since='10 minutes ago'
```
I've chosen "10 minutes ago", but you want to choose a time from when the computer was working correctly. I'm no expert, but see if you can spot an error.

---

### Post by Timothy Taylor on 2021-08-10
> **Paddy Landau said:**
> Remember REISUB for every time your Linux system hangs or otherwise prevents you from doing anything useful.

Very useful. Thanks! 

> **Paddy Landau said:**
> If your disk supports [SMART]("https://en.wikipedia.org/wiki/S.M.A.R.T."), you can see its diagnostics

I tried that: it lists most parameters as "old-age" or "pre-fail" but "Disk is OK".

> **Paddy Landau said:**
> Something else that you can do is to look at the journal. After you have recovered, open a terminal and view the journal with the following command.
```
journalctl --since='10 minutes ago'
```
I've chosen "10 minutes ago", but you want to choose a time from when the computer was working correctly. I'm no expert, but see if you can spot an error.

OK I'll have a look. Thanks again.

---

### Post by Impavidus on 2021-08-10
> **Paddy Landau said:**
> 
There is usually a way to force the system to shut down cleanly. It disables your desktop manager and goes directly to the kernel (I think) to do its work. Called [REISUB]("https://en.wikipedia.org/wiki/Magic_SysRq_key#Uses") (think BUSIER backwards), it goes like this (make a paper note for next time you need it):

[LIST=1]
[*]Alt+PrintScreen+R (Gives the base system direct access to your keyboard.) 
[*]Alt+PrintScreen+E (Asks all programs and systems nicely to shut down. Wait a few seconds after doing this, to give them time to do shut down.) 
[*]Alt+PrintScreen+I (Rudely kills all programs and systems that didn't manage to shut down in the previous step.) 
[*]Alt+PrintScreen+S (Flush the cache to disk, to do its best to prevent data loss.) 
[*]Alt+PrintScreen+U (Make all disks read-only, again to try to prevent data loss.) 
[*]Alt+PrintScreen+B (Immediately reboot.) 
[/LIST]
Remember REISUB for every time your Linux system hangs or otherwise prevents you from doing anything useful.

Also known as Raising Elephants Is So Utterly Boring, and you can make up your own mnemonic if you like. Actually, some of these functions have been disabled on Ubuntu as they enable attacks by people with keyboard access, so that only the SUB part works. That's usually sufficient to prevent filesystem damage, but doesn't allow you to gracefully terminate all applications. You can change it if you like: [https://askubuntu.com/questions/11002/alt-sysrq-reisub-doesnt-reboot-my-laptop/334292#334292](https://askubuntu.com/questions/11002/alt-sysrq-reisub-doesnt-reboot-my-laptop/334292#334292)

The key this is really about is the SysRq key. On many keyboards the SysRq key is no longer marked and it's usually the same key as PrintScreen, but not always. On my HP Probook laptop I have to use fn+delete. It's marked on my keyboard. Finally, if you're not on a qwerty keyboard, use the keys where REISUB would have been if it were a qwerty keyboard.

Some useful info on SMART: [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
Basically, you first ask it run a test (I suggest the long test), which may take a while (on my computer an hour), then view the results of that test. Make sure you actually run that test, or you may be viewing old data. Interpreting the results isn't always obvious and it pays off to monitor the numbers change over time. I run a check every few months. Data shows that my harddrive is getting old (it's 10 years), but still doing fine.

---

### Post by Timothy Taylor on 2021-08-10
Aha!
I got a BIOS blue screen saying no HDD found, so I had a look. I checked the drive cables and tried again = booted OK, but still wobbly and just locked if I tried system suspend.

I took my PC apart, cleaned everything. I found the BIOS backup battery was just 0.7V!  I wouldn't be surprised if that is involved in all this.

I reinstalled some apps that were playing up - all seems good so far.  Fingers crossed..

---

### Post by Timothy Taylor on 2021-08-10
.

---

### Post by Timothy Taylor on 2021-08-10
I spoke too soon - old problems are back!

Looking like I need a new HDD - but this is only 4 months old!
:-(

---

### Post by Paddy Landau on 2021-08-11
> **Timothy Taylor said:**
> I spoke too soon - old problems are back!
Bad luck, there.
> **Timothy Taylor said:**
> Looking like I need a new HDD - but this is only 4 months old!
If the disk is so new, the SMART diagnostics should not have been giving reports such as old-age or pre-fail. I think that you were sold a dud — did you buy it privately?

---

### Post by Impavidus on 2021-08-11
I think the tool mentions that some properties can be indicators of old age or pre-fail when they get high, but if the numbers are low, it's OK. So look at the actual numbers. For example, here some data from a smart test of my laptops harddrive from January 2019 (reporting only some lines):```
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   050    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0033   092   092   010    Pre-fail  Always       -       175
  7 Seek_Error_Rate         0x002f   100   100   050    Pre-fail  Always       -       0
  9 Power_On_Minutes        0x0032   042   042   000    Old_age   Always       -       390h+45m
183 Runtime_Bad_Block       0x0032   100   100   001    Old_age   Always       -       3
187 Reported_Uncorrect      0x0032   096   096   000    Old_age   Always       -       4
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   065   053   040    Old_age   Always       -       35 (Min/Max 14/40)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       27
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       36
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
```Current_Pending_Sector is an indicator of old age. When it begins to rise, your hard drive is almost dead. But it's zero here, so nothing to worry about.

The same output on the same hard drive, taken recently:```
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   050    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0033   090   090   010    Pre-fail  Always       -       211
  7 Seek_Error_Rate         0x002f   100   100   050    Pre-fail  Always       -       0
  9 Power_On_Minutes        0x0032   027   027   000    Old_age   Always       -       492h+27m
183 Runtime_Bad_Block       0x0032   100   100   001    Old_age   Always       -       3
187 Reported_Uncorrect      0x0032   096   096   000    Old_age   Always       -       4
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   072   053   040    Old_age   Always       -       28 (Min/Max 24/28)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       29
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       46
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
```
See how the Reallocated_Sector_Ct has increased? Now, this really is an old hard drive. I wonder how high I can let this number go before problems appear, but there are no problems yet, so if I had thrown away this hard drive when the reallocated sector count was at 175, I would have thrown it away at least 2.5 years early. I do keep proper backups. Also see the Reported_Uncorrect. It's at 4 and stays there. It's an indicator of old age, but I guess in this case only a production error. The Power_On_Minutes appear to be incorrect. It does measure something like power on time, but not in minutes.

---

### Post by Paddy Landau on 2021-08-11
> **Impavidus said:**
> … look at the actual numbers. …
That's interesting, Impavidus. Given that the OP's disk is a mere 4 months old, though, we wouldn't expect pre-fail and especially old-age, would we?

---

### Post by Impavidus on 2021-08-11
No, we wouldn't. We would expect all attributes of the old_age type to have low values.

---

### Post by TheFu on 2021-08-11
> **Paddy Landau said:**
> Bad luck, there.

If the disk is so new, the SMART diagnostics should not have been giving reports such as old-age or pre-fail. I think that you were sold a dud &#8212; did you buy it privately?

Brand new HDDs always report old-age and pre-fail for 95% of the SMART parameters.  I've checked brand new, retail, HDDs. They did.


There are steps to solving storage problems.
[LIST]
[*]Run fsck on all file systems
[*]Run a SMART test
[*]Run a SMART report
[*]Check the power and data cables
[*]Try a different SATA or USB port
[*]Connect the disk to another system, see if it is fine there.
[*]Connect another disk to the problem system, see if there are issues.
[/LIST]

All of this is a way to exclude and include specific parts of the system with issues. Slowly narrowing it down to just 1 component.
Problems could be just disk corruption due to a software bug or a bad cable. But it could be a disk that is starting to fail, bad data port, failing PSU, so each of those checks above are a way to determine if it is the disk or something else.


OH .... and always, always, always, check the system hardware and software log files for help with initial troubleshooting efforts.

---

### Post by Timothy Taylor on 2021-08-13
I've just installed 20.04.2 to a new HDD in my desktop PC.

I find that the system still locks up instead of suspending. Even Alt-PrtScr-B can't escape from this.  I see the same 
> LVM State, Physical volumes: Not OK (Bad)
in the system summary as in my OP.

I also find that my laptop can no longer recover from suspend, so I think something's broken in the latest update?  I have seen a few similar-themed threads.
I had planned to rebuild my system on the new HDD today.  Now I am wondering if I should be looking for a new OS altogether?

---

### Post by Paddy Landau on 2021-08-13
> **Timothy Taylor said:**
> I've just installed 20.04.2 to a new HDD in my desktop PC…
I've also been having [problems with suspending]("https://ubuntuforums.org/showthread.php?t=2465730") recently, to the extent that I've stopped suspending altogether.

Maybe it's a result of a recent upgrade.
> **Timothy Taylor said:**
> I am wondering if I should be looking for a new OS altogether?
I wonder if it's worth running Ubuntu or your proposed "new OS" from a Live CD, and seeing if suspend and resume work from there? I might do that myself if I get some time.

---

### Post by TheFu on 2021-08-13
If you boot into an older kernel, do things work?

I don't have any 20.04 systems that suspend, but I suspend an 18.04 laptop nightly and don't see any issues. That laptop is suspended now, can't ssh into it from here, but give me 15 minutes or so and I'll get the kernel version on it.  It is a 5.4.x kernel, which is what the base 20.04 runs.  My 20.04 desktop runs  
5.4.0-80-generic.  I don't have the HWE kernels.  A few weeks ago, the 5.8.x-HWE was upgraded to 5.11.x-HWE and 5.11 has been causing a number of issues. At least they are being reported in these forums.

Update: yep. It has the 5.4.0-80-generic kernel too.

---

### Post by Timothy Taylor on 2021-08-13
I notice something on my new HDD install: before the log-in screen appears, a screenful of error messages whizz past.
These say something with 'ACPI Error' and 'AE_NOT_FOUND' shortly before the login screen appears.  If I wasn't watching closely I'd have missed it.
No idea if this indicates something serious?

---

### Post by Timothy Taylor on 2021-08-13
deleted another duplicated post

---

### Post by Timothy Taylor on 2021-08-13
I was wondering about going back to 18.04, which was working fine.  I only upgraded to 20.04 because of the notice that 18.04 was EOL and would not get updates..

---

### Post by Paddy Landau on 2021-08-13
> **TheFu said:**
> If you boot into an older kernel, do things work?
Good question!

The latest kernel for Ubuntu 20.04 is 5.11.0-25, and this breaks on suspend.
I just booted into the previous kernel, 5.8.0-63, and suspend works!

So, yes, it's to do with the kernel!

@Timothy Taylor — So, it's to do with the kernel, not the distro.

Now, I just have to find out where to report it. @TheFu, do you know where we report this sort of error?

---

### Post by Timothy Taylor on 2021-08-13
> **Paddy Landau said:**
> @Timothy Taylor — So, it's to do with the kernel, not the distro.

That's good to hear.
I've never experienced toxic updates with Ubuntu, only Windoze..

---

### Post by TheFu on 2021-08-13
> **Timothy Taylor said:**
> That's good to hear.
I've never experienced toxic updates with Ubuntu, only Windoze..

I've been burned a few times by new code and by incorrect dependencies.  Earlier today, in another thread here, someone removed their LAMP stack and it took their desktop (all GUI stuff) install with it.  They posted logs.  It made no sense, but the logs are clear.

There are some really dumb dependency issues that I've noticed.  Why does a a hypervisor need bluetooth? It doesn't. Ever, yet that dependency was added a year ago for some reason.

When MariaDB was first available, a bad dependency removed it, installed mysql-server, and trashed a project management server here.  Took me about 3 hrs to figure that one out.

Automatic patching is a terrible idea.
Patching without logging it means never really knowing what happened.  Always log your patch sessions.
Patching mid-week is asking for days of downtime too.  I only patch over weekends.  The busier my plans are, the more likely something is to fail. The main servers I have to keep running are really easy to restore, which helps.  If something bad happens, I can get an email gateway system working from scratch in about 15 minutes. Even if the full email server takes a few days to fix an issue, the gateway can hold all inbound email until the real server is up and ready to accept it.  It should go without saying, but there is sufficient hardware here to put a static blog-clone or email gateway onto in 30 min or less total for both.  Heck, both can run off a single raspberry pi, if necessary.

Having fallback plans for really important things is a good idea.

Anyway, just boot using older kernels for the next week, then see if a fix has been pushed out.
For kernel issues, look in the bug reporting system for Canonical and let them deal with the upstream.  ***New is the enemy of stable***. I always say that.

---

### Post by Paddy Landau on 2021-08-13
> **Timothy Taylor said:**
> I've never experienced toxic updates with Ubuntu…
In fairness, it's a Linux kernel update, not an Ubuntu update.

---

### Post by Timothy Taylor on 2021-08-13
> **Paddy Landau said:**
> If the disk is so new, the SMART diagnostics should not have been giving reports such as old-age or pre-fail. I think that you were sold a dud — did you buy it privately?

Yes, it was a 'recertified' drive from ebay.

---

### Post by Paddy Landau on 2021-08-14
> **TheFu said:**
> I've been burned a few times by new code…
I have read update problems on the forums. I've been lucky in that I've never had a serious problem, perhaps because I use my computer for only simple things.
> **TheFu said:**
> For kernel issues, look in the bug reporting system for Canonical and let them deal with the upstream.
Thanks for the suggestion. It turns out that this has already been reported.

@Timothy Taylor — please [visit the bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1925843"), and log in (create an account if needed). Vote for the bug: Press the green link at the left near the top and select, "Yes, it affects me." The more people who vote for the bug, the higher the priority.

---

### Post by rbmorse on 2021-08-14
> **Timothy Taylor said:**
> Yes, it was a 'recertified' drive from ebay.

Toss it.  

If you don't, from this day forward that piece of kit will be suspect for every problem ranging from the system not booting to the sun failing to rise in the East. You don't need that kind of uncertainty or aggravation.

---

### Post by Timothy Taylor on 2021-08-15
> **Paddy Landau said:**
> @Timothy Taylor — please [visit the bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1925843"), and log in (create an account if needed). Vote for the bug: Press the green link at the left near the top and select, "Yes, it affects me." The more people who vote for the bug, the higher the priority.

Done.

I did the same for the  [ACPI Error]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1892909") I noticed on the fresh install. I gather that this bug results from a problem with ACPI code (?) and my only solution may be to update my BIOS.  
I think this must've been happening with 20.04 my old HDD, but I never noticed because my PC appeared to boot normally ?

---

### Post by Timothy Taylor on 2021-12-07
Update:
I have replaced my Nvidia GeForce 210 graphics card with a AMD Radeon HD 8490.  My PC now starts and run faster and suspend works again.  I guess the problem was related to the nouveau drivers for the Nvidia card?  Anyway - all sorted now.
:)

---

### Post by kurt18947 on 2021-12-10
> **Timothy Taylor said:**
> Update:
I have replaced my Nvidia GeForce 210 graphics card with a AMD Radeon HD 8490.  My PC now starts and run faster and suspend works again.  I guess the problem was related to the nouveau drivers for the Nvidia card?  Anyway - all sorted now.
:)

I had that problem with with same video card. Suspend only works when using Nvidia's driver. I've had good luck with AMD though I had a Ryzen 3 2200G that had significant issues with Ubuntu 18.04, as in it would lock up hard. It seemed okay with 20.04.

---

