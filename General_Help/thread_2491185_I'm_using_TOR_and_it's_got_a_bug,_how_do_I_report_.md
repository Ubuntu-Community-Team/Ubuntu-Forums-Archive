---
title: "I'm using TOR and it's got a bug, how do I report this bug to the TOR developers?"
date: 2023-09-28
forum: General Help
---

### Post by SpaceManJack on 2023-09-28
I think the bug is only for Linux users who use TOR. I have wiped TOR  from my system and reinstalled it and the bug still persists. You know  how you can choose which folder downloads will download to? Well  typically it will just automatically start downloading to your folder of  choice but my TOR browser doesn't do that for me at all. Ok so in TOR  it will typically just start downloading the files to whatever folder  you manually selected (it's smart like that, it seems to detect oh you  want to download your files to this folder ok I'll just automatically  download to this folder from now on, this is very handy when you're downloading  multiple files in one session) except starting about a few months ago my  TOR browser quit doing that. 

TOR seemed to be intelligent in that it would detect which folder you  were wanting to download to and it'd automatically select that folder  for you next time you went to download a file (this was extremely handy  when you were downloading multiple files over and over again), do you  understand what I'm trying to say? Well starting about a few months ago  TOR quit doing that for me, now it only downloads to just the standard  folder every single time, how it would intelligently detect which folder  I was wanting to download to is gone. I deleted TOR and reinstalled it  and the bug still persists. Who should I report this bug to?

TOR seems to be intelligent in that it would detect which folder you  wanted to download to and then it'd automatically select the folder for  you when you went to download something, it doesn't do this for me  anymore at all, this is a bug right? And yes I've already looked at the  settings.

---

### Post by MAFoElffen on 2023-09-28
I'm assuming this is the thread you want an answer in, and the duplicate at [https://ubuntuforums.org/showthread.php?t=2491184](https://ubuntuforums.org/showthread.php?t=2491184) you request to have deleted(?)

