---
title: "Firefox 26?"
date: 2013-12-11
forum: General Help
---

### Post by sasafrass452 on 2013-12-11
I noticed that Firefox 26 was released yesterday.... How soon can I expect to see it in the updates? Thanx.

---

### Post by vasa1 on 2013-12-11
> **sasafrass452 said:**
> I noticed that Firefox 26 was released yesterday.... How soon can I expect to see it in the updates? Thanx.
Soon :) How soon exactly isn't clear. Plus Ubuntu has a system of [s]throttling[/s] phasing updates so that not everyone gets them at the same time. This is a recently introduced precaution to minimize potential problems. If I find the link to that announcement, I'll post it here.

Here's a related article: [http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04)

And [http://www.murraytwins.com/blog/?p=127](http://www.murraytwins.com/blog/?p=127)

---

### Post by philinux on 2013-12-11
It's in the pipeline now. [http://www.ubuntuupdates.org/package_logs?utf8=%E2%9C%93&head_only=true&commit=Filter&noppa=0&vals=saucy&type=dists&levels](http://www.ubuntuupdates.org/package_logs?utf8=%E2%9C%93&head_only=true&commit=Filter&noppa=0&vals=saucy&type=dists&levels)[backports]=1&levels[proposed]=1&levels[security]=1&levels[base]=1&levels[updates]=1

As vasa said because of the phased updates not everyone will get it today. If you update via synaptic or terminal it's there now.
```
apt-cache policy firefox
firefox:
  Installed: 25.0.1+build1-0ubuntu0.13.10.1
  Candidate: 26.0+build2-0ubuntu0.13.10.2
```

[edit] Just checked update manager and I've got it. I must be in the first 10% maybe.

---

### Post by vasa1 on 2013-12-11
> **philinux said:**
> ... because of the phased updates not everyone will get it today. If you update via synaptic or terminal it's there now.
...
That's what I gathered as well. This phasing will impact only those who use the update manager. If you use synaptic or apt-get, there's no phasing. But the blog I linked to describes a way to use the update manager and bypass phasing:>  One can opt out of the Phased Update process by adding ‘Update-Manager::Never-Include-Phased-Updates “True”;’ to the configuration file “/etc/apt/apt.conf”.I haven't looked into that.

---

### Post by sasafrass452 on 2013-12-11
Thanx for the responses! I just installed synaptic & updated from there :)

---

