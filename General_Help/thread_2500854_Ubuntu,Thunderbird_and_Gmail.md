---
title: "Ubuntu,Thunderbird and Gmail"
date: 2024-09-13
forum: General Help
---

### Post by Norm24 on 2024-09-13
Starting a couple of days ago Thunderbird began having difficulties with Gmail in general.Very long wait times for both retrieval and sending of messages,other times simply won't do it at all and on rare occasions TB will behave normally with Gmail.I have other accounts thru my ISP and Yahoo and there are absolutely no issues.The settings in TB for Gmail are correct as far as I can tell and what I've researched on the web and Google confirms the settings are correct unless something has very recently changed.I've had these problems in both the latest stable versions of Supernova(115.15.0) and Nebula(128.0.1esr) but both these versions worked normally after updating from their previous versions until a couple of days ago.

 I do have a Win10 PC in the house and TB and Gmail play perfectly together.I have two machines running Mate 22.04.4 and 24.01.1 respectively and both have issues with TB and Gmail which leads me to believe this an issue with Ubuntu.

 I've searched the forums for this issue to no avail.If anyone else has had these problems I'd love to hear from you and would love to know even more how you solved this issue.

---

### Post by 1fallen on 2024-09-13
If your a snap fan, your not going to like my suggestion, and because it works for me  YMMV
First show us this please::
```
 apt policy thunderbird


```

---

### Post by Norm24 on 2024-09-13
Using the Mozilla build of TB.

---

### Post by Norm24 on 2024-09-13
> **1fallen2 said:**
> If your a snap fan, your not going to like my suggestion, and because it works for me  YMMV
First show us this please::
```
 apt policy thunderbird


```

This is what I get:
```
thunderbird:
  Installed: (none)
  Candidate: 2:1snap1-0ubuntu3
  Version table:
     2:1snap1-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages

```

---

### Post by 1fallen on 2024-09-13
Yes it is a snap, but I'll use the .deb TB
```
apt policy thunderbird
thunderbird:
  Installed: 1:115.15.0+build1-0ubuntu0.24.10.1~mt1
  Candidate: 1:115.15.0+build1-0ubuntu0.24.10.1~mt1
  Version table:
     2:1snap1-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu oracular/main amd64 Packages
 *** 1:115.15.0+build1-0ubuntu0.24.10.1~mt1 1001
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status

```
If your interested.

---

### Post by Norm24 on 2024-09-13
> **1fallen2 said:**
> Yes it is a snap, but I'll use the .deb TB
```
apt policy thunderbird
thunderbird:
  Installed: 1:115.15.0+build1-0ubuntu0.24.10.1~mt1
  Candidate: 1:115.15.0+build1-0ubuntu0.24.10.1~mt1
  Version table:
     2:1snap1-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu oracular/main amd64 Packages
 *** 1:115.15.0+build1-0ubuntu0.24.10.1~mt1 1001
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status

```
If your interested.

That's the crazy thing is that I am using .deb package installed through Ubuntuzilla.Been installing the Mozilla builds of FF and TB this way for over 15 years.

---

### Post by deadflowr on 2024-09-13
I see no snap installed, at least according to apt policy.
But that has no bearing on whether or not a snap is installed, only if the Ubuntu deb transitional packages is installed
'snap list' is more definitive for seeing what snaps are installed

The apt name for your deb is probably different, which is why it's not showing in the apt policy output.
try
```
dpkg -l | grep thunderbird
```
it should list the actual name.

---

### Post by Norm24 on 2024-09-13
> **deadflowr said:**
> I see no snap installed, at least according to apt policy.
But that has no bearing on whether or not a snap is installed, only if the Ubuntu deb transitional packages is installed
'snap list' is more definitive for seeing what snaps are installed

The apt name for your deb is probably different, which is why it's not showing in the apt policy output.
try
```
dpkg -l | grep thunderbird
```
it should list the actual name.

This is the output:

     
```
ii  thunderbird-mozilla-build                115.15.0-0ubuntu1                        amd64        Mozilla Thunderbird, official Mozilla build, packaged for Ubuntu by the Ubuntuzilla project.
```

