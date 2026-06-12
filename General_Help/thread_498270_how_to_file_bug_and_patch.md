---
title: "how to file bug and patch?"
date: 2007-07-11
forum: General Help
---

### Post by jblanca_upv on 2007-07-11
Hi:
I'm not new to ubuntu, I'm a long time debian/ubuntu user, but this is my first post in the forum.
I have found a bug and a patch that works for me but I don't know how to proceed.
The bug is in the package nut. When you try to use the driver bcmxcp for the ups UPS HP R3000 XR you get a:
Could not communicate with the ups
Driver failed to start (exit status=1)

I have googled and found the [solution]("http://www.mail-archive.com/nut-upsuser%40lists.alioth.debian.org/msg01102.html")
I have applied the patch in my installation and worked just fine.

This is how I did it:
apt-get source nut
mkdir tmp
cd tmp
cp -a ../nut-2.0.5 .
cp -a ../nut-2.0.5 nut-2.0.5.orig
cp /home/jose/nut/bcmxcp.patch nut-2.0.5/
cd nut-2.0.5
patch -p1 < bcmxcp.patch
rm bcmxcp.patch
cd ..
diff -Nru nut-2.0.5.orig nut-2.0.5 > patch-nut-bcmxcp
dpatch patch-template -p "01_nut-bcmxcp" "patch-nut-bcmxcp it solves the bcmxcp bug in nut 2.0.5" < patch-nut-bcmxcp > 01_nut-bcmxcp.dpatch
echo 01_nut-bcmxcp.dpatch > 00list
mkdir ../nut-2.0.5/debian/patches
cp 00list 01_nut-bcmxcp.dpatch ../nut-2.0.5/debian/patches/
sudo debuild -i -us -uc -b -d
dpkg -i nut_2.0.5-1_amd64.deb

Now nut is working ok.
I would like to file a bug with the patch, but I don't know what's the best way to do it. It's the first time that I rebuild a deb and I don't know anything about policies and package building. But I would like to be as usefull as possible.

My initial idea was to file the bug with the original patch, maybe that's just okay, is it?

---

### Post by yopnono on 2007-07-11
[https://launchpad.net/](https://launchpad.net/) maybe

---

### Post by Hendrixski on 2007-07-11
yup launchpad would be the place to file bugs and patches... and to search if the bug already exists and if anyone is already working on a fix or needs to test a patch.

If you want to fix the package, then check if it has a patch system (in your case dpatch, right? but there's a few out there) and add the patch to it then send the package to REVU so that it can be reviewed.

hop onto IRC channel #ubuntu-motu for that and you'll get reviewed within seconds of asking and your patch may make it through... or it may get a tweak or two.


:-) Welcome!  We're grateful for your contributions.

---

### Post by jblanca_upv on 2007-07-12
Thanks for the reply, I have file the patch.
I didn't used irc before, maybe later I'll give it a chance.

---

