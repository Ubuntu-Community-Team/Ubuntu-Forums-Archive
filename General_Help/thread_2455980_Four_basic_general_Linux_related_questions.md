---
title: "Four basic general Linux related questions"
date: 2021-01-01
forum: General Help
---

### Post by keijo-kukka on 2021-01-01
Hello Gurus!
I consider myself a Linux noob and have few quite basic Linux related general questions. Could someone please explain them to me? Thanks!!

1. Can someone please explain me in simple layman's terms, that what exactly are *symlinks*, or *symbolink links* in Linus? I did Google them, but I'm still uncertain.

2. Can someone also please explain me, that what are the *depencies* in Linus, what's their purpose and how they work?

3. What's the difference when I execute in Linux terminal (in Debian based distros) **sudo apt update && apt upgrade** compared to when I let e.g. Ubuntu's default *Software Center* to execute regular updates? I guess that both options update and upgrade same things; installed SW and also OS and kernel updates?

4. What is the whole purpose of */home* directory in Linux and what are the benefits of it? Once when I installed one Debian based distro, I was asked whether I'd like to create *a separate home directory*. The option was labeled for "advanced users", so I skipped it. Would you recommend to have a separate home directory? Someone once told me, that if I store all my personal files in /home directory it would be beneficial if I'd like to change the distro sometime later. In that case I could simply copy the whole /home directory from old distro to new distro and thus have all my old files saved. Is this also valid regarding installed software or is it related to only personal files, e.g. photos, videos and such?

Thank you very much, I greatly appreciate your help and try to help others as well!!

---

### Post by dino99 on 2021-01-01
1) [https://www.howtogeek.com/287014/how-to-create-and-use-symbolic-links-aka-symlinks-on-linux/](https://www.howtogeek.com/287014/how-to-create-and-use-symbolic-links-aka-symlinks-on-linux/)
2) [https://askubuntu.com/questions/361741/what-are-dependencies](https://askubuntu.com/questions/361741/what-are-dependencies)
3) update means 'get newer version(s) if availlable" from archives; upgrade means set that/these newer version(s) and get an uptodated system.
4) actual ubuntu default installation set a home directory; while setting a /home partition let you store and share all your data outside the system partition; so more secure in the case you need to reinstall the system

---

### Post by Hagar Delest on 2021-01-01
1. It's a shortcut, a bit more powerful than the Windows shortcut since it is interpreted by the OS directly. See also: [https://en.wikipedia.org/wiki/Symbolic_link](https://en.wikipedia.org/wiki/Symbolic_link)
2. They are libraries shared by several applications. So, to use an application, it often needs other packages. Like DLLs in Windows.
3. Same I guess but power user may tell if there is a kind of difference.
4. home is the place where all user data and customization is stored. You can set that place to another partition if you want so that when you install another flavor, you can still use the same "user profile". Personally, I keep the /home in the root of the system and store some profiles in a dedicated partition. Then when I upgrade, I update the symlinks (in fact I copy them from the previous install) so that they still point to the same configuration folders in the dedicated partition.

---

### Post by keijo-kukka on 2021-01-01
Excellent, thank you very much @dino99 and @Hagar Delest for your answers! They were very helpful! Hagar Delest your clear examples were especially helpful. &#55357;&#56898;

---

### Post by HermanAB on 2021-01-01
Regarding 1), there are also hard links, which literally are additional names for the same file.  

The main difference between soft and hard links become apparent when you want to delete a file:
If there is a symlink to a file and you delete the file, the symlink is left dangling and pointing to nothing.
If there are hard links to a file, and you try to delete the file, then the file will only be really deleted, once the last hard link is deleted.

If you have lots of duplicate files on a disk (e.g photos), then you can save space, by running a utility called hardlink, which will convert the dupes into links.

---

### Post by TheFu on 2021-01-01
> **keijo-kukka said:**
> Hello Gurus!
I consider myself a Linux noob and have few quite basic Linux related general questions. Could someone please explain them to me? Thanks!!

1. Can someone please explain me in simple layman's terms, that what exactly are *symlinks*, or *symbolink links* in Linus? I did Google them, but I'm still uncertain.

