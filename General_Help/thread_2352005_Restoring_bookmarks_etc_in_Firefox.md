---
title: "Restoring bookmarks etc in Firefox"
date: 2017-02-08
forum: General Help
---

### Post by rawlins02 on 2017-02-08
To diagnose a problem with Firefox freezing, I moved .mozilla directory to .mozilla-bak.  After running Firefox for a few minutes I moved .mozilla-bak back to .mozilla. But now I can't figure out how to restore my bookmarks and settings for Firefox. Starting Firefox brings up a bare browser. I'm running Firefox 51.0.1 on Ubuntu 14.04.

---

### Post by leunam12 on 2017-02-08
You have to edit a file in your /home/yourname/.mozilla/firefox directory to tell firefox to use your old profile. I think the file is profiles.ini or profiles.conf, something like that

---

### Post by Cavsfan on 2017-02-08
I always copy this folder to any new install and it keeps the bookmarks and everything that it had: /home/cavsfan/.mozilla/

[ATTACH=CONFIG]273589[/ATTACH]

This is what          leunam12 is referring to:

[ATTACH=CONFIG]273590[/ATTACH]


The contents of profiles.ini:

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default-1459117445437
IsRelative=1
Path=xap0oskp.default-1459117445437
```

Although I have never edited it before, never had the need to.

---

### Post by ajgreeny on 2017-02-08
> **leunam12 said:**
> You have to edit a file in your /home/yourname/.mozilla/firefox directory to tell firefox to use your old profile. I think the file is profiles.ini or profiles.conf, something like that
If you have backed up the complete .mozilla folder this should not be the problem as the profile.ini will be within that backed up folder.
However check that the profile.ini file is still pointing to the correct Path=xap0oskp.default and edit it if necessary.

I have copied the hidden .mozilla folder to all my separate machines and never had a need to edit the profile.ini file in order to get back all the add-ons, bookmarks and saved passwords etc etc, so I do not understand why you seem to have lost just your bookmarks; or is more missing than just those?

---

### Post by rawlins02 on 2017-02-08
As you suggest, I edited profile.ini with this

Path=xap0oskp.default

Now Firefox won't start, complaining it can't find a profile.

---

### Post by rawlins02 on 2017-02-08
I've gotten Firefox to start by changing back the Path line. But no bookmarks. Here is the profiles.ini file. I'm not sure what to do with it in response to the posts in this thread.

```

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=9exk5ftx.default
Default=1


```

---

### Post by &amp;KyT$0P# on 2017-02-08
> **rawlins02 said:**
> To diagnose a problem with Firefox freezing, I moved .mozilla directory to .mozilla-bak.  After running Firefox for a few minutes I moved .mozilla-bak back to .mozilla. 
Did you completely quit Firefox **before** moving those folders around?

---

### Post by oldfred on 2017-02-09
I believe I have used same profile for 10 years. I have copied to NTFS and used both XP & Ubuntu. Then copied to laptop when traveling & copied back.

When installing to new computer, I have profile in /mnt/data, so I have to edit profile.ini.

Same for both Thunderbird & Firefox.

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

I do normally start both Firefox & Thunderbird to create default profiles. I then copy my standard profile.ini & XXXXX.default profile.
Each user has a unique profile.

---

### Post by leunam12 on 2017-02-09
This is what happens: If you install Ubuntu and you copy your old .mozilla directory from your backup to your $HOME directory you won't have to edit your profiles.ini file; but if you rename your .mozilla directory and start Firefox, it will create a new profile and a new profiles.ini file; in that case, if you want your stored settings, you have to replace the new profiles.ini with the old one or edit it so that it points to your  old profile directory where you have all your settings stored.

I have been using the same profile for many years on both Windows and Ubuntu and very rarely I have to edit the profiles.in file but sometimes I have to do it for whatever reason (overwrote or deleted the old one).

---

### Post by rawlins02 on 2017-02-09
> **halogen2 said:**
> Did you completely quit Firefox **before** moving those folders around?

I can not recall the order of operations. At some point I quit Firefox and then restarted. If I understand your question correctly, I'm not certain if Firefox was running when I moved the directory name to .mozilla-bak.

---

### Post by rawlins02 on 2017-02-09
> **leunam12 said:**
> This is what happens: If you install Ubuntu and you copy your old .mozilla directory from your backup to your $HOME directory you won't have to edit your profiles.ini file; but if you rename your .mozilla directory and start Firefox, it will create a new profile and a new profiles.ini file; in that case, if you want your stored settings, you have to replace the new profiles.ini with the old one or edit it so that it points to your  old profile directory where you have all your settings stored.

I have been using the same profile for many years on both Windows and Ubuntu and very rarely I have to edit the profiles.in file but sometimes I have to do it for whatever reason (overwrote or deleted the old one).

This sounds right. For me, it looks as though I have just a new profile, and no others. The one with my prior bookmarks and settings is not in .mozilla/firefox. Guess I need to brush up on how this all works...

```

