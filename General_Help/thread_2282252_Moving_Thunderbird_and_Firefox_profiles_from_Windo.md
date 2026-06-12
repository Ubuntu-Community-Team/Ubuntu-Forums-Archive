---
title: "Moving Thunderbird and Firefox profiles from Windows to Ubuntu"
date: 2015-06-12
forum: General Help
---

### Post by RayTomes on 2015-06-12
I currently run Win-XP and have set up dual boot with Ubuntu last long life version and want to convert over to it.

I want to move Thunderbird and Firefox profiles from Windows to Ubuntu. Can I just copy the strange named directory under profiles from one to the other and expect it to work? What other considerations are there?

---

### Post by leunam12 on 2015-06-13
Just move the strange named directory and then change the profiles.ini file under .mozilla>firefox ```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=**z60detag.default**

```change everything after Path= to your own profile name.

---

### Post by RayTomes on 2015-06-13
Thanks leunam12, I will give it a try.

---

### Post by oldfred on 2015-06-13
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

If moving from NTFS to ext4, you may also have to reset ownership & permissions.

       [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
            [https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)
    
I have done this, but you never run -R on system folders, but I guess /home is ok. That is recursion so ever file and every level below is changes. If you accidentally change a system partition, you just might as well reinstall and restore from backups.

sudo chown -R $USER:$USER /home/$USER
 sudo chmod -R a+rwX,o-w /home/$USER

 #All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.

Back in 2007 I moved profiles to a shared NTFS data partition. And used XP & various versions of Ubuntu since and had no issues until just in the last few months. I also copy profiles to my laptop when traveling & back when I return. 

I assume I may have a permission or file copy issue as contents of emails disappear. But I am not using NTFS anymore and have profiles in default locations in my Ubuntu currently.

---

### Post by RayTomes on 2015-06-18
Thank you oldfred and others. I havent actually converted over to Ubuntu for email etc yet, but I have the info when the time comes.

---

### Post by jerry49 on 2015-06-18
I believed I did the profile move correctly, including updating the profile.ini and indeed Thunderbird from XP to Ubuntu 15.04 appears to have the XP image.  I have not yet tried to download email messages, still checking more benign stuff.  Thunderbird is set up to run two accounts and both appear in the left side of Thunderbird (must have a name) but:  the individual folders look to have been moved empty (I am testing in a separate netbook Starter 7 with a dual boot.. I have copied the profile from the target Dell XP desktop machine to the netbook).  I will go back to check the Dell XP to see if the folders are indeed empty.  This machine is for another owner and I can't now ask if anything is missing in the Ubuntu Thunderbird copy. 

My guess is the fact the Ubuntu Thunderbird displays the inbox for both accounts says the move has been accomplished.  That is I do not have a permission problem as discussed by "oldfred".. who I bet is younger than me : (

Edit: looking back I recall I found this forum using a web search that put me into this thread.  When I log into ubuntuforums.org I start in a table of contents, how to I find the group/type of discussions this thread is stored in?

---

### Post by oldfred on 2015-06-18
You can save thread.
[http://ubuntuforums.org/showthread.php?t=2282252](http://ubuntuforums.org/showthread.php?t=2282252)

I use search and look for any thread I have posted in. I only add my user name to search.
It only finds recent threads and threads  with new posts like this then are at top of list in bold.

You should also be able to go into your userid and it should show all your threads.

But sometime to find old threads that I did not save link, I use google and include
 site:ubuntuforum.org oldfred and whatever I thought was related to topic.

---

