---
title: "Install Emerald Window Decorator in Artful Aardvark 17.10"
date: 2018-01-01
forum: General Help
---

### Post by Cavsfan on 2018-01-01
Finally found a way to get emerald window decorator on 17.10 and have been trying for quite a while.

I got the Trusty 14.04 deb file from here: [https://pkgs.org/download/emerald](https://pkgs.org/download/emerald)

I had to also get the dependancy libemeraldengine0 deb file from here: [https://www.ubuntuupdates.org/package/webupd8/trusty/main/base/libemeraldengine0](https://www.ubuntuupdates.org/package/webupd8/trusty/main/base/libemeraldengine0)

Then got into my Downloads directory:
```
cd Downloads
```

Then since there were 2 deb files I wanted to use and they were the only ones in my Downloads directory I just had to enter this:
```
sudo dpkg -i *.deb
```

That worked without errors and then I tried **emerald --replace** in terminal just to test it out and it worked.

So, then I put that in CCSM Window Decoration and logged off and back in and it looks good.

[ATTACH=CONFIG]277996[/ATTACH]

[COLOR=#000000][FONT=Verdana]WebUpd8 usually keeps up with this but, for some reason they never added Artful to their PPA.[/FONT][/COLOR]

---

### Post by Cavsfan on 2018-01-02
Also, works well in Bionic Beaver 18.04 (development branch).

---

### Post by Cavsfan on 2018-05-24
Also, works well in Cosmic Cuttlefish 18.10 (development branch).

---

### Post by Cavsfan on 2019-04-24
If anyone is interested, this method still works on Xubuntu Bionic [COLOR=#000000]Beaver 18.04.2.

I re-installed it yesterday and could not get compiz to work but, I believe you have to install the components in this order:
[LIST=1]
[*]compiz-core
[*]libcompizconfig (which I believe pulls in as a dependency for #1.
[*]ccsm
[*]everything else
[*]emerald and libemeraldengine0 from the .deb files
[/LIST]

Seemed to work great using this method.
Maybe it was because I didn't install emerald too but, at any rate it works, the cube spins and all the bells and whistles work just fine. [/COLOR];)

---

