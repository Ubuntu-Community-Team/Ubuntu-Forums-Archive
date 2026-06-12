---
title: "transcode"
date: 2005-05-16
forum: General Help
---

### Post by cusco on 2005-05-16
Hi all...

I have an iPod where I can't copie ogg files.. so I asked what would people advise me to convert from ogg to mp3 and the answer i got was transcode! what happens is when I try to get it from the marillatt repositories some dependencies are not instalable:

```

cusco@Portatil:~$ sudo apt-get install transcode
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  transcode: Depends: libavcodeccvs (>= 2:20041227-woody0.1) but it is not going to be installed
             Depends: libdvdread2 but it is not installable
             Depends: libvorbis0 (>= 1.0rc3-1) but it is not installable
E: Broken packages

```

maybe someone could help me out!

---

### Post by shakin on 2005-05-17
Use the unofficial guide's part on installing a dvd ripper, which happens to install transcode as well.

[http://ubuntuguide.org/#dvdrip](http://ubuntuguide.org/#dvdrip)

---

