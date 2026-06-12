---
title: "Unable to remove nor reinstall docker-ce; Both apt and dpkg hang without error in CLI"
date: 2020-12-22
forum: General Help
---

### Post by kenzillla on 2020-12-22
I initially tried to reinstall the docker-ce package when its service was not starting successfully but reinstall would hang at 20% progress. When that wouldn't work I attempted to remove it, and then purging it as well.

I've also tried a handful of methods to try and remedy this including these commands without success
```
apt -f -install 
sudo dpkg --configure -a 
sudo dpkg -i /var/cache/apt/archives/*.deb
sudo dpkg -r --force-depends docker-ce:amd64
```

And running ```
ps -Af
``` during just shows two dpkg processes running under root (that I have left for hours)

Just tried reinstall and removal through Synaptic Package Manager knowing it likely wouldn't be any different, and yeah, no dice.

Is there a way to reinstall or remove a package that I haven't tried? How would I go about finding out what is at the root of this problem? As far as I can tell, it's the only package doing this; everything else functions like normal.

Thanks,
Ken

dpkg: [dpkg.log]("https://gist.github.com/KTheMan/e9c28303dd6565f9c30dd6bcd8c9f855")
apt: [history.log]("https://gist.github.com/KTheMan/77bebe7da3b5c6f150a3b4ea55dd2e91"), [term.log]("https://gist.github.com/KTheMan/e10eb34053b4682626b59f4b063b715d")

---

