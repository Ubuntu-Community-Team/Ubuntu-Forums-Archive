---
title: "Locking current source files..."
date: 2012-12-14
forum: General Help
---

### Post by Baldrick_NZ on 2012-12-14
I have Wine 1.5.19 currently installed, and it's very CPU intensive (89-95%) with a programme I run. The previous incarnation was much better (30-40% CPU).

The question is, and it's not just related to Wine - it could be any source package (.tar.bz2) - when there are no .deb files for a program, how can one compile and lock it so it doesn't update?

In this case, I have found this [http://sourceforge.net/projects/wine/files/Source/](http://sourceforge.net/projects/wine/files/Source/) page, from which I'd like to re-install version 1.5.18, and then lock that version. 

Any help would be very much appreciated!

Baldrick.

---

### Post by Baldrick_NZ on 2012-12-15
Bump... Anyone?

---

### Post by Rexilion on 2012-12-15
If you compile it yourself you won't have to lock it since the package manager will not even know your program is there.

If you lock ([hold it]("https://help.ubuntu.com/community/PinningHowto")) it, you don't need to compile since the update manager already keeps your prefered version there.

---

### Post by mc4man on 2012-12-15
The sourceforge page is quite outdated, wine sources there are 0.9 > 1.1.xx, the latest being 1.1.27

It appears?? you are using the Ubuntu Wine Team ppa, if so ppa's only hold prior builds for a short time so downgrading to your previous 1.5.xx could be problematic (they may be in /var/cache/apt/archives

There are still packages there for a prior i386 build, (wine 1.5 1.5.15) but really can't advise if/how to be useful to you.
[https://launchpad.net/~ubuntu-wine/+archive/ppa/+build/3900392](https://launchpad.net/~ubuntu-wine/+archive/ppa/+build/3900392)

As far as compiling wine it's not a trivial build, you could get earlier sources from the ppa or just use the current precise repo packages which are wine-1.4

---

### Post by Baldrick_NZ on 2012-12-16
> **Rexilion said:**
> If you compile it yourself you won't have to lock it since the package manager will not even know your program is there.

If you lock ([hold it]("https://help.ubuntu.com/community/PinningHowto")) it, you don't need to compile since the update manager already keeps your prefered version there.

Thanks for that,

But how do you compile from source (.tar.gz), when there isn't .deb files available?

---

### Post by Rexilion on 2012-12-16
You needed to scroll down on the sourceforge page, eventually the 1.5+ versions will appear. I see why you thought it was outdated, it is not.

I tried looking for 1.5.18 as a .deb but it's already gone. This kind of happens the moment 1.5.19 is published. Your best bet is to compile your own wine in your home directory. Like a dedicated installation for your specific purpose.

You can download [1.5.18 here]("http://sourceforge.net/projects/wine/files/Source/wine-1.5.18.tar.bz2/download").

This might or might not work, I did not test it. But it should be like 95% of what you want. It will build and install wine in ~/wine/1.5.18.

```
tar -xjf wine-1.5.18.tar.bz2
cd wine-1.5.18
aptitude -yR build-depends wine
mkdir ~/wine/1.5.18
./configure --prefix=~/wine/1.5.18
make
make install
```

To run this version you could do (but don't do it yet!):

```
~/wine/1.5.18/bin/wine <executable>
```

It is recommended to use a seperate installation prefix so it will not collide with the system version. The system version uses the default (~/.wine). So you could use something like ~/.wine-1.5.18.

```
env WINEPREFIX=~/.wine-1.5.18 ~/wine/1.5.18/bin/wine <executable>
```

Please not that the ppa version contains modifications that are not included in this tarball. The most notable one is probably pulseaudio support. You have to apply the patch yourself if you want to, or live without it.

---

