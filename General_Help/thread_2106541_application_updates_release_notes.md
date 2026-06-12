---
title: "application updates release notes"
date: 2013-01-19
forum: General Help
---

### Post by nanofa on 2013-01-19
Hi,

I have seen that I have got three updates of an application ready to update/upgrade. The fact is that I like to do it from de console.

apt-get update
apt-get upgrade

But I would like to see the release notes / change notes for the upgrade. When you use the unity version of software updater there is a tab called changes that shows what are the fixes/upgrades/... of the new release.

How can I see that information from the terminal?

Thank you very much
BTW Ubuntu 12.10

---

### Post by ibjsb4 on 2013-01-19
This what you looking for?

[http://www.ubuntuupdates.org/packages/latest_logs?utf8=%E2%9C%93&dist=quantal&commit=Filter&noppa=2&levels]("http://www.ubuntuupdates.org/packages/latest_logs?utf8=%E2%9C%93&dist=quantal&commit=Filter&noppa=2&levels")

---

### Post by mcduck on 2013-01-19
sudo apt-get changelog *packagename*

...of course you'll have to repeat this manually for each package you want to check. On the other hand, it will display the changes for previous versions as well which can sometimes be quite useful.

---

