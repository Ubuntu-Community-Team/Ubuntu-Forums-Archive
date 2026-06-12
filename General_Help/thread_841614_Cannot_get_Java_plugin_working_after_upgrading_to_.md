---
title: "Cannot get Java plugin working after upgrading to FF 3"
date: 2008-06-26
forum: General Help
---

### Post by tbraun on 2008-06-26
Hello!

I have installed Firefox 3 on my Ubuntu 7.10. The Java plugin worked fine for me when I still used FF 2, but now I can't get it to work anymore.

I installed FF 3 from the Mozilla site, but also tried FF 3 from the repositories. I installed the java-plugin from the repositories, and also manually from the SUN/Java web-site. All to no avail.

Flash and other plugins work, Java does not (as I can see from about : plugins).

Where do I have to install the Java plugin to make that work? I prefer to run FF 3 out of my own directory (after unpacking the download from the Mozilla web-site and running the executable in there directly), since it seems to work better for me than the FF 3 from the repositories...

Thank you very much...

---

### Post by tbraun on 2008-06-27
Bump?

---

### Post by jamesstansell on 2008-06-27
It sounds like the java plugin symbolic link from the mozilla system directory isn't being found.  That surprises me a little for the packaged FF, but not for the user install that you did.

You most likely want to create a symbolic link from ~/.mozilla/plugins/ to the libjavaplugin_oji.so file.

Does that make sense to you?

---

### Post by zoiks on 2008-07-05
I'm having what appears to be the same problem as tbraun's.

I'm using Firefox 3 and Ubuntu 8.04.

My wife uses [www.ritzpix.com](www.ritzpix.com) to upload pictures for printing. If anyone is able to use that site (requires that you create a login) with FF3, then I'd be curious how to do it.

My wife is getting frustrated with me because I keep telling her I'll have it fixed "soon" but I'm having no luck at all.

The applet used at the ritzpix.com site is a file chooser for multiple files to upload. It used to work fine under ubuntu 7.10, using firefox 2. Now I can't get it to work to save my life. It just shows a gray box where the file uploader used to be.

I've tried installing various java-related packages and I can't find this file libjavaplugin_oji.so of which you speak. What's more, there's no plugins directory in ~/.mozilla, though I could create one if needed. (Seems more likely I'd want to put it in /usr/lib/mozilla/plugins/).

Any help would be appreciated! As I said, it worked fine before, I just can't get it to work anymore.

---

### Post by jamesstansell on 2008-07-05
zoiks,

This is the first thing for you to try.  If it doesn't work then we might need to zero in on the 'grey box' effect you're seeing.
```
$ sudo apt-get remove icedtea-gcjwebplugin
$ sudo apt-get install sun-java6-plugin
$ sudo update-java-alternatives -s java-6-sun

```

If that doesn't work then please see if java shows up in about:plugins in firefox (and also if shows up more than once)

-james.

---

### Post by zoiks on 2008-07-05
> **jamesstansell said:**
> zoiks,

This is the first thing for you to try.  If it doesn't work then we might need to zero in on the 'grey box' effect you're seeing.
```
$ sudo apt-get remove icedtea-gcjwebplugin
$ sudo apt-get install sun-java6-plugin
$ sudo update-java-alternatives -s java-6-sun

```

If that doesn't work then please see if java shows up in about:plugins in firefox (and also if shows up more than once)

-james.

Thanks for the help.

OK at the second line I get:

```
~$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
```

So, no luck so far.

---

### Post by zoiks on 2008-07-05
Oh, and I looked at about:plugins in Firefox, no mention of java at all.

---

### Post by jamesstansell on 2008-07-06
> **zoiks said:**
> 
Package sun-java6-plugin is not available, but is referred to by another package.


I think this means you need to add the multiverse repository.  Just ask if you need an explanation for how to do that.  The wiki page I used to refer to doesn't have it anymore.

---

### Post by zoiks on 2008-07-06
> **jamesstansell said:**
> I think this means you need to add the multiverse repository.  Just ask if you need an explanation for how to do that.  The wiki page I used to refer to doesn't have it anymore.

I believe I have the multiverse repositories:

```
~$ grep -v "#" /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse


deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://archive.ubuntulinux.jp/ubuntu-ja hardy/

```

I've changed the repository list very little, only added the one for the japanese input method stuff.

Any other suggestions?

---

### Post by jamesstansell on 2008-07-07
> **zoiks said:**
> I believe I have the multiverse repositories:
...

Any other suggestions?

It certainly looks like you do.  I assume you've done an apt-get update recently.  What does this command show?
```
$ apt-cache policy sun-java6-plugin
```

It should be something like

  Version table:
     6-06-0ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages

---

### Post by zoiks on 2008-07-07
> **jamesstansell said:**
> It certainly looks like you do.  I assume you've done an apt-get update recently.  What does this command show?
```
$ apt-cache policy sun-java6-plugin
```

It should be something like

  Version table:
     6-06-0ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages

This is what I get:

```
~$ sudo apt-cache policy sun-java6-plugin
sun-java6-plugin:
  Installed: (none)
  Candidate: (none)
  Version table:
```

The version table just shows blank, as above.

Yes, I have done an apt-get update. I do that frequently. Thanks for your continued help, BTW.

---

### Post by jamesstansell on 2008-07-07
Very strange.  Are you running with 64bits, by chance?  There is no sun-java6-plugin for that architecture.

---

### Post by zoiks on 2008-07-07
I'm running the AMD64 version. (My CPU is an Intel T9300 dual core 2.5GHz, 64 bit, laptop.) Am I running the wrong version? Should I be running 32-bit???

---

### Post by zoiks on 2008-07-08
Is this bad? Would I need to change to a 32 bit kernel just to get java working for my wife? (I could mostly care less, but my wife uses it for the uploader for ritzpix.com so she can go pick up the pictures later.)

---

### Post by jamesstansell on 2008-07-08
Check out the sticky in the 64-bit users forum.  There seem be various ways to 'add' 32bit apps to your 64-bit system, but they might not be as seamless as you like.

In general beside the issue with Java, you could have issues with Flash and other multi-media things.

My laptop _could_ run 64-bits, but I haven't done it.  Just haven't seen the need so far.

---

### Post by zoiks on 2008-07-08
> **jamesstansell said:**
> Check out the sticky in the 64-bit users forum.  There seem be various ways to 'add' 32bit apps to your 64-bit system, but they might not be as seamless as you like.

In general beside the issue with Java, you could have issues with Flash and other multi-media things.

My laptop _could_ run 64-bits, but I haven't done it.  Just haven't seen the need so far.

Thanks, jamesstansell...

It looks like that's the problem. I had no idea that 64-bit ubuntu had so many problems with some packages. In fact, it explains some quirky issues I've had with adobe flash as well.

Oh well I guess I'll try to investigate ways I can get java working on my system. We'll see.

Thanks for the help.

---

