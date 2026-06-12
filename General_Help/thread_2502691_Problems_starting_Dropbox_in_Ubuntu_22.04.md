---
title: "Problems starting Dropbox in Ubuntu 22.04"
date: 2024-11-25
forum: General Help
---

### Post by agonzalesc on 2024-11-25
Hi
I have always used Dropbox on this version of Ubuntu and have never had any problems, but this time I do have errors when starting the service.

I downloaded the .deb from their official website and installed it using apt.
[https://www.dropbox.com/install-linux?_tk=install_view](https://www.dropbox.com/install-linux?_tk=install_view)

```
sudo apt install ./dropbox_2020.03.04_amd64.deb
```

After I run **dropbox start -i** and it shows thoses errors:

```
gonzalesc@pucco-hp:~$ dropbox start -i
Starting Dropbox...dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/cryptography.hazmat.bindings._openssl.abi3.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/cryptography.hazmat.bindings._padding.abi3.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/apex._apex.abi3.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/psutil._psutil_linux.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/psutil._psutil_posix.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/google._upb._message.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/tornado.speedups.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/wrapt._wrappers.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/PyQt5.QtCore.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/PyQt5.sip.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/PyQt5.QtGui.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/PyQt5.QtWidgets.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/PyQt5.QtDBus.so'
Done!

```


Then it sends me to Chrome to link the dropbox with my desktop and it seems to do that fine, but the Dropbox service never finishes initializing, it stays frozen in the "starting" state.


Searching for information I followed these steps but the results were the same, that is, I got the same errors.
[https://help.dropbox.com/installs/advanced-reinstall](https://help.dropbox.com/installs/advanced-reinstall)

I have installed these packages:
python3 v3.10.6
python3-gpg v1.16
equivs v2.3.1


PD: An unimportant fact but I mention it to give all the necessary information is that, when I installed the .deb, a Dropbox repository was added to my source-list but with an unverified key, so I had to verify it using a simple doc and the warning no longer appears when running **apt update**.

---

### Post by ActionParsnip on 2024-11-26
Dropbox is in the repos. Uninstall the deb then run:
```

sudo apt --purge autoremove
sudo apt install nautilus-dropbox

```

---

### Post by agonzalesc on 2024-11-26
Hi
Thanks for the reply.


I did these steps but the result was the same, the same errors from Dropbox start.

---

### Post by ActionParsnip on 2024-11-26
If you actually read the text rather than jumping to the code snippet you'll do much better. OK I'll walk you through it.
If you run
```

dpkg -l | grep -i dropbox

```
What is the output?

---

### Post by agonzalesc on 2024-11-26
Hi.

Here the output.

```
gonzalesc@pucco-hp:~$ LC_ALL=C sudo dpkg -l | grep -i dropbox
[sudo] password for gonzalesc: 
rc  dropbox                                    2020.03.04                                   amd64        cloud synchronization engine - CLI and Nautilus extension
ii  nautilus-dropbox                           2019.02.14-1ubuntu1                          amd64        Dropbox integration for Nautilus
gonzalesc@pucco-hp:~$ 
```

Regards

---

### Post by ActionParsnip on 2024-11-26
> **agonzalesc said:**
> Hi.

Here the output.

```
gonzalesc@pucco-hp:~$ LC_ALL=C sudo dpkg -l | grep -i dropbox
[sudo] password for gonzalesc: 
rc  dropbox                                    2020.03.04                                   amd64        cloud synchronization engine - CLI and Nautilus extension
ii  nautilus-dropbox                           2019.02.14-1ubuntu1                          amd64        Dropbox integration for Nautilus
gonzalesc@pucco-hp:~$ 
```

Regards

OK, run:

```

sudo dpkg -P dropbox
sudo apt --purge remove nautilus-dropbox
sudo apt --purge autoremove
sudo apt update
sudo apt clean
sudo apt install nautilus-dropbox

```

---

### Post by agonzalesc on 2024-11-26
Hi, thanks for your help, I appreciate it.


I ran them one by one and in that same order, but the result was the same.


```
gonzalesc@pucco-hp:~$ dropbox start -i
Starting Dropbox...dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/cryptography.hazmat.bindings._openssl.abi3.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/cryptography.hazmat.bindings._padding.abi3.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/apex._apex.abi3.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/psutil._psutil_linux.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/psutil._psutil_posix.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/google._upb._message.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/tornado.speedups.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/wrapt._wrappers.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/PyQt5.QtCore.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/PyQt5.sip.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/PyQt5.QtGui.so'
dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/PyQt5.QtWidgets.so'
Dropbox isn't running!
Done!
gonzalesc@pucco-hp:~$ dropbox: load fq extension '/home/gonzalesc/.dropbox-dist/dropbox-lnx.x86_64-212.4.5767/PyQt5.QtDBus.so'

```


Regards

---

### Post by agonzalesc on 2024-11-27
Hi
I had to delete my Dropbox folder and now it works.

Thanks

---

