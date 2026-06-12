---
title: "Software updater failed to download repository information?"
date: 2021-07-29
forum: General Help
---

### Post by Extreedoc on 2021-07-29
As title: it asks me to check my internet connection - which is fine. It is trying and failing to download 'Ubuntu base' 191kB
Any ideas?

---

### Post by Impavidus on 2021-07-29
Let's try and get a more specific error message. Run these commands and post the full output:```
sudo apt update
sudo apt upgrade
```

---

### Post by Extreedoc on 2021-07-29
Thanks, I can run the commands no probs but can you remind me how to post the output on here - sorry for the dumb question...

---

### Post by tea for one on 2021-07-29
Copy the relevant text from the terminal output.
Open [COLOR="#0000FF"]Go Advanced[/COLOR] editing screen (i.e not Quick Reply)
Click on the code tag icon and paste.
The text should now be within code tags.

Preview post to double check content.

---

### Post by Extreedoc on 2021-07-30
Thanks. Problem: I can't copy the content of the terminal, the 'Copy' option is greyed out. Ctrl, Shift, C doesn't work either.
Forget this, I've figured it out...

---

### Post by Extreedoc on 2021-07-30
Forget my last post, I figured it out and here it is:

```
user@user-MS-7721:~$ sudo apt update
[sudo] password for user: 
Hit:5 http://archive.canonical.com/ubuntu focal InRelease                      
Get:1 http://la-mirrors.evowise.com/ubuntu focal InRelease [600 kB]       
Get:2 http://la-mirrors.evowise.com/ubuntu focal-updates InRelease [600 kB]
Get:3 http://la-mirrors.evowise.com/ubuntu focal-backports InRelease [600 kB]
Get:4 http://la-mirrors.evowise.com/ubuntu focal-security InRelease [600 kB]
Err:1 http://la-mirrors.evowise.com/ubuntu focal InRelease
  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
Err:2 http://la-mirrors.evowise.com/ubuntu focal-updates InRelease
  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
Err:3 http://la-mirrors.evowise.com/ubuntu focal-backports InRelease
  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
Err:4 http://la-mirrors.evowise.com/ubuntu focal-security InRelease
  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
Reading package lists... Done     
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://la-mirrors.evowise.com/ubuntu focal InRelease' is no longer signed.
E: Failed to fetch http://la-mirrors.evowise.com/ubuntu/dists/focal/InRelease  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://la-mirrors.evowise.com/ubuntu focal-updates InRelease' is no longer signed.
E: Failed to fetch http://la-mirrors.evowise.com/ubuntu/dists/focal-updates/InRelease  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
E: Failed to fetch http://la-mirrors.evowise.com/ubuntu/dists/focal-backports/InRelease  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://la-mirrors.evowise.com/ubuntu focal-backports InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://la-mirrors.evowise.com/ubuntu/dists/focal-security/InRelease  Clearsigned file is not valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://la-mirrors.evowise.com/ubuntu focal-security InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
user@user-MS-7721:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  python3-distupgrade ubuntu-drivers-common ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk
4 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 191 kB of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue? [Y/n] 

```

---

### Post by westie457 on 2021-07-30
[COLOR=#000000]The mirror site you using is definitely broken.[/COLOR]
[COLOR=#000000]Open 'Software & Updates', in the first tab where it says Download from click in the box and change the server. Close the window and agree to the prompts.[/COLOR]
[COLOR=#000000]Open a terminal and run[/COLOR][COLOR=#000000]Code:
sudo apt update
sudo apt upgrade[/COLOR]
[COLOR=#000000]Post the output of the first command if any errors.[/COLOR]

---

### Post by Extreedoc on 2021-07-30
Thank you, that seems to have done the trick, no errors reported.

---

