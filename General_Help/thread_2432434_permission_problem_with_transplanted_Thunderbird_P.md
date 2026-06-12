---
title: "permission problem with transplanted Thunderbird Profile"
date: 2019-12-02
forum: General Help
---

### Post by pjstock on 2019-12-02
this problem arises while using Thunderbird but I susptect it is a general Permissions problem.

My desktop Thunderbird blew up recently. rather than struggle to figure out the problem and restore the original profile, I removed Thunderbird (which was coming up completely blank and unresponsive), reinstalled a fresh version and then copied my Thunderbird profile from my laptop to my desktop.
I then modified the Profiles.ini file to reference this transplanted profile.

Everything seemd to work well. Thunderbird launched happily and all my email accours were there and seemed intact.

HOWEVER. when I tried to send an email and attach a file from my desktop external USB harddrives, it failed. I got an error message "could not read contents of.... XYZ drive....... Permission Denied"

might this relate to permissions from my laptop Thunderbird not translating cleanly to my desktop version?

I could start from stracth and just rebuild all the email profiles (3 accounts) but that would be a bore.

many thanks as always

Peter

---

### Post by CatKiller on 2019-12-02
Did you install Thunderbird as a snap? They are limited in the locations they can read & write.

---

### Post by pjstock on 2019-12-09
what is "a Snap"? (so I guess I don't know.)

under my About I see version 60.3.0 (64-bit)

---

### Post by howefield on 2019-12-09
> **pjstock said:**
> what is "a Snap"? (so I guess I don't know.)

An alternative packaging format that Canonical are developing, if you open a terminal and use the command

```
snap list
```

you should get a list of any installed snaps, is Thunderbird there ? 

> under my About I see version 60.3.0 (64-bit)

You don't say which version of Ubuntu that you are using, but on this 19.10 install I see both the snap version at 60.3.0 and the deb version at 68.2.1

Also for info..

```
apt-cache policy thunderbird
```

will tell you if you have the traditional deb package installed.

---

### Post by pjstock on 2019-12-09
Ahhhah! I do see Thunderbird in the snap list. (and I also see KolourPaint which has also been giving me problems.)

I know this is not how one is supposed to post output from commands but....
re: apt-cache policy thunderbird

I get....

peter@peter-OptiPlex-990:~$ apt-cache policy thunderbird
thunderbird:
  Installed: (none)
  Candidate: 1:68.2.1+build1-0ubuntu0.18.04.1
  Version table:
     1:68.2.1+build1-0ubuntu0.18.04.1 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:52.7.0+build1-0ubuntu1 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages

and finally I am running Ubuntu 18.04.3 LTS

many thanks

---

### Post by TheFu on 2019-12-09
Aren't snaps supposed to be automatically updated and always fresher than the .deb versions?  Say it isn't so! 

I'm on 16.04.6 and have ```

$ dpkg -l |grep thunderb
ii  thunderbird                                 1:60.9.0+build1-0ubuntu0.16.04.2 
```

---

### Post by howefield on 2019-12-09
Just confirms that CatKiller was right on the money.

I'd suggest uninstalling the snap and installing the deb given that this particular snap appears not very likely to get an update to the current release.

A quote from the Thunderbird snap packager..

> "The thunderbird snap was really only meant to be a POC and has never been deemed stable enough to recommend use. We&#8217;ve had some discussions with upstream, but no concrete plans on them supporting the snap yet.""

---

### Post by howefield on 2019-12-11
> **TheFu said:**
> Aren't snaps supposed to be automatically updated

Indeed, snapd will check 4 times per day (default setting) for updates.

```
hugh@eoan:~$  snap refresh --time
timer: 00:00~24:00/4
last: today at 09:15 GMT
next: today at 14:24 GMT
hugh@eoan:~$ 
```

> and always fresher than the .deb versions?  Say it isn't so! 

It is so :) unless there is no update to be had, as in the case of Thunderbird.

---

### Post by TheFu on 2019-12-11
To me, having software change outside approved maintenance windows is a huge bug unless I've requested automatic updates.  4x a day is just, crazy.

Once again, we show that we aren't  1-size fits all.

---

### Post by rsteinmetz70112 on 2019-12-11
> **TheFu said:**
> To me, having software change outside approved maintenance windows is a huge bug unless I've requested automatic updates.  4x a day is just, crazy.

Once again, we show that we aren't  1-size fits all.

I agree. It may reduce the load on the servers and may be easy for pure desktop users used to Windows Update, I'm not sold.

I due manual updates about weekly sitting at the console, just so something won't go wrong without me knowing it and being able to fix it right away. It doesn't help to get an alert that something screwed up when I can't do anything about it. 

That doesn't mean I can't drink my coffee or check my email while it's running.

---

