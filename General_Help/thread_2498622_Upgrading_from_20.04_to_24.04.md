---
title: "Upgrading from 20.04 to 24.04"
date: 2024-06-21
forum: General Help
---

### Post by sniper8752 on 2024-06-21
Is there an easy way to do this in-place update? I tried the following, but it doesn't work:
`sudo do-release-upgrade
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.

---

### Post by ne29914 on 2024-06-21
No easy way. New install; or upgrade to 22.04, then to 23.10 and then upgrade to 24.04. Just been there myself.

---

### Post by sniper8752 on 2024-06-21
> **ne29914 said:**
> No easy way. New install; or upgrade to 22.04, then to 23.10 and then upgrade to 24.04. Just been there myself.

Trying to go to 22.04 with the following, but it still fails:
`sudo do-release-upgrade 
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading`

---

### Post by Tadaen_Sylvermane on 2024-06-21
Did you do what it said?

```
sudo apt update && sudo apt upgrade && sudo apt full-upgrade
```

Then run the release upgrade?

---

### Post by Bashing-om on 2024-06-21
sniper8752 Hello

24.04 remains "in Development" until the .1 release;
thus:
LTS to LTS upgrades aren't enabled until 24.04.1 - August 24-. -> However, you can still do-release-upgrade, if your mirror is up-to-date and your 22.04 release is fully updated.
```

sudo do-release-upgrade -d

```
Note the use of the -d switch for "development".

[INDENT]good preparations bring good luck
[/INDENT]

---

### Post by sniper8752 on 2024-06-22
The exact version I am running is 20.04.6 LTS.
In release-upgrades, Prompt is set to "lts".
When I run your command, it returns "There is no development version of an LTS available".  Do I want that set to normal?

---

### Post by Dennis N on 2024-06-22
> **sniper8752 said:**
> The exact version I am running is 20.04.6 LTS.
In release-upgrades, Prompt is set to "lts".
When I run your command, it returns "There is no development version of an LTS available".  Do I want that set to normal?
Don't use the -d option. It only applies if you run the command from the lastest release, currently 24.04, and only upgrades to a development release.

The upgrade path is open. You will be offered to upgrade to 22.04 if you have release notifications set to LTS.
After that, you need to set the notifications to "any new release". You will be offered 23.10.
Then from 23.10 "any new release" will offer 24.04.

As always with upgrading, things can go wrong. So be prepared with backup of important things.

I've done the last step (23.10 to 24.04) a number of times without any problem.

---

### Post by Impavidus on 2024-06-22
You cannot run a release upgrade (like 20.04 to 22.04) before you've installed all available upgrades for your current system. That's suggested in post #4. If this fails, something is messed up in your package manager and you have to fix that before attempting a release upgrade. You can only upgrade to 22.04. The upgrade path from 22.04 to 24.04 isn't open yet, but is available for testing purposes.

Alternatively, wipe your harddrive and install 24.04 from scratch. Takes less time.

---

