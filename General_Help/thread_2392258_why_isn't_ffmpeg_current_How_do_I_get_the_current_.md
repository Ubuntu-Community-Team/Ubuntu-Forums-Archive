---
title: "why isn't ffmpeg current? How do I get the current one?"
date: 2018-05-18
forum: General Help
---

### Post by NotQuiteSU on 2018-05-18
So I found my version of ffmpeg is a bit old, but there are no updates when I run apt-get, etc. But I see ffmpeg 4 is out.
How would I get the most current version?

I know this seems basic, but I'm stuck finding an official way

---

### Post by QIII on 2018-05-18
Hello!

It takes time to test and package applications before they are added to the repo.  Once a new version of Ubuntu has been released (actually, at the point of "feature freeze" during the development cycle), the packages in the repos are frozen unless a change represents a security fix.

ffmpeg 4 was not released until April 20th -- which was well after the feature freeze for Ubuntu 18.04.  It is possible that ffmpeg 4 will appear in future releases, but I am not privy to Canonical's plans and can't say with any authority.

You can always download the latest [here]("https://www.ffmpeg.org/download.html"), but that would make you responsible for keeping it current and up-to-date.

---

### Post by monkeybrain20122 on 2018-05-18
A major ffmpeg update will likely break the system because quite a few packages depend on it. It is easy to compile it from source locally.

---

### Post by NotQuiteSU on 2018-05-18
I may be a bit slow. I'm pretty new to some of this stuff. 
I'm on a much older version of ffmpeg

ffmpeg version 2.8.14-0 

I'm on ubuntu0.16.04.1

I looked at [https://www.ffmpeg.org/download.html](https://www.ffmpeg.org/download.html), but I just don't see what I'm supposed to download/install.

If I click on [https://launchpad.net/ubuntu/+source/ffmpeg](https://launchpad.net/ubuntu/+source/ffmpeg), I see at the bottom versions 2.8

---

### Post by QIII on 2018-05-18
16.04.1 is the first point release of Xenial Xerus (at the bottom of the list of releases).

You have the appropriate version for your Ubuntu release.  If you look closely, you will see that the version of ffmpeg you have referenced is a security release, as I indicated above.

---

### Post by monkeybrain20122 on 2018-05-18
If you are on Ubuntu 16.04, maybe can give mc3man's ppa a try. [https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test](https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test)

---

### Post by NotQuiteSU on 2018-05-18
Ah, I see. I've seen various search results offering different repositories for ffmpeg3/4. Do you know if there will be any updates to this one, or do I have to update Ubuntu to 18.04?

---

### Post by QIII on 2018-05-18
Disclaimer:  PPAs are Personal Package Archives.  They are not official.  The maintainer -- another user like you -- prepares them.  You assume the risk of breakage.  In this case, the PPA maintainer has used the word "test" and given warning.

---

### Post by monkeybrain20122 on 2018-05-18
> **QIII said:**
> Disclaimer:  PPAs are Personal Package Archives.  They are not official.  The maintainer -- another user like you -- prepares them.  You assume the risk of breakage.  In this case, the PPA maintainer has used the word "test" and given warning.

Mc3man is a very respected member of the community and a frequent contributor of this forum. I would trust him. Also the version is ffmpeg-static, so it is installed in /opt and won't interfere with the system's version.

As a general point you are right about PPAs. so only use the well known ones, there are a few like mc3man's webupd8 etc.

---

### Post by NotQuiteSU on 2018-05-18
What does the static mean with relation to /opt?
Does that also mean that when I need to use ffmpeg, I have to point to /opt, vs the default of it being in the PATH?

---

### Post by SeijiSensei on 2018-05-18
"Static" binaries include all the required dependencies built into the compiled output.  They operate in a stand-alone fashion and don't require any other software to be installed on the machine. (ffmpeg has a **ton** of dependencies.)  Storing in /opt is just one possibility; I usually put local binaries in /usr/local/bin and /usr/local/sbin.  Those directories are in the standard path.

I've both compiled ffmpeg from scratch and also used McMahon's PPA.  If you've never compiled software before, I'd stick with the PPA route.

---

### Post by mc4man on 2018-05-18
The "test" part of that was about providing a newer ffmpeg version without conflicting or removing the ffmpeg package in 16.04. 
In this case it's only for the use of the ffmpeg binaries so no shared ffmpeg libs are built. (hence "static" in the name, ffmpeg binaries are statically built. It is not a portable build..

The method chosen was to use new binary names, i.e, ffmpeg2, ffprobe2, ffplay2.
The reason to install to /opt was to insure the headers would not be used if someone built a source that used ffmpeg libraries.

I've kept it up because there are a number of users of that ppa who want a reasonably current ffmpeg binary for encoding and decoding. At times requests are fulfilled, last was to provide a newer vpx, also added vp9-highbitdepth support. 

Alternatives were an actual 'portable' ffmpeg build here - [https://johnvansickle.com/ffmpeg/](https://johnvansickle.com/ffmpeg/)  though atm suspended as he wants $$
(these builds were never full featured..

It's probable I'll provide a shared ffmpeg 4.0 release for 16.04 here in near future or so as the shared libs can now co-exist with 16.04's current ones. Currently it's at 3.4.1
[https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media](https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media)
This build does replace the repo's ffmpeg package & can be used to build off of.

---

### Post by NotQuiteSU on 2018-06-13
Thank you guys for the response. And sorry for the delay. Last stupid question - how do i tell a script to use the /opt/ version of ffmpeg if ffmpeg is installed and in my path? Do I specify it as a variable, pointing to /opt?

---

### Post by mc4man on 2018-06-13
> **NotQuiteSU said:**
> Thank you guys for the response. And sorry for the delay. Last stupid question - how do i tell a script to use the /opt/ version of ffmpeg if ffmpeg is installed and in my path? Do I specify it as a variable, pointing to /opt?
If you're referring to those builds I put in the ffmpeg-test ppa,
1. Did you read the [ppa page]("https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test")?
2. While the actual binaries are installed to /opt/ffmpeg/bin there are symlinks in /usr/bin named ffmpeg2, ffplay2, ffprobe2
3. So command to use that ffmpeg binary is ffmpeg2

---

### Post by NotQuiteSU on 2018-06-13
No, I didn't I apologize. I'm working on a script and trying to make it portable. Just have to make some custom changes on my end.

---

### Post by mc4man on 2018-06-13
> **NotQuiteSU said:**
> No, I didn't I apologize. I'm working on a script and trying to make it portable. Just have to make some custom changes on my end.

If you're installing a self build to /opt/ then in your script you'd need to full path the ffmpeg binary or you'd need to add  that /opt/whatever/bin to your $PATH and have it before /usr/bin

The best way for self builds is shown here (installs to your $HOME dir.
[https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)

---

