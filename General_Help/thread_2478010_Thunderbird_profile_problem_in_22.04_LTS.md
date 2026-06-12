---
title: "Thunderbird profile problem in 22.04 LTS"
date: 2022-08-14
forum: General Help
---

### Post by nought2 on 2022-08-14
I've been happily running the same TB profile for more than 10y. My daily email needs are satisfied by my web-based email service provider. I use TB infrequently to archive messages and to search the archive.

Last time I used TB may have been about 2w ago, but it could have been 6w ago, I'm not sure because I've been away. In any event, whenever that last time was TB worked A-OK. Today things go wrong after I enter my primary password. After a delay of ~15sec TB launches but account/folder pane on left & message pane on right are vacant, blank.

I have no idea why TB is playing up. I haven't been mucking around with my system. Have only installed updates via apt and Flatpak.

In username/home/.thunderbird there's a 'Crash Reports' folder which contains a string of date & time stamped InstallTime files. The most recent of these are as follows:
InstallTime2022052005021   Modified 26 May
InstallTime2022062800715   Modified 05 Aug

05 Aug is the date I returned to my computer and applied updates via apt and Flatpak. 

Current version of TB installed to my Ubuntu 20.04 system is 91.11.0.

I have tried TB in Mozilla safe-mode to no avail. Same problem persists.

I thought it might be worth trying my profile in other versions of TB by removing it via apt and then installing via Flatpak or Snap.
Current TB available out of Flathub for Flatpak is 91.12.0.
Current TB available out of Snapcraft for Snap is 102.1.0-2 (latest/stable).

Installing TB via Flatpak was straightforward, however I do not know how to start the TB profile manager for this installation to permit me to pick up my existing profile.

Trying out the very latest TB version via Snap sounds appealing. Have not tried that yet because I fear I'll have a similar issue with hooking it up to my existing profile.

Tips on how to get Flatpak TB or Snap TB connected to an existing profile would be appreciated.
Also, have other TB users on Ubuntu 20.04 experienced profile problems after software update?

I am hoping this is an update glitch and that my long-time TB profile has not been corrupted and trashed.

---

### Post by SeijiSensei on 2022-08-14
First, your entire profile resides in /home/username/.thunderbird (note the leading dot). I recommend backing up this directory before trying anything else.

I suggest you start by creating a new profile just to make sure everything is working correctly. After backing up the profile directory use 
```

cd ~
mv .thunderbird .thunderbird.old

```
then start Thunderbird. If everything works correctly, you could simply set up your account again from scratch. If the account uses IMAP, Thunderbird will automatically download your folders and build its search database. If the account is set up to use POP, then we'll have to figure out how to fix your existing profile. But I suggest starting from scratch and seeing how it goes. I've rebuilt my Thunderbird profile a few times. Takes a while depending on how many messages you have and how fast the connection.

I avoid snap packages and always use regular .deb packages. Haven't really tried Flatpack. However if you want to keep up with the latest and greatest Thunderbird, you can add the Mozilla PPA:
```

sudo add-apt-repository ppa:mozillateam/thunderbird-stable 
sudo apt update
sudo apt install thunderbird

```

---

### Post by nought2 on 2022-08-15
> **SeijiSensei said:**
> First, your entire profile resides in  /home/username/.thunderbird (note the leading dot). I recommend backing  up this directory before trying anything else.Um, no. I put my profile folder on a separate HDD to allow it to be accessed by multiple operating systems. Thank you for correcting my sloppy file path syntax for the .thunderbird folder.

In my opening post I neglected to mention that I subscribe to a web-based email service provider, Fastmail. Sure, TB syncs my FM account via IMAP / JMAP, but my primary use for TB for a long stretch of years, and this profile in particular, has been to archive old messages when my online account storage is near full and for searching that archive to retrieve old messages.

Although I cannot open my TB profile my daily email use has not been interrupted. I don't use TB to send & receive messages, I do all that via FM's web-app in browser (FF) and FM's Android phone app.

When backing up my profile folder today the copy process produced three error messages:
1.) Error while copying "global-messages-db.sqlite"
error splicing file: input/output error
2.) Error while copying "INBOX-3" (sub-folder of mail.messagingengine.com)
error splicing file: input/output error
3.) Error while copying "cache.sqlite" (sub-folder of calendar-data)
error splicing file: input/output error

The bung files seem to suggest the profile could be corrupted.

Here's a screenshot of the TB window that appears 15sec after primary password has been entered and another with when I attempted to open the TB address book:
[URL="https://postimg.cc/7JhBcpf6"][IMG]https://i.postimg.cc/7JhBcpf6/20220815-TB-scnsht.png[/IMG]
[/URL][[IMG]https://i.postimg.cc/MX33RKFj/20220815-TB-and-Adrs-Bk-scnsht.png[/IMG]]("https://postimg.cc/MX33RKFj")

None of the functions I tried to access from the menu bar work. The TB window is to all intents and purposes dead.

I had a few add-ons installed. One enabled my FM address book to sync with TB via CardDAV protocol. If the profile was working addresses should be visible.

Following your advice I created a new folder on the same HDD and in the same directory as the troublesome profile. Using TB's profile manager I successfully added a new profile to this folder using credentials for my IMAP account. Which proves that my apt package manager installation of TB is working normally.

If you are able to assist me to rebuild my old archive folder I would be extremely grateful.

---

### Post by nought2 on 2022-08-17
There was a painless way out after all. Copy errors produced during old profile folder backup were the clues that led to a successful outcome.

After considering my options I decided to try deleting files that produced copy error notices one by one.

After deleting "global-messages-db.sqlite" at TB restart both account/folder pane and message pane were populated again. Much happiness! Although TB was sluggish while it was rebuilding the global-messages* file.

I shutdown TB and deleted "cache.sqlite". At next launch TB was significantly faster.

Decided not to delete "INBOX-3". It was >900MB and likely contained the messages of my IMAP inbox. If elements of it were corrupt it wouldn't be a problem, a good version would be present in my new TB profile, all its messages had been freshly synced.

New profile was completed by copying "Local Folders" folder from old profile into new profile. Just a simple copy-paste. At next launch of new TB profile all my archived messages were accessible. Beauty!

Both profiles now appear to be working normally. Speed of old one is same as new one. Will continue using new one in case of hidden issues in old one.

Job done.

---

