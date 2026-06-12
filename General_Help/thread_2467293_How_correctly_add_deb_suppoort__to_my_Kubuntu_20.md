---
title: "How correctly add deb suppoort  to my Kubuntu 20?"
date: 2021-09-22
forum: General Help
---

### Post by petrogromovo on 2021-09-22
Hello,
Trying to add docker to my Kubuntu 20 I run command and got error :

```
$ deb [arch=amd64] https://download.docker.com/linux/ubuntu artful stable

Command 'deb' not found, did you mean:

  command 'den' from snap den (1.2.0-0)
  command 'dub' from snap dub (1.19.0)
  command 'dep' from deb go-dep (0.5.4-3)
  command 'dex' from deb dex (0.8.0-2)
  command 'derb' from deb icu-devtools (66.1-2ubuntu2)
  command 'deb3' from deb quilt (0.65-3)
  command 'dub' from deb dub (1.19.0-1build2)
  command 'dab' from deb bsdgames (2.17-28build1)
  command 'debc' from deb devscripts (2.20.2ubuntu2)
  command 'debi' from deb devscripts (2.20.2ubuntu2)
  command 'edb' from deb edb-debugger (1.0.0-1build3)

See 'snap info <snapname>' for additional versions.

```
Seems snap is not very good way, how correctly add deb suppoort ?

Thanks!

---

### Post by ActionParsnip on 2021-09-22
The first line is not a command. It's a line for a config file. If you run:
```

sudo vi /etc/apt/sources.list.d/docker.list

```
Then add the line in the file, save the new file, exit vi and run
```

sudo apt update

```
Then you'll read the new package source.

---

### Post by ActionParsnip on 2021-09-22
Note that Ubuntu Artful is no longer supported. You should change that to the release of Ubuntu that you are using. If you are unsure then run:
```

lsb_release -c

```

---

### Post by grahammechanical on 2021-09-22
Just to be clear for anyone reading this thread and does not know: The Debian (deb) package format is still the standard package format for applications that run on Ubuntu and distributions based upon Ubuntu such as Kubuntu. There is no need to add deb support. Ubuntu is itself based upon Debian so it has deb support built in. And that will not change for a long time. Flatpack and Snap are new package formats and Ubuntu supports both of them. I am not sure if Kubuntu supports Snap.

The command to install a deb packaged application is:

```
sudo apt <package name>
```

As for Docker I am not think that Docker images for Ubuntu are in the Ubuntu repositories. I think a person needs to set a repository in the sources.list file from which the Docker image can be downloaded. Here is a list of images available and it does not include one for Ubuntu artful.

[https://gallery.ecr.aws/lts/ubuntu](https://gallery.ecr.aws/lts/ubuntu)

[https://hub.docker.com/u/ubuntu/](https://hub.docker.com/u/ubuntu/)

Regards

---

