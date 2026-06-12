---
title: "Firefox. Separate User Profiles. Where best to save new folders for them."
date: 2015-10-06
forum: General Help
---

### Post by mikodo on 2015-10-06
Hello everyone.

In the [support.mozilla ...profile-manager-create ]("https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles")it states one can choose where to save folders for profiles. I would like to do that.

I want to create a couple of folders as they suggest, and name them, "Banking", "E-Purchases" but, I don't want to stick them in /home/user/.mozilla, as I want them separate from there.

So, can I make the folders anywhere in /home/user? What would be best, do you think?

Thank you.

---

### Post by Dennis N on 2015-10-06
There is an button to choose a custom folder when you create a new profile with Firefox profile manager. As to where, I think it must be within your home folder. If you use the default, all profiles end up as files located in: 
~/.mozilla/firefox

```
dmn@Roxanne:~/.mozilla/firefox$ ls
Crash Reports  laf9qi63.default  profiles.ini  r4dell4r.Classic

```
shows two profiles: default and Classic.

profiles.ini contains the paths to each profile that has been created.

---

### Post by mikodo on 2015-10-06
Thank you, Dennis.

As I was waiting to hear responses, I thought about what I might do. I started a folder in Documents called FF_Profiles. Inside of the sub-directory, I made five folders, FF_Backup. (Just a place holder for when I start saving my .mozilla profiles). And; 4 more called: Banks, E_Purchases, Professional_Associations, and Transfer_Profile.

I am going to backup FF_Profiles, with all backup scenarios. I don't backup my ~ as, I use a symlink to /mnt/data from ~ to populate the sub-directories I use and backup /mnt/data/, that holds my Documents/and/others. Until now, I have been using FF Sync to save my .profiles and it has never failed me across a few installs but, I know better than depending on an outside service, solely. I am going to start saving them in my own backup nodes too.

I haven't started working with the FF Profile Manager as yet. That's next now, that I have your response.

I appreciate, the direction again. I will go ahead with my plans now.

Kink Regards.

---

### Post by mikodo on 2015-10-07
What I did is this:

Made a Folder ~/Documents/FF_ Profiles/ Inside it, I made five folders.

Banks
Professional_Associations
E_Purchases
Transfer_Profile
FF_Backup

The Transfer_Profile has all the privacy and safety features I use including, the extensions like NoScript, Privacy Badger etc. It is a completely virgin profile.

The E_Purchases folder can have as many "profiles" in it I want. I made 5 to begin with. (Well, I did read that FF Profile Manager, has a limit of 30 lol).

In the FF Profile Manager, I make Profiles fitting to each of the folders. Banking, E_Purchases(0,1,2,3,4) and so on. One can use a descriptive name to remember it. When I want to buy something, I plan to use one of those for going to only the site I am buying from (have a url from my desktop to place in the browser to go to directly to the site), then, delete that Profile when, I am happy with my purchase.

For populating the profiles for each of the new folders, I just copy and paste from Thunar, the profiles from the Transfer_Profile's folder and stick them in any new folder's profiles I have started after, deleting its' original profiles that FF populates it with, upon inception. Easy to set up new Folder's profiles with, the settings I want.

FF_Backup, is for saving the profiles from my default FF browser for, placing in my backup scenarios.

I will only use the default FF browser profile for, surfing the net.

Now I have the security of FF that I am familiar with and, I don't need to mess with any other browsers and still keep things separate, as I like.

---

### Post by mikodo on 2015-10-12
Well, I cleaned up what I wrote in the earlier posts. If anyone stumbles across this thread, I hope it is clearer how I have set up and use multiple FF user profiles.

Thank you.

---

