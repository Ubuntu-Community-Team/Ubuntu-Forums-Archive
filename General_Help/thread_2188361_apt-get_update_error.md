---
title: "apt-get update error"
date: 2013-11-16
forum: General Help
---

### Post by ydamiri on 2013-11-16
[COLOR=#000000][FONT=Arial]i'm trying to install mongodb on an ubuntu micro ec2 instance and have had to run the apt-get update command. i'm following the [/FONT][/COLOR][directions here]("http://docs.mongodb.org/manual/tutorial/install-mongodb-on-ubuntu/")[COLOR=#000000][FONT=Arial]. i've tried all of the below from this forum to no avail.
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
```
sudo rm /var/lib/dpkg/lock
sudo rm /var/lib/apt/lists/* -rf

```
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]can anyone give me some advice on how to proceed? below is the error i get:[/FONT][/COLOR]


```
[ubuntu@ip-172-31-40-131:~]$sudo apt-get update
Get:1 http://us-west-2.ec2.archive.ubuntu.com precise Release.gpg [198 B]
Get:2 http://us-west-2.ec2.archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:3 http://us-west-2.ec2.archive.ubuntu.com precise Release [49.6 kB]
Get:4 http://us-west-2.ec2.archive.ubuntu.com precise-updates Release [49.6 kB]
Get:5 http://us-west-2.ec2.archive.ubuntu.com precise/main Sources [934 kB]
Get:6 http://ppa.launchpad.net precise Release.gpg [316 B]
Get:7 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:8 http://us-west-2.ec2.archive.ubuntu.com precise/universe Sources [5019 kB]
Get:9 http://toolbelt.heroku.com ./ Release.gpg [490 B]
Get:10 http://ppa.launchpad.net precise Release [11.9 kB]
Get:11 http://security.ubuntu.com precise-security Release [49.6 kB]
Get:12 http://ppa.launchpad.net precise/main Sources [2112 B]
Get:13 http://toolbelt.heroku.com ./ Release [1673 B]
Get:14 http://ppa.launchpad.net precise/main amd64 Packages [4376 B]
Get:15 http://security.ubuntu.com precise-security/main Sources [93.6 kB]
Get:16 http://ppa.launchpad.net precise/main i386 Packages [4379 B]
Get:17 http://us-west-2.ec2.archive.ubuntu.com precise/main amd64 Packages [1273 kB]
Ign http://ppa.launchpad.net precise/main TranslationIndex
Get:18 http://toolbelt.heroku.com ./ Packages [1040 B]
Get:19 http://us-west-2.ec2.archive.ubuntu.com precise/universe amd64 Packages [4786 kB]
Get:20 http://security.ubuntu.com precise-security/universe Sources [29.9 kB]
Get:21 http://security.ubuntu.com precise-security/main amd64 Packages [341 kB]
Ign http://ppa.launchpad.net precise/main Translation-en
Get:22 http://us-west-2.ec2.archive.ubuntu.com precise/main i386 Packages [1274 kB]
Get:23 http://us-west-2.ec2.archive.ubuntu.com precise/universe i386 Packages [4796 kB]
Get:24 http://us-west-2.ec2.archive.ubuntu.com precise/main TranslationIndex [3706 B]
Get:25 http://us-west-2.ec2.archive.ubuntu.com precise/universe TranslationIndex [2922 B]
Get:26 http://security.ubuntu.com precise-security/universe amd64 Packages [85.1 kB]
Get:27 http://us-west-2.ec2.archive.ubuntu.com precise-updates/main Sources [426 kB]
Get:28 http://us-west-2.ec2.archive.ubuntu.com precise-updates/universe Sources [99.5 kB]
Get:29 http://security.ubuntu.com precise-security/main i386 Packages [359 kB]
Get:30 http://us-west-2.ec2.archive.ubuntu.com precise-updates/main amd64 Packages [708 kB]
Ign http://toolbelt.heroku.com ./ Translation-en
Get:31 http://us-west-2.ec2.archive.ubuntu.com precise-updates/universe amd64 Packages [221 kB]
Get:32 http://us-west-2.ec2.archive.ubuntu.com precise-updates/main i386 Packages [729 kB]
Get:33 http://us-west-2.ec2.archive.ubuntu.com precise-updates/universe i386 Packages [226 kB]
Get:34 http://us-west-2.ec2.archive.ubuntu.com precise-updates/main TranslationIndex [3564 B]
Get:35 http://us-west-2.ec2.archive.ubuntu.com precise-updates/universe TranslationIndex [2850 B]
Get:36 http://us-west-2.ec2.archive.ubuntu.com precise/main Translation-en [726 kB]
Get:37 http://security.ubuntu.com precise-security/universe i386 Packages [88.9 kB]
Get:38 http://us-west-2.ec2.archive.ubuntu.com precise/universe Translation-en [3341 kB]
Get:39 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:40 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:41 http://us-west-2.ec2.archive.ubuntu.com precise-updates/main Translation-en [298 kB]
Get:42 http://security.ubuntu.com precise-security/main Translation-en [161 kB]
Get:43 http://us-west-2.ec2.archive.ubuntu.com precise-updates/universe Translation-en [123 kB]
Get:44 http://security.ubuntu.com precise-security/universe Translation-en [54.4 kB]
Fetched 26.4 MB in 1min 23s (314 kB/s)
Reading package lists... Error!



```

---

### Post by ibjsb4 on 2013-11-17
Open a terminal and please post the output of:

```
cat /etc/apt/sources.list
```

and
```

ls /etc/apt/sources.list.d
```

---

### Post by tgalati4 on 2013-11-17
Post the output of:

```
sudo apt-get clean
sudo apt-get check
```

---

