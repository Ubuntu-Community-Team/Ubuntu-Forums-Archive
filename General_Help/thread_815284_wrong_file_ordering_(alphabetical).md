---
title: "wrong file ordering (alphabetical)"
date: 2008-06-01
forum: General Help
---

### Post by Hiperi0n on 2008-06-01
Hello. I upgraded some packages from the standard update, some of them were language packs. Now, files in nautilus are not correctly ordered, uppercase letters seem to have priority.

For example, instead of seeing:

documents Pictures Videos work

I now see:

Pictures Videos documents work


It is getting very annoying and I can't manage to solve this problem, I have rebooted, tried to update again... with no results. In terminal, with the ls command the ordering is correct, this seems to be a nautilus or gnome language pack related error.

Thank you.

---

### Post by mike2357 on 2008-06-01
In your Nautilus window, did you try selecting View -> Arrange Items to make sure "By Name" is selected?

Another option:  Select Edit -> Preferences -> Views and make sure the Default View setting is what you want.

---

### Post by Hiperi0n on 2008-06-01
Yes, I have tried arranging them and changing the arrangement types but arranging by name always throws the same result: uppercase letters have priority :(

---

### Post by Hiperi0n on 2008-06-01
I can't fix it. Is it possible to uninstall those last installed packages?

---

### Post by llama320 on 2008-06-01
> **Hiperi0n said:**
> I can't fix it. Is it possible to uninstall those last installed packages?

I'm not on a debian-based distro right now, so I can't give specifics about synaptic, but if you know the packages that were upgraded, you can search for those packages and either right click or look in the menues for "force version," and click on the version you had before. then just apply and you should be set.

If you just want to uninstall them, go into synaptic and right click on the package and go to "compete removal" or alternatively you can go into terminal and type
```
sudo apt-get purge package_name
```

Good Luck

---

### Post by Hiperi0n on 2008-06-01
Thanks llama320, but I don't know the names of the packages, just that they were somehow language related and told me to remove some old ones which I did. If there was a possibilitiy of uninstalling all the packages from the last update...

I guess the solution would be reinstalling ubuntu from scratch and paying more attention to warnings and so, as I have all software sources checked (unsupported, pre-released...)

Thanks for your help.

---

### Post by forestpixie on 2008-06-01
If you go to synaptic - you can get history in the file menu

---

### Post by Hiperi0n on 2008-06-01
Thank you forestpixie. However, I installed those packages from terminal using aptitude. I have opened /var/log/apt/term.log and it seems I have messed quite a lot with many things:

> [93G[ OK ]

Removing language-pack-gnome-en ...

Removing openoffice.org-help-en-gb ...

Removing openoffice.org-l10n-en-gb ...

Removing thunderbird-locale-en-gb ...

Removing language-support-en ...

Removing language-pack-en ...

(Reading database ... 122478 files and directories currently installed.)

Preparing to replace openoffice.org-calc 1:2.4.0-3ubuntu6 (using .../openoffice.org-calc_1%3a2.4.1~rc1-1ubuntu1_i386.deb) ...

Unpacking replacement openoffice.org-calc ...

perl: warning: Setting locale failed.

perl: warning: Please check that your locale settings:

	LANGUAGE = (unset),

	LC_ALL = (unset),

	LANG = "en_US.UTF-8"

    are supported and installed on your system.

perl: warning: Falling back to the standard locale ("C").

---

### Post by Hiperi0n on 2008-06-01
Do you think that forcing a reinstallation of those removed packages would solve anything? At least trying...

---

### Post by forestpixie on 2008-06-01
Not sure tbh - was it by any chance an openoffice 2.4 update - I just got a proposed update for it and it's (openoffice) broken - starts to start and that's it - if it is there is a sticky on the installation forum about it if it is.

---

### Post by Hiperi0n on 2008-06-01
Thanks a lot. That's exactly what happened to me. I tried a partial upgrade but didn't work, so I went to a terminal and did a sudo aptitude full-upgrade. I guess I didn't had to...

My fault, I shouldn't mess with those important things. Hope I can fix it.

thx :)

---

