---
title: "Chkrootkit update--safe?"
date: 2005-06-15
forum: General Help
---

### Post by jonrkc on 2005-06-15
I did a routine "sudo apt-get update" followed by "sudo apt-get upgrade" and was told that there was an upgrade for chkrootkit available.  But also that it could not be authenticated.

Now I frequently install unauthenticated packages, as the risk is most likely minor, and mainly because, if I didn't, a lot of stuff would just never get installed.

But in the case of a security tool like chkrootkit I found it alarming that the package was not authenticatable, so I refused upgrading.

Was I over-cautious?  It seems really odd that a security package lacks authentication.

---

### Post by ubuntu_demon on 2005-06-15
[QUOTE=jonrkc]I did a routine "sudo apt-get update" followed by "sudo apt-get upgrade" and was told that there was an upgrade for chkrootkit available.  But also that it could not be authenticated.

Now I frequently install unauthenticated packages, as the risk is most likely minor, and mainly because, if I didn't, a lot of stuff would just never get installed.

But in the case of a security tool like chkrootkit I found it alarming that the package was not authenticatable, so I refused upgrading.

Was I over-cautious?  It seems really odd that a security package lacks authentication.[/QUOTE]
 what does your sources.list look like ?

I recommend using this one :

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Maybe comment out the backports if you don't want to use them. Don't add other repositories.

---

### Post by jonrkc on 2005-06-15
[QUOTE=demon666_nl]what does your sources.list look like ?

I recommend using this one :

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Maybe comment out the backports if you don't want to use them. Don't add other repositories.[/QUOTE]
My sources list is:

```


deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.

 deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

 deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

 deb http://security.ubuntu.com/ubuntu hoary-security main restricted
 deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

 deb http://security.ubuntu.com/ubuntu hoary-security universe
 deb-src http://security.ubuntu.com/ubuntu hoary-security universe
 
 ##The following is a backports mirror: and the two following lines are needed too
 ##according to a poster replying to a query of mine (jrr-5-31-05)
 
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted

deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
 
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

```

I've had to obtain a good many programs I wanted or needed from the backports, so I'd rather not do without those....

But I guess I'll wait till I see an authenticated version of chkrootkit or anything else security-oriented, to install it.

Meanwhile I do update and run rkhunter daily as a cron job.

---

### Post by ubuntu_demon on 2005-06-15
chkrootkit is in staging see :

[http://ubuntuforums.org/showthread.php?t=41505](http://ubuntuforums.org/showthread.php?t=41505)

So this isn't a security update.

At this moment none of the backport packages are gpg signed.

You shouldn't use staging unless you know what you are doing. staging is intended for testing backports.

You should revert to the sources.list from ubuntuguide.org

In a while chkrootkit will enter backports. It's fine to accept the update when that happens.

---

