---
title: "Questions about creating new firefox profile"
date: 2021-07-17
forum: General Help
---

### Post by sofasurfer on 2021-07-17
Apparently I screwed up my system yesterday. Last night I lost my internet connection and it was still gone this morning. I was able to use me other OS so I knew it was a problem with my installation. I did a system restore. But when I opened firefox I was informed that using my old profile could cause bookmark, etc loss. So I restored my /home folder. I then got the same warning message. I had the option of creating a new profile so I did. But my bookmarks were gone so I then restored bookmarks from a backup file. Now everything seems good. 
My question is, why was a restore of my /home folder not enough to get firefox running? Why did I need a new profile? Can I now delete my old profile?

---

### Post by dragonfly41 on 2021-07-18
[This gives some documentation relating to Firefox profiles.]("https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles")

You can jump in by running this command in terminal:

[B]firefox -P

[/B]You will see a GUI with list of your profiles.

Regarding your question, it depends on what you mean by "restored my /home folder"
Were hidden files restored?
As you found you had to copy your bookmarks from a backup.
Similarly you would need to copy firefox profiles from a backup.

---

### Post by Impavidus on 2021-07-18
When you restored your system, you restored an old version of Firefox. Old versions of Firefox don't like new versions of the profile. You must have upgraded and used Firefox after creating the backup. Restoring a backup of your /home directory, assuming it included all hidden directories, should have fixed the problem, unless that backup was created after upgrading and using Firefox. That's not unlikely, as I installed a new version of Firefox from the repos just 2 days ago.

One thing you could have tried is to upgrade Firefox after restoring your system backup. That should have given you the right version of Firefox for your profile. If you still have you old profile, maybe you can use it again after upgrading Firefox.

---

### Post by sofasurfer on 2021-07-19
Thanks Dragon. That GUI is just what I need.

Impavidus. Thanks for the info. I used Firefox -P command to switch back to my old profile and it seems to wok fine now. I don't know why it would since it did not after I did he restore.
Another question to see if I undertand...if I did a backup and then updated my system, my system would be newer than my backup copy. If I then restored my newer system with the older backup would I then just do an update and everything would be good?

---

### Post by Impavidus on 2021-07-19
> **sofasurfer said:**
> I don't know why it would since it did not after I did he restore.
Because the profile had version 90 and the system backup had Firefox version 89. Then you upgraded Firefox (or it was upgraded automatically, if you have automatic updates), so you got Firefox 90 and the old profile worked again.
> Another question to see if I undertand...if I did a backup and then updated my system, my system would be newer than my backup copy. If I then restored my newer system with the older backup would I then just do an update and everything would be good?Yes. The backup had Firefox 89, but your profile was for Firefox 90. Doing an update would give Firefox 90, fixing the problem.

---

