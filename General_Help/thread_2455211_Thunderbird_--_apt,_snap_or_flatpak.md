---
title: "Thunderbird -- apt, snap or flatpak?"
date: 2020-12-15
forum: General Help
---

### Post by shmu26 on 2020-12-15
I am on Kubuntu 20.04 LTS. 
Discover gives me three choices for Thunderbird: the regular distro-specific apt version from the repo, or flatpak, or snap. I could also download the official Mozilla version and install that, if I want to. Which should i choose? It looks like I have the standard distro version installed.

This question applies to other apps as well, such as LibreOffice and Firefox.

---

### Post by CatKiller on 2020-12-15
Generally native (apt) packages are best unless you have a specific reason to use snaps or flatpaks.

The specific benefit and drawback of snaps/flatpaks is that they're run in a container. So you'll get newer versions sooner (or any versions at all for some proprietary software) because the application doesn't need to worry about the other software libraries on your machine, and it's more secure. But it's also less integrated with the system for things like themeing, and you might need to give specific permission for it to access other parts of your system (or it might not be able to at all) because of that isolation.

---

### Post by shmu26 on 2020-12-15
> **CatKiller said:**
> Generally native (apt) packages are best unless you have a specific reason to use snaps or flatpaks.

The specific benefit and drawback of snaps/flatpaks is that they're run in a container. So you'll get newer versions sooner (or any versions at all for some proprietary software) because the application doesn't need to worry about the other software libraries on your machine, and it's more secure. But it's also less integrated with the system for things like themeing, and you might need to give specific permission for it to access other parts of your system (or it might not be able to at all) because of that isolation.
Okay, so native is better, all things being equal. 
What if I need to choose between Snap and Flatpak?
For instance, I experience a little bug with the native version of Libreoffice. Some buttons don't display properly on the Format toolbar. I posted on the LibreOffice forum about it, and no solution emerged from the discussion. But I discovered that the Flatpak version doesn't have that bug.

---

### Post by CatKiller on 2020-12-15
> **shmu26 said:**
> What if I need to choose between Snap and Flatpak?
Then prepare yourself for holy wars, of the like not seen since Emacs vs Vi.

---

### Post by deadflowr on 2020-12-15
Why choose?
You can run them all at the same time. Or a least have them all installed.
It's by design for you to be able to do that.

---

### Post by walts48 on 2020-12-15
> **shmu26 said:**
> I am on Kubuntu 20.04 LTS. 
Discover gives me three choices for Thunderbird: the regular distro-specific apt version from the repo, or flatpak, or snap. I could also download the official Mozilla version and install that, if I want to. Which should i choose? It looks like I have the standard distro version installed.

This question applies to other apps as well, such as LibreOffice and Firefox.

The Official Mozilla version of Firefox is kept pretty much updated in the repo.

The Ubuntu repo Thunderbird version 68.10.0 is way behind, and I recommend installing the latest 78.6.0 from [https://www.thunderbird.net/en-US/thunderbird/all/](https://www.thunderbird.net/en-US/thunderbird/all/).

---

### Post by ActionParsnip on 2020-12-15
Just run
```

sudo apt install thunderbird

```
and be done :)

---

### Post by shmu26 on 2020-12-15
> **walts48 said:**
> The Official Mozilla version of Firefox is kept pretty much updated in the repo.

