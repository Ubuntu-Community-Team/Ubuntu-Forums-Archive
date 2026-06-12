---
title: "Getting an error E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2017-09-21
forum: General Help
---

### Post by ninjagod on 2017-09-21
So I run this command

```
[COLOR=#008000]dylan@dylan-desktop[/COLOR][COLOR=#696969]:[/COLOR][COLOR=#0000ff]~/gitian-builder[/COLOR][COLOR=#696969]$ sudo bin/make-base-vm -precise --arch amd64[/COLOR]
```[COLOR=#808080]

[/COLOR]It runs for about 5 minutes and gets around halfway through the build but then returns this error,

```
[COLOR=#696969]Errors were encountered whilst processing:
  [/COLOR][COLOR=#696969]sudo[/COLOR][COLOR=#696969]
Extracting templates from packages: 100%
W: --force-yes is deprecated, use one of the options starting with --[/COLOR][COLOR=#696969]allow[/COLOR][COLOR=#696969] instead.
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/COLOR]
```

Does anyone know the solution to the problem? Or could someone please help me troubleshoot it? 
Thanks

---

### Post by ian-weisser on 2017-09-21
dpkg error code (1) simply means: "Something clearly didn't work, but not dpkg's fault"

Troubleshooting starts with wherever you got that bin/make-base-vm command from.
A bit more information about the steps you took before that command, and the instructions you followed, would be helpful.

---

### Post by ninjagod on 2017-09-21
I was just trying to follow this video [https://www.youtube.com/watch?v=YF3oE5uIP64](https://www.youtube.com/watch?v=YF3oE5uIP64)

You can skip to the 01:30 minute mark.

I downloaded all the dependencies in the description and gitian-builder but he gives no clear instructions.

Also, in the video I realise that he used ```
--precise
``` but, when I try to use ```
--precise
``` I get this error;

```
unrecognized option: --precise
```

so instead I use

```
sudo bin/make-base-vm -precise --arch amd64
```

Note: I only used one dash instead of two

which returns the error:

```
[COLOR=#696969]Errors were encountered whilst processing:
  [/COLOR][COLOR=#696969]sudo[/COLOR][COLOR=#696969]
Extracting templates from packages: 100%
W: --force-yes is deprecated, use one of the options starting with --[/COLOR][COLOR=#696969]allow[/COLOR][COLOR=#696969] instead.
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/COLOR]
```
Thanks

---

### Post by ian-weisser on 2017-09-21
'Precise' is Ubuntu 12.04, which is EOL, no longer supported, and those software repositories have been withdrawn.
Hint: Try the release name of *your *version of Ubuntu instead.

The number of dashes matters. Really matters. Copy them carefully.

Random old YouTube videos are a poor learning tool. This method of learning does not provide you the breadth of knowledge that you need to maintain and support your system over the long term. You may succeed at building your cryptocurrency tool, but the first time it breaks (it will!) you won't have the skills to diagnose or fix it.

---

### Post by ninjagod on 2017-09-21
Ok thanks. I will try to learn more! 

So to fix the problem, should I just remove all the dependencies and find the newer versions of them?
Also, what command should I use instead of --precise?

I have tried --zesty and --xenial but neither of them work. Btw I am using Ubuntu 17.04.

---

### Post by ian-weisser on 2017-09-21
You must determine of your approach will work with 17.04 at all.
That means looking carefully at your 'bin/make-base-vm' script to determine which versions of Ubuntu it's compatible with.

---

### Post by ninjagod on 2017-09-21
[COLOR=#000000]So I looked at the emacs of the bin/make-base-vm and this is what it says at the top[/COLOR]
[COLOR=#000000]
```
[COLOR=#ff0000]#!/bin/[/COLOR][COLOR=#ee82ee]sh[/COLOR]
[COLOR=#0000ff]set[/COLOR] -e

[COLOR=#a52a2a]DISTRO[/COLOR]=ubuntu
[COLOR=#a52a2a]SUITE[/COLOR]=xenial
[COLOR=#a52a2a]ARCH[/COLOR]=amd64
[COLOR=#a52a2a]MIRROR_BASE[/COLOR]=http://${[COLOR=#a52a2a]MIRROR_HOST[/COLOR]:-127.0.0.1}:3142
[COLOR=#a52a2a]LXC[/COLOR]=0
[COLOR=#a52a2a]VBOX[/COLOR]=0
```
[/COLOR]
[COLOR=#000000]Does this mean that it is now compatible with xenial?[/COLOR]

---

### Post by ninjagod on 2017-09-21
[COLOR=#000000][COLOR=#000000]So I looked at the emacs of the bin/make-base-vm and this is what it says at the top[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]
```
[COLOR=#ff0000]#!/bin/[/COLOR][COLOR=#ee82ee]sh[/COLOR]
[COLOR=#0000ff]set[/COLOR] -e

[COLOR=#a52a2a]DISTRO[/COLOR]=ubuntu
[COLOR=#a52a2a]SUITE[/COLOR]=xenial
[COLOR=#a52a2a]ARCH[/COLOR]=amd64
[COLOR=#a52a2a]MIRROR_BASE[/COLOR]=http://${[COLOR=#a52a2a]MIRROR_HOST[/COLOR]:-127.0.0.1}:3142
[COLOR=#a52a2a]LXC[/COLOR]=0
[COLOR=#a52a2a]VBOX[/COLOR]=0
```
[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Does this mean that it is now compatible with xenial?[/COLOR][/COLOR]

---

