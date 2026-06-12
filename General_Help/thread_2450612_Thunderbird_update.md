---
title: "Thunderbird update?"
date: 2020-09-17
forum: General Help
---

### Post by walts48 on 2020-09-17
Thunderbird 68.11.0 was released on July 30, 2020, 68.12.0 on August 25, 2020.

The Ubuntu version is still 68.10.0.

Will there be an update to 68.12.0, or will we have to wait for 78.3.0 due sometime in the next couple of weeks?

---

### Post by TheFu on 2020-09-17
You can always use a PPA if you want bleeding edge.  Newer isn't always better.  For LTS installs, the goal isn't to have the newest version, but to have the same capabilities. Only security updates should be back-ported to the LTS distro most of the time.

Though browsers and email programs do often get special considerations due to the way they need to work with servers around the world, not just locally.

There is a daily build PPA: [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ubuntu/ppa)  Probably not a good idea.
Mozilla "beta" PPA: [https://launchpad.net/~mozillateam/+archive/ubuntu/thunderbird-next](https://launchpad.net/~mozillateam/+archive/ubuntu/thunderbird-next)
Mozilla Team PPA links: [https://launchpad.net/~mozillateam](https://launchpad.net/~mozillateam)  Choose your poison.

---

### Post by walts48 on 2020-09-18
I don't need more ppa's, just would like to know the plan for 68.10.0 upgrade.

I guess these security fixes aren't enough to warrant an update to 68.12.0.

[https://www.mozilla.org/en-US/security/advisories/mfsa2020-35/](https://www.mozilla.org/en-US/security/advisories/mfsa2020-35/)

[https://www.mozilla.org/en-US/security/advisories/mfsa2020-40/](https://www.mozilla.org/en-US/security/advisories/mfsa2020-40/)

---

### Post by SeijiSensei on 2020-09-18
The Thunderbird that comes with 20.10 is 78.2.1. The version on my updated 20.04 desktop is 68.10.0.

---

### Post by walts48 on 2020-09-19
> **SeijiSensei said:**
> The Thunderbird that comes with 20.10 is 78.2.1. The version on my updated 20.04 desktop is 68.10.0.

That's nice. The versions on both of them are outdated.

The most recent versions are 68.12.0 and 78.2.2.

I'll be testing the 78.3.0 release candidate later today.

Myself and others are using 18.04 LTS. I don't plan to update until necessary.

I thought it was a long term support version that doesn't reach EOL until April 2023.

Most other Linux distributions have updated to 68.12.0 as you can see here by clicking on the name of the distribution.[URL="https://lwn.net/Alerts/"]

[/URL][https://lwn.net/Alerts/](https://lwn.net/Alerts/) 

So, AIUI there will be no update to 68.12.0 for Ubuntu 18.04 LTS.

What will be the next version for it?

---

### Post by walts48 on 2020-09-24
So now that version 78.3.0 has been released, will Ubuntu users be upgraded to that version, or 68.12.0 skipping 68.11.0, like they did with the update to 68.10.0 from 68.8.0, skipping 68.8.1 and 68.9.

And breaking news the update from 78.2.2 to 78.3.0 has been aborted.

I still would like to know what the plan is for updating. :D

---

### Post by walts48 on 2020-09-26
The fix is in and 78.3.1 is out! 

[https://www.thunderbird.net/en-US/thunderbird/78.3.1/releasenotes/](https://www.thunderbird.net/en-US/thunderbird/78.3.1/releasenotes/)

This will be the version that users of 68.12.0 will be updated to as updates are deployed.

Now which one of the other distros that have updated to 68.12.0 do I want to check out?

---

### Post by walts48 on 2020-10-01
There will be a 68.12.1 update from 68.12.0 which has now been released.

Meanwhile Mageia is the first to update users to 78.3.1.

[https://lwn.net/Articles/833102/](https://lwn.net/Articles/833102/)

---

### Post by walts48 on 2020-10-07
[URL="https://www.thunderbird.net/en-US/thunderbird/78.3.2/releasenotes/"]https://www.thunderbird.net/en-US/thunderbird/78.3.2/releasenotes/
[/URL]

---

### Post by jamesl-bestweb on 2020-10-11
> **TheFu said:**
> You can always use a PPA if you want bleeding edge.  

There is a daily build PPA: [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ubuntu/ppa)  Probably not a good idea.
Mozilla "beta" PPA: [https://launchpad.net/~mozillateam/+archive/ubuntu/thunderbird-next](https://launchpad.net/~mozillateam/+archive/ubuntu/thunderbird-next)
Mozilla Team PPA links: [https://launchpad.net/~mozillateam](https://launchpad.net/~mozillateam)  Choose your poison.

None of those have the updated Thunderbird releases.  In fact a couple of them are significantly out-of-date.

Although, seeing as the particular "bug" I'm trying to work around is Thunderbird insisting that a profile (entire ~/.thunderbird directory) copied from a Mint/Ubuntu TB 68.10 system to a Fedora system with TB 68.11 warrants forcing me into a completely NEW profile.  It's a *point* release difference, both are x86_64 systems, there should be no compatibility issues between the two.  I figured if I could at least bring my .deb version to 68.11 (or even 68.12) I could let the Mint copy update itself, then rsync the directory over (TB does have a switch to revert a "newer" profile back to an older build).

---

### Post by walts48 on 2020-10-11
You do know about the --allow-downgrade switch?

[https://support.mozilla.org/en-US/kb/dedicated-profile-thunderbird-installation#w_what-happens-to-my-profile-if-i-downgrade-to-a-previous-version-of-thunderbird](https://support.mozilla.org/en-US/kb/dedicated-profile-thunderbird-installation#w_what-happens-to-my-profile-if-i-downgrade-to-a-previous-version-of-thunderbird)

---

### Post by walts48 on 2020-10-23
Thunderbird 78.4.0 has been released. The 68 ESR version is now officially EOL.

[https://www.thunderbird.net/en-US/thunderbird/78.4.0/releasenotes/](https://www.thunderbird.net/en-US/thunderbird/78.4.0/releasenotes/)

---

### Post by Ralph L on 2020-10-24
The appImage version is available at [https://appimage.github.io/Thunderbird/](https://appimage.github.io/Thunderbird/) .  I have never tried it, but most appimages are pretty recent.  Also, there is a snap version at [https://snapcraft.io/thunderbird](https://snapcraft.io/thunderbird) .  I tried snap only once for Strawberry, but was advised when I tried to run it that the ppa version was better.

---

### Post by walts48 on 2020-10-25
> **Ralph L said:**
> The appImage version is available at [https://appimage.github.io/Thunderbird/](https://appimage.github.io/Thunderbird/) .  I have never tried it, but most appimages are pretty recent.  Also, there is a snap version at [https://snapcraft.io/thunderbird](https://snapcraft.io/thunderbird) .  I tried snap only once for Strawberry, but was advised when I tried to run it that the ppa version was better.

If I wanted one of those that would be nice.

I still haven't seen an answer as to why it isn't in the normal security update channel which is the reason for the post on Sept 17th.

[https://ubuntuforums.org/showthread.php?t=2450612&p=13986981#post13986981](https://ubuntuforums.org/showthread.php?t=2450612&p=13986981#post13986981)

---

### Post by walts48 on 2020-11-07
Ubuntu supplied version stalled at 68.10.0 and Thunderbird 78.4.0 was released with bug fixes and security updates on Oct. 21st.

[https://www.thunderbird.net/en-US/thunderbird/78.4.0/releasenotes/](https://www.thunderbird.net/en-US/thunderbird/78.4.0/releasenotes/)

Thunderbird 78.4.1 was released yesterday.

[URL="https://www.thunderbird.net/en-US/thunderbird/78.4.1/releasenotes/"]https://www.thunderbird.net/en-US/thunderbird/78.4.1/releasenotes/

[/URL]

---

### Post by deadflowr on 2020-11-07
It looks like thunderbird 78.X is being prepared for focal and bionic:
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1895643]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1895643")
How long it takes to move it up, I'm not sure.

> I still haven't seen an answer as to why it isn't in the normal security update channel which is the reason for the post on Sept 17th.
The reason is that it's such a major update for Thunderbird with many things added and some things removed they cannot just update it, they need to figure out what is what.
As the bug report linked alludes to at least one issue has come up from one user about an add-on breakage.
The last thing the Ubuntu developers want is to update a major package like this and find out it breaks for a large section of the user base.

---

### Post by walts48 on 2020-11-08
Thanks for that.

Windows and Mac users experienced unexpected extension breakage, and I'm sure the users of the other Linux distributions that have updated have as well.

---

### Post by walts48 on 2020-11-10
And now we have Thunderbird 78.4.2 a critical security vulnerability update.

[https://www.mozilla.org/en-US/security/advisories/mfsa2020-49/](https://www.mozilla.org/en-US/security/advisories/mfsa2020-49/)

---

### Post by ajgreeny on 2020-11-10
One thing that I make a lot of use of is the "today pane" which shows items from the current lightning calendar extension into a pane on the right hand side of the window.  I find this to be a terrific *aide-memoire*.

T'Bird 78 versions, which now have lightning calendar incorporated and not as an extension, do not appear to have the "Today pane" available; a great pity and I hope the possibility to get it back comes soon.

---

### Post by rbmorse on 2020-11-10
Running 78.3.2 obtained via update.  You can toggle the desired and appreciated "today pane" by pressing <F11> with the mail pane active.

---

### Post by ajgreeny on 2020-11-11
> **rbmorse said:**
> Running 78.3.2 obtained via update.  You can toggle the desired and appreciated "today pane" by pressing <F11> with the mail pane active.

That's the version of TBird I have in my Xubuntu 20.10 but F11 does not show me the today pane when in the mail tab.

---

### Post by rbmorse on 2020-11-11
Odd. 

 Do you have the today pane enabled in the view tab?  If so,  Under preferences, do you have a setting for the number of days shown in the upcoming section?

---

### Post by ajgreeny on 2020-11-11
OK, I've just figured this out.

The way to get the Today pane showing is actually to open the **Tasks and Events** tab, which I generally never use, and then at the bottom of the left hand pane of that click on the Enable button for the Home calendar? (I think that's what it was in my case) then the Today pane suddenly appears in the Mail tab and can now be shown or hidden in the same way that it was before with F11 or clicking below it in the staus bar if that is enabled.

This seems completely different to enabling the Today Pane previously, and I can only presume it is because the old lightning callendar extension no longer exists in the form that it used to.

---

### Post by walts48 on 2020-12-03
Security vulnerability fixed in Thunderbird 78.5.1 and still no update for the 68.10.0 from the update repo.

[https://www.mozilla.org/en-US/security/advisories/mfsa2020-53/](https://www.mozilla.org/en-US/security/advisories/mfsa2020-53/)[URL="https://www.mozilla.org/en-US/security/advisories/mfsa2020-53/"]

> When reading SMTP server status codes, Thunderbird writes an integer  value to a position on the stack that is intended to contain just one  byte. Depending on processor architecture and stack layout, this leads  to stack corruption that may be exploitable.

[/URL]

---

### Post by rbmorse on 2020-12-03
I'm on 20.10 and Thunderbird updated to 78.5.0

---

### Post by Frogs Hair on 2020-12-03
The latest version, 78.5.1 is available on the development release. I don't know when or if the update will be uploaded to the standard repositories.

---

### Post by walts48 on 2020-12-04
Well, with the absence of complaints from Ubuntu 20.10 users about the UI changes and loss of extensions that weren't updated to work with 78.x.x I'm lead to believe the application isn't used that much and Ubuntu users use some other apps for email.

I'll continue to test the release candidates for the Thunderbird team, and celebrate when Ubuntu finally backports 78 to 18.04 and 20.04. I sure hope that will be before version 91.3 scheduled for next year.

[https://wiki.mozilla.org/Release_Management/Calendar](https://wiki.mozilla.org/Release_Management/Calendar)

---

### Post by walts48 on 2021-01-30
Thunderbird 78.7.0 is out.

[https://www.thunderbird.net/en-US/thunderbird/78.7.0/releasenotes/](https://www.thunderbird.net/en-US/thunderbird/78.7.0/releasenotes/)

My Fedora 33.0 just updated today.

---