The Ubuntu repo Thunderbird version 68.10.0 is way behind, and I recommend installing the latest 78.6.0 from [https://www.thunderbird.net/en-US/thunderbird/all/](https://www.thunderbird.net/en-US/thunderbird/all/).
Not sure what Thunderbird version I had before, but I just upgraded now to Kubuntu 20.10, and Thunderbird shows [COLOR=#000000]78.5.0 (64-bit)[/COLOR]

---

### Post by deadflowr on 2020-12-15
> **shmu26 said:**
> Not sure what Thunderbird version I had before, but I just upgraded now to Kubuntu 20.10, and Thunderbird shows [COLOR=#000000]78.5.0 (64-bit)[/COLOR]

Ubuntu 20.10 shipped with the updated version.
Usually the older supported releases get the updated version too.
But because of a few big changes between 68.X and 78.X, that upgrade has been delayed.

---

### Post by walts48 on 2020-12-16
> **deadflowr said:**
> Ubuntu 20.10 shipped with the updated version.
Usually the older supported releases get the updated version too.
But because of a few big changes between 68.X and 78.X, that upgrade has been delayed.

Why? Every other Linux distribution has updated.

Don't give me the weak extensions break excuse.

---

### Post by #&amp;thj^% on 2020-12-16
> **walts48 said:**
> Why? Every other Linux distribution has updated.

Don't give me the weak extensions break excuse.

From Mozilla>>>
> Updates from 68 to 78 that are prompted by TB's internal update process have not yet been deployed, due to several unresolved issues. That doesn't stop users from updating manually, but it's not recommended unless careful attention is paid to profile configuration and data migration. It's recommended to wait until Ubuntu releases the update and it's performed from within TB. 
Source: [https://support.mozilla.org/en-US/questions/1302459](https://support.mozilla.org/en-US/questions/1302459)

---

### Post by TheFu on 2020-12-16
> **shmu26 said:**
> Okay, so native is better, all things being equal. 
What if I need to choose between Snap and Flatpak?
For instance, I experience a little bug with the native version of Libreoffice. Some buttons don't display properly on the Format toolbar. I posted on the LibreOffice forum about it, and no solution emerged from the discussion. But I discovered that the Flatpak version doesn't have that bug.

There are always trade-offs.

Thick client email programs are the front-line programs to be hacked, so perhaps having a little extra security around them is a good idea.  We have a few choices.
[LIST]
[*]standard client from APT
[*]standard client from APT, but run inside a constrained environment
[*]client from APT using a PPA
[*]client from APT using a PPA, but run inside a constrained environment
[*]snap package
[*]flatpak
[*]Linux containerized setup
[/LIST]
There are pros/cons for each.
I find the snap constraints to be just a little too restrictive. No local overrides possible.
Based on reading, flatpaks can be constrained in the same way, but with local overrides possible as needed.
A linux container setup is non-trivial. Getting any graphics/desktop program working between a normal desktop and the container isn't easy.

I use thunderbird, the APT version, but run it inside a constrained environment with firejail. For me, that is just enough protection, but not so much that it gets in the way or breaks stuff. Wish I could say that same about snap packages, but that hasn't been my experience. On a few systems, snaps of any sort will not run at all due to problems known since at least 2017.  I'm on 68.x.x still, but need a few plugins for LDAP, iCal and lightning so I'm afraid of newer releases.

Everyone needs to figure out the correct mix for their needs.

---

### Post by shmu26 on 2020-12-16
On Ubuntu 20.04 LTS, my vote goes to the snap version of Thunderbird.
1 It is on the latest edition 
2 It supports the command
> thunderbird -ProfileManager
which is important for importing a profile. (The flatpak version doesn't support this command.)
3 Despite being a Snap app, it is still compatible with Birdtray, which creates a system tray icon that shows unread count etc. Birdtray is in the repo.

EDIT: Actually, there is a flatpak version of Birdtray. And the command that I claimed doesn't work on flatpak might indeed work if you give the right path for the thunderbird executable.

---

### Post by ajgreeny on 2020-12-16
I am still using T'bird from the standard repos in 20.04 and I must have lightning alongside it.
So far I have not used T'bird 78 but as I understand it, the lightning that is incorporated into that version will not use the calendar configuration from 68.

Can anyone tell me if this is so and if there's a way to export/import the many calendars I now use into the new version. Without that version 78 will be a non starter for me.

---

### Post by TheFu on 2020-12-16
> **ajgreeny said:**
> I am still using T'bird from the standard repos in 20.04 and I must have lightning alongside it.
So far I have not used T'bird 78 but as I understand it, the lightning that is incorporated into that version will not use the calendar configuration from 68.

Can anyone tell me if this is so and if there's a way to export/import the many calendars I now use into the new version. Without that version 78 will be a non starter for me.

^^^^^ This.  
Not really a non-starter, but just a pain.  I use different calendars for every project so they can be archived with project files.  I need to plan time and will want to capture all the URLs for my different network calendars BEFORE I begin any migration to a version of Lightning that breaks it.  Would hate to miss an appointment personal or professional over something like this.

---

### Post by walts48 on 2020-12-17
> **1fallen said:**
> From Mozilla>>>

Source: [https://support.mozilla.org/en-US/questions/1302459](https://support.mozilla.org/en-US/questions/1302459)

Old post.

Updates from 68.12.1 were enabled with version 78.2.2 released on September 10, 2020.

[https://www.thunderbird.net/en-US/thunderbird/78.2.2/releasenotes/](https://www.thunderbird.net/en-US/thunderbird/78.2.2/releasenotes/)

We are now up to 78.6.0 released 12/15/2020.

---

### Post by walts48 on 2020-12-17
> **ajgreeny said:**
> I am still using T'bird from the standard repos in 20.04 and I must have lightning alongside it.
So far I have not used T'bird 78 but as I understand it, the lightning that is incorporated into that version will not use the calendar configuration from 68.

Can anyone tell me if this is so and if there's a way to export/import the many calendars I now use into the new version. Without that version 78 will be a non starter for me.

What configuration?

Using a Google calendar with the Provider for Google Calendar extension? Update the extension.

---

### Post by ajgreeny on 2020-12-17
No, not google-calendar, which I do not use, but my own various separate calendars which I use a lot.

It looks as if I can use the **Events and Tasks** menu of T'bird, Export and export as .ics files which I assume can then be imported into T'bird 78.

---

### Post by walts48 on 2020-12-18
I had no issue with my calendars when I upgraded my 68 version from Thunderbird to the 78 version from Thunderbird. The calendar is integrated. No extension necessary.

If it makes you feel safer the export the calendars.

I do that regularly, along with backing up the profile.

---

### Post by TheFu on 2020-12-18
> **walts48 said:**
> I had no issue with my calendars when I upgraded my 68 version from Thunderbird to the 78 version from Thunderbird. The calendar is integrated. No extension necessary. 

For your situation.  Which calendar types did you NOT see any issues?  Local, Google, any ICS, any iCal, any other specific calendar services like nextcloud, owncloud, Zimbra, or one of the 50 others?

Not everyone is you or me.  We have different needs.  For me, stability trumps "new" every time.  Sometimes stability trumps security too. Just depends on what other steps your admin or network is taking too.  Nearly all my calendars are Zimbra, but a few are from nextcloud local and federated instances.  I don't do any local calendars, since there are too many clients and I want to see the same views in every client, but also want to push a sleep reminder across all clients from any client saying to sleep 2 hrs (wk meeting) or 3 days (bdays).

Not everyone is you.   Or me.  It is safe to say that I'm odd.

---

### Post by ajgreeny on 2020-12-18
You did not say whether or not the calendar in T'bird 78 picks up local calendars, not online ones such as google calendar, when you upgrade from 68 to 78; that's what I need to know, because there is always a problem if I upgrade to 78 with T'bird profiles opened in any newer version when returning to an older version.

Until Xubuntu 20.04 moves to T'bird 78 I shall stay with T'bird 68, the default from the repos; it works for me and gets security updates as needed.

---

### Post by walts48 on 2020-12-19
Just get 68.10.0 updated in the repo.

All other distros have and if you really want to stay on 68 download and install it from Thunderbird.

---

### Post by ajgreeny on 2020-12-19
> **walts48 said:**
> Just get 68.10.0 updated in the repo.

All other distros have and if you really want to stay on 68 download and install it from Thunderbird.
Why install it direct from Thunderbird when it's already in the repos?
That's how things are done in Windows but not in Linux where we use the repos wherever possible!

---

### Post by walts48 on 2020-12-20
> **ajgreeny said:**
> Why install it direct from Thunderbird when it's already in the repos?
That's how things are done in Windows but not in Linux where we use the repos wherever possible!

You got an update to 78.something from 68.10.0 using the Software Updater? I haven't even seen 68.12.0.

Well, if we use repos wherever possible please keep the main updater one updated. Thank you.

---

### Post by TheFu on 2020-12-20
Mr walts48 doesn't understand that nobody here works for Canonical (including the volunteer moderators) and we don't have any control over what is or isn't included/updated.  

Some systems cannot have any feature changes, so moving from 68.x.x --> 69.x.x isn't allowed, much less going to 78.x.x.  That would break businesses and isn't how LTS releases work.  For an LTS, no new features.  Period.  Only security or crashing bug updates are allowed.  I don't know how freely non-LTS releases are about software updates. Sorry. I consider non-LTS releases throw-away. Basically a toy to try out for a week or two.

If a new version of some software is desired in the next Ubuntu Release, 21.04 in April, open a request for that in the Dev+1 tracking system.  Thunderbird will definitely get updated, but to which level would depend on timing.  I figure everyone here can google to find the request page in launchpad.

Anyone who wants the latest version of any specific package can use either a PPA or a snap package [https://snapcraft.io/thunderbird](https://snapcraft.io/thunderbird) or a flatpak.  We people who cannot have newer versions need the expected, default rules, to keep working as planned.
```
$ snap info thunderbird
name:      thunderbird
summary:   Mozilla Thunderbird email application
publisher: Canonical&#10003;
store-url: [https://snapcraft.io/thunderbird](https://snapcraft.io/thunderbird)
contact:   [https://launchpad.net/distros/ubuntu/+source/thunderbird](https://launchpad.net/distros/ubuntu/+source/thunderbird)
license:   MPL-2.0
description: |
  Thunderbird is a free and open source email, newsfeed, chat, and calendaring client, that’s easy
  to set up and customize. One of the core principles of Thunderbird is the use and promotion of
  open standards - this focus is a rejection of our world of closed platforms and services that
  can’t communicate with each other. We want our users to have freedom and choice in how they
  communicate.
snap-id: k1Ml1O9GzSO2QftV0ZlWSbUfQ78nN460
channels:
  latest/stable:    78.6.0 2020-12-15 (97) 69MB -
  latest/candidate: &#8593;                           
  latest/beta:      &#8593;                           
  latest/edge:      78.6.0 2020-12-15 (98) 69MB -
```
Use either the Software Center or **sudo snap install thunderbird**.  From that point forward, your system will get the new thunderbird snap package whether you want it or not.

---

### Post by ajgreeny on 2020-12-20
@walts48.
What you said in post 22 was 
"All other distros have and if you really want to stay on 68 download and install it from Thunderbird."

What I meant was why install version 68 direct from Thunderbird as you suggest when 68 is already in the repos; it makes no sense at all.

Like TheFu, I am very much wanting stability and continuity, but not necessarily the newest and best(?) version of such an important application as thunderbird so whilst I am using 20.04 I shall stick with T'bird 68 from the repos.

---

### Post by walts48 on 2020-12-21
> **ajgreeny said:**
> @walts48.
What you said in post 22 was 
"All other distros have and if you really want to stay on 68 download and install it from Thunderbird."

What I meant was why install version 68 direct from Thunderbird as you suggest when 68 is already in the repos; it makes no sense at all.

Like TheFu, I am very much wanting stability and continuity, but not necessarily the newest and best(?) version of such an important application as thunderbird so whilst I am using 20.04 I shall stick with T'bird 68 from the repos.

I meant when Ubuntu finally updates to whatever 78.x.x version and users want to stay on version 68.

I'll recommend using 68.12.0.

@TheFu

I understand that nobody here works for Canonical, just like nobody that works for Mozilla is on mozillaZine. :wink::wink:

There was no 69.x.x Thunderbird release. Thunderbird closely follows the Firefox ESR release schedule.

Thunderbird 78.6.0 is almost halfway through that cycle, and 78.7.0 will be released sometime next month.

[https://wiki.mozilla.org/Release_Management/Calendar](https://wiki.mozilla.org/Release_Management/Calendar)

I'll pass on the snaps and other PPA's, use Thunderbird from Thunderbird and continue advocating for an update for the users that only update through the Software Updater.

---

### Post by TheFu on 2020-12-21
In another thread, Doug posted this helpful link: [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

### Post by walts48 on 2020-12-22
> **TheFu said:**
> In another thread, Doug posted this helpful link: [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

Thanks for that.

Meanwhile, [https://lwn.net/Articles/840938/](https://lwn.net/Articles/840938/), [https://lwn.net/Articles/840960/](https://lwn.net/Articles/840960/), [https://lwn.net/Articles/840921/](https://lwn.net/Articles/840921/) and [https://lwn.net/Articles/840920/](https://lwn.net/Articles/840920/).

---