---

### Post by 1fallen on 2024-09-13
There is more to it you may have forgot

```
sudo snap remove --purge thunderbird
```

Next we tell apt how to handle both:

```
sudo nano /etc/apt/preferences.d/mozillateamppa
```

When file opens, paste following lines and save it:

```
Package: thunderbird*
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1001
```

That should be enough, and may have to purge .deb TB first so Apt knows about the priority.

```
dpkg -l | grep thunderbird
ii  thunderbird                                              1:115.15.0+build1-0ubuntu0.24.10.1~mt1        amd64        Email, RSS and newsgroup client with integrated spam filter


```

---

### Post by Norm24 on 2024-09-13
> **1fallen2 said:**
> There is more to it you may have forgot

```
sudo snap remove --purge thunderbird
```

Next we tell apt how to handle both:

```
sudo nano /etc/apt/preferences.d/mozillateamppa
```

When file opens, paste following lines and save it:

```
Package: thunderbird*
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1001
```

That should be enough, and may have to purge .deb TB first so Apt knows about the priority.

```
dpkg -l | grep thunderbird
ii  thunderbird                                              1:115.15.0+build1-0ubuntu0.24.10.1~mt1        amd64        Email, RSS and newsgroup client with integrated spam filter


```

Mozilla Build of Thunderbird is the installed version through the Ubuntuzilla PPA.Post #8.

---

### Post by Norm24 on 2024-09-13
This is the complete list of Snaps installed:

```
Name                       Version                     Rev    Tracking         Publisher   Notes
bare                       1.0                         5      latest/stable    canonical&#10003;  base
canonical-livepatch        10.8.3                      282    latest/stable    canonical&#10003;  -
core                       16-2.61.4-20240607          17200  latest/stable    canonical&#10003;  core
core18                     20240612                    2829   latest/stable    canonical&#10003;  base
core22                     20240823                    1612   latest/stable    canonical&#10003;  base
firmware-updater           0+git.5007558               127    latest/stable/&#8230;  canonical&#10003;  -
gnome-3-28-1804            3.28.0-19-g98f9e67.98f9e67  198    latest/stable    canonical&#10003;  -
gnome-42-2204              0+git.510a601               176    latest/stable/&#8230;  canonical&#10003;  -
gtk-common-themes          0.1-81-g442e511             1535   latest/stable/&#8230;  canonical&#10003;  -
gtk2-common-themes         0.1                         13     latest/stable    canonical&#10003;  -
snap-store                 41.3-77-g7dc86c8            1113   latest/stable    canonical&#10003;  -
snapd                      2.63                        21759  latest/stable    canonical&#10003;  snapd
snapd-desktop-integration  0.9                         178    latest/stable/&#8230;  c
```

---

### Post by 1fallen on 2024-09-13
Yep I did see that #8, but I have no issues with TB currently along with Proton or Gmail.

I use Proton Mail for personal and Gmail for everyone related to Linux.

Are you using any "addons"?

And I never did see this:
```
less /etc/apt/preferences.d/mozillateamppa
Package: thunderbird*
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1001

```

---

### Post by Norm24 on 2024-09-13
> **1fallen2 said:**
> Yep I did see that #8, but I have no issues with TB currently along with Proton or Gmail.

I use Proton Mail for personal and Gmail for everyone related to Linux.

Are you using any "addons"?

And I never did see this:
```
less /etc/apt/preferences.d/mozillateamppa
Package: thunderbird*
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1001

```

TB not installed thru mozillateam but through Ubuntuzilla ppa. And zero addons.

---

### Post by ajgreeny on 2024-09-13
Hopefully I'm not adding any further confusion with this post but since I installed Xubuntu 24.04 I've been using the direct download of the thunderbird.tar.bz2, currently version 128 in the same way as I've been using Firefox since that became a snap in 22.04.  I don't think that is how Norm24 is using TB but it might be another thing to try.

Both FF and TB have worked brilliantly using this method.
I also use TB for gmail and have seen no problems at all.

---