If you installed Tor from the Ubuntu Repo package, then you would report it through Ubuntu Lauchpad via
```

ubuntu-bug tor

```
If you installed it though packages directly from torproject.org, then: [https://support.torproject.org/#misc_bug-or-feedback](https://support.torproject.org/#misc_bug-or-feedback)

---

### Post by SpaceManJack on 2023-09-30
> **MAFoElffen said:**
> I'm assuming this is the thread you want an answer in, and the duplicate at [https://ubuntuforums.org/showthread.php?t=2491184](https://ubuntuforums.org/showthread.php?t=2491184) you request to have deleted(?)

If you installed Tor from the Ubuntu Repo package, then you would report it through Ubuntu Lauchpad via
```

ubuntu-bug tor

```
If you installed it though packages directly from torproject.org, then: [https://support.torproject.org/#misc_bug-or-feedback](https://support.torproject.org/#misc_bug-or-feedback)

I manually installed TOR using flathub, if you go here [https://flathub.org/apps/com.github.micahflee.torbrowser-launcher](https://flathub.org/apps/com.github.micahflee.torbrowser-launcher) there's an option for a manual install of TOR if you click the check mark. So should I report this bug to micahflee on github then? So I'm not supposed to report this bug directly to the TOR developers?

Do you use TOR at all, what I'm experiencing is a bug right? I gave a pretty good explanation of it. That's a bug right?

---

### Post by guiverc on 2023-09-30
[TOR]("https://packages.ubuntu.com/lunar/tor") is the *anonymizing overlay network for TCP* and relates to networking.

The [TOR BROWSER]("https://packages.ubuntu.com/lunar/torbrowser-launcher") is a different package, a modified version of firefox that will use the TOR network.

You mention TOR but seem to be talking about the TOR BROWSER itself.

if reporting bugs, report to the correct tool.

FYI:  I also don't think what you're describing is a bug, but a design choice that was intended to improve security, as it allows easier *confinement* and reduces the chance that an impacted *tor browser* can touch your other files (*I've not read the reason given in the code for the change; this is just my assumption for it*).

---

### Post by SpaceManJack on 2023-09-30
> **guiverc said:**
> [TOR]("https://packages.ubuntu.com/lunar/tor") is the *anonymizing overlay network for TCP* and relates to networking.

The [TOR BROWSER]("https://packages.ubuntu.com/lunar/torbrowser-launcher") is a different package, a modified version of firefox that will use the TOR network.

You mention TOR but seem to be talking about the TOR BROWSER itself.

if reporting bugs, report to the correct tool.

FYI:  I also don't think what you're describing is a bug, but a design choice that was intended to improve security, as it allows easier *confinement* and reduces the chance that an impacted *tor browser* can touch your other files (*I've not read the reason given in the code for the change; this is just my assumption for it*).

Well I know it's a bug cause I've been using TOR browser on Linux for a while now and it always did that but then it stopped doing that suddenly a couple of months ago. Also I didn't mention this but when I go into settings and go to "Downloads" you can choose which folder you want your files saved to, the default folder is downloads but when I choose a different folder it will literally cause TOR to crash for me, nothing will download at all. To fix this I have to delete TOR browser and reinstall it and not mess with it. So yeah it's definitely bugged.

So say I have just freshly installed the TOR browser, now I'm not going to mess with any of the settings, so I won't touch the settings at all, now if I just start downloading a bunch of files and manually choose the same folder for the downloads to be downloaded to, TOR seems to intelligently detect which folder I'd like my downloads to go to so next time it'll just automatically select that particular folder for me and all I have to do is click the download button and commence the download. TOR browser has always done this for me and I have used TOR for years now. I used to use TOR on Windows and this is how it behaved for me. I have used the TOR browser for years and it always did this for me whether on Windows or Linux but it just stopped doing this about a couple of months ago.

And like I said if I go into the settings and choose the folder which I'd like it to download for me TOR will literally crash and nothing will download at all, and then I have to delete TOR and reinstall it. So that's why I'm here asking for help.

---

### Post by #&amp;thj^% on 2023-09-30
> **scott130 said:**
> 

And like I said if I go into the settings and choose the folder which I'd like it to download for me TOR will literally crash and nothing will download at all, and then I have to delete TOR and reinstall it. So that's why I'm here asking for help.

I'm not seeing that at all see screenshot.
```
flatpak list | grep torbrowser
Tor Browser Launcher	com.github.micahflee.torbrowser-launcher	0.3.6	stable	system

```
This is accurate:
> **guiverc said:**
> 
FYI:  I also don't think what you're describing is a bug, but a design choice that was intended to improve security, as it allows easier *confinement* and reduces the chance that an impacted *tor browser* can touch your other files (*I've not read the reason given in the code for the change; this is just my assumption for it*).

---

### Post by SpaceManJack on 2023-10-07
> **1fallen said:**
> I'm not seeing that at all see screenshot.
```
flatpak list | grep torbrowser
Tor Browser Launcher    com.github.micahflee.torbrowser-launcher    0.3.6    stable    system

```
This is accurate:

Who cares if it's stable, they may not even know that I'm experiencing this bug at all. Maybe I'm experiencing one of those rare bugs.

I mean are you someone whose been using TOR for years and years like I have? I used to use TOR on Windows for many years and then a couple of years ago I switched to Ubuntu, it's as I described previously in perfect detail, it seems TOR would automatically detect which folder you wanted your downloads saved to and it would automatically pick that one for you the next time you went to download something, and of course it would reset with each new TOR session, so when you first started your TOR session it'd download to the default "Downloads" folder but if you selected a different folder it'd intelligently detect which folder you'd like to save your files to and it would just automatically select that folder for you (I mean have you been using TOR for years like I have, are you saying you've never seen TOR do this?), it did this on Windows and it did this on Linux as well, but it stopped doing this about a couple of months ago. And here's how I know my TOR is definitely bugging out.
 
When you launch TOR go into settings and scroll down to Files and Applications where you'll see Downloads, there you'll see "Save files to" you can manually choose the folder you want your downloads saved to. The default folder is the "Downloads" folder but when I change this, I won't be able to download anything at all, I'll try to download something but it won't download, it'll literally break my TOR and the only way I can fix it is to delete TOR and reinstall it. So this is how I know I'm experiencing a major bug.

So should I report this to micahflee? Do I go contact him on github? Thanks.

---

### Post by #&amp;thj^% on 2023-10-07
> **scott130 said:**
> 
I mean are you someone whose been using TOR for years and years like I have? 
(I mean have you been using TOR for years like I have, are you saying you've never seen TOR do this?), it did this on Windows and it did this on Linux as well, but it stopped doing this about a couple of months ago. And here's how I know my TOR is definitely bugging out.
 


So should I report this to micahflee? Do I go contact him on github? Thanks.

I've been around since 2005, strictly a Linux user, And maybe I'm getting older now but I just don't remember torbrowser ever allowing a different Download Folder.
Flatpak default folder:
```
*ls /home/me/.var/app/com.github.micahflee.torbrowser-launcher/cache/torbrowser/download/
release.xml
tor-browser-linux64-12.5.2_ALL.tar.xz
tor-browser-linux64-12.5.2_ALL.tar.xz.asc

```
I can build folders as already shown inside of Downloads
But it is not a bug, but yes feel free to ask @ micahflee for Flatpak installs or:
```
apt policy torbrowser-launcher
torbrowser-launcher:
  Installed: (none)
  Candidate: 0.3.6-2
  Version table:
     0.3.6-2 500
        500 http://archive.ubuntu.com/ubuntu mantic/universe amd64 Packages

```
Ubuntu for the above stock installer.
And if you have a PPA for a source you would ask here: [https://support.torproject.org/apt/tor-deb-repo/](https://support.torproject.org/apt/tor-deb-repo/)
**EDIT: So it seems I'm wrong,** with the flatpak application I can choose folders, but you have tick the box ask where to save to.
And now I see a prompt for choices as well.
See screenshot

---

### Post by SpaceManJack on 2023-10-13
> **1fallen said:**
> I've been around since 2005, strictly a Linux user, And maybe I'm getting older now but I just don't remember torbrowser ever allowing a different Download Folder.
Flatpak default folder:
```
*ls /home/me/.var/app/com.github.micahflee.torbrowser-launcher/cache/torbrowser/download/
release.xml
tor-browser-linux64-12.5.2_ALL.tar.xz
tor-browser-linux64-12.5.2_ALL.tar.xz.asc

```
I can build folders as already shown inside of Downloads
But it is not a bug, but yes feel free to ask @ micahflee for Flatpak installs or:
```
apt policy torbrowser-launcher
torbrowser-launcher:
  Installed: (none)
  Candidate: 0.3.6-2
  Version table:
     0.3.6-2 500
        500 http://archive.ubuntu.com/ubuntu mantic/universe amd64 Packages

```
Ubuntu for the above stock installer.
And if you have a PPA for a source you would ask here: [https://support.torproject.org/apt/tor-deb-repo/](https://support.torproject.org/apt/tor-deb-repo/)
**EDIT: So it seems I'm wrong,** with the flatpak application I can choose folders, but you have tick the box ask where to save to.
And now I see a prompt for choices as well.
See screenshot

So you've thoroughly read what I said and you're saying you've never seen TOR do that for you, you've never seen TOR just automatically select the folder for you? Man I must be losing my mind or something then cause I swear it was doing that for me. You know, how when you go to download a file on TOR you'll go find the precise folder you want your download to save to, well, if you do that enough times TOR would just automatically select that folder for you the next time you went to download something but you're saying you've never seen TOR do this?

I must be losing my mind. Well, trust me it definitely did that on Windows, I used TOR on windows for years, or, maybe I'm mistaken. You're saying I'm totally wrong about what I'm saying?

---

### Post by #&amp;thj^% on 2023-10-13
I corrected the post 6 days ago ie:
> EDIT: So it seems I'm wrong, with the flatpak application I can choose folders, but you have tick the box ask where to save to.
And now I see a prompt for choices as well.
See screenshot
Did you happen to notice that change?
And No I'm not saying you've lost your mind or your wrong, but for Windows I'll have to take that as Gospel cuz I don't use Windows especially with tor or torbrowser.
By all means file a bug against it and please link this thread to it, and if you do post that bug report link back here please.

---

### Post by bobunderwood99 on 2023-10-14
Since Tor Browser is based on Firefox you may find the following on point:

[https://support.mozilla.org/mk/questions/1386344](https://support.mozilla.org/mk/questions/1386344) 

"This issue has appeared before and the advice to fix it was to go  about:config, search for browser.download.lastDir.savePerSite and make  sure it is set at TRUE. I have done this, but the issue remains: Firefox  no longer remembers saved file directory paths on a per-URL basis."

---

