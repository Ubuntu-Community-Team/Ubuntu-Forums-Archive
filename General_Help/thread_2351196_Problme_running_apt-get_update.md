---
title: "Problme running apt-get update"
date: 2017-02-01
forum: General Help
---

### Post by satimis on 2017-02-01
Hi all,

Ubuntu 16.04

On running;
&#10219; sudo apt-get update
following warning popup

```

Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

But on /etc/apt/sources.list
I couldn't find ppa.launchpad.net

Please advise how to fix the problem

Thanks in advance

Regards
satimis

---

### Post by deadflowr on 2017-02-01
The ppa should be in the /etc/apt/sources.list.d folder.
It should be listed as it's own file.

You can delete the file or open and comment out the source entry(ies) it contains.

---

### Post by bearlake on 2017-02-01
> **satimis said:**
> Hi all,

Ubuntu 16.04

On running;
&#10219; sudo apt-get update
following warning popup

```

Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

But on /etc/apt/sources.list
I couldn't find ppa.launchpad.net

Please advise how to fix the problem

Thanks in advance

Regards
satimis

Hi,

Try looking in /etc/apt/sources.list.d

You can comment out "http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/xenial/main/binary-amd64/Packages"untill you find out what's happening with the ppa.

---

### Post by bearlake on 2017-02-01
> **deadflowr said:**
> The ppa should be in the /etc/apt/sources.list.d folder.
It should be listed as it's own file.

You can delete the file or open and comment out the source entry(ies) it contains.

beat again. :P

---

### Post by satimis on 2017-02-01
> **deadflowr said:**
> The ppa should be in the /etc/apt/sources.list.d folder.
It should be listed as it's own file.

You can delete the file or open and comment out the source entry(ies) it contains.
Hi,

&#10219; ls /etc/apt/sources.list.d/```

jonoomph-ubuntu-openshot-edge-xenial.list        thomas-schiex-ubuntu-blender-xenial.list
openshot_developers-ubuntu-ppa-xenial.list       thomas-schiex-ubuntu-blender-xenial.list.save
openshot_developers-ubuntu-ppa-xenial.list.save

```

Edit:
Deleted - jonoomph-ubuntu-openshot-edge-xenial.list

No warning popup on running sudo apt-get update

Thanks

Regards
satimis

---

### Post by deadflowr on 2017-02-01
It's the top one, for openshot-edge.
That ppa has no packages for anything beyond quantal, aka 12.10.

Luckily the openshot-developers ppa does.

So unless you haven't already, remove that ppa
you can simply delete it or use the add-apt-repository -r command
in this case
```
sudo add-apt-repository -r ppa:jonoomph/openshot-edge
```

hope it helps

---

### Post by satimis on 2017-02-02
> **deadflowr said:**
> It's the top one, for openshot-edge.
That ppa has no packages for anything beyond quantal, aka 12.10.

Luckily the openshot-developers ppa does.

So unless you haven't already, remove that ppa
you can simply delete it or use the add-apt-repository -r command
in this case
```
sudo add-apt-repository -r ppa:jonoomph/openshot-edge
```

hope it helps

Hi,

Thanks for your advice.  I have deleted the repo

Blender 2.69 works on OpenShot but not other versions above.

I'm prepared testing Kdenlive

Regards
satimis

---

