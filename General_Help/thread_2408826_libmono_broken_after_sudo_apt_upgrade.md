---
title: "libmono broken after sudo apt upgrade"
date: 2018-12-23
forum: General Help
---

### Post by kornster on 2018-12-23
Morning All,

hopefully this is the right place to get some help on this. I have been using Ubuntu 18.04LTS desktop for some time now to serve my media via Emby. As part of that i`ve been using applications to require mono to run them. I had it working perfectly yesterday and when i ssh`d into the PC i saw there was 158 packages that could be updated. I attempted a sudo apt upgrade and it all appeared to be working well then i got thrown an error for what i interperate as libmono. Now the apt upgrade command tells me to run "apt --fix-broken install" which fails. I cant uninstall mono for some reason as i was hoping an uninstall and re-install would resolve the problem but no joy. When i run "sudo apt upgrade" i get the following

158 packages can be updated.
0 updates are security updates.


Last login: Sun Dec 23 14:12:10 2018 from 192.168.0.5
administrator@white-forest:~$ sudo apt upgrade
[sudo] password for administrator:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libmono-corlib4.5-cil : Depends: mono-runtime (>= 5.18.0.225) but 3.2.8+dfsg-4ubuntu1.1 is installed
 libmono-custommarshalers4.0-cil : Depends: mono-runtime (>= 5.18.0.225) but 3.2.8+dfsg-4ubuntu1.1 is installed
 libmono-debugger-soft4.0a-cil : Depends: mono-runtime (>= 5.18.0.225) but 3.2.8+dfsg-4ubuntu1.1 is installed
 libmono-i18n-cjk4.0-cil : Depends: mono-runtime (>= 5.18.0.225) but 3.2.8+dfsg-4ubuntu1.1 is installed
 libmono-i18n4.0-cil : Depends: mono-runtime (>= 5.18.0.225) but 3.2.8+dfsg-4ubuntu1.1 is installed
 libmono-system-configuration4.0-cil : Depends: mono-runtime (>= 5.18.0.225) but 3.2.8+dfsg-4ubuntu1.1 is installed
 libmono-system-web4.0-cil : Depends: mono-runtime (>= 5.18.0.225) but 3.2.8+dfsg-4ubuntu1.1 is installed
 libmono-system4.0-cil : Depends: mono-runtime (>= 5.18.0.225) but 3.2.8+dfsg-4ubuntu1.1 is installed
                         Recommends: ca-certificates-mono (= 5.18.0.225-0xamarin1+ubuntu1804b1) but 4.6.2.7+dfsg-1ubu
 libmono-tasklets4.0-cil : Depends: mono-runtime (>= 5.18.0.225) but 3.2.8+dfsg-4ubuntu1.1 is installed
 mono-devel : Depends: ca-certificates-mono (= 5.18.0.225-0xamarin1+ubuntu1804b1) but 4.6.2.7+dfsg-1ubuntu1 is instal
 mono-runtime : Depends: mono-runtime-sgen (= 3.2.8+dfsg-4ubuntu1.1) but 5.18.0.225-0xamarin1+ubuntu1804b1 is install
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

I`ve tried manually running ca-certificates-mono_4.6.2.7+dfsg-1ubuntu1_all.deb & mono-runtime_3.2.8+dfsg-4ubuntu1.1_amd64.deb via dpkg -i and it just tells me to run the --fix-broken install command


I`ve uploaded the log from --fix-broken install to my OneDrive as its over the limit for the forums
[https://1drv.ms/f/s!ArlPClPjvE7-nYcR87-VHlgt8JK5-A](https://1drv.ms/f/s!ArlPClPjvE7-nYcR87-VHlgt8JK5-A)

Regards
Danny

---

### Post by mcglowca on 2019-08-11
Hey man,

So I just ran into this problem or maybe a similar problem. I searched for a solution using:
```
sudo apt-get --fix-broken install
sudo apt-get autoremove && sudo apt-get autoclean
sudo apt remove --purge mono* libmono*

```
Nothing worked.Then I ran into this site. [HTML]https://github.com/mono/mono/issues/12316[/HTML] I found my solution there. All I did was:
```

mv /etc/mono/config.dpkg-new /etc/mono/config
sudo apt-get autoremove && sudo apt-get autoclean
sudo apt update && sudo apt upgrade

```

Everything works after that. I need to figure out why it messed up in the first place. Maybe my repo was misconfigured to the wrong builds or something.

---

