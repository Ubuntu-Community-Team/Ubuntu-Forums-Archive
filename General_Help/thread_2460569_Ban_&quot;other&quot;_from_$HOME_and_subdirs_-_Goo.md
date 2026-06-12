---
title: "Ban &quot;other&quot; from $HOME and subdirs - Good or Bad Idea?"
date: 2021-04-13
forum: General Help
---

### Post by GhX6GZMB on 2021-04-13
I have changed the ownerships of $HOME and subdirectories to only have default "owner" and "group" permissions using the following command:

```
~$ chmod o-rwx -R ./* ./.[!.]*

```

Can this potentially cause any issues?

Background: I have several users on the same machine, and would like to isolate their documents and workspaces from each other.
Each owner has an own group like: tom:tom, jerry:jerry, acme:acme
On top of that, my own adm account as well, where I've done the same thing.

Until now I've seen no ill effects, but the devil's in the detail.

Thanks.

---

### Post by CatKiller on 2021-04-13
It's the default from 21.04 onwards. It was an oversight that they hadn't fixed it before, really. You're just ahead of the curve.

---

### Post by GhX6GZMB on 2021-04-13
> **CatKiller said:**
> It's the default from 21.04 onwards. It was an oversight that they hadn't fixed it before, really. You're just ahead of the curve.

Really? I feel good now :)

Thanks, CatKiller.

---

### Post by GhX6GZMB on 2021-04-13
OK, just ran into a minor issue. The "icon.png" for the user login needs to be set as "read" for "other" in $HOME. No big deal...

Also, do not remove "other" from $HOME, but only the subdirs and files _except_ icon.png.

---

### Post by CatKiller on 2021-04-13
> **ml9104 said:**
> OK, just ran into a minor issue. The "icon.png" for the user login needs to be set as "read" for "other" in $HOME. No big deal...

Also, do not remove "other" from $HOME, but only the subdirs and files _except_ icon.png.

I suspect - but you're the one doing the testing - that all you'd need is the execute permission for others on the directory itself, plus the read permission on that face icon. Execute on directories is the permission to traverse it. Certainly they wouldn't need write, but I don't think they'd need read either.

---

