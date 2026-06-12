---
title: "Timeshift not retaining Include/Exclude patterns?"
date: 2022-03-06
forum: General Help
---

### Post by wyattwhiteeagle on 2022-03-06
Why is Timeshift not retaining my custom Include/Exclude patterns?

I open Timeshift.
Click on settings.
Click on Filters.
Click "Add".
I add 3 things...
```
Include /home/wyatt/Desktop/***
Exclude /home/.cache
Exclude /home/.local/share/Trash
```
Then I click ok.
Then I click on filters and it's back to the default.

---

### Post by dragonfly41 on 2022-03-06
I believe that your filters example should be .. (one * instead of three) .. [corrected]

Include /home/wyatt/Desktop/*
Exclude /home/wyatt/.cache
Exclude /home/wyatt/.local/share/Trash

---

### Post by wyattwhiteeagle on 2022-03-06
> **dragonfly41 said:**
> I believe that your filters example should be .. (one * instead of three) .. [corrected]

Include /home/wyatt/Desktop/*
Exclude /home/wyatt/.cache
Exclude /home/wyatt/.local/share/Trash
Making the corrections, It still isn't retaining the settings.

I'm wondering if I should go to BackInTime for my "simple system restore's".

---

### Post by dragonfly41 on 2022-03-06
I am looking at my (old) TimeShift app .. not used for some time when I was experimenting ..
and when I view Include/Exclude table I do see ** syntax. But if you click on Summary you see * syntax.
I am not able to remove old patterns.

So I'm not sure what is going on.

---

### Post by wyattwhiteeagle on 2022-03-06
> **dragonfly41 said:**
> I am looking at my (old) TimeShift app .. not used for some time when I was experimenting ..
and when I view Include/Exclude table I do see ** syntax. But if you click on Summary you see * syntax.
I am not able to remove old patterns.

So I'm not sure what is going on.

What are you currently using now in place of Timeshift (besides rdiff-backup)?

---

### Post by dragonfly41 on 2022-03-06
First, I have just searched around and read that TimeShift settings are in

/etc/timeshift.json

Second, as explained in earlier discussions, my *ambitions* are to build a general purpose desktop/cloud services automation tool to apply to many processes, rdiff-backup being just one small example.

There are many, many examples of scripts dotted throughout this forum, and other forums, and I also experiment with many applications.

I referred to an earlier basic tool named clicompanion2 which holds a repository of clicommands. The later version (clicompanion2) works with Python3.

This leads to the topic of desktop automation where the control of the desktop is taken over by an intelligent bot to "drive" the desktop UI.

Before we say &#8220;Jack Robinson&#8221; the counter argument will come up that the classical Unix scripting can be used for tasks, so why bother?  And so the endless process of copying and pasting commands and bash scripts from forums continues. 

Even worse, if we rely on YouTube tutorials we (of ageing eyesight) have to contend with peering at screenshots of commands and code.

Also there is the consideration of handing over acquired knowledge of desktop processes  to a successor

The earlier Actiona discussion is an example of a &#8220;booting&#8221; application (or bot) which can launch a higher level tool .. which floats above the chosen application window. I have elected to use Electron app for this higher intelligent layer.

So Actiona can be thought of as a &#8220;boot&#8221; layer to interact with UI.

Those of a certain age will remember the old Microsoft and Apple helper widgets. They could be annoying and were only actors on the screen.

So to answer your question I am developing (largely for my own development purposes) a tool which hovers above the desktop for each application and automates multiple tasks. Into this tool I will inject commands to drive different processes.

Just try learning Blender UI for example.

This tool will be cross-platform.  Linux and Windows.

And just to illustrate that this is not such a daft idea, this blog link came into my mailbox today:

[https://www.ibm.com/cloud/blog/can-intelligent-automation-address-some-of-the-supply-chains-labor-woes](https://www.ibm.com/cloud/blog/can-intelligent-automation-address-some-of-the-supply-chains-labor-woes)

I will point you to an earlier tool Aptik but this Ubuntu developer now charges bucks for the latest. The earlier version is free.

[https://www.makeuseof.com/backup-linux-with-aptik/](https://www.makeuseof.com/backup-linux-with-aptik/)

When I have an Actiona microtool for just rdiff-backup I will post if, if you still retain Actiona.

---

### Post by Tadaen_Sylvermane on 2022-03-06
[https://forums.linuxmint.com/viewtopic.php?t=299573](https://forums.linuxmint.com/viewtopic.php?t=299573)

Timeshift isn't designed for keeping up with personal files. This thread has a few good points in it I thought.

---

### Post by dragonfly41 on 2022-03-06
I intend to add borg backup to my toolset.

---

### Post by wyattwhiteeagle on 2022-03-06
Wait...
Actiona is a "Booting" bot that hi-jacks my desktop UI by launching a higher level tool leaving me with no control over my system?

Am I understanding this clearly?

> **dragonfly41 said:**
> First, I have just searched around and read that TimeShift settings are in

/etc/timeshift.json

timeshift.json is a "read-only" file containing the following...
```
{
  "backup_device_uuid" : "3a587504-92ab-4e58-801e-421eda63b4ee",
  "parent_device_uuid" : "",
  "do_first_run" : "false",
  "btrfs_mode" : "false",
  "include_btrfs_home_for_backup" : "false",
  "include_btrfs_home_for_restore" : "false",
  "stop_cron_emails" : "true",
  "btrfs_use_qgroup" : "true",
  "schedule_monthly" : "false",
  "schedule_weekly" : "false",
  "schedule_daily" : "true",
  "schedule_hourly" : "false",
  "schedule_boot" : "false",
  "count_monthly" : "2",
  "count_weekly" : "3",
  "count_daily" : "5",
  "count_hourly" : "6",
  "count_boot" : "5",
  "snapshot_size" : "0",
  "snapshot_count" : "175971",
  "date_format" : "%Y-%m-%d %H:%M:%S",
  "exclude" : [
    "+ /home/wyatt/.**",
    "/root/**"
  ],
  "exclude-apps" : [
  ]
}

```
> **dragonfly41 said:**
> Second, as explained in earlier discussions, my *ambitions* are to build a general purpose desktop/cloud services automation tool to apply to many processes, rdiff-backup being just one small example.

There are many, many examples of scripts dotted throughout this forum, and other forums, and I also experiment with many applications.

I referred to an earlier basic tool named clicompanion2 which holds a repository of clicommands. The later version (clicompanion2) works with Python3.

This leads to the topic of desktop automation where the control of the desktop is taken over by an intelligent bot to "drive" the desktop UI.

Before we say &#8220;Jack Robinson&#8221; the counter argument will come up that the classical Unix scripting can be used for tasks, so why bother?  And so the endless process of copying and pasting commands and bash scripts from forums continues. 

Even worse, if we rely on YouTube tutorials we (of ageing eyesight) have to contend with peering at screenshots of commands and code.

Also there is the consideration of handing over acquired knowledge of desktop processes  to a successor

The earlier Actiona discussion is an example of a &#8220;booting&#8221; application (or bot) which can launch a higher level tool .. which floats above the chosen application window. I have elected to use Electron app for this higher intelligent layer.

So Actiona can be thought of as a &#8220;boot&#8221; layer to interact with UI.

Those of a certain age will remember the old Microsoft and Apple helper widgets. They could be annoying and were only actors on the screen.

So to answer your question I am developing (largely for my own development purposes) a tool which hovers above the desktop for each application and automates multiple tasks. Into this tool I will inject commands to drive different processes.

Just try learning Blender UI for example.

This tool will be cross-platform.  Linux and Windows.

And just to illustrate that this is not such a daft idea, this blog link came into my mailbox today:

[https://www.ibm.com/cloud/blog/can-intelligent-automation-address-some-of-the-supply-chains-labor-woes](https://www.ibm.com/cloud/blog/can-intelligent-automation-address-some-of-the-supply-chains-labor-woes)

I will point you to an earlier tool Aptik but this Ubuntu developer now charges bucks for the latest. The earlier version is free.

[https://www.makeuseof.com/backup-linux-with-aptik/](https://www.makeuseof.com/backup-linux-with-aptik/)

When I have an Actiona microtool for just rdiff-backup I will post if, if you still retain Actiona.

---

### Post by wyattwhiteeagle on 2022-03-06
> **Tadaen_Sylvermane said:**
> [https://forums.linuxmint.com/viewtopic.php?t=299573](https://forums.linuxmint.com/viewtopic.php?t=299573)

Timeshift isn't designed for keeping up with personal files. This thread has a few good points in it I thought.

Thank you

---

### Post by GhX6GZMB on 2022-03-06
I had the same problems with Timeshift in the beginning. There seems to be a bug in the include/exclude functionality.
I found two solutions:
1: add a "dummy" exclude folder/file at the end of your exclude list (the last entry isn't properly recognized by Timeshift). This is unsatisfactory, though.
2: edit /etc/timeshift.json manually (_NOT_ /etc/timeshift/timeshift.json)

I attach a screenprint of my Timeshift setup and one of the /etc/timeshift.json file.

Timeshift works for me 100% reliably, both for ad hoc backup/restores (when experimenting) and for a complete bare metal reinstall.
/home is a different issue, there I use BackInTime.

PS/EDIT: I used to think adding $HOME/Desktop to the backup is a good idea. It may be if it's a single-user machine. Otherwise it belongs in the /home backup. I found out along the way...

---

### Post by dragonfly41 on 2022-03-07
> 
Wait...
Actiona is a "Booting" bot that hi-jacks my desktop UI by launching a higher 
level tool leaving me with no control over my system?


Am I understanding this clearly?


To answer this:
Not really. There is no intent on "highjacking" user control.
The user always retains control.
The higher level depends on what automation is undertaken.
If it is a basic automation task the default Actiona Message Box is adequate (HTML format).
If we wish to present more complex output we can publish to our browser, or a  localhost server instance.
we can simply use command: php -S localhost:8000 $myoutput  .. (file composed within Actiona)
For example install agedu and publish results to a browser.
Or visualise history.


Perhaps my choice of description "booting bot" was not the best since some bots can be malicious.


Similar goals in some ways to "Composer" where multiple assets (packages, 
tools) can be orchestrated at desktop level.


[https://getcomposer.org/](https://getcomposer.org/)




Another automation initiative is SikuliX which started at MIT.


[http://sikulix.com/](http://sikulix.com/)


I have decided to invest my time in developing a gallery of examples, since 
replying to such multiple discussions is not the best way of promoting UI automation 
ideas which are being developed in parallel. 
[COLOR=#000000]

[/COLOR]

---

### Post by wyattwhiteeagle on 2022-03-08
> **ml9104 said:**
> I had the same problems with Timeshift in the beginning. There seems to be a bug in the include/exclude functionality.
I found two solutions:
1: add a "dummy" exclude folder/file at the end of your exclude list (the last entry isn't properly recognized by Timeshift). This is unsatisfactory, though.
2: edit /etc/timeshift.json manually (_NOT_ /etc/timeshift/timeshift.json)

I attach a screenprint of my Timeshift setup and one of the /etc/timeshift.json file.

Timeshift works for me 100% reliably, both for ad hoc backup/restores (when experimenting) and for a complete bare metal reinstall.
/home is a different issue, there I use BackInTime.

PS/EDIT: I used to think adding $HOME/Desktop to the backup is a good idea. It may be if it's a single-user machine. Otherwise it belongs in the /home backup. I found out along the way...

If sudo won't allow me to manually edit /etc/timeshift.json...then what will?
```

wyatt@wyatt-Latitude-E5400:~$ sudo /etc/timeshift.json
[sudo] password for wyatt: 
sudo: /etc/timeshift.json: command not found
wyatt@wyatt-Latitude-E5400:~$ 



```

---

### Post by deadflowr on 2022-03-08
You need to use a text editor of some sort.
*sudo /etc/timeshift.json* means it's trying to run some program called /etc/timeshift.json, which is not a thing.
try
```
sudoedit /etc/timeshift.json
```
sudoedit will use the set editor, which is nano by default.
(But it can be set any other terminal-based editor such as vi or ed, or whatever.)


Anther option is to copy the file over to you home folder and use a regular text editor, 
that method won't require root to do the editing.
Then copy it back after the edit.
(Maybe also make a backup copy of the original in home before editing it, calling it something like timeshift.json-original.
That way if the edit goes wrong you can revert back to that original version easily.)

---

