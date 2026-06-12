---
title: "[SOLVED] Problems With the Repository Listings When Updating"
date: 2008-06-05
forum: General Help
---

### Post by yman on 2008-06-05
Hi.
I have no clue what's causing it, but each time I try checking for updates, I get this:

```
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Xiong Chiamiov on 2008-06-05
Can you please post the contents of your /etc/apt/sources.list file?

---

### Post by yman on 2008-06-05
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted web
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse web
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted web
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
# deb http://ubuntu.org.ua/ getdeb/
```

---

### Post by Xiong Chiamiov on 2008-06-05
Hmm, that's odd.  I don't see anything wrong with your file, and I have those same lines (along with a bunch of other crap) and I'm able to update my listing just fine.  I'm assuming that this is happening when you run
```

sudo apt-get update

```
or
```

sudo aptitude update

```
?

I'll do some Googling.

EDIT:  [Mmhmm]("https://answers.launchpad.net/ubuntu/+question/22021")?  Looks like you need to remove the word "web" from the lines that have it.

---

### Post by iaculallad on 2008-06-05
You can try running this command on your terminal:

```
sudo apt-get install --fix-missing
```

---

### Post by yman on 2008-06-05
I did it from GUI, so I had to run the command now just to confirm. It's the same (sudo apt-get update):
```
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Xiong Chiamiov on 2008-06-05
Did you try what I slipped into my post in an edit?

---

### Post by yman on 2008-06-05
> **iaculallad said:**
> You can try running this command on your terminal:

```
sudo apt-get install --fix-missing
```

Thanks, but it didn't seem to do anything.

> **Xiong Chiamiov said:**
> Did you try what I slipped into my post in an edit?

I missed that one. It seems to have done the trick, but no updates are showing. Maybe it means my system is up to date, or maybe it means I have a new error, but for now, thanks.

---

### Post by Xiong Chiamiov on 2008-06-05
> **Xiong Chiamiov said:**
> 
EDIT:  [Mmhmm]("https://answers.launchpad.net/ubuntu/+question/22021")?  Looks like you need to remove the word "web" from the lines that have it.

This is what I was referring to.

---

### Post by iaculallad on 2008-06-05
Try changing your download server. Navigate to System->Administration->Software Sources, under the "Ubuntu Software" tab, "Download From" and select "Main Server". Click on close and on your terminal, issue the command:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Xiong Chiamiov on 2008-06-05
> **iaculallad said:**
> Try changing your download server. Navigate to System->Administration->Software Sources, under the "Ubuntu Software" tab, "Download From" and select "Main Server". Click on close and on your terminal, issue the command:

```
sudo apt-get update && sudo apt-get upgrade
```
As indicated [here]("https://answers.launchpad.net/ubuntu/+question/22021"), changing the download location won't solve anything, since the web package is bogus; it just somehow got added in on accident.

> **yman said:**
> I missed that one. It seems to have done the trick, but no updates are showing. Maybe it means my system is up to date, or maybe it means I have a new error, but for now, thanks.

Well, you'll probably only have to wait a day or two to find out.  If the lists all download, then you should be fine.

---

### Post by iaculallad on 2008-06-05
> **Xiong Chiamiov said:**
> As indicated [here]("https://answers.launchpad.net/ubuntu/+question/22021"), changing the download location won't solve anything, since the web package is bogus; it just somehow got added in on accident.



Well, you'll probably only have to wait a day or two to find out.  If the lists all download, then you should be fine.


Ok, thanks for pointing it out. I did not see the launchpad myself :)

---

### Post by Xiong Chiamiov on 2008-06-05
> **iaculallad said:**
> Ok, thanks for pointing it out. I did not see the launchpad myself :)
No problems.  I just don't want you to continue trying to find answers if he's gotten it working.

---

### Post by yman on 2008-06-05
I confirmed it. All is well.

---

