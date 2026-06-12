---
title: "About Docker"
date: 2017-07-16
forum: General Help
---

### Post by satimis on 2017-07-16
Hi all,

Just came across "Docker"

What is Docker? | Opensource.com
[https://opensource.com/resources/what-docker](https://opensource.com/resources/what-docker)

Can I test it on a VM of Oracle VirtualBox?  If NO, then I have to build a clean PC for testing Docker.

On a brief googling I found following links;

Docker for Ubuntu
[https://www.docker.com/docker-ubuntu](https://www.docker.com/docker-ubuntu)

How To Install and Use Docker on Ubuntu 16.04
[https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04)

Running Docker Machine on a Ubuntu VM from VirtualBox
[https://forums.docker.com/t/running-docker-machine-on-a-ubuntu-vm-from-virtualbox/10779](https://forums.docker.com/t/running-docker-machine-on-a-ubuntu-vm-from-virtualbox/10779)

Thanks in advance.

Regards
satimis

---

### Post by TheFu on 2017-07-17
Yes, you can run docker inside a VM.  Any Linux kernel supports "linux containers" like docker. It is not tied to hardware, so ARM CPUs or x86 or MIPS or ...   anything running the normal Linux kernel can use linux containers.

It is actually a "best practice" to run containers inside a VM.

You could have tested this already, probably. I think it takes about 15 minutes to get any dependencies for docker loaded and to setup a small, 1st test, container, by following the quick-start instruction.

---

### Post by satimis on 2017-07-17
> **TheFu said:**
> Yes, you can run docker inside a VM.  Any Linux kernel supports "linux containers" like docker. It is not tied to hardware, so ARM CPUs or x86 or MIPS or ...   anything running the normal Linux kernel can use linux containers.

It is actually a "best practice" to run containers inside a VM.

You could have tested this already, probably. I think it takes about 15 minutes to get any dependencies for docker loaded and to setup a small, 1st test, container, by following the quick-start instruction.
Hi,

Thanks for your advice.  I'll try it later.

I have registered on Docker community forum;

[https://hub.docker.com/](https://hub.docker.com/)

but unable to post.  I was allowed to type in my questions but I couldn't find the key to post them. It is a little bid strange to me.

Regards
satimis

---

### Post by satimis on 2017-07-20
Hi TheFu,

Can I install and run Docker on Ubuntu 16.04 desktop?  I have problem to configure Ubuntu 16.04 server installed on a VM.  The font on the console is very small.  Mouse pointer can't work on console screen.

Please see my posting on;
How to increase font size on console etc 
[https://ubuntuforums.org/showthread.php?t=2366656](https://ubuntuforums.org/showthread.php?t=2366656)

Thanks

Regards
satimis

---

### Post by deadflowr on 2017-07-20
There's a docker snap package you can install with relative ease.
Something something about that here:
[https://lists.ubuntu.com/archives/snapcraft/2016-October/001382.html]("https://lists.ubuntu.com/archives/snapcraft/2016-October/001382.html")
food for thought

---

### Post by satimis on 2017-07-20
> **deadflowr said:**
> There's a docker snap package you can install with relative ease.
Something something about that here:
[https://lists.ubuntu.com/archives/snapcraft/2016-October/001382.html]("https://lists.ubuntu.com/archives/snapcraft/2016-October/001382.html")
food for thought
Hi,

Thanks for your advice and link.

My problem here is unable to configure Ubuntu 16.04 server newly installed on a VM.  I'm still struggling.

I have at least >15 VMs running Ubuntu 16.04 desktop here, all without problem.  If possible I'll clone a Ubuntu 16.04 desktop for testing Docker.

Thanks

Regards
satimis

---

### Post by TheFu on 2017-07-21
Already answered.
> Any Linux kernel supports "linux containers" like docker.

A linux server is different from a desktop.  You'll need server knowledge, not point-n-click knowledge. There are many resources about that. A web search will find thousands. 

Or just get a 16.04 Server book and start from the beginning working your way through it.

Or find the Ubuntu Server Guide, but know that it doesn't explain many important details.

Or you could get the free LPI training materials.  Start with "Essentials", then Admin-1, Admin-2, Admin-3.  That should take about a year.

---

### Post by satimis on 2017-07-22
> **TheFu said:**
> Already answered.


A linux server is different from a desktop.  You'll need server knowledge, not point-n-click knowledge. There are many resources about that. A web search will find thousands. 

Or just get a 16.04 Server book and start from the beginning working your way through it.

Or find the Ubuntu Server Guide, but know that it doesn't explain many important details.

Or you could get the free LPI training materials.  Start with "Essentials", then Admin-1, Admin-2, Admin-3.  That should take about a year.
Hi,

Thanks for your advice

My Dell 25" display supporting resolution 2560x1400.  However the maximum resolution which I can set on console is only 1280x1024 with maximum font size 16.  So the console screen looks rather small.  I suppose it is its limitation.

I prefer command line operation rather than clicking around on screen.  The server (lamp, openssh, samba) is running.  I just tested remote access and admin on SSH and it worked.

I have some documentation here including;
Initial Server Setup with Ubuntu 16.04
[https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04)

Ubuntu Server Guide
[https://help.ubuntu.com/lts/serverguide/index.html](https://help.ubuntu.com/lts/serverguide/index.html)
[https://help.ubuntu.com/lts/serverguide/serverguide.pdf](https://help.ubuntu.com/lts/serverguide/serverguide.pdf)

How to administer Ubuntu Server remotely using Webmin
[http://www.havetheknowhow.com/Configure-the-server/Install-Webmin.html](http://www.havetheknowhow.com/Configure-the-server/Install-Webmin.html)

Remote Administration
[https://help.ubuntu.com/lts/serverguide/remote-administration.html](https://help.ubuntu.com/lts/serverguide/remote-administration.html)

etc.

I have no idea about the use of Docker only I know it is a container similar to virtualization.  I came across it last week.  Just for curiosity I'm trying to find out its use.

Regards
satimis

---

### Post by TheFu on 2017-07-22
Containers are NOT the same as virtualization, though it might appear so.
There are many ways that containers _can_ be used.
There are a few ways that containers _should_ be used.

In general, a container shouldn't have a full OS, shouldn't have ssh, should have only enough inside to run 1 service, nothing more.  There shouldn't be any "patching" inside a container.  When a container is out of date, usually weekly, it should be shot in the head like a zombie and rebuilt from scratch using updated versions of all the components.

Webmin - don't.  Just don't.  There are many, many, many, reasons tools like that are a bad idea, especially for someone new to Linux.

I use consoles for about 30 seconds on each new machine, then effectively never again.  I've never needed to worry about text size for a console. Not once.

ssh is the way to connect and administrate all Unix-like systems.  Don't forget that containers are administered from OUTSIDE the container by controlling the container build process.

Those links are lacking the deeper knowledge that an admin requires to be effective.  They tell you what to type, but miss the "why" which only comes from understanding nearby commands too.

---

### Post by satimis on 2017-07-22
> **TheFu said:**
> Containers are NOT the same as virtualization, though it might appear so.
There are many ways that containers _can_ be used.
There are a few ways that containers _should_ be used.

In general, a container shouldn't have a full OS, shouldn't have ssh, should have only enough inside to run 1 service, nothing more.  There shouldn't be any "patching" inside a container.  When a container is out of date, usually weekly, it should be shot in the head like a zombie and rebuilt from scratch using updated versions of all the components.

Webmin - don't.  Just don't.  There are many, many, many, reasons tools like that are a bad idea, especially for someone new to Linux.

I use consoles for about 30 seconds on each new machine, then effectively never again.  I've never needed to worry about text size for a console. Not once.

ssh is the way to connect and administrate all Unix-like systems.  Don't forget that containers are administered from OUTSIDE the container by controlling the container build process.

Those links are lacking the deeper knowledge that an admin requires to be effective.  They tell you what to type, but miss the "why" which only comes from understanding nearby commands too.
Hi TheFu,

Following the steps on;
Docker: Installation and Basic usage on Ubuntu 16.04
[https://www.howtoforge.com/tutorial/docker-installation-and-usage-on-ubuntu-16.04/](https://www.howtoforge.com/tutorial/docker-installation-and-usage-on-ubuntu-16.04/)

Now I have Docker installed on Ubuntu 16.04 server(VM) without problem

Steps performed as follows;
=====================
On Host terminal remote-connected Ubuntu 16.04 server as root

root@ub1604server00:~# apt-get install -y docker.io
Installation went through w/o problem.

root@ub1604server00:~# systemctl start docker
root@ub1604server00:~# systemctl enable docker```

Synchronizing state of docker.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install enable docker
```

root@ub1604server00:~# docker version```

Client:
 Version:      1.12.6
 API version:  1.24
 Go version:   go1.6.2
 Git commit:   78d1802
 Built:        Tue Jan 31 23:35:14 2017
 OS/Arch:      linux/amd64

Server:
 Version:      1.12.6
 API version:  1.24
 Go version:   go1.6.2
 Git commit:   78d1802
 Built:        Tue Jan 31 23:35:14 2017
 OS/Arch:      linux/amd64

```

I'll perform the "Basic Usage of Docker" listed on the document later.

I suppose I have searched sufficient documents for testing Docker as a beginner:

An Example Use Case for Docker
[https://larry-price.com/blog/2015/01/11/an-example-use-case-for-docker](https://larry-price.com/blog/2015/01/11/an-example-use-case-for-docker)

Docker for Ubuntu
[https://www.docker.com/docker-ubuntu](https://www.docker.com/docker-ubuntu)

Docker Tutorials
[https://www.digitalocean.com/community/tags/docker?type=tutorials](https://www.digitalocean.com/community/tags/docker?type=tutorials)

Docker Tutorial Series
[https://rominirani.com/docker-tutorial-series-a7e6ff90a023](https://rominirani.com/docker-tutorial-series-a7e6ff90a023)

Get Started, Part 1: Orientation and Setup
[https://docs.docker.com/get-started/](https://docs.docker.com/get-started/)

How To Install and Use Docker: Getting Started
[https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-getting-started](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-getting-started)

How To Install Docker Compose on Ubuntu 16.04
[https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-16-04)

How To Install Wordpress and PhpMyAdmin with Docker Compose on Ubuntu 14.04
[https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-and-phpmyadmin-with-docker-compose-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-and-phpmyadmin-with-docker-compose-on-ubuntu-14-04)

How To Run OpenVPN in a Docker Container on Ubuntu 14.04
[https://www.digitalocean.com/community/tutorials/how-to-run-openvpn-in-a-docker-container-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-run-openvpn-in-a-docker-container-on-ubuntu-14-04)

How to Use Docker: Creating Your First Docker Container
[https://www.vultr.com/docs/how-to-use-docker-creating-your-first-docker-container](https://www.vultr.com/docs/how-to-use-docker-creating-your-first-docker-container)

How to use Docker in a practical way (part 1 - Introduction)
[https://www.howtoforge.com/tutorial/how-to-use-docker-introduction/](https://www.howtoforge.com/tutorial/how-to-use-docker-introduction/)

Installing VirtualBox, Ubuntu, and Docker
[https://pods.iplantcollaborative.org/wiki/display/HDFDE/Installing+VirtualBox%2C+Ubuntu%2C+and+Docker](https://pods.iplantcollaborative.org/wiki/display/HDFDE/Installing+VirtualBox%2C+Ubuntu%2C+and+Docker)

Running Docker Machine on a Ubuntu VM from VirtualBox
[https://forums.docker.com/t/running-docker-machine-on-a-ubuntu-vm-from-virtualbox/10779](https://forums.docker.com/t/running-docker-machine-on-a-ubuntu-vm-from-virtualbox/10779)

What is Docker? | Opensource.com
[https://opensource.com/resources/what-docker](https://opensource.com/resources/what-docker)

What is Docker Container? Part 1: The Docker Open Source Project
[https://www.sdxcentral.com/cloud/containers/definitions/what-is-docker-container-open-source-project/](https://www.sdxcentral.com/cloud/containers/definitions/what-is-docker-container-open-source-project/)

What is Docker Container? Part 2: How Docker Containers Work
[https://www.sdxcentral.com/cloud/containers/definitions/how-does-a-docker-container-work-explanation/](https://www.sdxcentral.com/cloud/containers/definitions/how-does-a-docker-container-work-explanation/)

Why use Docker's container software when VMs do the job
[http://searchcloudapplications.techtarget.com/tip/Why-use-Dockers-container-software-when-VMs-do-the-job](http://searchcloudapplications.techtarget.com/tip/Why-use-Dockers-container-software-when-VMs-do-the-job)

Regards
satimis

---

