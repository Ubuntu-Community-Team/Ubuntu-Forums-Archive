---
title: "building a new home server, LTS question"
date: 2008-01-04
forum: General Help
---

### Post by jabster on 2008-01-04
Hi all.

The hard drive on my home server is dying, and I thus need to rebuild it. I am currently running the last LTS version.

I hate to install the previous ubuntu LTS, knowing there is a new version just around the corner. But I need to something now, and can't wait for that.

So, what's my best option here?
a) Install the previous LTS and then upgrade in a few months
b) Install the most recent Ubuntu, then upgrade to LTS in a few months
c) Install the current beta(?) version of the upcoming LTS, and seamlessly(?) upgrade in a few months
d) Install some other current distro

Here's what my server needs to do:
[LIST]
[*]mail server (fetchmail, procmail, spamassassin, imap, etc)
[*]samba, preferably as a pdc for the windows boxes
[*]NFS server (for my box :)  ) (file serving via nfs and samba obviously)
[*]slimserver
[*]ssh
[/LIST]

It is in a closet, so remote administration is a must. So I don't need a GUI, but if there is a really good disto with a GUI that I can access via nomachine (I hate VNC) that would be acceptable.

If not one of the ubuntu options mentioned above, can someone recommend a good distro that would be easy to use and setup. Ultimately, I'd like it to be wife-friendly for at least adding users and email accounts. Webmin does not really fall into that category.

thanks,
john

---

### Post by cheahk on 2008-01-04
I'm using the current Ubuntu 7.10 server version to do all that.  I don't use NFS but ssh/fuse instead.  The machine is an old 1.7 Mhz P4, and is basically running headless.  I don't use slimserver, but use FireFly and MediaTomb to serve media to my Soundbridge and PS3 instead.

I can't comment about a good GUI for administering user/email accounts, as I do everything on the commandline (and you can probably script that with expect if you know how to).

From what I've seen so far, upgrades seem to be pretty seamless if you don't go too far off the beaten track.  (pretty seamless from the list of apps you provided)

-K

---

### Post by markharding557 on 2008-01-04
you have to decide if you intend to upgrade or not because this choice will determine which version you use.
me?i would use 606 lts for stability and it still has about 21mths support.
gutsy server may be less stable you have to weigh up the risk

---

