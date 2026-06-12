---
title: "Best way to change NVIDIA drivers"
date: 2016-04-04
forum: General Help
---

### Post by Aydos on 2016-04-04
Hello All,

I am using the graphics drivers repos and I have installed the 364.12 beta driver.

If I wanted to go to the stable driver what would be my best route?

Thanks in advance.

---

### Post by deadflowr on 2016-04-04
From a ppa?
Install the package called ppa-purge
```
sudo apt-get install ppa-purge
```
then run 
```
sudo ppa-purge ppa:name/of/ppa
```
this uninstalls all the ppa packages and reverts the system to the oringinal pre-ppa state.

---

### Post by Aydos on 2016-04-04
> **deadflowr said:**
> From a ppa?
Install the package called ppa-purge
```
sudo apt-get install ppa-purge
```
then run 
```
sudo ppa-purge ppa:name/of/ppa
```
this uninstalls all the ppa packages and reverts the system to the oringinal pre-ppa state.

hmm when I run sudo ppa-purge ppa:graphics-drivers/ppa It returns with Warning:  apt-get update failed for some reasonHowever, I am able to sudo apt-get update like normal.

---

### Post by Bucky Ball on 2016-04-04
Hmm. Don't think that's going to work. You need the full name of the nvidia ppa that you added and doubt if that called 'graphics-drivers/ppa', but I could be wrong. Look in Software and Updates> Other Software and get the exact name of the PPA, use that in the command given.

If you don't actually mention which PPA you've installed it makes it a little tough for us to tell you how to remove it.

---

### Post by grahammechanical on 2016-04-04
I do not have a graphic adapter new enough to make use of the very latest proprietary video drivers. So, I have not tested that PPA but have you tried Additional Drivers? Does the newly installed Nvidia driver appear in additional drivers?

I am not sure purging the PPA will remove the installed proprietary video driver. This link confirms the name of the ppa as ppa:graphic-drivers/ppa.

[URL="https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa"]https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa

[/URL]I am never interested in hearing that someone is seeing error messages. But I do get curious when someone tells us what the error message was. Cannot help with error messages when we do not know what the message said.

This will remove an installed Nvidia driver. But I would say that Additional Drivers is the best way.

```
sudo purge nvidia*
```

This will install the current stable proprietary video driver

```
sudo ubuntu-drivers autoinstall
```

Regards.

---

### Post by Aydos on 2016-04-04
> **Bucky Ball said:**
> Hmm. Don't think that's going to work. You need the full name of the nvidia ppa that you added and doubt if that called 'graphics-drivers/ppa', but I could be wrong. Look in Software and Updates> Other Software and get the exact name of the PPA, use that in the command given.

If you don't actually mention which PPA you've installed it makes it a little tough for us to tell you how to remove it.


I did put the ppa in the post. 

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

That is the official Nvidia/Ubuntu ppa.

---

### Post by Aydos on 2016-04-04
> **grahammechanical said:**
> I do not have a graphic adapter new enough to make use of the very latest proprietary video drivers. So, I have not tested that PPA but have you tried Additional Drivers? Does the newly installed Nvidia driver appear in additional drivers?

I am not sure purging the PPA will remove the installed proprietary video driver. This link confirms the name of the ppa as ppa:graphic-drivers/ppa.

[URL="https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa"]https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa

[/URL]I am never interested in hearing that someone is seeing error messages. But I do get curious when someone tells us what the error message was. Cannot help with error messages when we do not know what the message said.

This will remove an installed Nvidia driver. But I would say that Additional Drivers is the best way.

```
sudo purge nvidia*
```

This will install the current stable proprietary video driver

```
sudo ubuntu-drivers autoinstall
```

Regards.


I did post the error message. 

It says Verbatim "Warning: apt-get update failed for some reason" . That is copy and pasted from my terminal. 

The driver I installed and the driver I want are in the same PPA. They keep like 4-5 versions in there. It also auto black lists and everything for you. 

The drivers here are much newer than the original drivers one. 

This is the official PPA for graphics drivers that came out  when shortly after Ubuntu became the only officially supported distro for Steam. 

Knowing all of that would I still follow these directions?

---

### Post by deadflowr on 2016-04-04
Sorry.
My bad.

I forget that ppa-purge works best to revert packages back to the original version used in Ubuntu (which ever version you are using)

I do not think it works quite as well if you have nstall packages that do not exist in Ubuntu.
(In your case that would be the nvidia-364 drivers.)

I think in these cases it might be better to the remove repository command and a apt-get purge of the nvdia packages.
Something like
```
sudo apt-get purge nvidia*
```
and then run
```
sudo add-apt-repository --remove ppa:graphics-drivers/ppa
```
then run apt-get update.
and then try installing the drivers from normal Ubuntu repositories.

Note that even after you uninstall the 364 drivers, because they would be currently active, they will still be in use until you reboot.
So with that stated, I do not know if it is better to try to reinstalling the old drivers before or after a reboot.
I think either way works, but i personally like to believe it's cleaner if i reboot first, for some bizarre reason.

Hope it helps

---

### Post by Aydos on 2016-04-04
> **deadflowr said:**
> Sorry.
My bad.

I forget that ppa-purge works best to revert packages back to the original version used in Ubuntu (which ever version you are using)

I do not think it works quite as well if you have nstall packages that do not exist in Ubuntu.
(In your case that would be the nvidia-364 drivers.)

I think in these cases it might be better to the remove repository command and a apt-get purge of the nvdia packages.
Something like
```
sudo apt-get purge nvidia*
```
and then run
```
sudo add-apt-repository --remove ppa:graphics-drivers/ppa
```
then run apt-get update.
and then try installing the drivers from normal Ubuntu repositories.

Note that even after you uninstall the 364 drivers, because they would be currently active, they will still be in use until you reboot.
So with that stated, I do not know if it is better to try to reinstalling the old drivers before or after a reboot.
I think either way works, but i personally like to believe it's cleaner if i reboot first, for some bizarre reason.

Hope it helps

Yeah the rebooting before or after the uninstall was something I was not sure of as well as wondering if the purge would unblacklist the nouveau temporarily. 

I was also not sure on a purge or remove. 

Now the driver I want to try is in the same ppa so I do not want to remove the repository.

---

### Post by SeijiSensei on 2016-04-05
You didn't tell us what version of Ubuntu you're running.  If I run "apt-cache search nvidia" on 14.04, the standard repositories have 

nvidia-304
nvidia-340
nvidia-346

I'd start by removing whatever driver you have now and running
```
sudo apt-get update
sudo apt-get install nvidia-304

```
if you have a fairly old NVIDIA adapter.  Otherwise try nvidia-346.

---

