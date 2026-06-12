---
title: "Not able to &quot;add-apt-repository&quot;"
date: 2013-08-06
forum: General Help
---

### Post by Greg_White on 2013-08-06
I'm having a problem when I try to add any ppa to my sources list:

```
greg@greg-gateway:~$ sudo add-apt-repository ppa:webupd8team/y-ppa-manager
You are about to add the following PPA to your system:
 Y PPA Manager

Info and feedback: http://www.webupd8.org/2010/11/y-ppa-manager-easily-search-add-remove.html

This PPA is for Y PPA Manager and also includes the latest YAD for Quantal, Precise, Oneiric, Natty, Maverick and Lucid (YAD is a dependency for Y PPA Manager): http://code.google.com/p/yad/
 More info: https://launchpad.net/~webupd8team/+archive/y-ppa-manager
Press [ENTER] to continue or ctrl-c to cancel adding it

Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 551, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 99, in run
    self.add_ppa_signing_key(self.ppa_path)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 132, in add_ppa_signing_key
    tmp_keyring_dir = tempfile.mkdtemp()
  File "/usr/lib/python2.7/tempfile.py", line 322, in mkdtemp
    name = names.next()
  File "/usr/lib/python2.7/tempfile.py", line 141, in next
    letters = [choose(c) for dummy in "123456"]
  File "/usr/lib/python2.7/random.py", line 274, in choice
    return seq[int(self.random() * len(seq))]  # raises IndexError if seq is empty
ValueError: cannot convert float NaN to integer

greg@greg-gateway:~$ 
```

This is happening on Zentyal 3.0 server (which is a light-weight Lubuntu desktop on Ubuntu 12.04 LTS Server}.  I've been runing this server as a gateway for a home network since it's release a year ago.  This is the first time I've done any updates and was trying to add the Hagucichi repository when I ran into the problem.  I get the python errors regardless of what repository I try to add.  Prior to this output, it told me that there "add-apt-repository" was an invalid command, but running "apt-get upgrade" repeadly made that go away.  I have no idea how to resolve the issue, so any help would be appreciated.

---

### Post by oldos2er on 2013-08-06
Is the package software-properties installed?

---

### Post by Greg_White on 2013-08-07
There seemed to be problems wit the install, so I built a new hard drive.  I also added the entire Lubuntu desktop to this install and completely set the gateway server back up from scratch.  Then I tried adding the ppa repository with these results:

> greg@greg-gateway:~/Downloads$ sudo add-apt-repository ppa:webupd8team/haguichi [sudo] password for greg: 
You are about to add the following PPA to your system:
 Haguichi provides a graphical frontend for Hamachi 2 on Linux that integrates smoothly into your GNOME desktop. [http://www.haguichi.net/](http://www.haguichi.net/)

To add this PPA and install haguichi:
sudo add-apt-repository ppa:webupd8team/haguichi
sudo apt-get update
sudo apt-get install haguichi haguichi-appindicator

Report any bugs you may find @ [https://bugs.launchpad.net/haguichi](https://bugs.launchpad.net/haguichi)
 More info: [https://launchpad.net/~webupd8team/+archive/haguichi](https://launchpad.net/~webupd8team/+archive/haguichi)
Press [ENTER] to continue or ctrl-c to cancel adding it

Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 551, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 99, in run
    self.add_ppa_signing_key(self.ppa_path)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 132, in add_ppa_signing_key
    tmp_keyring_dir = tempfile.mkdtemp()
  File "/usr/lib/python2.7/tempfile.py", line 322, in mkdtemp
    name = names.next()
  File "/usr/lib/python2.7/tempfile.py", line 141, in next
    letters = [choose(c) for dummy in "123456"]
  File "/usr/lib/python2.7/random.py", line 274, in choice
    return seq[int(self.random() * len(seq))]  # raises IndexError if seq is empty
ValueError: cannot convert float NaN to integer

greg@greg-gateway:~/Downloads$ 

Everything seems OK with this install, so looking for something wrong with the ppa since both repositories are from the webupd8team.  Will test adding different repository and report back.

---

### Post by Greg_White on 2013-08-07
I think that I found the problem, and or solution ...

Ubuntu server does not have add-apt-repository command.  (By installing parts of Lubuntu desktop, I got some functionalitly.)  This issues is discussed here ...

[http://askubuntu.com/questions/38021/how-to-add-a-ppa-on-a-server](http://askubuntu.com/questions/38021/how-to-add-a-ppa-on-a-server)

I will work though this resolution and post results.

---

### Post by oldos2er on 2013-08-07
I'm running Server 13.10 with python-software-properties installed and it works fine.

---

