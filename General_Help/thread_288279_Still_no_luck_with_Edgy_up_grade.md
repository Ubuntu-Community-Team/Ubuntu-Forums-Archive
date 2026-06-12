---
title: "Still no luck with Edgy up grade"
date: 2006-10-29
forum: General Help
---

### Post by Tobster on 2006-10-29
I get an error message with the way people told me :(  This is the message:

Thanks 

Toby

---

### Post by aysiu on 2006-10-29
Can you post the output of this [terminal](http://www.psychocats.net/ubuntu/terminal) command? ```
cat /etc/apt/sources.list
```

---

### Post by Tobster on 2006-10-29
toby@toby-desktop:~$ cat /etc/apt/sources.list
sudo nano /etc/apt/sources.list
sudo vi /etc/apt/sources.list
toby@toby-desktop:~$


Thanks

Toby

---

### Post by aysiu on 2006-10-29
Yeah, those aren't valid sources. Those are commands to edit your sources.list.

To get a fresh sources.list, go here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Tobster on 2006-10-29
Cool,

Thanks for your help,  I did a lot of stuff when I was learning Ubuntu and gone were know Tobster had gone before so I may hvw messesd something up witout realizing.

I love Ubuntu my Windows days are long gone just got to tell everyone else :)

---

### Post by Tobster on 2006-10-29
I done that now... Do I need to rebot:confused:

---

### Post by Tobster on 2006-10-29
Forget that last message..  Im really happy now i got the update icon on my computer :)

Thanks your help means alot to me :D

---

### Post by llamakc on 2006-10-29
No, you need to update. In a Terminal that would be:

sudo apt-get update

---

### Post by llamakc on 2006-10-29
And there's a page here:

[http://www.ubuntu.com/download/releasenotes/610?highlight=%28update-manager%29](http://www.ubuntu.com/download/releasenotes/610?highlight=%28update-manager%29)

---

### Post by Tobster on 2006-10-29
Thank I do that Terminal command now :)

---

### Post by Tobster on 2006-10-29
I got this error message now 

Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg) Temporary failure resolving ‘packages.freecontrib.org’

---

### Post by llamakc on 2006-10-29
Where did you get your sources.list for Edgy?

Here's mine:

```

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe multiverse

deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

---

### Post by iamhugeinjapan on 2006-10-29
Don't worry about the packages.freecontrib.org source. You don't need it to install Edgy. You can comment it out in your sources file by putting a # in front of it or untick it in Synaptic.  Settings - Repositories.

The sources list posted above looks like a nice clean one for you to use instead.

---

