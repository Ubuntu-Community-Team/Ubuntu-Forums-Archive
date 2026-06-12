---
title: "A little help with 'gpg' with a local repository"
date: 2007-03-26
forum: General Help
---

### Post by BobSongs on 2007-03-26
[FONT=Verdana][SOLVED]

Well. This is one of those embarassing moments. I've created a **HowTo** and I've overcome some obstacles. However I need a little assistance with one remaining part.

The HowTo, [**Make Your Own Ubuntu Repository DVDs**]("http://ubuntuforums.org/showthread.php?t=352460") works flawlessly. That's not the issue.

After creating the tutorial I realised it was possible to point **apt** to the local (downloaded in ~/UbuntuRepos) repositories. It works, however it throws a warning that these local repos might not be trustworthy. How this is done is detailed in step 10:[/FONT]

> [FONT=Verdana]**[SIZE=4]10. Point Apt locally[/SIZE]**
If you keep this set of local repositories up to date and you'd like to use them to install software on your system, then use the following steps for lightening fast installations.

At a terminal do the following:
[/FONT]```
cd ~/UbuntuRepos 
```[FONT=Verdana]
This step may take some time:
[/FONT]```
dpkg-scanpackages . /dev/null > Packages && gzip Packages 
```[FONT=Verdana]
Now insert in your **sources.list** file the following:
[/FONT]```
deb file:/home/[USER NAME HERE]/UbuntuRepos ./ 
```[FONT=Verdana]I know this can be fixed somehow with the **gpg** command. But upon viewing the billions of various switches/options I'm afraid I'm in over my head. I've tried the following at the command prompt but to no avail:

```
gpg --keyserver subkeys.pgp.net --recv-keys 437D05B5
``````
gpg --edit-key 437D05B5
```to which I enter **trust**, **5**, and **y** and **quit**. This is supposed to tell **gpg** that I ultimately trust the local repos (downloaded on the hard drive).

However **apt** still fusses about the local repositories (downloaded from **archive.ubuntu.com**).

The repositories are downloaded by **debmirror** to ~/UbuntuRepos

Packages are installable. It's just the pesky warning before each installation that could be silenced. Any suggestions?

Thanks. You'll be credited in the tutorial.[/FONT]

---

### Post by BobSongs on 2007-03-27
[FONT=Verdana][B]*bump* - and only bump. It's not terribly important. But I'm looking to resolve this problem. I know it's a) a bit of a challenge and, b) not of great importance. But I thought I'd start here.
[/B][/FONT]

---

### Post by qjohnston on 2007-05-31
I've got this exact same problem with debmirror.  I'm just using the --ignore-release-gpg and --ignore-small-errors switches to get by the errors, but it's definitely not a solution.

---

### Post by adadof6 on 2008-01-21
Glad to see you've got it resolved.

Mark your post resolved if possible.

---

