---
title: "Ubuntu wont start after latest upgrade (ubuntu studio)"
date: 2015-08-11
forum: General Help
---

### Post by freddyfields on 2015-08-11
Hi all. About a week ago i downloaded an upgrade and prompted to restart after update. I believe when i rebooted i chose to use windows instead of reloading straight to Ubuntu. Anyways, when i tried loading ubuntu, i type in password and it comes to my homescreen with background and mouse courser,. no icons or anything. Nothing else loads. Ive repeatedly restarted and tried again.  When i log into guest account, computer starts but mozilla stalls out on most any page i start. Well, i really only tried youtube and bing but got discouraged after having to click it off and seemly stalling out.  IDK whats going on. I mean, i could try reinstalling, but rather not. Anyone have any idea whats going on? I believe im using Ubuntu Studio 13.10, might be 14 but i doubt it.

---

### Post by coffeecat on 2015-08-11
Support, not an Ubuntu, Linux & OS Chat question.

*Thread moved to **General Help**.*

I've moved this to General Help rather than the Ubuntu Studio sub-forum, as it's probably a better fit for your particular problem.

[quote=freddyfields]I believe im using Ubuntu Studio 13.10, might be 14 but i doubt it. [/quote]

If you are using Ubuntu Studio 13.10, you are using something out of support and with no more available updates. If so, it might be easier to re-install with a supported version. So that people can help and advise, please follow this procedure to post information that tells us which release you are using:

When you get to your broken desktop, press ctrl-alt-F1 to get to a virtual console. Login at the console prompt - you have to log in even if you have already logged into the graphical desktop. Now run this command:

```
cat /etc/lsb-release 
```

Copy down the four-line output and post it here.

After you have finished in the virtual console, you can return to your graphical desktop with ctrl-alt-F7, or you can shut down from the console with:

```
sudo shutdown -h now
```

---

### Post by freddyfields on 2015-08-12
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"

i didnt copy Past, i just copied down

---

