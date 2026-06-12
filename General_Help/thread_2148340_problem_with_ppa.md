---
title: "problem with ppa"
date: 2013-05-24
forum: General Help
---

### Post by dador33 on 2013-05-24
I cant agregate ppa : this is the error


sudo add-apt-repository ppa:xubuntu-dev/xfce-4.10
[sudo] password for dado33: 
You are about to add the following PPA to your system:
 Xfce 4.10 packages for Xubuntu 12.04 LTS (Precise Pangolin).

Please note that only Xfce 4.8 is officially supported on Xubuntu 12.04. Therefore, any bug report filed with this PPA enabled is likely to get rejected, or you may be asked to reproduce the issue with Xfce 4.8. The first Xubuntu release to feature Xfce 4.10 will be Xubuntu 12.10 (Quantal Quetzal).
 More info: [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)
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

---

### Post by 2F4U on 2013-05-25
Is this the direct output from the command add-apt-repository? If not, provide the exact order of commands. After adding the repository you should execute the following commands:

```

sudo apt-get update 
sudo apt-get dist-upgrade

```

---