### Post by 1fallen on 2024-09-13
> **Norm24 said:**
> TB not installed thru mozillateam but through Ubuntuzilla ppa. And zero addons.

It seems like I was using the same for awhile but switched to "mozillateam"

Any who you seem to not want to  show this:  "/etc/apt/preferences.d/"
So I'll leave it to someone else then :)
BTW: I use both:
```
 ls /etc/apt/preferences.d/
mozilla  mozillateamppa  nosnap.pref  ubuntu-pro-esm-apps  ubuntu-pro-esm-infra

```
The Above may confuse things a bit, this is what I would like to view:
```
less /etc/apt/preferences.d/mozillateamppa
```
And this one:
```
less /etc/apt/preferences.d/mozilla

```
Mine on 24.10
Firefox:
```

Package: *
Pin: origin packages.mozilla.org
Pin-Priority: 1000



```
TB
```
Package: thunderbird*
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1001
```

---

### Post by Norm24 on 2024-09-13
I'll show the output of :/etc/apt/preferences.d/

```
bash: /etc/apt/preferences.d/: Is a directory
``` 

And:less /etc/apt/preferences.d/mozilla

```
/etc/apt/preferences.d/mozilla: No such file or directory
```

---

### Post by Norm24 on 2024-09-13
So far what's been determined is that they're are no snaps involved,that I'm using Mozilla Build of Thunderbird (115.15.0) installed thru the Ubuntuzilla PPA  and it just doesn't want to play well with Gmail.

Looking like its time to wipe TB completely and start over using some other type of installation method.

---

### Post by 1fallen on 2024-09-13
> **Norm24 said:**
> I'll show the output of :/etc/apt/preferences.d/

```
bash: /etc/apt/preferences.d/: Is a directory
``` 

And:less /etc/apt/preferences.d/mozilla

```
/etc/apt/preferences.d/mozilla: No such file or directory
```

:lolflag: I buy you books and what do you do, Beat the Teacher...
You Missed a bit here:
```

less /etc/apt/preferences.d/mozilla
```
Don't Omit "less"

---

### Post by donald187 on 2024-09-14
> **Norm24 said:**
> If anyone else has had these problems I'd love to  hear from you and would love to know even more how you solved this  issue.
I have had this problem several times for the better part of a day generally.  I don't think it has lasted longer than that.  I can't remember if it was on Debian, Ubuntu or both but I've almost entirely only used Thunderbird installed from the distribution repositories.  I'm currently on Debian and it isn't happening now.  Up until a few weeks ago I was Ubuntu 22.04 and it hadn't happened there for quite some time.

---

### Post by Norm24 on 2024-09-14
I was up for a portion of the night thinking about what had changed recently and tried different TB versions to no avail.Also there was a recent kernal update to 6.8.0-44-generic so I reverted back to the previous kernal and all seemed well and then back to the same issue though I am getting my emails just at a very slow pace and even hitting the "get messages" tab there is still quite a lag.Sending is still taking quite a bit of time also.

Possibly thought it might also be an issue with the firewall so I disabled ufw and still the issue persists.

edit:Also tried Gmail with Evolution and Seamonkey and same issue.

---

### Post by Norm24 on 2024-09-14
> **1fallen2 said:**
> :lolflag: I buy you books and what do you do, Beat the Teacher...
You Missed a bit here:
```

less /etc/apt/preferences.d/mozilla
```
Don't Omit "less"

I didn't miss "less" it was copied and pasted as posted and this is the output:

```
/etc/apt/preferences.d/mozilla: No such file or directory
```

---

### Post by Norm24 on 2024-09-14
This is just one I can't figure out.Gmail no longer seems to be functional with any email clients on both my Mate 22.04.4 and 24.04.1 machines.I absolutely hate the idea of using webmail to access my Gmail account but that seems to be the only solution at this point.

---

### Post by ajgreeny on 2024-09-14
Absolutely no problem using TB for gmail on my Xubuntu 22.04 or 24.04, and my 24.04 is also using kernel 6.8.0-44 so that can't be the total reason either.

---

