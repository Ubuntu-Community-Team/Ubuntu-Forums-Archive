---
title: "problem with the software center"
date: 2012-10-29
forum: General Help
---

### Post by majorburt on 2012-10-29
every time i try to download something from the software center it always says: 
"Requires installation of untrusted packages.
The action would require the installation of packages from not authenticated sources."

i have two options, the first is "ok" which does nothing. the second is "repair" which also does nothing". 

my theory is that it's something to do with my security settings. this would be fine if i could find the security center in Linux, but i cant.

how do i fix this?:confused:

---

### Post by jerrrys on 2012-10-29
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update

And please post the results

---

### Post by majorburt on 2012-10-29
> **jerrrys said:**
> [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update

And please post the results

the error happened at about 95% for the update

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease: File /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-backports_InRelease doesn't start with a clearsigned message
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security InRelease: File /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-security_InRelease doesn't start with a clearsigned message
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)

---

### Post by kanikilu on 2012-10-29
Looks like you have 2 issues. For the GPG errors, try the following commands in a terminal:

```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

*[source](http://ubuntuforums.org/showthread.php?t=1657004)

Hold off on the last command to update until you fix the duplicate sources warning.

For that one, open up your /etc/apt/sources.list file and see if the 'partner' repository is listed more than once. If so, just comment out one of them. I just replied to another thread with the same issue earlier today:

[http://ubuntuforums.org/showpost.php?p=12324686&postcount=4](http://ubuntuforums.org/showpost.php?p=12324686&postcount=4)

---

### Post by jerrrys on 2012-10-29
Enter these commands one at a time.

sudo -i
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

kanikilu's got the answer too  :)

---

### Post by majorburt on 2012-10-30
> **kanikilu said:**
> Looks like you have 2 issues. For the GPG errors, try the following commands in a terminal:

```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

