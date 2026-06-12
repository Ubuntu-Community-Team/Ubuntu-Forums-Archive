---
title: "Install openssh circular errors."
date: 2018-12-07
forum: General Help
---

### Post by pet-tro on 2018-12-07
I'm new to Ubuntu.  I set it up the other week based on a guide.  It's running 18.04 LTS desktop.

1.  I created a user and password.
2.  I used the following script to install an open-source home automation suite called home-assistant.  This is the script.  It's running HA in docker:

```
sudo -i
add-apt-repository universe
apt-get install -y apparmor-utils apt-transport-https avahi-daemon ca-certificates curl dbus jq network-manager socat software-properties-common
curl -sSL [https://get.docker.com]("https://get.docker.com/") [COLOR=#D73A49]|[/COLOR] sh
curl -sL [COLOR=#032F62]"https://raw.githubusercontent.com/home-assistant/hassio-build/master/install/hassio_install"[/COLOR] [COLOR=#D73A49]|[/COLOR] bash -s
```

3. After about 2 weeks of using HA without a hitch, I decided I needed the ability to SSH into the machine.
4. I log into the machine.  Open terminal.

--- This is where the issue starts ---

I try to install openssh with the following command:

```
sudo apt-get install openssh-server
```

I'm met with an error that prompts me to install 2 dependencies and 1 recommendation:  openssh-client, openssh-sftp-server, ssh-import-id

So I install openssh-client using 

    ```
sudo apt-get install openssh-server
```

This works fine.  I then attempt to install openssh-sftp-server

```
sudo apt-get install openssh-sftp-server
```

And it's telling me i need openssh-server.

How do I install this?  No one online seems to have this issue accept me.  All the tutorials show a simple quick sudo apt-get install openssh-server and everything goes swimmingly.  

I'm lost.

---

### Post by QIII on 2018-12-07
Hello!

Would you please provide the exact text of the results of the command.?  Details can be important.

---

### Post by pet-tro on 2018-12-07
This is what I get

```
$ sudo apt-get install openssh-server
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 openssh-server : Depends: openssh-client (= 1:7.6p1-4)
                  Depends: openssh-sftp-server but it is not going to be installed
                  Recommends: ssh-import-id but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```






```
$ sudo apt-get install openssh-sftp-server
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 openssh-sftp-server : Depends: openssh-client (= 1:7.6p1-4)
                       Recommends: openssh-server or
                                   ssh-server
E: Unable to correct problems, you have held broken packages.
```

FYI.  I've looked and I have zero broken packages.

I have also tried the following commands:

[COLOR=#2C2F34][FONT=-apple-system]sudo dpkg &#8211;configure -a
sudo apt-get install -f
sudo apt-get dist-upgrade[/FONT][/COLOR]

---

### Post by CatKiller on 2018-12-07
The mention of Incoming is troubling: it suggests that it's picking the packages from a non-Ubuntu repository.

You can probably help your package manager out by installing all the packages together, though, on one line.

```
sudo apt-get install openssh-server openssh-client openssh-sftp-server
```

---

### Post by pet-tro on 2018-12-07
[FONT=-apple-system, BlinkMacSystemFont, segoe ui, Roboto, Oxygen, Oxygen-Sans, Ubuntu, Cantarell, helvetica neue, open sans, sans-serif][COLOR=#2c2f34][B]thats met with more of the same:

[/B][/COLOR][/FONT]$ sudo apt-get install openssh-server openssh-sftp-server openssh-client ssh-import-id


Reading package lists... Done
Building dependency tree       
Reading state information... Done
ssh-import-id is already the newest version (5.7-0ubuntu1).
openssh-client is already the newest version (1:7.6p1-4ubuntu0.1).
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 openssh-server : Depends: openssh-client (= 1:7.6p1-4)
 openssh-sftp-server : Depends: openssh-client (= 1:7.6p1-4)
E: Unable to correct problems, you have held broken packages.

---

### Post by Skaperen on 2018-12-08
if you are going to ssh into the machine or container and never ssh out from there, then that machine or container only needs the server components and not the client components.  likewise, if you are never going to ssh into your desktop and just ssh out to others, then that desktop only needs the client components and not the server components.  you can choose to install both, if you wish.  then you can have that machine or container ssh to itself, which can be useful to run tests of scripts that run ssh.

---

