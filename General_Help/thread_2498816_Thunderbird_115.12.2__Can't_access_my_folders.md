---
title: "Thunderbird 115.12.2 : Can't access my folders"
date: 2024-06-28
forum: General Help
---

### Post by trenien2 on 2024-06-28
Hi,
as it says in the title. I've just upgraded Thunderbird to 115.12.2, and now I can't access the folders.
To be precise : Thunderbird appears to works (the number of unread messages is shown as it should), but I see neither headers nor mail content and a right click on any of the folders doesn't open a contextual menu.

What to do now ?

Thanks

---

### Post by TheFu on 2024-06-28
Snap package or debian package?
snap packages have constraints that block access to some areas on the file system.  Do a little reading about that.

---

### Post by trenien2 on 2024-06-28
Debian, so I guess not ?

---

### Post by deadflowr on 2024-06-28
It's either from a PPA or flatpak.
The version in Ubuntu is only 115.12.0

edit:
or maybe from -proposed?

---

### Post by ajgreeny on 2024-06-28
> **trenien2 said:**
> Debian, so I guess not ?
Do you mean that you're actually running Debian, not.Ubuntu, and if it's Debian, which version, Stable, Testing or Unstable (Sid)?
Tell us in full detail all about your OS and how you install Thunderbird.

I am using Xubuntu 24.04 and to avoid the snap version I download the thunderbird.tar.bz direct from Mozilla and run the application direct from the executable in that.
It is currently version 115.12.2, the same as yours and is running totally normally, so it is not simply the version that is your problem.

---