*[source](http://ubuntuforums.org/showthread.php?t=1657004)

Hold off on the last command to update until you fix the duplicate sources warning.

For that one, open up your /etc/apt/sources.list file and see if the 'partner' repository is listed more than once. If so, just comment out one of them. I just replied to another thread with the same issue earlier today:

[http://ubuntuforums.org/showpost.php?p=12324686&postcount=4](http://ubuntuforums.org/showpost.php?p=12324686&postcount=4)

i do have a duplicate "partner" repository how do i "comment" it out? do you mean that i should edit the file somehow?

---

### Post by kanikilu on 2012-10-30
> **majorburt said:**
> i do have a duplicate "partner" repository how do i "comment" it out? do you mean that i should edit the file somehow? Follow the link I put in the last post - I gave (relatively) detailed instructions on how to edit the file.

I'm honestly not sure if duplicates show up in the Software Sources GUI, but if you want to check that first, go to the dash and search for "Software Sources". Choose that and then go to the "Other Software" tab. If you have multiple 'partner' repos checked, uncheck on of them.

---

### Post by majorburt on 2012-10-31
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages

does the above tell me where the duplicate sources are or something else?

---

### Post by kanikilu on 2012-10-31
> **majorburt said:**
> does the above tell me where the duplicate sources are or something else? Yes: > W: Duplicate [COLOR="Red"]**sources.list**[/COLOR] entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages Edit that file, or check the Software Sources program first if you are more comfortable with the GUI.

---

### Post by majorburt on 2012-10-31
> **kanikilu said:**
> Yes:  Edit that file, or check the Software Sources program first if you are more comfortable with the GUI.

ok, so just to be sure, i input (gksu gedit/etc/apt/sources.list)
into the terminal.

once it opens the file, i alter
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

by putting "#" at the start of both. 

resulting in
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

am i correct?

---

### Post by kanikilu on 2012-10-31
Yep, that should do it.

---

### Post by majorburt on 2012-11-01
> **kanikilu said:**
> Looks like you have 2 issues. For the GPG errors, try the following commands in a terminal:

```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

*[source](http://ubuntuforums.org/showthread.php?t=1657004)

Hold off on the last command to update until you fix the duplicate sources warning.

For that one, open up your /etc/apt/sources.list file and see if the 'partner' repository is listed more than once. If so, just comment out one of them. I just replied to another thread with the same issue earlier today:

[http://ubuntuforums.org/showpost.php?p=12324686&postcount=4](http://ubuntuforums.org/showpost.php?p=12324686&postcount=4)
(cd /var/lib/apt)went into the terminal just fine. however,when i try to input the command (sudo mv lists lists.old)into the terminal, it comes back with this error (mv: cannot move `lists' to `lists.old/lists': Directory not empty). 

did i do something wrong?

---

### Post by dannyboy79 on 2012-11-01
you can try the -f option (force) to move it

```
sudo mv -f lists lists.old
```

---

### Post by dannyboy79 on 2012-11-01
SORRY, double post

---

### Post by majorburt on 2012-11-01
> **dannyboy79 said:**
> you can try the -f option (force) to move it

```
sudo mv -f lists lists.old
```

that didn't work. 
just a shot in the dark but, what if i removed or deleted the file that "sudo mv -f lists lists.old" is trying to move?

---

### Post by dannyboy79 on 2012-11-01
what error are you getting?

what returns when you issue

```
ls -la /var/lib/apt/
```

and then

```
ls -la /var/lib/apt/lists
```

---

### Post by kanikilu on 2012-11-01
I don't think removing it will necessarily be a problem. But, I'm a little confused as to why it can't move it :confused: My /var/lib/apt/lists/ is not empty either, and it moved it just fine.

I suppose you could also try copying it first, and then removing it - basically breaking the "mv" command into 2 steps:

```
sudo cp -R lists lists.old
sudo rm -rf lists
```

Obviously, take care anytime you need to resort to using rm -rf, especially with sudo! Be sure of what directory you are in, and that the target folder is indeed the one you want to remove...

---

### Post by majorburt on 2012-11-01
> **dannyboy79 said:**
> what error are you getting?

what returns when you issue

```
ls -la /var/lib/apt/
```

and then

```
ls -la /var/lib/apt/lists
```
i get the same error as earlier (mv: cannot move `lists' to `lists.old/lists': Directory not empty)

what returns for "ls -la /var/lib/apt/" is this:

total 80
drwxr-xr-x  7 root root  4096 Nov  1 12:19 .
drwxr-xr-x 65 root root  4096 Oct 27 23:47 ..
-rw-r--r--  1 root root   223 Oct 16 18:26 cdroms.list
-rw-r--r--  1 root root 19956 Nov  1 12:19 extended_states
drwxr-xr-x  2 root root  4096 Aug 17 18:05 keyrings
drwxr-xr-x  3 root root 12288 Nov  1 13:42 lists
drwxr-xr-x  4 root root 20480 Oct 31 12:50 lists.old
drwxr-xr-x  3 root root  4096 Aug 17 18:05 mirrors
drwxr-xr-x  2 root root  4096 Oct 16 19:29 periodic

and as for "ls -la /var/lib/apt/lists" :

total 8228
drwxr-xr-x 3 root root   12288 Nov  1 13:42 .
drwxr-xr-x 7 root root    4096 Nov  1 12:19 ..
-rw-r--r-- 1 root root   21621 Oct 25 03:04 archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages
-rw-r--r-- 1 root root   13920 Oct 25 03:04 archive.canonical.com_ubuntu_dists_precise_partner_source_Sources
-rw-r--r-- 1 root root    7078 Oct 25 03:04 archive.canonical.com_ubuntu_dists_precise_Release
-rw-r--r-- 1 root root     198 Oct 25 03:04 archive.canonical.com_ubuntu_dists_precise_Release.gpg
-rw-r--r-- 1 root root   31928 Oct  9 20:01 extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
-rw-r--r-- 1 root root   29980 Oct  9 20:01 extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources
-rw-r--r-- 1 root root   11875 Oct  9 16:46 extras.ubuntu.com_ubuntu_dists_precise_Release
-rw-r--r-- 1 root root      72 Nov  1 12:01 extras.ubuntu.com_ubuntu_dists_precise_Release.gpg
-rw-r--r-- 1 root root    2233 Aug  8  2011 gmusicbrowser.org_deb_._Packages
-rw-r--r-- 1 root root    1076 Aug  8  2011 gmusicbrowser.org_deb_._Release
-rw-r--r-- 1 root root     198 Aug  8  2011 gmusicbrowser.org_deb_._Release.gpg
-rw-r----- 1 root root       0 Oct 31 12:50 lock
drwxr-xr-x 2 root root    4096 Nov  1 13:42 partial
-rw-r--r-- 1 root root    1413 Sep 25 23:23 ppa.launchpad.net_format-junkie-team_release_ubuntu_dists_precise_main_binary-i386_Packages
-rw-r--r-- 1 root root    1088 Sep 25 23:23 ppa.launchpad.net_format-junkie-team_release_ubuntu_dists_precise_main_source_Sources
-rw-r--r-- 1 root root   11874 Sep 25 23:23 ppa.launchpad.net_format-junkie-team_release_ubuntu_dists_precise_Release
-rw-r--r-- 1 root root    9008 Oct 29 18:25 ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_main_binary-i386_Packages
-rw-r--r-- 1 root root    1752 Oct 29 18:25 ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_main_source_Sources
-rw-r--r-- 1 root root   11884 Oct 29 18:25 ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_Release
-rw-r--r-- 1 root root     316 Oct 29 18:25 ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_Release.gpg
-rw-r--r-- 1 root root    1039 Oct 24 10:56 private-ppa.launchpad.net_commercial-ppa-uploaders_pct-listen_ubuntu_dists_precise_main_binary-i386_Packages
-rw-r--r-- 1 root root   11872 Oct 24 10:56 private-ppa.launchpad.net_commercial-ppa-uploaders_pct-listen_ubuntu_dists_precise_Release
-rw-r--r-- 1 root root     316 Oct 24 10:56 private-ppa.launchpad.net_commercial-ppa-uploaders_pct-listen_ubuntu_dists_precise_Release.gpg
-rw-r--r-- 1 root root    1071 May  8 08:06 private-ppa.launchpad.net_commercial-ppa-uploaders_tiberiumalliances_ubuntu_dists_precise_main_binary-i386_Packages
-rw-r--r-- 1 root root   11910 May  8 08:06 private-ppa.launchpad.net_commercial-ppa-uploaders_tiberiumalliances_ubuntu_dists_precise_Release
-rw-r--r-- 1 root root     316 May  8 08:06 private-ppa.launchpad.net_commercial-ppa-uploaders_tiberiumalliances_ubuntu_dists_precise_Release.gpg
-rw-r--r-- 1 root root    4925 Nov  1 11:39 us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-i386_Packages
-rw-r--r-- 1 root root      72 Oct 30 19:50 us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Index
-rw-r--r-- 1 root root    2315 Jul 23 08:05 us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Translation-en
-rw-r--r-- 1 root root    7991 Nov  1 11:39 us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root      72 Oct 30 19:50 us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Index
-rw-r--r-- 1 root root    3483 Sep 20 08:21 us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Translation-en
-rw-r--r-- 1 root root    8086 Nov  1 11:39 us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_source_Sources
-rw-r--r-- 1 root root   26050 Nov  1 12:40 us.archive.ubuntu.com_ubuntu_dists_precise-backports_Release
-rw-r--r-- 1 root root       0 Nov  1 11:39 us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-i386_Packages
-rw-r--r-- 1 root root      70 Oct 30 19:50 us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Index
-rw-r--r-- 1 root root       0 Oct 13  2011 us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Translation-en
-rw-r--r-- 1 root root       0 Nov  1 11:39 us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_source_Sources
-rw-r--r-- 1 root root   65924 Nov  1 11:39 us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages
-rw-r--r-- 1 root root      73 Oct 30 19:50 us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Index
-rw-r--r-- 1 root root   37272 Oct 30 19:50 us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Translation-en
-rw-r--r-- 1 root root   63977 Nov  1 11:39 us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_source_Sources
-rw-r--r-- 1 root root 4356187 Apr 25  2012 us.archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources
-rw-r--r-- 1 root root  628753 Apr 25  2012 us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_source_Sources
-rw-r--r-- 1 root root   12579 Oct 29 21:50 us.archive.ubuntu.com_ubuntu_dists_precise_Release
-rw-r--r-- 1 root root  134582 Apr 25  2012 us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages
-rw-r--r-- 1 root root   19001 Apr 25  2012 us.archive.ubuntu.com_ubuntu_dists_precise_restricted_source_Sources
-rw-r--r-- 1 root root 1219760 Oct 29 21:47 us.archive.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages
-rw-r--r-- 1 root root      73 Oct 29 21:51 us.archive.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Index
-rw-r--r-- 1 root root  684802 Oct 26 08:14 us.archive.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en
-rw-r--r-- 1 root root  238082 Oct 29 21:50 us.archive.ubuntu.com_ubuntu_dists_precise-security_main_source_Sources
-rw-r--r-- 1 root root    6524 Oct 29 21:47 us.archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root      71 Oct 29 21:51 us.archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Index
-rw-r--r-- 1 root root    2175 Aug 16 02:06 us.archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en
-rw-r--r-- 1 root root    3078 Oct 31 14:10 us.archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_source_Sources
-rw-r--r-- 1 root root     198 Nov  1 11:39 us.archive.ubuntu.com_ubuntu_dists_precise-security_Release
-rw-r--r-- 1 root root   74082 Oct 29 21:47 us.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages
-rw-r--r-- 1 root root      71 Oct 29 21:51 us.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Index
-rw-r--r-- 1 root root    4028 Aug  6 08:45 us.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en
-rw-r--r-- 1 root root    6740 Oct 31 14:10 us.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_source_Sources
-rw-r--r-- 1 root root  254756 Oct 29 21:47 us.archive.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages
-rw-r--r-- 1 root root      73 Oct 29 21:51 us.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index
-rw-r--r-- 1 root root  144758 Oct 11 23:39 us.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en
-rw-r--r-- 1 root root   50400 Oct 31 14:10 us.archive.ubuntu.com_ubuntu_dists_precise-security_universe_source_Sources
-rw-r--r-- 1 root root   11171 Nov  1 13:39 us.archive.ubuntu.com_ubuntu_dists_precise-updates_Release

---

### Post by dannyboy79 on 2012-11-01
> **majorburt said:**
> i get the same error as earlier (mv: cannot move `lists' to `lists.old/lists': Directory not empty)

what returns for "ls -la /var/lib/apt/" is this:

total 80
drwxr-xr-x  7 root root  4096 Nov  1 12:19 .
drwxr-xr-x 65 root root  4096 Oct 27 23:47 ..
-rw-r--r--  1 root root   223 Oct 16 18:26 cdroms.list
-rw-r--r--  1 root root 19956 Nov  1 12:19 extended_states
drwxr-xr-x  2 root root  4096 Aug 17 18:05 keyrings
drwxr-xr-x  3 root root 12288 Nov  1 13:42 lists
**drwxr-xr-x  4 root root 20480 Oct 31 12:50 lists.old**
drwxr-xr-x  3 root root  4096 Aug 17 18:05 mirrors
drwxr-xr-x  2 root root  4096 Oct 16 19:29 periodic
that's why you can't move it, you already have a lists.old!!!!!!!!!!!

so try
```
sudo mv lists lists.old2
```
which should move your current lists folder to lists.old2. 

GOod luck

---

### Post by majorburt on 2012-11-03
> **dannyboy79 said:**
> that's why you can't move it, you already have a lists.old!!!!!!!!!!!

so try
```
sudo mv lists lists.old2
```
which should move your current lists folder to lists.old2. 

GOod luck

ok, so that moved the file correctly and allowed me to go through with kanikilu's instructions. i can now download from "authenticated sources" but not "non-authenticated sources". 

is there some way to override the "non-authenticated sources" error through the terminal or some other means?

---

