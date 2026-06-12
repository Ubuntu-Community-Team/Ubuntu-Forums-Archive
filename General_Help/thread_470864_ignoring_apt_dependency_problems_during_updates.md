---
title: "ignoring apt dependency problems during updates"
date: 2007-06-11
forum: General Help
---

### Post by timtoo on 2007-06-11
I (once again) found I needed a newer version of a package than is available in the fiesty universe. Happily I discovered the latest version is in the new gutsy repositories, so i grabbed the deb from there and installed it manually with dpkg. I had to use --ignore-depends to get around the libc version (yes, i know the dangers here, but it's okay in this case). 

Now I find I can no longer upgrade other packages via apt-get or aptitude, or adept... due to the dependency problem trying to force removal of these two rogue packages I need installed.

I fumbled around for hours trying various things i stumbled across. I tried using --set-selection to mark the packages with "hold", and add Ignore-Hold "true" to apt.conf. Tried adding a bunch of variations on --ignore-depends to the DPkg Options in apt.conf ... but none of this seems to have any effect.

Surely there's a simple method someone can tip me off about... 

(Besides building the software i need from source, which was the beauty of Gentoo... but i'm trying to get away from now for my desktop...)

Thanks.

---

### Post by Amalekite on 2007-06-13
> **timtoo said:**
> 
I fumbled around for hours trying various things i stumbled across. I tried using --set-selection to mark the packages with "hold", and add Ignore-Hold "true" to apt.conf. Tried adding a bunch of variations on --ignore-depends to the DPkg Options in apt.conf ... but none of this seems to have any effect.


I had a similar problem with the netatalk package... after "manually" installing & compiling it with OpenSSL (for encrypted passwords) apt-get keeps insisting on installing the original.

That was a pain 'coz I had to reinstall my compiled version every time I ran apt-get.  However, after picking up the hint in your post, about using --set-selections with dpkg, I managed to get it to work... I did something like:

   echo "netatalk hold" > /tmp/dpkg-tempfile
   sudo dpkg --set-selections < /tmp/dpkg-tempfile

and it worked!  I checked using

   sudo dpkg --get-selections netatalk

which returned

   netatalk        hold

> **timtoo said:**
> 
Surely there's a simple method someone can tip me off about... 


I hope my trick works for you.  Thanks for the tip about dpkg's --set-selections flag... wouldn't have thought to use dpkg otherwise  ;-)

Cheers.

---

### Post by timtoo on 2007-06-14
The dpkg --set-selections is something I tried, but isn't working for me. The packages are set to "hold" but i still have dependency problems when trying to manage any packages. 

I'll be more specific for anyone else who might wander in with some additional knowledge on the subject:

```
# dpkg --get-selections | grep hold
postgresql-8.2-slony1                           hold
slony1-bin                                      hold
```

So those are the manually installed debs. I have marked them as "hold", experimentally, however that doesn't seem to do anything in my "broken dependency" situation. When i try to install/upgrade any other software (using command line here, but using the UI tools has the same result):

```
 # apt-get install libexif12
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  postgresql-8.2-slony1: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is to be installed
  slony1-bin: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I've also  tried using apt-get --force-yes (with --no-remove), to no effect.

Searching around with google i find a lot of people out there have had similar problems, and there seems to be no answer... which is kind of weird. I guess apt has no interest in people who need to stray slightly outside its sandbox.

However, tipped off by a post i found what I did end up doing was manually with a text editor going into 
/var/lib/dpkg/status and finding the two package names above, and editing the "Depends:" line to remove the "libc6 (>= 2.5-5)"... and amazingly this worked. The system no longer knows that those two installed packages have a dependency on libc6 at all.

After doing the above I learned there is a program called "equivs" (in universe) which will install a "dummy package" to trick apt into thinking whatever dependency you need is already installed. This seems to me a worse hack than even manually editing the dpkg/status file (because then you have a fake package installed that might interfere with other unexpected things thinking it is there when it is not)... but it might be more agreeable to some.

---