### Post by trenien2 on 2024-06-28
I was replying directly after reading.
Deb package from the ubuntu-mozillateam (not quite sure how to check whether it's backported)

---

### Post by TheFu on 2024-06-28
I'm using 115.12.0 and haven't seen any issues on Linux Mint 21.2 (that's 22.04-based).  I switched from Ubuntu on my main desktop system to avoid unwanted, forced, snaps, wayland, and ... 20 other small issues.  I should move to Mint 21.3.

I'm only connected to email servers that I run/manage, so I'm fairly certain Thunderbird is still following standards.
**Update:**
I patched on Saturday.  Still have 
```
thunderbird               1:115.12.0+build3-0ubuntu0.22.04.1
```
so I'm uncertain how you are getting 115.12.**2**.

---

### Post by trenien2 on 2024-06-28
The thing is, I haven't changed anything except updating Thunderbird. So something has gone wrong (and it's 115.12.**2**)
Question is, what ?

---

### Post by trenien2 on 2024-06-29
I'll add I haven't found any parameter that could explain the problem.

---

### Post by ajgreeny on 2024-06-29
Why not try the .tar.bz archive that I mentioned in post #5.

Backup yout hidden .thunderbird folder first then download that archive, extract it and run thunderbird by double clicking the executable file in that.
 It should find your current configuration and run just like before, showing all your emails etc etc.

---

### Post by dragonfly41 on 2024-06-29
As a Thunderbird 115.12 user on Ubuntu 22.04 I read the tip from @theFu in post#7.
I too need to stay with Xorg because I need desktop orchestration by UI scripting. Wayland does not allow that I understand.
Thunderbird reliability is absolutely key to my workflow (personal and now business) so my thoughts from reading this discussion are to take note and now move from dual boot to triple boot with added Mint 21.3 as @TheFu suggests. Having external powered dual docking bay makes that deployment easier and rEFInd can switch between OS.
Windows 10
Ubuntu 22.04
Mint 21.3

All with synchronised Thunderbird profiles.

Returning to the main OP point "[COLOR=#000000]I haven't found any parameter that could explain the problem."  I would start by researching Thunderbird > Tools > Developer Tools, Error console etc. to look for clues.[/COLOR]

---

### Post by trenien2 on 2024-06-29
Well, the tar does show the mail, but it didn't find the config files, I had to do the mail setup again.
As a stopgap measure, until I find out what went wrong.

---

### Post by trenien2 on 2024-06-29
I didn't pay attention to the Wayland/X11 problem (I also had weird minor display artifacts). That might somehow be it, I'll take a look.

---

### Post by trenien2 on 2024-06-29
Well, nope, This isn't it : still X11.

---

### Post by trenien2 on 2024-06-29
Well, looking at the developer console, I get a few warnings and the following error :
```
Uncaught TypeError: multiMessageBrowser.contentWindow.gMessageSummary is undefined    clearMessages chrome://messenger/content/about3Pane.js:6047

    clearAll chrome://messenger/content/about3Pane.js:5974

    _onSelect chrome://messenger/content/about3Pane.js:2527

    handleEvent chrome://messenger/content/about3Pane.js:1597

    <anonymous> chrome://messenger/content/about3Pane.js:128



[about3Pane.js:6047:5]("chrome://messenger/content/about3Pane.js")    clearMessages chrome://messenger/content/about3Pane.js:6047

    clearAll chrome://messenger/content/about3Pane.js:5974

    _onSelect chrome://messenger/content/about3Pane.js:2527

    handleEvent chrome://messenger/content/about3Pane.js:1597

    <anonyme> chrome://messenger/content/about3Pane.js:128

    AsyncFunctionNext self-hosted:852






```
Way beyond my understanding.

---

### Post by dragonfly41 on 2024-06-29
I freely admit these days with multiple balls being juggled that I call on AI assistant to do the heavy lifting for me to then diagnose deeper. In addition to human responses. All hands to the pump.


I subscribe to Phind.com.


I just posed this Query (be precise in Querying or Prompting).
> ThunderBird 115.12.**2** on Ubuntu is not displaying mail headers or content and right click on ThunderBird folders does not open context menu.
What diagnostic steps should follow?
This spat out a number of suggestions.
Including
[B]
Check For Upgrades[/B]
```
sudo apt update && sudo apt upgrade thunderbird
```

**Run Safe Mode**

[LIST]
[*]Open Thunderbird.
[*]Click on "Help" > "Restart with Add-ons Disabled...".
[*]Follow the prompts to start Thunderbird in Safe Mode.
[/LIST]
**New Profile**

[LIST]
[*]Close Thunderbird.
[*]Run thunderbird -ProfileManager in the terminal.
[*]Click "Create Profile", give it a name, and follow the prompts.
[*]Start Thunderbird with the new profile and check if the issue persists.
[/LIST]
**Check File Permissions**
Incorrect file permissions can prevent Thunderbird from accessing necessary files, leading to display issues.

[LIST]
[*]Navigate to your Thunderbird profile folder (usually located at ~/.thunderbird/xxxxxxxx.default).
[*]Ensure that your user account has read/write access to this directory and its contents.
[/LIST]
You can adjust permissions using the chmod command if necessary, but be cautious and ensure you understand the implications.


**Reinstall**
If none of the above steps work, consider reinstalling Thunderbird. This can resolve issues caused by corrupted application files.
sudo apt remove --purge thunderbird sudo apt install thunderbird
If the problem persists, consult Thunderbird's log files for any error messages that might indicate what's going wrong. These logs can usually be found within your profile folder under ~/.thunderbird/xxxxxxxx.default/Logs.
Additionally, searching through or asking questions on forums such as Mozilla Support or Ubuntu Forums can provide insights from users who may have faced similar issues.
By following these diagnostic steps, you should be able to identify and possibly resolve the issue with Thunderbird not displaying mail headers or content and the right-click context menu not functioning properly on Ubuntu.

END OF PHIND ADVICE


Next I used as Prompt the error message you posted which was beyond your ken.
When submitting error messages it is very important to place the message between CODE tags


```
Uncaught TypeError: multiMessageBrowser.contentWindow.gMessageSummary is undefined    clearMessages chrome://messenger/content/about3Pane.js:6047
    clearAll chrome://messenger/content/about3Pane.js:5974
    _onSelect chrome://messenger/content/about3Pane.js:2527
    handleEvent chrome://messenger/content/about3Pane.js:1597
    <anonymous> chrome://messenger/content/about3Pane.js:128
    
```


    
    
    Conclusion: Phind..com is a helpful AI assistant to call on but does not substitute for the human intuition in this forum. There are good ideas found above.

---

### Post by trenien2 on 2024-06-29
Well, problem solved, although I'm not exactly sure why : restarting thunderbird in safe mode brought back everything (so there was an extension I had forgotten about, I guess). On the other hand, although I did nothing else, normal function resumed when restarting in normal mode ?!?

Oh, well...

---

### Post by elsie555 on 2024-07-01
If Thunderbird 115.12.2 isn't showing folders, try these steps:

[LIST=1]
[*]Restart Thunderbird by closing and reopening the application.
[*]Start Thunderbird in Safe Mode by holding Shift while launching to see if the issue persists.
[*]Right-click on the folder (if possible), select Properties, and click Repair Folder.
[*]Disable any add-ons that might be causing the issue.
[*]Delete the global-messages-db.sqlite file from your profile folder to force reindexing.
[*]Create a new profile using Thunderbird Profile Manager to see if the issue is with your profile.
[/LIST]
If none of these work[,]("https://www.healthquestbilling.com/services/") consider reinstalling Thunderbird or checking for updates.

---

### Post by dragonfly41 on 2024-07-01
Your helpful pointers #3 and #5 I had missed in my research when I posted in #16 above.
In particular the "folder repair" open (right click on subfolders not the main account folder I now see). But OP is still puzzled why switching to Safe Mode and then back again "repaired" the setup (marked as SOLVED).
Perhaps we need something like "Boot Repair" script to go through the Thunderbird workflow since it is mission critical.

---

