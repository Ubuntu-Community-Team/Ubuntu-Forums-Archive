---
title: "how do I create a packages signature?"
date: 2016-06-21
forum: General Help
---

### Post by a.dusty.trail on 2016-06-21
```
N: Can't drop privileges for downloading as file '/usr/local/mydebs/./InRelease' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied) 
W: The repository 'file:/usr/local/mydebs ./ Release' does not have a Release file. 
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use. 
N: See apt-secure(8) manpage for repository creation and user configuration details. 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...rity/InRelease](http://security.ubuntu.com/ubuntu/di...rity/InRelease) Temporary failure resolving 'security.ubuntu.com' 
E: Failed to fetch file:/usr/local/mydebs/./Packages File not found - /usr/local/mydebs/./Packages (2: No such file or directory) 
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

I'm trying to create a local repository for deb packages
All the tutorials don't mention what to do to fix these errors..

How do I sign the packages file?
How do I create a release file?

Hopefully some what simple instructions that work for 16.04 most info I found was over 2 years old

---

### Post by vasa1 on 2016-06-21
When you're posting stuff you've copied from the terminal, please do so within **code tags**. Doing so makes the contents more easily readable. I tried adding code tags to the stuff you posted above. I hope I got it right.

---

### Post by a.dusty.trail on 2016-06-21
I see no option to use code tags while surfing with a mobile device.
Maybe that's a desktop option only

---

### Post by vasa1 on 2016-06-21
You can also add the code tags manually by typing in the words [noparse]```
 and its closing counterpart 
```[/noparse] before and after whatever you want.

Thanks, runrickus and CantankRus (for the noparse advice)!

---

### Post by a.dusty.trail on 2016-06-22
If it's not worth implementing into the mobile version on the website.And I have not seen a mobile app.
I'm sure it's not something I'm going to spend a lot of effort on to memorize.
But I'll try to keep it in mind while I'm searching for the answer to my actual question.

---

### Post by a.dusty.trail on 2016-07-03
bump

---

