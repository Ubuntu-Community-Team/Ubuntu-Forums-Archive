---
title: "Help installing sun-j2re1.5"
date: 2005-10-07
forum: General Help
---

### Post by larry_steiner on 2005-10-07
Hi Team,
With the current changes/ removal of the backports, I have been having problems.  I would like to install sun-j2re1.5 so I can use Limewire p2p.

I did a search on sun-j2re1.5 on Synaptic and got no match.  Here is what I have for etc/apt.  Can you please help?  Thanks.

deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary main restricted universe multiverse
deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-updates main restricted
deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-updates main restricted

deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-security main restricted
deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
#backup Mirror - FAST
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse

---

### Post by jrib on 2005-10-07
You can install Sun Java.  Instructions are available on the wiki: [https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca).

---

### Post by Zelut on 2005-10-07
You can also use these instructions:

download the JRE & JDK .bin files (JDK needed by other apps like Azureus)
you can get those here ([http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp))
$apt-get install java-package (from multiverse - needed for next steps)
$fakeroot make-jpkg .bin files (this'll convert them to .deb packages)
$sudo dpkg -i *.deb (install the .deb packages)

Also you can find these instruction here in this post
[http://www.ubuntuforums.org/showthread.php?t=70428&highlight=jdk](http://www.ubuntuforums.org/showthread.php?t=70428&highlight=jdk)

---

### Post by ubuntumaneh on 2005-10-07
Try this:

deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) hoary main

just edit this line in your source-list. Then use apt-get (ignore a error auth message in the end of update). The name is java-package. Many things that used to be on repositories is still here. But be cautious, this things are not supported.

---

### Post by tehwa on 2005-10-07
Sorry to add another reply, but this wiki page worked a treat for me:

[https://wiki.ubuntu.com/JavaPackageBuildNewVersions](https://wiki.ubuntu.com/JavaPackageBuildNewVersions)

Which is basically just an extension of the wiki page that _jason posted.

Also, if you add the cipherfunk.org repos, its a good idea to comment the line out of your sources.list after you've got what you want, otherwise you will get a bunch of upgrades that probably aren't welcome.

---

### Post by skirkpatrick on 2005-10-07
I wonder if anybody has noticed the Unofficial Ubuntu 5.10 Starter Guide in System->Help, which is remarkably like the old Unofficial Hoary Guide.  It also has the instructions.

---

### Post by Sheytan on 2005-10-08
You can download the [Unofficial Ubuntu 5.04 Add-On CD]("http://www.ubuntuforums.org/showthread.php?t=30147&highlight=add-on") and install it that way

---

### Post by larry_steiner on 2005-10-08
Thanks for the help.  Jason's solution worked first time.

Just a thought.
The news groups are very helpful.  It could be made better if things like the now out of date unofficial guide were removed and only the most current version remained.  It creates lots of confusion and unneeded posts.  I'm sure that many of us don't follow the news groups on a day by day basis and tend to go to what had worked in the past.  It's the not seeing the forest because of all the trees principal.  At any rate thanks again.

The last post had me confused.  Not a hard thing to do.  When I look at system > help  I see version 5.04.  And could not find the now “Official” “Unofficial guide”.  Are you using the beta?

---

### Post by skirkpatrick on 2005-10-08
[QUOTE=larry_steiner]
The last post had me confused.  Not a hard thing to do.  When I look at system > help  I see version 5.04.  And could not find the now “Official” “Unofficial guide”.  Are you using the beta?[/QUOTE]

It's a fresh install of 5.10 Preview.  I was pleasantly surprised to see it.

---