### Post by Norm24 on 2024-09-14
> **ajgreeny said:**
> Absolutely no problem using TB for gmail on my Xubuntu 22.04 or 24.04, and my 24.04 is also using kernel 6.8.0-44 so that can't be the total reason either.

This one is totally driving me nuts.

Could this be an IP issue maybe?

---

### Post by 1fallen on 2024-09-14
> **Norm24 said:**
> This one is totally driving me nuts.

Could this be an IP issue maybe?

Possibly, but I would for sure contact Google first. (Take the guess work out)

And No it's not a kernel problem, "Linux Legion-5-15ACH6-zfs 6.11.0-1002-lowlatency"

---

### Post by maglin2 on 2024-09-15
I rarely use TB nowadays, but I've just fired it up and it's currently working fine with gmail.
The main reason I now rarely use it (having used it for a decade or more) is that about about a year ago I had the same issue as you (22.04 then). Either no connection or very slow connection to gmail account. This continued, on and off, for  couple of weeks. I checked with a neighbour who also used 22.04, TB and gmail and he had the same problem. Different ISP though. Also different IP of course.
The problem cleared, then returned a month or so later.
All this time webmail connection to gmail in Firefox was fine, so I pretty much gave up on TB and have used webmail since.

---

### Post by Norm24 on 2024-09-15
> **maglin2 said:**
> I rarely use TB nowadays, but I've just fired it up and it's currently working fine with gmail.
The main reason I now rarely use it (having used it for a decade or more) is that about about a year ago I had the same issue as you (22.04 then). Either no connection or very slow connection to gmail account. This continued, on and off, for  couple of weeks. I checked with a neighbour who also used 22.04, TB and gmail and he had the same problem. Different ISP though. Also different IP of course.
The problem cleared, then returned a month or so later.
All this time webmail connection to gmail in Firefox was fine, so I pretty much gave up on TB and have used webmail since.

Exactly the issue I'm having,every so often it seems to be fine and then right back to slow or no connection.I've pretty much given up on this and have put a FF link to Gmail on the desktop for easy access.My ISP and Yahoo mail accounts are still completely functional with TB and all the other clients I've tried just no love from Gmail.Oh well.

---

### Post by Norm24 on 2024-09-15
> **1fallen2 said:**
> Possibly, but I would for sure contact Google first. (Take the guess work out)

And No it's not a kernel problem, "Linux Legion-5-15ACH6-zfs 6.11.0-1002-lowlatency"

Been trolling Google support and other forums but really haven't found out much as very few if any seem to be having this issue and those that are having it haven't found any reason why this is happening or a solution for it.

---

### Post by hedgehog123 on 2024-09-16
If you let Thunderbird create a logfile, you can maybe find some errors. To enable logging for IMAP you could e.g. use

```
[FONT=monospace][COLOR=#000000]MOZ_LOG=IMAP:4 MOZ_LOG_FILE=~/thunderbird thunder[/COLOR][COLOR=#000000]bird[/COLOR][/FONT]
```