First, it is "Linux", not Linus.
These questions seem like class assignments.  Wikipedia: [https://en.wikipedia.org/wiki/Symlink](https://en.wikipedia.org/wiki/Symlink)

> **keijo-kukka said:**
> 2. Can someone also please explain me, that what are the *depencies* in Linus, what's their purpose and how they work?
"Dependencies" is a generic term for 1 thing that is dependent on another.  In software, there are all sorts of dependencies. Basically, something that must be true of exist, before the next thing.  Some might call them "prerequisites." instead. 

For example, I like to use a scanning tool called gscantopdf.  It is a small GUI that leverages some "_dependencies_" in xsane and sane for the scanning part and some PDF creation tools which have _dependencies_ on text and image tools.  For gscantopdf to work, those other tools and their dependencies need to be installed.  APT is the name of the packaging system on Debian-based Linux distros. In the package files, dependencies are listed.  And those dependencies have dependencies, and so on.  APT will get the list and ensure that the dependencies are installed, provided you stay within the package manager system for each.  If you manually install a program (like Windows does), then the APT system won't know about the dependencies and you'll need to manually hunt those down. That isn't fun.  We had to do that in the early 1990s.

> **keijo-kukka said:**
> 3. What's the difference when I execute in Linux terminal (in Debian based distros) **sudo apt update && apt upgrade** compared to when I let e.g. Ubuntu's default *Software Center* to execute regular updates? I guess that both options update and upgrade same things; installed SW and also OS and kernel updates?
I honestly don't know. I've not used the "Software Center", ever.  Every week, I do **sudo apt update && sudo apt full-upgrade**.  For what these commands do, we have manpages which detail what the option does if you want to know more.

> **keijo-kukka said:**
> 4. What is the whole purpose of */home* directory in Linux and what are the benefits of it? Once when I installed one Debian based distro, I was asked whether I'd like to create *a separate home directory*. The option was labeled for "advanced users", so I skipped it. Would you recommend to have a separate home directory? Someone once told me, that if I store all my personal files in /home directory it would be beneficial if I'd like to change the distro sometime later. In that case I could simply copy the whole /home directory from old distro to new distro and thus have all my old files saved. Is this also valid regarding installed software or is it related to only personal files, e.g. photos, videos and such?

/home/ isn't just Linux. It is for every Unix-like OS since 1970. On systems with 6,000 users, files need to be kept separate for each userid.  The HOME directory, controlled in the /etc/passwd file for each account, does that. HOME is where each userid stores their files, settings, by default.  Also, the HOME can be located anywhere, there is no requirement for it to be /home/{username}. That is just how home Linux users see it, typically.  For each user, the HOME is usually their most important files and settings. Backing up the HOME for each userid would be needed.  But it isn't just the files. It is the metadata about those files too.  That is the owner, group, permissions, ACLs, and xattrs.  All of those are necessary for a proper backup.

Some files that need to be shared by the entire system or multiple users don't belong in a single user's HOME. Unix has techniques using groups and permissions to make sharing access to files and directories possible, while not allowing the entire world to have access.  Windows has this idea too, but defaults to allowing everyone access, so you've probably never bothered to learn it.  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) explains, but it takes a little time to digest everything around permissions.

When you are new, learning things in a thoughtful order will make life easier.  Here's a reasonable book, free, no hassle download to help: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  If you work through the first 250-ish pages, then quickly skim over the rest (1 sec per page), you'll have a good basic skill set.  Do all the exercises, so solidify knowledge.

---

### Post by grahammechanical on 2021-01-01
The Software Centre>updates tab and Software & Updates application are graphical frontends for running Linux commands to update and upgrade the operating system and the installed applications (packages).

I recently installed Debian and I was asked if I wanted a separate /home partition and not a separate /home directory. In Linux Home is a directory. Directories are what Windows users would call folders. I can remember when Microsoft also used the term "directory." The term "folder" began to be used with graphical desktop environments when an icon of a folder was used as a link to a directory.

Do you want to know what a WIMP interfaces is? Windows, Icons, Menus, Pointer. The desktop environment and the user interface that we are so familiar with is in fact an example of the WIMP interface.

No wonder there are so many words in the English language!

Regards.

---

### Post by keijo-kukka on 2021-01-01
Thank you very much @[**[COLOR=#000000]HermanAB[/COLOR]**]("https://ubuntuforums.org/member.php?u=44990"), [**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685") (and sorry about Linus -> Linux typo) and [**[COLOR=#000000]grahammechanical[/COLOR]**]("https://ubuntuforums.org/member.php?u=1087323") for your profound answers! I really appreciate it all! This forum seems to have very kind people. Hopefully it stays that way. :D

---

