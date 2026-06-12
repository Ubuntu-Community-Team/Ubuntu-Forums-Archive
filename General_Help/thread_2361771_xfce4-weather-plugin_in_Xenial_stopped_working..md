---
title: "xfce4-weather-plugin in Xenial stopped working."
date: 2017-05-20
forum: General Help
---

### Post by ajgreeny on 2017-05-20
I posted this information inn the hope that it may help others searching with the same problem.

My main system is using Xubuntu 16.04 64bit and for the past week or so the panel weather-update applet, ie xfce4-weather-plugin -0.8.6-1 has been unable to show any weather information.

A bug was posted for this yesterday (related to Mint, but same plugin version) to which I subscribed.
[https://bugs.launchpad.net/linuxmint/+bug/1692016](https://bugs.launchpad.net/linuxmint/+bug/1692016)

Further searches found that it might be worth trying a more recent version of the plugin so I have downloaded the version for Zesty 0.8.9-1 from [https://launchpad.net/ubuntu/+source/xfce4-weather-plugin/0.8.9-0ubuntu1/+build/12025316](https://launchpad.net/ubuntu/+source/xfce4-weather-plugin/0.8.9-0ubuntu1/+build/12025316) which installed without problem in Xenial using gdebi and immediately has started working as it should.

I have no idea why the 0.8.6-1 version has stopped, but I do now have a working version; I will keep an eye open on the bug and report back if any other solution is found.

---

### Post by slickymaster on 2017-05-20
The xfce4-weather-plugin package is outdated, ajgreeny. There is a new version because weather datacenter changed api: [https://bugzilla.xfce.org/show_bug.cgi?id=13527](https://bugzilla.xfce.org/show_bug.cgi?id=13527)

---

### Post by slickymaster on 2017-05-20
ajgreeny, see [https://bugs.launchpad.net/ubuntu/+source/xfce4-weather-plugin/+bug/1688056](https://bugs.launchpad.net/ubuntu/+source/xfce4-weather-plugin/+bug/1688056)

---

### Post by ajgreeny on 2017-05-20
> **slickymaster said:**
> The xfce4-weather-plugin package is outdated, ajgreeny. There is a new version because weather datacenter changed api: [https://bugzilla.xfce.org/show_bug.cgi?id=13527](https://bugzilla.xfce.org/show_bug.cgi?id=13527)
Thanks slickymaster.  A search didn't find either of those links that you've now pointed me to.

However, even after reading this link (and the next one in your following post) I am still a little confused; does it mean that the version I now have from zesty may also fail, or has the 0.8.9-1 version that I have already been patched so it will continue to work?

---

### Post by slickymaster on 2017-05-21
The patch for the 0.8.9-1 version was released on 2017-05-12

---

### Post by NTL2009 on 2017-05-22
How can I update this for my system which is still on 14.04 Xubuntu?

When I tried installing the 8.9.1 deb, I get:

"Dependency is not satisfiable: libxfce4util7 (>=4.9.0)

---

### Post by Yellow Pasque on 2017-05-23
> **NTL2009 said:**
> How can I update this for my system which is still on 14.04 Xubuntu?

When I tried installing the 8.9.1 deb, I get:
"Dependency is not satisfiable: libxfce4util7 (>=4.9.0)

Xubuntu 14.04 is no longer officially supported (support ended last month). The 0.8.9 weather package needs xfce 4.12 and Xubuntu 14.04 uses xfce 4.10

---

### Post by ajgreeny on 2017-09-19
I have just noticed that there is again a problem with this applet, though not the same problem as previously.

Now it is impossible for me to make any changes to the location displayed in the applet; searching for any new locations fails completely.

I have purged and reinstalled the applet (xfce4-weather-plugin (0.8.9-0ubuntu0.16.04.1) xenial) and also cleared the contents of ~/.cache/xfce4/weather but still no go.

Anyone got the same problem? Has the API used changed again?

I have updated the bug that I was already subscribed to for this; [https://bugs.launchpad.net/ubuntu/+source/xfce4-weather-plugin/+bug/1688056](https://bugs.launchpad.net/ubuntu/+source/xfce4-weather-plugin/+bug/1688056)

---

### Post by Yellow Pasque on 2017-09-19
I have the same issue, in Xubuntu 16.04.1. I don't see any changes to the API: [http://api.met.no/weatherapi/locationforecastlts/1.3/documentation](http://api.met.no/weatherapi/locationforecastlts/1.3/documentation)

---

### Post by ajgreeny on 2017-09-27
I note the same problem in 17.04 as well; it is basically the same version 0.8.9-0 so either this is now a deprecated app or there is just a bug in that as well as the 16.04 version.

---

