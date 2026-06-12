---
title: "&quot;Sub-process https received signal 4&quot; after adding any additional repositories"
date: 2022-05-18
forum: General Help
---

### Post by dvvilly on 2022-05-18
[FONT=monospace][COLOR=#000000]```

$ cat /etc/lsb-release[/COLOR]
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=22.04 
DISTRIB_CODENAME=jammy 
DISTRIB_DESCRIPTION="Ubuntu 22.04 LTS"

```

```

$ uname -a
[/FONT][FONT=monospace][FONT=monospace][COLOR=#000000]Linux myhostname 5.15.0-30-generic #31-Ubuntu SMP Thu May 5 10:00:34 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux[/COLOR][/FONT][/FONT]

```[FONT=monospace][FONT=monospace][FONT=monospace]
[/FONT]
Hello all,

I am having a problem when trying to use ANY additional repositories in my fresh Server (minimal) 22.04 LTS.

I have repeated the below steps on a second brand new installation with the same outcome. My research to date has not found anyone experiencing the same.

**Process:**
Create new VM in ESXi 7.
Install Ubuntu Server (minimal) 22.04LTS

```

$ sudo apt update && sudo dist-upgrade -y && sudo apt autoremove -y
$ sudo reboot

```

At this point, running ```
sudo apt update
``` runs as expected and without errors.

The purpose of this server is to run docker, so I have followed the steps found here [on Docker's website]("https://docs.docker.com/engine/install/ubuntu/"):

**Install the GPG Key**
[/FONT][/FONT]```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```[B]
Add the Docker Repository

[/B]```

$ echo \   "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

[B]Update the package index

[/B]```

$ sudo apt update

<snip>
[FONT=monospace][COLOR=#000000]Reading package lists... Done                       [/COLOR]
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Method https has died unexpectedly! [/COLOR]
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Sub-process https received signal 4.[/COLOR]
[/FONT]
```[FONT=monospace]


At first I thought this might be an issue between 22.04LTS and Docker - but it now appears that as soon as I add **any** additional repository I get the same outcome.

[/FONT][FONT=monospace][FONT=monospace][COLOR=#000000]```

$ ls /etc/apt/sources.list.d/ 
```[/COLOR]```

total 16K 
-rw-r--r-- 1 root root  130 May 18 11:53 docker.list

$ cat /etc/apt/sources.list.d/docker.list

```[/FONT][/FONT]```

[FONT=monospace][FONT=monospace][FONT=monospace][COLOR=#000000]deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu   jammy stable[/COLOR]
[/FONT][/FONT][/FONT]
```[FONT=monospace]

I have also tried the same with the 'R' installation process after first commenting out the docker repository from the above.

```

$ wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo gpg --dearmor -o /usr/share/keyrings/r-project.gpg
$ echo "deb [signed-by=/usr/share/keyrings/r-project.gpg] https://cloud.r-project.org/bin/linux/ubuntu jammy-cran40/" | sudo tee -a /etc/apt/sources.list.d/r-project.list

```

In summary, as soon as I add an additional repository to /etc/apt/sources.list.d/ - ```
sudo apt update
``` fails to run.

Any tips or suggestions would be greatly appreciated!
[/FONT]

---

### Post by bob4ever on 2022-05-30
Hey there,

I ran into the same error last week. Not only apt update fails with a signal 4 error but also git (git-remote-https died of signal 4). The strange part for me was that wget and curl still worked with HTTPS. I used Virtualbox "5.1.38_Ubuntur122592" (which is already a bit aged). 

I've solved this issue for me by updating my virtualbox version. With Virtualbox "6.1.34 r150636" (Windows) the error doesn't occur anymore. 

Multiple posts I've found to this issue also say that signale 4 has something to do with an hardware error. Have you tried to update your ESXi server?

---

