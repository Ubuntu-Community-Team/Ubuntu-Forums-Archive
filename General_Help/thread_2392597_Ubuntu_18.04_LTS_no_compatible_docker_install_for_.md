---
title: "Ubuntu 18.04 LTS no compatible docker install for Kubernetes and Rancher!"
date: 2018-05-23
forum: General Help
---

### Post by lucevers on 2018-05-23
Rancher supported docker versions:1.12.6
1.13.1
17.03.2
Ubuntu 18.04 LTS docker versions: (snap or [docker.io]("http://docker.io/"))
docker 17.06.2-ce

It's important as Rancher partner to follow the right docker versions!
Kubernetes is not compatible with the new Ubuntu version, is it possible to change the docker version for snap (or apt) installations?

---

### Post by Selmer79 on 2018-05-24
Yep, this is currently a "no-go" case for upgrading our 16.04 LTS to 18.04 LTS at this time.
While there *are *workarounds, in a production environment we really don't want to rely on such. It leads to a lot of extra work when maintaining the servers.

---

### Post by deadflowr on 2018-05-24
> is it possible to change the docker version for snap 
current docker snaps
```
snap info docker
name:      docker
summary:   The docker app deployment mechanism
publisher: docker-inc
contact:   snappy-devel@lists.ubuntu.com
license:   Apache-2.0
description: |
  Docker for snappy.
  
  This snap allows you to use the full capabilities of docker on snappy.
  
  In order to use 'docker build', 'docker save' and 'docker load', you need to
  place your dockerfile within $HOME. All files that you want docker to access
  to must be within this path.
  
  You may also use the 'docker-privilege' command to allow you to use 'docker
  run --privileged'. Because docker is unencumbered on snappy, it is recommended
  that you follow the Docker project's recommendations for using docker
  securely.
snap-id: sLCsFAO8PKM5Z0fAKNszUOX0YASjQfeZ
channels:                             
  stable:          17.06.2-ce   (179) 43MB -
  candidate:       17.06.2-ce   (179) 43MB -
  beta:            17.09.1-ce   (232) 44MB -
  edge:            17.03.1-ce-1 (248) 38MB -
  17.03/stable:    17.03.2-ce-1 (159) 42MB -
  17.03/candidate: 17.03.2-ce-1 (159) 42MB -
  17.03/beta:      &#8593;                       
  17.03/edge:      17.03.2-ce-1 (159) 42MB -
  17.06/stable:    17.06.2-ce   (179) 43MB -
  17.06/candidate: 17.06.2-ce   (179) 43MB -
  17.06/beta:      &#8593;                       
  17.06/edge:      17.06.2-ce-1 (237) 44MB -
  17.09/stable:    &#8211;                       
  17.09/candidate: 17.09.1-ce   (232) 44MB -
  17.09/beta:      17.09.1-ce   (232) 44MB -
  17.09/edge:      17.09.1-ce   (232) 44MB -
```

So, yes, you can change docker installed snap versions.
```
snap help
```

I'm guessing you want the 17.03 stable version?
try
```
sudo snap install docker --channel=17.03/stable
```
Maybe check out dockers snap page:
[https://snapcraft.io/docker]("https://snapcraft.io/docker")


Or maybe I'm lost as to what you want.
Hope it helps

---

### Post by lucevers on 2018-05-25
Thanks for info, but it should be better to follow the Kubernetes docker version!
"snap install docker" and you are ready to install kubernetes .

---

### Post by lucevers on 2018-06-09
For info
  snap is unusable for installing rke kubernetes:   
  
_Additional info:_ 
  [https://forum.snapcraft.io/t/snap-docker-and-rke-kubernetes/5845](https://forum.snapcraft.io/t/snap-docker-and-rke-kubernetes/5845)

---

### Post by ablaauw on 2018-06-22
The required Docker versions for K8s use isn't Rancher's fault. With the advent and subsequent release of Rancher 2 this still remains a K8s requirement issue.
Rancher 1.6.18 works flawless with Bionics' default docker.io install; it's 17.12-ce. So time to upgrade your Rancher instance IMHO. I know i'm going that route.
Once K8s plays catch-up with the newer Docker versions, let's say... 17-12-ce ;) you can run Rancher 1.6.18 and Rancher 2.1.x on the same Host/OS setup.
Support for Rancer 1.6.x will continue until ~Q4 next year; all other versions of Rancher have been and are deprecated. Upgrade. Upgrade. Upgrade.

---

### Post by mayconfsbrito on 2018-09-11
It's possible to install docker 17.03 in Ubuntu 18.04 (Bionic) by binary package. I've created an ansible role to do this, you can access by this link:


[https://galaxy.ansible.com/mayconfsbrito/ansible_docker_bin](https://galaxy.ansible.com/mayconfsbrito/ansible_docker_bin)


Anyway, I will post here the task of this role to guide you in this process, because I needed to configure some steps (like storage driver, docker group) that aren't explicit in the documentation.
[https://github.com/mayconfsbrito/ansible-docker-bin/blob/master/tasks/main.yml](https://github.com/mayconfsbrito/ansible-docker-bin/blob/master/tasks/main.yml)


I used the documentation below:


Install from binary:
[https://docs.docker.com/v17.09/engine/installation/linux/docker-ce/binaries/#install-static-binaries](https://docs.docker.com/v17.09/engine/installation/linux/docker-ce/binaries/#install-static-binaries)


Post install:
[https://docs.docker.com/install/linux/linux-postinstall/](https://docs.docker.com/install/linux/linux-postinstall/)

---

