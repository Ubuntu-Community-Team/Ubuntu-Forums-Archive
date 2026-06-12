---
title: "[SOLVED] Irssi 0.8.12 - Installation problems"
date: 2008-03-31
forum: General Help
---

### Post by ilych on 2008-03-31
Hello,

**Method #1**: I first tried to install Irssi via the binary package listed on [irssi.org/download]("http://irssi.org/download"). This doesn't seem to work. After sudo apt-get install irssi, I cannot even run Irssi, although there is no error message.

> Debian: Sid: Irssi is available from sid. Just run apt-get install irssi. Sarge: edit your /etc/apt/sources.list file and add:
deb [http://www.davidpashley.com/debian/irssi-sarge/](http://www.davidpashley.com/debian/irssi-sarge/) ./
Then run apt-get update; apt-get install irssi

**Method #2**: I then tried to make a .deb package from the source code (.tar.gz) on the [Irssi website]("http://irssi.org/download") with [checkinstall]("ttp://www.falkotimme.com/howtos/checkinstall/"). I am able to install the .deb package, but upon running Irssi, I receive the following error whenever I try to load any script, e.g.,

```
Irssi: Error in script awl.v0.7a
Can't locate Irssi.pm in @INC (@INC contains: /home/ilych/.irssi/scripts /usr/local/share/irssi/scripts /etc/perl  /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8  /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 20) line 1.
```

Side Question: Why are there two /.irssi folders? If the program did work, where should I place my scripts?

**Method #3**: Finally, via LinuxAppFinder, I was able to find a v.0.8.12 .deb package ([gutsy-backports 0.8.12-2ubuntu1~gutsy1]("http://linuxappfinder.com/package/irssi")). Installation fails if I install this .deb package from ~/, but it works perfectly if I move the .deb file to /usr/local and install it from there. Why is this the case? Where should I generally install a .deb file?

So while Method #3 works, I am wondering why both Method #1 and #2 do not work.

Thanks for any help!
ilych

**Other Notes**:
Packages I installed that are necessary for Irssi to install:
sudo apt-get install build-essential (for C compiler)
sudo apt-get install ncurses-dev
sudo apt-get install libperl-dev

---

### Post by gsmanners on 2008-03-31
Ubuntu is not Debian. You *do not* edit your /etc/apt/sources.list or you will mess up your system.

---

### Post by ilych on 2008-03-31
> **gsmanners said:**
> Ubuntu is not Debian. You *do not* edit your /etc/apt/sources.list or you will mess up your system.

Thanks, I didn't know this. I deleted the lines I added.

---

