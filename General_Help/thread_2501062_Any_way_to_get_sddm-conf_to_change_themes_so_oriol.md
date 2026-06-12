---
title: "Any way to get sddm-conf to change themes so oriole can “suspend” in sddm window?"
date: 2024-09-21
forum: General Help
---

### Post by este.el.paz on 2024-09-21
Folks:
 Posted to the Lu users list-serve && Lubuntu Discourse for Developmental, and in ubuntu developmental sub-forum, but so far no response, so I’m trying here.


 Not sure if oriole has changed how sddm looks or functions at the log
in window, but I recently had a similar issue in my Tumbleweed install, where
sddm log in toolbar applets only showed options to “reboot” or “shutdown” and their
forum walked me through how to change themes in the sddm-conf app . .
.  .

 It now seems like Lubuntu oriole has the same issue, “default” theme
with the two options, but no option to "suspend."  So, I copied the “elarun” theme from my Debian Sid
install, figuring that would work better than possibly the TW data . . .
launched sddm-conf, changed the theme to the newly listed
“debian-elarun” . . . saved it and logged out.  No change. 

 Checked the other option that was already there before I added my two Debians
to “ubuntu-theme” and again no change.


 Any way to get sddm-configuration to accept new themes??   in GUI or in  console so that I could suspend from the sddm log in  window, without  having to log in, to then suspend??

---

### Post by este.el.paz on 2024-09-25
<bump>  Doesn't seem to be any insights available for resolving this problem . . .????

---

### Post by TheFu on 2024-09-25
Well, Ubuntu people tend not to customize their systems too much, so if sddm isn't the default login manager, very few people will use it with Ubuntu.
I customize my setup, but don't use sddm.  I use slim.

