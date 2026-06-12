---
title: "while updating software in and out of cockpit (how to fix)"
date: 2023-11-23
forum: General Help
---

### Post by rzmuda on 2023-11-23
[h=1]Loading available updates failed[/h]
```
E: The repository 'cdrom://Ubuntu 22.04.3 LTS _Jammy Jellyfish_ - Release amd64 (20230807.2) jammy Release' does not have a Release file. 
W: Updating from such a repository can't be done securely, and is therefore disabled by default. 
W: See apt-secure(8) manpage for repository creation and user configuration details. 
E: cdrom://Ubuntu 22.04.3 LTS _Jammy Jellyfish_ - Release amd64 (20230807.2) jammy Release is not (yet) available 
(Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs) 
E: The repository 'https://ppa.launchpadcontent.net/mc3man/xerus-media/ubuntu jammy Release' does not have a Release file. 
W: Updating from such a repository can't be done securely, and is therefore disabled by default. 
W: See apt-secure(8) manpage for repository creation and user configuration details.
Please reload the page after resolving the issue.
```

---

### Post by deadflowr on 2023-11-23
Run
```
sudo apt edit-sources
```
this will open the sources.list in your default editor, usually nano, but could be vim or other.
The first line will read deb cdrom blah blah blah
Add a hash # to that line to comment it out.
and then save the file

Next run
```
sudo add-apt-repository --remove ppa:mc3man/xerus-media
```

Then run
```
sudo apt update
```

---