rawlins@computer2:~/.mozilla/firefox>ls -l
total 12
-rw-rw-r--  1 rawlins rawlins   95 Feb  8 21:15 profiles.ini
drwx------ 14 rawlins rawlins 4096 Feb  9 11:30 9exk5ftx.default/
drwx------  5 rawlins rawlins 4096 Feb  9 11:33 Crash Reports/


```

---

### Post by ajgreeny on 2017-02-09
Have a look in the *.mozilla/firefox/**qn4bdmr0.default**/bookmarkbackups/* folder and there should be some older backups of your bookmarks as files which you can import back into the current FF you are running.

Your system will have a different alphanumeric name for the folder from my qn4bdmr0.default but the rest of the pathway should be the same.

---

### Post by &amp;KyT$0P# on 2017-02-09
> **rawlins02 said:**
> If I understand your question correctly, I'm not certain if Firefox was running when I moved the directory name to .mozilla-bak.
That's part 1 of the answer.  Part 2 is whether Firefox was running when you replaced your original .mozilla folder.

It is very important to completely quit Firefox before manually touching [FONT=Courier New]~/.mozilla/firefox[/FONT] or its contents.  Otherwise the manual changes will be overwritten (at best).  Or you could end up with a totally corrupted profile (at worst).

This is written at the top of the settings file, [prefs.js]("http://kb.mozillazine.org/Prefs.js_file") -
```
# Mozilla User Preferences

/* Do not edit this file.
 *
 * If you make changes to this file while the application is running,
 * the changes will be overwritten when the application exits.
 *
 * To make a manual change to preferences, you can visit the URL about:config
 */
```
Unless you have another backup of [FONT=Courier New]~/.mozilla[/FONT], your settings are probably lost.

As for bookmarks?  Cross your fingers and follow ajgreeny's suggestion.  Into Bookmarks menu > Show all bookmarks, then look under Import and Backup > Restore.  Keep trying files in the list until you get your bookmarks back.  You won't get the favicons back, but everything else should be in place.

Hope this helps.

---

### Post by rawlins02 on 2017-02-09
> **ajgreeny said:**
> Have a look in the *.mozilla/firefox/**qn4bdmr0.default**/bookmarkbackups/* folder and there should be some older backups of your bookmarks as files which you can import back into the current FF you are running.

Your system will have a different alphanumeric name for the folder from my qn4bdmr0.default but the rest of the pathway should be the same.


Not sure it matters, but my directory is .mozilla/firefox/9exk5ftx.default/.  Assume that specific directory you listed is from your machine, and not a common one I should have.

I have nothing in that backup directory older than yesterday when this all went wrong.

```

rawlins@computer2:~/.mozilla/firefox/9exk5ftx.default/bookmarkbackups>ls -l
total 8
-rw------- 1 rawlins rawlins 1871 Feb  8 13:49 bookmarks-2017-02-08_19_ESntpjgnTmc6sQbowgChmg==.jsonlz4
-rw------- 1 rawlins rawlins 1884 Feb  9 09:19 bookmarks-2017-02-09_19_SqvwdGS9NPAqFfJwxupCtg==.jsonlz4


