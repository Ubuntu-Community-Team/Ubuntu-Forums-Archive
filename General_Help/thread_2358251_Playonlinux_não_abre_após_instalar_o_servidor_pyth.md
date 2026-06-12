---
title: "Playonlinux não abre após instalar o servidor python"
date: 2017-04-11
forum: General Help
---

### Post by portifa3d on 2017-04-11
Hello, I'm using ubuntu studio vr 16.04, I installed the playonlinux and everything was good, so I tried to install the python server to run it along with the sublime text and install it. The visual studio code and the asp net, gave total zica, to have problems to start any program that I installed in playonlinux, the same does not open click on the shortcut and nothing happens, I installed python 3.0 by the program center until apt-get Began to give problem, if someone can give me a light thanks. I tried to remove the lock file to run the apt-get that was giving stick, but nothing, to have a headache, I've been trying to solve the problem for 3 days, usually I search the net and solve it only by seeing in forums, but this time I had to post asking for a help. Thank you guys that can help.

I tried to reinstall python, did not work, uninstall tbm no, I tried to reinstall the playonlinux nothing, in synaptic to reinstall in the end gives the following error:

```
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:59
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/libretro-ubuntu-stable-xenial.list:2 and /etc/apt/sources.list.d/libretro-ubuntu-stable-xenial.list:3
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/libretro-ubuntu-stable-xenial.list:2 and /etc/apt/sources.list.d/libretro-ubuntu-stable-xenial.list:4
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/noobslab-ubuntu-apps-xenial.list:2 and /etc/apt/sources.list.d/noobslab-ubuntu-apps-xenial.list:3
```

If anyone can give me a light, I thank you.

---

### Post by howefield on 2017-04-11
Hello portifa3d and welcome to the forums.

Please note that these are English language forums unless you post in the Loco forums.

Thread moved to the "*General Help*" for the time being but perhaps [https://ubuntuforum-pt.org/](https://ubuntuforum-pt.org/) would be a better venue for you ?

Google translate offers...

> Hello, I'm using ubuntu studio vr 16.04, I installed the playonlinux and everything was good, so I tried to install the python server to run it along with the sublime text and install it. The visual studio code and the asp net, gave total zica, to have problems to start any program that I installed in playonlinux, the same does not open click on the shortcut and nothing happens, I installed python 3.0 by the program center until apt-get Began to give problem, if someone can give me a light thanks. I tried to remove the lock file to run the apt-get that was giving stick, but nothing, to have a headache, I've been trying to solve the problem for 3 days, usually I search the net and solve it only by seeing in forums, but this time I had to post asking for a help. Thank you guys that can help.
I tried to reinstall python, did not work, uninstall tbm no, I tried to reinstall the playonlinux nothing, in synaptic to reinstall in the end gives the following error:

W: Target Sources (main / source / Sources) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:59
W: Target Sources (main / source / Sources) is configured multiple times in /etc/apt/sources.list.d/libretro-ubuntu-stable-xenial.list:2 and /etc/apt/sources.list.d/ Libretro-ubuntu-stable-xenial.list: 3
W: Target Sources (main / source / Sources) is configured multiple times in /etc/apt/sources.list.d/libretro-ubuntu-stable-xenial.list:2 and /etc/apt/sources.list.d/ Libretro-ubuntu-stable-xenial.list: 4
W: Target Sources (main / source / Sources) is configured multiple times in /etc/apt/sources.list.d/noobslab-ubuntu-apps-xenial.list:2 and /etc/apt/sources.list.d/ Noobslab-ubuntu-apps-xenial.list: 3

If anyone can give me a light, I thank you.

---

### Post by dragonfly41 on 2017-04-11
If I understand correctly (I am basing on Google English translation) you are having problem removing a lock file?
I had that problem yesterday and found advice here.  [https://ubuntuforums.org/showthread.php?t=1858466](https://ubuntuforums.org/showthread.php?t=1858466)
In summary ..
```
sudo lsof /var/lib/dpkg/lock
...
... find PID of lock
then
sudo kill -TERM <PID_NUMBER>

```

---

### Post by portifa3d on 2017-04-11
```
Looking for python... 2.7.13 - Traceback (most recent call last):
  File "/usr/share/playonlinux/python/check_python.py", line 1, in <module>
    import os, wxversion
ImportError: No module named wxversion
failed tests
Looking for python2.7... 2.7.13 - Traceback (most recent call last):
  File "/usr/share/playonlinux/python/check_python.py", line 1, in <module>
    import os, wxversion
ImportError: No module named wxversion
failed tests
Looking for python2.6... 
Looking for python2... 2.7.13 - Traceback (most recent call last):
  File "/usr/share/playonlinux/python/check_python.py", line 1, in <module>
    import os, wxversion
ImportError: No module named wxversion
failed tests
Please install python before trying to run this program
```

How i fix this problem?

---

### Post by slickymaster on 2017-04-11
> **portifa3d said:**
> [COLOR=#333333][FONT=&amp]Olá galera do ubuntu forums, eu utilizo o ubuntu studio vr 16.04, instalei o playonlinux e tava tudo de boa rodava o photoshop, ilustrator e o zbrush de boa, até que ao tentar instalar o servidor python para rodar junto com o sublime text e instalar o visual studio code e o asp net, deu zica total, to tendo problemas para iniciar qualquer programa que instalei no playonlinux, o mesmo não abre clico no atalho e não acontece nada, instalei o python 3.0 pela central de programas até o apt-get começou a dar problema, se alguém puder me dar uma luz agradeço. Tentei remover o arquivo lock pra funcionar o apt-get que tava dando pau, mas nada, to tendo uma baita dor de cabeça, faz 3 dias tentando resolver a parada, geralmente eu pesquiso na net e resolvo só vendo em foruns, mas dessa vez tive de postar pedindo um help. Agradeço a galera que puder colaborar.
Tentei reinstalar o python, não deu certo, desinstalar tbm não, tentei reinstalar o playonlinux nada, no synaptic ao reinstalar no final dá o seguinte erro:

[/FONT][/COLOR]W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:59
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/libretro-ubuntu-stable-xenial.list:2 and /etc/apt/sources.list.d/libretro-ubuntu-stable-xenial.list:3
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/libretro-ubuntu-stable-xenial.list:2 and /etc/apt/sources.list.d/libretro-ubuntu-stable-xenial.list:4
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/noobslab-ubuntu-apps-xenial.list:2 and /etc/apt/sources.list.d/noobslab-ubuntu-apps-xenial.list:3

Se alguém puder me dar uma luz agradeço.
 [COLOR=#333333][FONT=&amp]
[/FONT][/COLOR]

portifa3d, take a look at this thread -> [How can I automatically fix W: Target Packages … is configured multiple times?]("http://askubuntu.com/questions/760896/how-can-i-automatically-fix-w-target-packages-is-configured-multiple-times")

It address the problem you're facing.

---