The logfile is then in [FONT=monospace][COLOR=#000000]~/thunderbird.moz_log[/COLOR]
[/FONT]

---

### Post by C.Snyder on 2024-09-20
3 days ago, there was a recommended update that I followed up with the usual apt-get update and apt update.
Just yesterday, Thunderbird and gmail stopped downloading the new  emails.  It says it will send an email but does not want to copy it to  the sent folder or the copy process is so extraordinarily slow that I  did not wait long enough to see it do so.

Prowling around other forums I only found the advice about settings and add-ons that revealed no reasons for the dysfunction.
  
Applying some of the suggestions posted to this thread:
```
$ apt policy thunderbird thunderbird:
  Installed: 1:115.15.0+build1-0ubuntu0.22.04.1
  Candidate: 1:115.15.0+build1-0ubuntu0.22.04.1
  Version table:
 *** 1:115.15.0+build1-0ubuntu0.22.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:91.8.0+build2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

```
$ dpkg -l | grep thunderbird
ii  thunderbird                                1:115.15.0+build1-0ubuntu0.22.04.1                amd64        Email, RSS and newsgroup client with integrated spam filter

```

```
$ less /etc/apt/preferences.d/mozilla
/etc/apt/preferences.d/mozilla: No such file or directory
```

Reaching beyond my comfort zone I set up the log file as was suggested in hedghog123's post:
```
~/thunderbird.moz_log
bash: /home/pablo/thunderbird.moz_log: Permission denied

```

This change of TB function could not come at a worse time as I am managing a small community volunteer organization and rely extensively on email contact.
And yes, since I upgraded to 22.04 (a clean install) the usual day to day function of this laptop has been slow and somewhat twitchy.

My thanks to those of you who have taken the time to post to this thread.

I hope this thread is not stalled.

---

### Post by hedgehog123 on 2024-09-20
> **C.Snyder said:**
> 
```
~/thunderbird.moz_log
bash: /home/pablo/thunderbird.moz_log: Permission denied

```


If you want to see the logfile, you can open it in an editor or on the command line e.g. with
```
less ~/thunderbird.moz_log
```

Did you check your Thunderbird settings against the Google recommendations - [https://support.google.com/mail/answer/78892?hl=en&ref_topic=7280141&sjid=11542685716241816999-EU#zippy=%2Cthunderbird](https://support.google.com/mail/answer/78892?hl=en&ref_topic=7280141&sjid=11542685716241816999-EU#zippy=%2Cthunderbird)

---

### Post by Norm24 on 2024-09-21
> **hedgehog123 said:**
> Did you check your Thunderbird settings against the Google recommendations - [https://support.google.com/mail/answer/78892?hl=en&ref_topic=7280141&sjid=11542685716241816999-EU#zippy=%2Cthunderbird](https://support.google.com/mail/answer/78892?hl=en&ref_topic=7280141&sjid=11542685716241816999-EU#zippy=%2Cthunderbird)




I've tried every recommended setting from Google and sometimes TB and Gmail work great and the next minute right back to the same slow or no send/receive.Again to the point this is only happening with Ubuntu...these issues do not happen within Windows or Mac.My ISP email and Yahoo mail work perfectly within TB and Ubuntu,the only common thing here between Gmail and TB not functioning is Ubuntu or my particular case Ubuntu Mate.

My only solution to this point is add a FF (or whatever browser you use) link to the desktop and panel and give it an email emblem of my choosing.

---

### Post by dragonfly41 on 2024-09-21
This might be a red herring but recently I created a Proton Mail account in addition to my Thunderbird accounts. You can push gmail through Proton and then there is a Proton Mail Bridge to Thunderbird.

---

### Post by C.Snyder on 2024-09-23
hedgehog123, Norm24 & dragonfly41,
Thank you for the input.

Although I have not posted till now, I have been checking this thread regularly.   I also kept digging into other forums regarding the issue and opening   TB to check those recommended settings and mostly checking to see if the emails were being forwarded.  I could find no evidence that they were being delivered elsewhere.

I did considered uninstalling and reinstalling TB but did not for concern over what would happen to my TB profile and the accumulated emails in the two gmail accounts that I maintain.  I keep many of emails in local folders in TB on my laptop.  I did successfully use the Restore function in the bundled Deja Dupe backup after a clean OS install and those files did make it back into the newer version of TB.  I hesitate to 

Well..., some *magic* has happened and TB 115.15.0 is now "fetching" the new gmail messages.  I cannot say that there was some particular action that I took that caused the change in it's function.
I do notice one minor change being that when I highlight a line item or a block of items and Rt click then delete the highlighted selection the result is a line through of the messages rather than an immediate removal of those messages.   Not a problem, but different.

I do have a question about the log file.  When I open the log file in a terminal I do not find any content other than:
```
/home/pablo/thunderbird.moz_log (END)
```

If I hit enter for some unknown execution, the terminal window fills with "~"s at the left most edge and "(END)" at the bottom.  Never having delved into a log file before, would you please explain what it is that I am missing about the use of this diagnostic tool?

I will look into the Proton Mail.

Once again, thank you.

---

### Post by hedgehog123 on 2024-09-23
> **C.Snyder said:**
> 

I do have a question about the log file.  When I open the log file in a terminal I do not find any content other than:
```
/home/pablo/thunderbird.moz_log (END)
```

If I hit enter for some unknown execution, the terminal window fills with "~"s at the left most edge and "(END)" at the bottom.  Never having delved into a log file before, would you please explain what it is that I am missing about the use of this diagnostic tool?

Your logfile is empty. Did you close Thunderbird before the call?

1) Close Thunderbird
2) Run in terminal "[FONT=monospace][COLOR=#000000]MOZ_LOG=IMAP:4 MOZ_LOG_FILE=~/thunderbird thunderbird[/COLOR]"[/FONT]
3) Thunderbird opens and tries to connect to the mail server
4) Close Thunderbird
5) Run in terminal "[FONT=monospace][COLOR=#000000]less ~/thunderbird.moz_log[/COLOR]" or "[/FONT][FONT=monospace][COLOR=#000000]cat ~/thunderbird.moz_log[/COLOR]" or open the file in a GUI editor[/FONT]
6) Log starts e.g. for me with "[FONT=monospace][COLOR=#000000][Parent 33220: IMAP]: D/IMAP ImapThreadMainLoop entering[/COLOR]"[/FONT]

In the log you should see how Thunderbird tries to connect to the mail server, sends the password and so on. If you can find an error, this might help to figure out what's going wrong.

---

### Post by Norm24 on 2024-09-25
For the past 36 hours TB and Gmail are working just fine!This applies to both 22.04.5 and 24.04.1.

I've done absolutely no changes and yet there it is.This has been a very confusing and frustrating adventure to say the least.Keeping my fingers crossed that this trend continues.

---

### Post by maglin2 on 2024-10-15
I'm having this slow thunderbird problem today (it was OK a couple of days ago). 
Anyone else currently experiencing it?
Might help identify if it's a local or wider issue.

---

### Post by Norm24 on 2024-10-15
> **maglin2 said:**
> I'm having this slow thunderbird problem today (it was OK a couple of days ago). 
Anyone else currently experiencing it?
Might help identify if it's a local or wider issue.

Is TB just all around slow or is it slow only with Gmail?Are you using .deb,Snap or Flatpak install?I'm using a .deb install of TB.

My issues were only with Gmail and trust me I tried every possible recommended setting and just could not get TB to work well with Gmail.My IP email and Yahoo accounts had no issues.

I know that Google was making changes to Workspace (which includes Gmail) and those changes were finalized on Sept.30.Might be worth a read.
[https://workspaceupdates.googleblog.com/2023/09/winding-down-google-sync-and-less-secure-apps-support.html](https://workspaceupdates.googleblog.com/2023/09/winding-down-google-sync-and-less-secure-apps-support.html)

Even though I had implemented the proper changes/settings quite some time back I was still having issues with TB and Gmail.Coincidentally about two weeks ago everything just started working "right" again.

---

### Post by maglin2 on 2024-10-15
> **Norm24 said:**
> Is TB just all around slow or is it slow only with Gmail?Are you using .deb,Snap or Flatpak install?I'm using a .deb install of TB.

My issues were only with Gmail and trust me I tried every possible recommended setting and just could not get TB to work well with Gmail.My IP email and Yahoo accounts had no issues.

I know that Google was making changes to Workspace (which includes Gmail) and those changes were finalized on Sept.30.Might be worth a read.
[https://workspaceupdates.googleblog.com/2023/09/winding-down-google-sync-and-less-secure-apps-support.html](https://workspaceupdates.googleblog.com/2023/09/winding-down-google-sync-and-less-secure-apps-support.html)

Even though I had implemented the proper changes/settings quite some time back I was still having issues with TB and Gmail.Coincidentally about two weeks ago everything just started working "right" again.

I only use TB with gmail, so can only comment on that.
It's the snap install.
I rarely use Thunderbird, but did a couple of days ago (when it was fine) and today (when it wasn't). 
Just thought I'd enquire to see if folks elsewhere had seen the same today - would have added a bit more knowledge of the issue.

---

### Post by maglin2 on 2024-10-15
.....and now TB/gmail is working normally again......

---