Google found this from the Lubuntu guys: [https://manual.lubuntu.me/stable/2/2.4/2.4.9/SDDM-Configuration.html](https://manual.lubuntu.me/stable/2/2.4/2.4.9/SDDM-Configuration.html)  I do find it a bit concerning they use ACLs. That's a person issue, since I've needed to use ACLs very few times, less than 5 in 30 yrs, as a Unix/Linux admin.

Not sure I understand the issue, but systemd has made a number of things that used to be addressed by logging out of a session and back in, no require a reboot for some reason.  I can only guess that the systemd team decided to cache certain information at boot time and never check if those configs had changed later.  Just a guess.

---

### Post by este.el.paz on 2024-09-25
> **TheFu said:**
> Well, Ubuntu people tend not to customize their systems too much, so if sddm isn't the default login manager, very few people will use it with Ubuntu.
I customize my setup, but don't use sddm.  I use slim.

Google found this from the Lubuntu guys: [https://manual.lubuntu.me/stable/2/2.4/2.4.9/SDDM-Configuration.html](https://manual.lubuntu.me/stable/2/2.4/2.4.9/SDDM-Configuration.html)  I do find it a bit concerning they use ACLs. That's a person issue, since I've needed to use ACLs very few times, less than 5 in 30 yrs, as a Unix/Linux admin.

Not sure I understand the issue, but systemd has made a number of things that used to be addressed by logging out of a session and back in, no require a reboot for some reason.  I can only guess that the systemd team decided to cache certain information at boot time and never check if those configs had changed later.  Just a guess.


@TheFu:

Thanks for taking the time on it . . . I have had my Lubuntu install running on this machine since perhaps '16 . . . and I don't tend to mess too much, unless there is some problem with the stock setup.  Usually that relates to "suspend" and the system not reviving from it, etc.  And that is something that perhaps was fixed with going to sddm . . . some time back.

I took a fast look at your linked data . . . and that is what I did to fix the problem that was happening in my TW install . . . changing the "theme" to "elarun" gives me the option to suspend at the log in window.  But, in Lubuntu, moving that theme into the system and then selecting it in the config app . . . does not make the changes that it did in TW . . . .  Using the "elarun" directory from one of my Debian installs . . . to keep it in "the family" . . . .

And, clicking on the "preview" button doesn't provide a preview, it only opens a small box upper left saying "cancel preview" . . . ????

So, it's not a deal breaker on using the system . . . just a minor inconvenience . . . the question is, "why?" . . . .  It shows "elarun" in the selected theme slot . . .  but, then, it doesn't make the changes ???  I boot a different linux install each day, so I have restarted Lubuntu a number of times since I started on trying to fix it, as was done successfully on TW . . . .

---

### Post by TheFu on 2024-09-25
2016 Lubuntu supported ended in 2019.  In 2020, the new Lubuntu switched from GTK+ LXDE to Qt LXQt, which means a fresh install was recommended.

I know nothing recent about TW, so I won't pretend to have any knowledge.  I did run SuSE for a few years in 2002-ish.  I only use Debian on servers, not desktops.

And I haven't used Lubuntu seriously since around 2012.  The good news is that when 24.04 was released, only the Lubuntu version installed and was stable in my testing for a few days before I decided 24.04 wasn't going to meet my needs as a desktop base OS ... ever.

Anyway, really just wanted you to know that someone was reading your post.  Can't offer much more than that.

---

### Post by este.el.paz on 2024-09-25
> **TheFu said:**
> 2016 Lubuntu supported ended in 2019.  In 2020, the new Lubuntu switched from GTK+ LXDE to Qt LXQt, which means a fresh install was recommended.

I know nothing recent about TW, so I won't pretend to have any knowledge.  I did run SuSE for a few years in 2002-ish.  I only use Debian on servers, not desktops.

And I haven't used Lubuntu seriously since around 2012.  The good news is that when 24.04 was released, only the Lubuntu version installed and was stable in my testing for a few days before I decided 24.04 wasn't going to meet my needs as a desktop base OS ... ever.

Anyway, really just wanted you to know that someone was reading your post.  Can't offer much more than that.

@TheFu:

Thanks for the followup on it . . . so, the joy of linux is, so many choices to choose from . . . .  But, then seemingly, no one choice will cover **everything** . . . so that is why I multi-boot across a range of systems.

I think my Lubuntu experience goes back to '07-ish with the PPC version . . . .  Now I just edit the repos to the latest iteration . . . once doing the fresh install on a machine.  Keep the / and the /home on separate partitions . . . so if something blows up I could do a fresh install of / and /home is ready to go.  For the most part haven't had to run a fresh install of Lubuntu in quite awhile . . . it's on the oldest drive in the machine and still going.

TW is "rolling" and it does rebuild the system frequently . . . bleeding edge stuff . . . which I like, but then it tends to break stuff more often . . . .  But, their forum is pretty good . . . someone there helped me with the sddm "theme" issue . . . which had not messed with until then.

Carry on with it.  I'll post back if and when Lu figures out how to change its theme to allow suspend . . . .  Maybe on a riny dy I'll try to switch to another log in manager, I think I have a few installed.

---

### Post by guiverc on 2024-09-25
> **este.el.paz said:**
> 

Carry on with it.  I'll post back if and when Lu figures out how to change its theme to allow suspend . . . .

I do recall a change being made that caused `sddm` to look rather different (*it may have even been problematic; but as Qt6, newer LXQt etc were rolling thru, and what we were getting wasn't the whole system I ignored it and waited*). 

The next change I saw was after all had completed, and our new Lubuntu *oracular* theme was present, and it works perfectly fine on my install. As this install is multi-desktop; I'm selecting other desktops occasionally, so I'm using the session selector button somewhat regularly.

I just booted another box that has *oracular* installed, and it works there too.. including the SUSPEND function (*though I don't use that on my primary box; on my primary box where I suspend most nights, the session is locked with the lock function handled by xscreensaver OR whatever the other DE i'm using has configured and thus I'm not returned to sddm*).

FYI:  Both the boxes I mentioned are using a default theme, the secondary box I did the suspend test on was only recently re-installed (*though install was non-destructive so any settings in $HOME survived; but sddm config doesn't use anything there*). I keep them on default Lubuntu theme for QA purposes.

This question was asked on Lubuntu's discourse at [https://discourse.lubuntu.me/t/any-way-to-get-sddm-conf-to-change-themes-to-get-oriole-to-suspend-in-log-in-window/5128](https://discourse.lubuntu.me/t/any-way-to-get-sddm-conf-to-change-themes-to-get-oriole-to-suspend-in-log-in-window/5128)

---

### Post by este.el.paz on 2024-09-25
> **guiverc said:**
> I do recall a change being made that caused `sddm` to look rather different (*it may have even been problematic; but as Qt6, newer LXQt etc were rolling thru, and what we were getting wasn't the whole system I ignored it and waited*). 

The next change I saw was after all had completed, and our new Lubuntu *oracular* theme was present, and it works perfectly fine on my install. As this install is multi-desktop; I'm selecting other desktops occasionally, so I'm using the session selector button somewhat regularly.

I just booted another box that has *oracular* installed, and it works there too.. including the SUSPEND function (*though I don't use that on my primary box; on my primary box where I suspend most nights, the session is locked with the lock function handled by xscreensaver OR whatever the other DE i'm using has configured and thus I'm not returned to sddm*).

FYI:  Both the boxes I mentioned are using a default theme, the secondary box I did the suspend test on was only recently re-installed (*though install was non-destructive so any settings in $HOME survived; but sddm config doesn't use anything there*). I keep them on default Lubuntu theme for QA purposes.

This question was asked on Lubuntu's discourse at [https://discourse.lubuntu.me/t/any-way-to-get-sddm-conf-to-change-themes-to-get-oriole-to-suspend-in-log-in-window/5128](https://discourse.lubuntu.me/t/any-way-to-get-sddm-conf-to-change-themes-to-get-oriole-to-suspend-in-log-in-window/5128)

@guiverc:

Since there has been a conversation here, I will continue here . . . so, not entirely clear what you are saying . . . ??  Your are using sddm with its default theme??  Because I believe I tried to change the sddm theme from "default" to "elarun" and then I think it has a "ubuntu" theme???  saving each of those changes did not result in a change happening.  Just two applet, restart or shut down are offered . . . from the log in window.

Or, you are using another log in manager altogether??

I am running oracular in Lubuntu . . . LXQT . . . etc.

---

### Post by guiverc on 2024-09-25
No, I'm saying I don't really understand your issue, and can't re-create it (*though I didn't explore very far, my focus was primarily ensuring we/Lubuntu don't have an issue with a default setup!*)

My *primary* box has been used & updated (3x) daily for the last year, and I've not noticed any problems with operation of `sddm` on it.

The other box I booted (my *secondary* PC) gets regularly re-installed (*non-destructively*), so everything outside of $HOME (*ie. user configs*) should reflect a ~new install  (*until the oracular cycle, I used to re-install this box weekly; its less often currently, doing this instead of the normal application of upgrades*).

Yes as updated packages rolled out, the operation of `sddm` wasn't normal for a number of days, but those issues resolved; there was a large number of packages that needed building & didn't roll out at the same time (not just LXQt or Qt6 was involved; impacting Kubuntu/KDE Plasma, Ubuntu Studio etc & other packages in the repository). I'm just ignoring this short period, as once package rollout completed with no changes the *issues* I'd encountered resolved themselves as expected (hoped?).

I am aware that some of my boxes will not suspend reliably; and wonder if your box is like those, however those boxes of mine that won't suspend, are boxes I don't need to suspend, thus I've not explored any further. This my primary box I suspend ~13 of 14 nights (*I reboot about once per fornight*), but I'm only suspending with a running desktop (LXQt, Xfce, GNOME..) and don't have issue (*nor is sddm involved as I mentioned*). My *secondary* box that I used for suspend maybe suspended once or twice per fortnight as its only used 2-4 hours per day.

(*I have two boxes were i do run a modified sddm, but those are not running oracular, one of which has Kubuntu (KDE Plasma) & Lubuntu (LXQt) installed and the changes to sddm are thus made thru KDE settings*).

I read your post on ML & Lubuntu discourse, but I suspect it was made during the rolling out of updates, which meant I didn't want to consider testing until all changes were rolled out, and I couldn't re-create any issue after changes were rolled out; thus had nothing to offer. I'm in the same *boat* now/today, having tried again on two boxes & not had issues (*suspending only my other box though*), both boxes using a default config.

I've experienced no issues, and have nothing to offer sorry.

---

### Post by este.el.paz on 2024-09-26
@guiverc:

I am not sure why the problem can't be understood, it's not that I can't suspend the system at all . . . it's not being able to suspend from the sddm log in window . . . which I think has been stated several times???  And, then the other problem is not being able to change the theme to a theme that will allow me to do that, as I did with TW and possibly Trixie??

The log in window only shows "restart" or "shut down" applets . . . in my other systems I can do that AND I can "suspend" or possibly "hibernate" . . . from the sddm log in window.  Sometimes I run an update on a system and then I want to see if logging out and back in will work . . . but then I need to go feed the cats or something, so I want to suspend from the sddm log in window . . . .

I could change that theme in my TW install . . . and transferred that same theme from my Debian Trixie over to Lubuntu . . . but . . . the sddm-config app will not actually make the change, nor will it show the preview of the theme change . . . .

Hopefully the problem is at least clear . . . whether or not anything can be done about it remains to be seen.  I can't recall if this was a problem before upgrading to oriole or not . . . but it exists now . . . .  :():P

---

