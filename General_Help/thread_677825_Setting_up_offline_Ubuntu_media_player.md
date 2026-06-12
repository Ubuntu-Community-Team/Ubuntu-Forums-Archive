---
title: "Setting up offline Ubuntu media player"
date: 2008-01-25
forum: General Help
---

### Post by acidd_uk on 2008-01-25
Hi,

I have a bit of a problem - I have a PC that I have set up with the lovely Ubuntu 7.10. It boots to X, all is well. However, the intended use of this PC is as a media player, hooked up to my TV and home cinema whatchamajigger. It will play mp3s splendidly and <insert other general praise of Ubuntu here>.

However, by default it wont play DVDs or divx, xvid etc etc, which I have quite a collection of. I understand that I need the restricted packages as detailed at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) . Specifically I need the 'ubuntu-restricted-extras'. However, I have no internet connection at home, so I need to download all the relevant packages manually (at work :-/).

I tried getting synaptic to generate a package download script as described here: [https://help.ubuntu.com/community/InstallingSoftware#head-14060f8896fc0efa378412ca379a89c8c332da14](https://help.ubuntu.com/community/InstallingSoftware#head-14060f8896fc0efa378412ca379a89c8c332da14) but it seems that because my PC has never seen the restricted repo, it doesn't know anything about it, or what packages it contains. So synaptic refuses to accept that ubuntu-restricted-extras is a package and obviously doesn't know anything about its dependancies either.

Now, in the absolute worst case, I could go to [http://packages.ubuntu.com/gutsy/metapackages/ubuntu-restricted-extras](http://packages.ubuntu.com/gutsy/metapackages/ubuntu-restricted-extras) and download all the packages manually, but some of them have a lot of dependencies and I'm fairly sure a lot of them are installed already on a 7.10 CD install (eg libc...).

If you've got this far, then you've probably already worked out what I'm going to ask, but in case you haven't, here it is:

Does anyone (have | know of | could make me) a list of all the packages & sub dependencies that I need (preferably excluding those installed as part of a default 7.10) or a windows or linux script to get them or an archive containing said packages? It seems like an obvious thing that maybe other people have requested in the past, but I can't see any threads on the same subject.

Obviously I am working on getting an internet connection at home (curse you British Telecom), but it's not going to happen any time soon :(.

Thanks for your kind help!

- Tom

---

