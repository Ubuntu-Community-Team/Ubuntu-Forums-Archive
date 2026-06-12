---
title: "Firefox common bookmarks"
date: 2008-02-12
forum: General Help
---

### Post by rm-rf on 2008-02-12
I need to setup a group of common bookmarks for all users on the system, while still allowing them to create their own. I need to do this in such a way that if I update the common bookmarks, it will not override their own bookmarks. 

Could somebody help? Pretty please?

# rm-rf

---

### Post by y-lee on 2008-02-13
Unfortunately you have ask a question that I don't know the answer to. I spent a few hours yesterday and a few this morning researching the topic and all i found was a suggestion on the Mozilla website that this feature be added to firefox. 

Ok what i do know is:

First, profile information is kept by default in **/home/username/.mozilla/firefox/** and bookmarks for a given profile are kept in that profiles folder in that location. This location can however be changed by an **[noparse]about:config[/noparse]** tweak. 

 In my case for the default profile the location is **/home/username/.mozilla/firefox/57wj47mm.default** and the bookmark file's name is **bookmarks.html**. The **57wj47mm** part will be probably be different for you and the **default** part is the profile name.

Second in my case I have several versions of firefox installed ***but* **using the firefox installed with Ubuntu (Dapper Drake) when a user creates a new profile or starts firefox for the first time, bookmarks are imported from the file **bookmarks.html** found at ** /etc/firefox/profile**. So that you could create your own profile call it common and then add the bookmarks you wish to applied across the system to that profile. And after you've added all the bookmarks you wish to be system wide  you can now copy the **bookmarks.html ** file for that profile found at **[noparse]/home/yourusername/.mozilla/firefox/57wj47mm.common[/noparse]** to **/etc/firefox/profile/bookmarks.html** replacing the old file with the new one. *Note you must be root or superuser to copy to this location.*

Now after this has been done when any user creates a new profile or starts firefox for the first time then the bookmarks you've added will be imported into their bookmarks. These users will however be able to delete move or change these bookmarks as well as add their own. So this in fact allows bookmarks to be system wide in a sense. 

**However**, this trick will not allow you to add new bookmarks to be applied system wide to profiles which already exist. These bookmarks are only imported the first time a profile is used. So it answers your question only partially.

Third I've not been able to find any firefox add on greasemonkey or stylish script that really answers your question fully.  But it *may* be and probably is possible to create an add on to do this or create a [UserChrome.js]("http://kb.mozillazine.org/UserChrome.js") script to allow a system bookmarks file that is merged at Firefox's startup with the users profile bookmarks. Doing such a change involves more than  I currently know about the inner workings of firefox. Altho, I've created a couple of simple UserChrome.js scripts just playing around but I don't really know what I am doing. :lolflag:

Fourth maybe one could add some or all of the following preference tweaks to a profiles **[noparse]about:config[/noparse]** or to a given profiles  **pref.js**  file to automatically import bookmarks

[LIST]
[*]browser.bookmarks.added_static_root = Enabled
[*]browser.bookmarks.import_system_favorites = Enabled
[*]profile.allow_automigration = Enabled
[*]profile.confirm_automigration = Disabled
[/LIST]

But I haven't tried it and these are mostly used to import IE favorites into firefox in WIndows. I am not sure how they act in Linux or if enabled where firefox tries to import them from. But if these tweaks are added to **[noparse]about:config[/noparse]** a user could change them easily but adding them to the profiles **pref.js** file and then changing that files permissions could prevent that.

I also suspect  that if these tweaks were stored in the **firefox.js**  file found  at **/etc/firefox/pref** on Dapper and for the default FF installed with Ubuntu then these tweaks would be system wide but probably only be imported the first time Firefox is started by a given user or a given profile.

Fifth this is an interesting question and I plan on researching it some more and maybe trying the above configuration  tweaks. Google doesn't help me much here so it will take some experimenting :confused:

Sorry i couldn't answer this fully or promptly. Just wanted you to know I am  trying   and it will take time for me,

---

