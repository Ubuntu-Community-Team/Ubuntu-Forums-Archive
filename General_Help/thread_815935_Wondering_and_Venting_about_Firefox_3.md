---
title: "Wondering and Venting about Firefox 3"
date: 2008-06-02
forum: General Help
---

### Post by nlvivar on 2008-06-02
So a link asking to upgrade Google Earth opened up Firefox 3 on me and disabled a number of my Firefox 2 addons. So now I'm going to spend some time fixing my profile.

I was just wondering a few things:

1) Who decided that Firefox 3 should be the *default* for Hardy? I can understand including it, but not making it the default. Blerg.

2) Is it planned for the latest Firefox 3 Release Candidate to be included into the repositories? It is odd that they would include a beta, but not let you upgrade to the RC.

3) Is it planned for the repositories to include the Firefox 3 Final when it does come out?

Just wondering and venting.

---

### Post by kid-pro-quo on 2008-06-02
The reason they chose to include Firefox 3 as the default is because 8.04 is a LTS release. Whatever they'd gone for as default they'll have to support for the entire LTS cycle, and it wouldn't make any sense to still be having to support Firefox 2 in four years time!

The same goes for all the other stuff like pulse audio etc. There's no point including programs which are in about to be depreciated in a LTS release.

---

### Post by sdennie on 2008-06-02
Also, the FF3 RC1 is already in the proposed repositories.  If you enable "proposed" with synaptic, you'll get it (it's infinitely better than the last beta).

---

### Post by OliverW on 2008-06-02
1. See kid-pro-quo
2. Yes, RC1 is coming... it's already in hardy-proposed (I'm already running it)
3. Of course :)

---

### Post by nlvivar on 2008-06-02
Ok. That makes sense. But then why the delay with upgrading to RC1?

---

### Post by nlvivar on 2008-06-02
OK. Thanks I will do that. I'm happy now. I didn't hear of the Proposed repo until now. Is this about on par with Debian's Testing Repo?

---

### Post by sdennie on 2008-06-02
Ubuntu isn't a free for all and so just because a new version of a package has come out doesn't mean it will hit the repos immediately.  This philosophy can be frustrating at times (like with FF3) but, in the long run, it's actually a very good thing.

---

### Post by Zorael on 2008-06-02
> **kid-pro-quo said:**
> The reason they chose to include Firefox 3 as the default is because 8.04 is a LTS release. Whatever they'd gone for as default they'll have to support for the entire LTS cycle, and it wouldn't make any sense to still be having to support Firefox 2 in four years time!

The same goes for all the other stuff like pulse audio etc. There's no point including programs which are in about to be depreciated in a LTS release.
Precisely.

