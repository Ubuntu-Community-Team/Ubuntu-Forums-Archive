---
title: "Error on running software update"
date: 2017-04-10
forum: General Help
---

### Post by ganesh3 on 2017-04-10
Hi,

I am getting the below errors when I run 'sudo apt-get update'. I recently upgraded from 16.04 to 16.10 post which I am getting the below error. I had enabled the below PPA's post the upgrade assuming they will work fine but I am not sure why is it not working. Can someone please help?


```
E: The repository 'http://cran.rstudio.com/bin/linux/ubuntu xenial/ Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.canonical.com/ubuntu xenial Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://download.fpcomplete.com/ubuntu yakkety Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu yakkety Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu yakkety-updates Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu yakkety-backports Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu yakkety-security Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/elementary-os/daily/ubuntu yakkety Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/libreoffice/ppa/ubuntu yakkety Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/ne0sight/chrome-gnome-shell/ubuntu yakkety Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/ne0sight/chrome-gnome-shell/ubuntu xenial Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/oranchelo/oranchelo-icon-theme/ubuntu yakkety Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/plexydesk/plexydesk/ubuntu yakkety Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/varlesh-l/papirus-pack/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/webupd8team/java/ubuntu yakkety Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```


Regards
Ganesh Bhat

---

### Post by Bucky Ball on 2017-04-10
```
... does not have a Release file.
```

and

```
... does no longer have a Release file.
```

... say it all. You have manually installed a lot of third-party and sundry PPAs by the looks. They are dead or not supported in 16.10 by the error you're getting. You may need to delete the old ones and reinstall the 16.10 versions if still required and if they exist. 

Open 'Software and Updates> Other Software' and either disable (untick) or delete the problem PPAs. Follow the list from your terminal in your post.

---

### Post by ganesh3 on 2017-04-10
Thanks. Unchecked all the PPA in 'Others' but still getting the below error:

Err:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety Release
  Connection failed [IP: 91.189.88.149 80]
Err:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-updates Release
  Connection failed [IP: 91.189.88.162 80]
Err:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-backports Release
  Connection failed [IP: 91.189.88.149 80]
Err:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety-security Release
  Connection failed [IP: 91.189.88.162 80]
Reading package lists... Done
E: The repository 'http://archive.ubuntu.com/ubuntu yakkety Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu yakkety-updates Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu yakkety-backports Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu yakkety-security Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by kc1di on 2017-04-10
It looks like there is no connection to the repository on the server your using. try changing servers and then
```
sudo apt-get autoclean 
sudo apt-get clean
sudo apt-get update
```

---

### Post by ganesh3 on 2017-04-10
I was connecting to the main server changed it to India and it is working now.


Thanks
Ganesh Bhat

---

### Post by vasa1 on 2017-04-10
@ganesh, please read [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Thanks!

---

### Post by kc1di on 2017-04-10
Your welcome, Enjoy !

---