### Post by y-lee on 2008-02-13
> **y-lee said:**
> Fourth maybe one could add some or all of the following preference tweaks to a profiles **[noparse]about:config[/noparse]** or to a given profiles  **pref.js**  file to automatically import bookmarks

[LIST]
[*]browser.bookmarks.added_static_root = Enabled
[*]browser.bookmarks.import_system_favorites = Enabled
[*]profile.allow_automigration = Enabled
[*]profile.confirm_automigration = Disabled
[/LIST]

But I haven't tried it and these are mostly used to import IE favorites into firefox in WIndows. I am not sure how they act in Linux or if enabled where firefox tries to import them from.

As far as I can tell the preferences above have no effect in Linux. Firefox does not try to import anything for me no matter what I set these too. Unless I'm somehow missing something :confused:

But here is a possible solution to your question:

> I need to setup a group of common bookmarks for all users on the system, while still allowing them to create their own. I need to do this in such a way that if I update the common bookmarks, it will not override their own bookmarks.

First set up the common bookmarks in a profile named common say as I outlined above. Copy this profiles bookmarks to  **/etc/firefox/profile/bookmarks.html** replacing the old file with the new one as I already described.

Second if you have any existing users have them start new firefox profiles and delete  the old profiles. (You can delete their old profiles as superuser if you want to be mean about it). **IMPORTANT** have all users both current and all new install the firefox addon  [foxmarks]("http://www.foxmarks.com/") and set up a foxmarks account. Foxmarks **must** be installed on all profiles, except yours it doesn't matter there.

Third any time you add or otherwise change bookmarks to your common profile, the bookmarks you wish to be system wide, then you must copy that bookmark file after the changes back to **/etc/firefox/profile/bookmarks.html**. And then after doing so you must go into EVERY users Firefox profiles and delete the **bookmarks.htm**l file and **bookmarks.bak** file and also the backup files found in the **bookmarkbackups** folder. You must delete *everyone *of these if not firefox reconstructs the old bookmarks.  Doing this should force firefox to reload the bookmarks you wish to be common from **/etc/firefox/profile/bookmarks.html** the next time your users start firefox. (*It does for me anyway.*) 

One could try to write a script to automated these steps btw. 

Now your users will seemingly have lost their own personal bookmarks yet have the common ones you wish to be system wide. * BUT* here is where Foxmarks comes in, Foxmarks should download all the old bookmarks from their web server and merge them with the common ones and therefore restore the bookmarks to the way they were *with *the addition of the ones you added.

Foxmarks preferences have to be set to enable Automatic Synchronization for all users, But this should work.

And yeah I know it is terribly inelegant and messing :(

Anyone else have any better ideas I would love to know it, any programmers want to write an extension for this I'd love to see it. But it is the best I can come up with for now as I can't  figure out how to edit a profiles bookmarks.html file directly and have firefox actually use the edited version. Even when i delete all backups it somehow knows the file has been edited. Probably relates to the line

```
<H1 LAST_MODIFIED="1202078191">Bookmarks</H1>
``` 

found in said file. After all the file says clearly > This is an automatically generated file.
     It will be read and overwritten.
     DO NOT EDIT!

And btw, foxmarks is planning on adding the ability to upload or download only some of your bookmarks sometime in the future. That would yield a slightly better solution to your problem.

---

### Post by rm-rf on 2008-02-14
Thanks a lot for taking the time to look look into this. I have been on the same boat before; somebody asks about something that pick my curiosity and next thing I know I spend hours working on the puzzle :rolleyes:

I think the easiest way right now will be to parse the bookmarks.html file with a script. I could cron it so the script will check to see if there is an update available, maybe using wget, and if so, to edit the bookmarks.html file with the information it needs to replace. 

One problem with this approach is that if a user has Firefox open and saves/deletes/edit a bookmark, the changes will get overwritten. Also, deleting the root folder where the changes are meant to go will destroy the process. I guess for those two instances I can have the script pop some meaningful information to the screen.

Again, thanks and take care.

# rm-rf

---