*(copy/paste):* LTS does not mean that the distro is guaranteed to be completely bug-free. In a few months, FF3 and PulseAudio may very well be the de facto standards, and if Hardy were to have FF2 and plain ALSA (boo! [OSS4!](http://tinyurl.com/5c6luu) :>), it'd be considerably out-of-date.

To be fair, most of it seems to be caused by Flash not playing nice at all with FF3. Ensue blame game, but developers can't do jack about Flash's source.

I'm going to shamelessly suggest you remove FF3 completely for the time being. Perhaps even FF2 and migrating to Swiftweasel! Rarr!

[http://swiftweasel.tuxfamily.org](http://swiftweasel.tuxfamily.org)
> **Wikipedia][SIZE="4"]Optimization[/SIZE]

Swiftweasel is optimized using the following methods:

**Binary code optimization**
[list]
    [*] Compiled with options that optimize for speed rather than binary size.[list]
          [*] Swiftweasel is compiled -O3, (the highest level)[list]
                [*] The resulting Swiftweasel binary is larger than Firefox.[/list]
          [*] Firefox is compiled -Os (which is for binary size).[/list]
    [*] Binaries incorporate additional instruction sets.[list]
          [*] Intel and AMD: SSE, SSE2, SSE3, and MMX.
          [*] AMD only: 3DNow![/list]
    [*] Optimization specific to the build microprocessor architecture.[list]
          [*] Intel 32bit: Pentium 4, Pentium 3, Pentium M, Pentium 3M, Pentium 2, Prescott.
          [*] Intel 64bit: Nocona
          [*] AMD: Athlon XP, Athlon, K6-2, Athlon.
          [*] AMD64: Athlon64, Opteron[/list]
    [*] Compiled with newer version of GCC (Firefox 2.0 uses 3.3.2, Swiftweasel 2.0 uses 4.0.3).[/list]

**Increased Security**[list]
    [*] Better protection from Buffer overflow attacks (Swiftweasel 2.0 uses -D_FORTIFY_SOURCE=2 said:**
> 

**Simplify**[list]
    [*] IPv6 DNS lookups are disabled, preventing slowdowns 
    [*] HTTP pipelining is enabled by default. Note that Fasterfox provides a GUI to adjust these settings.
    [*] For full details, users can download source packages with all changes listed.[/list]

```
$ sudo su
# echo "deb http://download.tuxfamily.org/swiftweasel hardy multiverse" > /etc/apt/sources.list.d/swiftweasel.list
# aptitude update
# aptitude install ~nfirefox-3.0_ ~nfirefox-2_ *swiftweasel*
```
Bookmarks and extensions will not be removed. If you want a further optimized build of Swiftweasel, replace 'swiftweasel' in the above command with swiftweasel-*<prefix>*. Available such:
[list][*]swiftweasel-athlon64
[*]swiftweasel-pentium3
[*]swiftweasel-pentium3m
[*]swiftweasel-athlontbird
[*]swiftweasel-athlonxp
[*]swiftweasel-pentium4
[*]swiftweasel-k6
[*]swiftweasel-pentium4m
[*]swiftweasel-k8
[*]swiftweasel-pentiumm
[*]swiftweasel-nocona
[*]swiftweasel-prescott
[*]swiftweasel-pentium2[/list]
> [SIZE="4"]Which Build Is Right For My Computer?[/SIZE]
The names of the builds can be confusing. This page will seek to help you choose the correct build for your computer.

[list][*]**Amd64**
This build is recommended for AMD 64bit processors. Including the AMD 64 x2, but excludes the Opteron.
[*]**Athlon-XP**
This build is recommended for the 32bit Athlon, Athlon XP, and K-7 processors
[*]**Athlon-Tbird**
This build is recommended for the older 32bit Athlon and other K-7 processors.
[*]**Opteron**
This build is recommended for AMD Opteron processors.
[*]**K6**
This build is recommended for AMD K6 processors
[*]**Pentium 3**
This build is recommended for Pentium 3 processors. This includes the Celeron II (Coppermine and Tualatin) based on the pentium 3.
[*]**Pentium 3m**
This build is recommended for Pentium 3 mobile processors and the mobile Celerons.
[*]**Pentium 4**
This build is recommended for Pentium 4 processors This includes the Celerons IIII (Willamette and Northwood) based on the pentium 4.
[*]**Pentium 4m**
This build is recommended for Pentium 4 mobile processors
[*]**Prescott**
This build is recommended for the Core Duo (32bit) and Celeron D (64bit) processors
[*]**Nocona**
This build is recommended for the Intel 64bit chips including the Core 2 Duo.[/list]
To find out what you have:
```
$ lshw -C processor | grep product
```

---

### Post by nlvivar on 2008-06-02
I understand the desire not to be a free-for-all, but it seems a bit arbitary to put out FF3 as a beta and not make a big push to move FF3 RC1 out ASAP.

Anyways, I'm glad I started this little rant of a post since I found out about the Proposed Repo. Now I can install FF3 RC1 AND start filing some bug reports on launchpad.

Thanks, everyone.

---

### Post by sdennie on 2008-06-02
FF3 RC1 will make it to the masses soon enough.  Ubuntu doesn't just drop major updates on people.  It puts them in proposed so people who want to can test them out and, once it works well, the changes propagate to the main repos.  It can be annoying with things like FF3 but, it really is in the spirit of making a more stable system.  ;)

---

