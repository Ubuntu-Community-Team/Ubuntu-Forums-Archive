---
title: "some update changed my files if not default"
date: 2020-03-24
forum: General Help
---

### Post by trpted on 2020-03-24
I use /usr/bin/update-manager to check and install updates.

If a file was changed from the default I used to be asked at least: Keep existing File (wording was, keep your currently-installed version), compare (wording was, show the differences between the versions), overwrite with defaults (wording was, install the package maintainer's version).

Now it seems to be that it tries to pop up a new window waits a certain amount of time. Since I can't see the contents of the new window, it times out and goes to overwrite with defaults.

Any ideas of how to make it ask me again without timing out and going to overwrite with defaults?

OR should I update via command line only, instead of via a GUI? And if so how do I do that?

Please and thank you

---

### Post by guiverc on 2020-03-24
You haven't mentioned which release you are talking about, however I know the prompt you are referring it to (and see it on occasion, but can't recall that last time I did on ths box I'm typing on right now), but I'm not aware of any prompts that timeout & accept a default answer with regards upgrades.  However I only upgrade via terminal/command.

The command I use is actually two, ie. 

```
sudo apt update
```

which will upgrade my software lists, ie. letting my box know what software package versions are available, and thus what upgrades can be downloaded, followed by

```
sudo apt full-upgrade
```

which actually performs the upgrade of packages. If upgrades are found, I'll be asked to accept/install them, this waits forever (usually 4-5 hours later when I perform it again in another window & I get get a lock; it's because I never answered the question & it's still waiting...).

The two commands can be combined into one via

```
sudo apt upgrade && sudo apt full-upgrade
```

(a ";" could be used instead of the "&&", but "&&" lets the second command execute only if there were no errors on the first)

---

### Post by trpted on 2020-03-24
> **guiverc said:**
> 
You haven't mentioned which release you are talking about.


Sorry. It is the last of the LTS's that support 32bit. Right now on that is 18.04.4.

> **guiverc said:**
> 
However I know the prompt you are referring it to (and see it on occasion, but can't recall that last time I did on ths box I'm typing on right now).


Good to hear/read. :)

> **guiverc said:**
> 
but I'm not aware of any prompts that timeout & accept a default answer with regards upgrades.



I remember seeing something about **unattended-upgrades**. It is installed, should I un-install that?

> **guiverc said:**
> 
However I only upgrade via terminal/command.

The command I use is actually two, ie. 

```
sudo apt update
```

which will upgrade my software lists, ie. letting my box know what software package versions are available, and thus what upgrades can be downloaded, followed by

```
sudo apt full-upgrade
```

which actually performs the upgrade of packages. If upgrades are found, I'll be asked to accept/install them, this waits forever (usually 4-5 hours later when I perform it again in another window & I get get a lock; it's because I never answered the question & it's still waiting...).

The two commands can be combined into one via

```
sudo apt upgrade && sudo apt full-upgrade
```

(a ";" could be used instead of the "&&", but "&&" lets the second command execute only if there were no errors on the first)



Thank you for that info. I may consider that.

---