### Post by deadflowr on 2021-04-13
You can read about Ubuntu's recent decision to make this change here:
[https://discourse.ubuntu.com/t/private-home-directories-for-ubuntu-21-04-onwards/19533]("https://discourse.ubuntu.com/t/private-home-directories-for-ubuntu-21-04-onwards/19533")
And the very old bug report on it here: [https://bugs.launchpad.net/ubuntu/+source/adduser/+bug/48734]("https://bugs.launchpad.net/ubuntu/+source/adduser/+bug/48734")

---

### Post by GhX6GZMB on 2021-04-14
Interesting reading, Thank You @deadflowr for the link.

---

### Post by TheFu on 2021-04-14
I can't see any reason why any setting other than 700 would be cause for issues.  At other jobs, we ran that way by defaults.  For end-users, we'd often run with  500, so they couldn't accidentally modify files in their HOME.

Inside companies, the userid:userid setup that Ubuntu uses is very uncommon.  We usually put people into a default group based on their team membership. Then they could choose to share files/directories with team members OR not.  That was a team decision.  Users had to open permissions if they wanted others to see anything.  Usually the first day in a new team, their mentor/boss would help setup whatever environment the team used.  

We generally didn't work in our HOME directories for team projects/files.  The setgid flag and group management was commonly used to allow access to shared areas just for the team members. Those would be located on NFS mounted storage that all the team's workstations could access.  Ubuntu's use of snap package breaks much of this. For a home user, I could be convinced that mainly working from HOME is fine for small files and documents. I cannot be convinced that videos or audio files belong in HOME, however.

I'm not worried at all about the upcoming change in the umask to 007. It won't matter at all to most people, unless they setup samba shares to directories in their HOME.  That has always seemed like a terrible idea to me, but there are lots of opinions on that.  I always have HOME with just 1 LV/partition. I don't want to mount added storage under HOME per userid or just to share elsewhere.  I prefer to keep big data on other storage, outside HOME.

I am worried a little about the systemd team's plans for portable HOME directories. It is a fairly complex problem, but the goal is interesting.  We'd be able to have our HOMEs on flash storage that we take with us to any Linux desktop, connect it up, and have access to that system using our passwords, groups, encryption, and storage 100% self contained.  We can copy the HOME storage between different computers and sync that data as needed (how the sync happens is TBD).  Basically, it seems targeted for people who have shared computers at work ("hoteling"), but mainly work from home. They'd take their HOME directory with them daily into work and back home, so they can have as close to the same environment and all the exact same work files with them always without lugging a laptop around.   [https://systemd.io/HOME_DIRECTORY/](https://systemd.io/HOME_DIRECTORY/) has more information.  I didn't re-read it, so my take is probably beyond what they've said.

---

### Post by GhX6GZMB on 2021-04-14
> **CatKiller said:**
> I suspect - but you're the one doing the testing - that all you'd need is the execute permission for others on the directory itself, plus the read permission on that face icon. Execute on directories is the permission to traverse it. Certainly they wouldn't need write, but I don't think they'd need read either.

Good call!
I've tested it. Every $HOME should have the "x" attribute set for "other". Anything below that should have rwx "other" attributes cleared, with one exception: *.face.icon* must have read enabled.

This makes sense, as it is used by sddm for login, and before login no user:group is selected.

I'm extremely happy with this functionality. The $HOME directories are visible (which they are during login anyway), but trying to go below that you hit a brick wall.

For a group laptop with a handful of non-simultaneous users, it's perfect.

---

### Post by TheFu on 2021-04-14
> **ml9104 said:**
> Good call!
I've tested it. Every $HOME should have the "x" attribute set for "other". Anything below that should have rwx "other" attributes cleared, with one exception: *.face.icon* must have read enabled.

This makes sense, as it is used by sddm for login, and before login no user:group is selected.

I'm extremely happy with this functionality. The $HOME directories are visible (which they are during login anyway), but trying to go below that you hit a brick wall.

For a group laptop with a handful of non-simultaneous users, it's perfect.

Not sure, but perhaps you missed the subtle aspect to Catkiller's suggestion.  Read on a directory isn't always needed. Often, eXecute would be fine.
751 would likely work.  Most programs don't scan directories for filenames.  They assume both a directory AND a filename. A compiled program will work perfectly fine without read access, just eXecute alone.  Scripts need read, since they have to be read and interpreted.  

For Mate, it appears that personalized Icons can be located anywhere. In my reading, the example used was ~/Icons/ ... but each program icon still had to be individually setup.  Yuck.  Appears icons could be placed outside HOME, at least for people in the sudo group.  This should allow the functionality you describe, but a more locked down HOME.

---

### Post by GhX6GZMB on 2021-04-14
> **TheFu said:**
> Not sure, but perhaps you missed the subtle aspect to Catkiller's suggestion.  Read on a directory isn't always needed. Often, eXecute would be fine.
751 would likely work.  Most programs don't scan directories for filenames.  They assume both a directory AND a filename. A compiled program will work perfectly fine without read access, just eXecute alone.  Scripts need read, since they have to be read and interpreted.  

For Mate, it appears that personalized Icons can be located anywhere. In my reading, the example used was ~/Icons/ ... but each program icon still had to be individually setup.  Yuck.  Appears icons could be placed outside HOME, at least for people in the sudo group.  This should allow the functionality you describe, but a more locked down HOME.

You've lost me bit here, but the discussion is interesting.

For /home everything is default. For $HOME only x is set for "other". No read permission. For all subdirs to $HOME "other" has no rights at all. This works.
The exception is the *$HOME/.face.icon* file, which is used by SDDM at login and needs "r" as "other".

---