```

@halogen2: I agree settings are probably lost.

---

### Post by &amp;KyT$0P# on 2017-02-09
And neither of those .jsonlz4 files contain your bookmarks?

Do you still have the other .mozilla directory?  If so, does it have any bookmark backups?

---

### Post by rawlins02 on 2017-02-10
> **halogen2 said:**
> And neither of those .jsonlz4 files contain your bookmarks?

Do you still have the other .mozilla directory?  If so, does it have any bookmark backups?

The .jsonlz4 files are not ASCII. Not clear to me what's in them.

Since I moved .mozilla-bak to .mozilla, I only have the one directory. 

I'm going to try to migrate a .mozilla profile from another computer, assuming I can do so without screwing up my profile on the other machine. Will do more homework and cross my fingers.

---

### Post by ajgreeny on 2017-02-10
> **rawlins02 said:**
> The .jsonlz4 files are not ASCII. Not clear to me what's in them.

Since I moved .mozilla-bak to .mozilla, I only have the one directory. 

I'm going to try to migrate a .mozilla profile from another computer, assuming I can do so without screwing up my profile on the other machine. Will do more homework and cross my fingers.
If you have another computer with a hidden .mozilla folder simply copy that complete folder, not just the 9exk5ftx.default subfolder or you will again have the profile.ini pointing to the wrong folder.

---

### Post by &amp;KyT$0P# on 2017-02-10
> **rawlins02 said:**
> The .jsonlz4 files are not ASCII. Not clear to me what's in them.
The only way I know to see the contents is to restore them and see what shows up.

> I'm going to try to migrate a .mozilla profile from another computer, assuming I can do so without screwing up my profile on the other machine. 
As long as you completely quit Firefox on both machines **before** copying/replacing the .mozilla folder, this should go fine.  I do this all the time.

---

### Post by rawlins02 on 2017-02-10
The .jsonlz4 files are new, so no surprise nothing in them when I restore. Tomorrow I will copy over the .mozilla folder from my other computer. Hopefully one way to solve the problem.

---

### Post by ortermagic on 2017-02-10
I make a .json file using ...bookmarks>show all bookmarks>import and backup>import backups from html this makes a .json which you can use to restore bookmarks to your toolbar.
Maybe i'm being simplistic here tho

---

### Post by ortermagic on 2017-02-10
I always carry a .json copy on a usb flash drive and update when necessary

---

### Post by ajgreeny on 2017-02-11
But it's a bit late now when the bookmarks are already lost, so there is nothing there to export to json or html or anything else.

Incidentally you can if you wish easily make FF save an html file of your bookmarks by going to **about:config** in firefox, accept the dragons warning and then either change the boolean entry at **browser.bookmarks.autoExportHTML** to true, or create it if it does not exist already.

You will then find a bookmarks.html file in the .mozilla/firefox/a9he4k0.default folder (yours will be a different alphanumeric name) which is much easier to read than the new **bookmarks-2016-12-28_586_mcD2gYyMoS655PjAWOidAQ==.jsonlz4** files saved by default, which I assume are archived files though I have not managed to open one yet.

---

### Post by rawlins02 on 2017-02-16
> **ajgreeny said:**
> But it's a bit late now when the bookmarks are already lost, so there is nothing there to export to json or html or anything else.

Incidentally you can if you wish easily make FF save an html file of your bookmarks by going to **about:config** in firefox, accept the dragons warning and then either change the boolean entry at **browser.bookmarks.autoExportHTML** to true, or create it if it does not exist already.

You will then find a bookmarks.html file in the .mozilla/firefox/a9he4k0.default folder (yours will be a different alphanumeric name) which is much easier to read than the new **bookmarks-2016-12-28_586_mcD2gYyMoS655PjAWOidAQ==.jsonlz4** files saved by default, which I assume are archived files though I have not managed to open one yet.

I've tried this. I see the bookmarks.html file. Will explore more.

In trying to understand how this all works, I've been referring to this page:
[https://support.mozilla.org/t5/Install-and-Update/Back-up-and-restore-information-in-Firefox-profiles/ta-p/2045](https://support.mozilla.org/t5/Install-and-Update/Back-up-and-restore-information-in-Firefox-profiles/ta-p/2045)

As a test I'm trying to load the bookmarks and settings from computer 1 to computer 2. Using the guidance in that support.mozilla.org page. I've copied directory computer1_profile/ into ~/.mozilla/firefox on computer 2. Then started the profile manager with firefox -P and loaded the new profile. Firefox still starts with no bookmarks  or settings. On computer 2, the files that are being updated in the new computer1 profile I loaded earlier. But none of the bookmarks or settings from computer 1 are showing.

@ortermagic, you suggested using the .json files. Any web resources that explain more?

---

### Post by oldfred on 2017-02-16
Are you resetting profile.ini with old profile?
See also links in post #8.

I always start Firefox & Thunderbird, so it creates new default profiles. Then copy my profiles over & update profile.ini.

Now I actually must have my profile in /mnt/data and in every install change just profile.ini to use that.

---

### Post by rawlins02 on 2017-02-16
> **oldfred said:**
> Are you resetting profile.ini with old profile?
See also links in post #8.

I always start Firefox & Thunderbird, so it creates new default profiles. Then copy my profiles over & update profile.ini.

Now I actually must have my profile in /mnt/data and in every install change just profile.ini to use that.

No, I have not changed profile.ini. 

I have a separate external hard drive that I can use like your /mnt/data. I use this external drive to sync the two laptops. So, is this the specific part of the web page you listed in post #8 that I should consult if I want to keep the same profile going on both laptops?

[http://kb.mozillazine.org/Moving_your_profile_folder#Modify_profiles.ini_to_point_to_the_new_location_-_Advanced](http://kb.mozillazine.org/Moving_your_profile_folder#Modify_profiles.ini_to_point_to_the_new_location_-_Advanced)

---

### Post by oldfred on 2017-02-16
If you are directly mounting it.
Its just with a removable drive, if that drive is not there, then you will have issues.

this is my profile.ini

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/mnt/data/mozilla/firefox/wojjex8t.default
Default=1

```

I change the IsRelative and Path to match where my profile xxxxxx.default really is.

---

### Post by rawlins02 on 2017-02-18
> **oldfred said:**
> If you are directly mounting it.
Its just with a removable drive, if that drive is not there, then you will have issues.

this is my profile.ini

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/mnt/data/mozilla/firefox/wojjex8t.default
Default=1

```

I change the IsRelative and Path to match where my profile xxxxxx.default really is.

OK I think I understand the process much better now. This page has the relevant information on copying files and directories into new a profile:
[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

I've restored bookmarks from a bookmarkbackup folder. That's the important part. Going forward I'll probably keep one profile as suggested and migrate it to new installs and computers.

---

