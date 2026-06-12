---
title: "updater fails, with error; &quot;package operation failed&quot;"
date: 2018-04-16
forum: General Help
---

### Post by james2b on 2018-04-16
I have Ubuntu 16.04.3 installed and boots up okay except the updater fails, with error; "package operation failed". So how do I remove and re-install the updater to fix this issue?

---

### Post by cruzer001 on 2018-04-16
Please post the output of:

```
sudo apt update
```

If that runs without errors:

```
sudo apt full-upgrade
```

---

### Post by james2b on 2018-04-17
Or is it; sudo apt-get update ? What if I try to remove and then install again the update manager package, such as with; "sudo apt-get remove dpkg", and then in place of remove put install. Is that going to work? Okay I will try to run these soon, but what will that full-upgrade do, install the newer version? Okay thanks.

---

### Post by Yellow Pasque on 2018-04-17
> **james2b said:**
> Or is it; sudo apt-get update?

[https://askubuntu.com/questions/445384/what-is-the-difference-between-apt-and-apt-get](https://askubuntu.com/questions/445384/what-is-the-difference-between-apt-and-apt-get)

> What if I try to remove and then install again the update manager package, such as with; "sudo apt-get remove dpkg", and then in place of remove put install. Is that going to work?

It sounds like a really bad idea to me. Try the commands provided and see if you can get a more specific error message. "package operation failed" is very vague.

---

### Post by Impavidus on 2018-04-17
"package operation failed" just means there was some error installing or removing some package. Now it wants you to tell it how to solve the problem. Reinstalling the package manager won't help. And uninstalling the package manager sounds like a really bad idea, because you need the package manager to reinstall it.

Just run the commands provided by cruzer001 and post the output. That should tell us what's going on.

Edit:
```
sudo apt full-upgrade
```will attempt to install all available upgrades for your release of Ubuntu. It will not attempt to upgrade to the next release.

---

### Post by james2b on 2018-04-17
Okay this issue is now fixed by running those commands found at the AptGet How to at; help.ubuntu.com/community/AptGet/Howto. When I ran the apt-get update it ran through with no errors. And with apt-get upgrade it gave error code 1 until it finally got solved. When it was not working and returned that error, the Software Updater only showed Ubuntu base 15kb. So thanks for the help to all.

---

