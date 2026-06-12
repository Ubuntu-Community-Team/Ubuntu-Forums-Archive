---
title: "Dropbox quit working?"
date: 2014-01-09
forum: General Help
---

### Post by wolfen10862 on 2014-01-09
Hi, I use dropbox on Ubuntu 13.10 to import photos from my android phone, however dropbox quit working, I did the usual, uninstalled and installed, upon installation it says Nautilus needs to be restarted, so I click ok a few minutes later I click the dropbox iocn and wait, then a security box comes up saying it need authentication for super user permission but it never starts......why?

---

### Post by ant2 on 2014-01-09
When you click on the Dropbox icon in the system tray do you get a pop-up menu? If so, try opening 'Preferences' then choose the 'Account' tab, hold down the 'ctrl' key and the 'Unlink Computer' button should change to 'Fix Permissions'. You could give that a try.

---

### Post by wolfen10862 on 2014-01-11
nope all I get is that dialog box about authorizing it, Is there any other way to fix it?

---

### Post by wolfen10862 on 2014-01-11
Ok guys I have no idea what I just did but I got it working :)
I used the search to find it and totally uninstall it then went to drop box's site and downloaded the 32 bit for Ubuntu and used the software center to install it and no it works like its supposed to and I was already logged in so it HAD to be a issue between the software center and my computer.

---

### Post by Old_Grey_Wolf on 2014-01-11
From Dropbox website [https://tech.dropbox.com/2014/01/dropbox-status-update/](https://tech.dropbox.com/2014/01/dropbox-status-update/)

---

### Post by vasa1 on 2014-01-11
> **Old_Grey_Wolf said:**
> From Dropbox website [https://tech.dropbox.com/2014/01/dropbox-status-update/](https://tech.dropbox.com/2014/01/dropbox-status-update/)Thanks for posting that. Ran into the problem myself. All is well now.

---

### Post by evaristegalois on 2014-01-12
I had a similar problem, running Ubuntu 13.10. Dropbox suddenly no longer appeared in the tray. I tried 

dropbox stop

and 

dropbox start

on the command line, which revealed the following error message:

VerificationError: importing '/home/myusername/pylinux/__pycache__/_cffi__xa0c4f46bx1d95b4de.so': No module named _cffi__xa0c4f46bx1d95b4d

I tried all kinds of things, restarted the computer, uninstalled dropbox and reinstalled it, removed the configuration files (.dropbox in the home directory) -- nothing helped. Finally, I located cffi/verifier.py in /var/lib/dropbox and removed the whole folder by running

sudo rm -r /var/lib/dropbox/

Then I uninstalled dropbox and reinstalled it using the Software Centre. Finally, this got dropbox working again.

---

### Post by buzzingrobot on 2014-01-12
The lesson here is that when an online service, like Dropbox, stops working, don't immediately leap to the conclusion that it's a local problem and start adding and removing things. Check if the site is down first.

---

### Post by vasa1 on 2014-01-12
> **buzzingrobot said:**
> The lesson here is that when an online service, like Dropbox, stops working, don't immediately leap to the conclusion that it's a local problem and start adding and removing things. Check if the site is down first.
Well, I pinged dropbox.com and that was "up". But I totally agree with giving online stuff some time. Outages aren't uncommon.

I've seen "panic" responses on the day Google Chrome updates. People get errors and assume something's wrong with *their* setup. Just trying a few hours later without any uninstalling/reinstalling, logging out and in, or rebooting often sorts things out.

---

### Post by ernitron on 2014-01-28
I just found a solution that worked for me. 

```
sudo rm -rf /var/lib/dropbox/.dropbox-dist
dropbox start -i
```

These commands will reinstall dropbox.

---

### Post by kjaspan on 2014-02-02
I, too had the same problem. I am running Xubuntu 13.10 on a 64 bit AMD powered HP desktop. I was not seeing the Dropbox icon in the system tray and was prompted on reboot for the admin password.

I reinstalled Dropbox via the Ubuntu Software Center and it still was not working. Here's what I got:

ps -aef|grep -i dropbox
kevin     2738  2242  0 11:02 ?        00:00:00 /usr/bin/python /usr/bin/dropbox start -i
root      3446  2738 87 11:03 ?        00:03:58 /usr/bin/python /usr/bin/dropbox update
root      3745  2923  0 11:07 pts/3    00:00:00 grep --color=auto -i dropbox
root@civet:~# ps -aef|grep -i dropbox
root      5301  2923  0 11:17 pts/3    00:00:00 grep --color=auto -i dropbox
root@civet:~# ps -aef|grep -i dropbox
root      5303  2923  0 11:17 pts/3    00:00:00 grep --color=auto -i dropbox
root@civet:~# dropbox start
Starting Dropbox...Traceback (most recent call last):
  File "dropbox/client/main.py", line 13, in <module>
  File "autogen_explicit_imports.py", line 13, in <module>
  File "ui/common/selective_sync.py", line 6, in <module>
  File "arch/__init__.py", line 28, in <module>
  File "arch/linux/tracing.py", line 8, in <module>
  File "hard_trace.py", line 6, in <module>
  File "client_api/connection_hub.py", line 21, in <module>
  File "client_api/kv_connection.py", line 23, in <module>
  File "pylinux/__init__.py", line 71, in <module>
  File "cffi/api.py", line 311, in verify
  File "dropbox/overrides.py", line 398, in load_library
  File "cffi/verifier.py", line 69, in load_library
  File "cffi/verifier.py", line 154, in _load_library
  File "cffi/vengine_cpy.py", line 124, in load_library
VerificationError: importing '/root/pylinux/__pycache__/_cffi__xa0c4f46bx1d95b4de.so': No module named _cffi__xa0c4f46bx1d95b4de




The Dropbox daemon is not installed!
Run "dropbox start -i" to install the daemon
root@civet:~# 
root@civet:~# 
root@civet:~# 
root@civet:~# dropbox start -i
Starting Dropbox...Traceback (most recent call last):
  File "dropbox/client/main.py", line 13, in <module>
  File "autogen_explicit_imports.py", line 13, in <module>
  File "ui/common/selective_sync.py", line 6, in <module>
  File "arch/__init__.py", line 28, in <module>
  File "arch/linux/tracing.py", line 8, in <module>
  File "hard_trace.py", line 6, in <module>
  File "client_api/connection_hub.py", line 21, in <module>
  File "client_api/kv_connection.py", line 23, in <module>
  File "pylinux/__init__.py", line 71, in <module>
  File "cffi/api.py", line 311, in verify
  File "dropbox/overrides.py", line 398, in load_library
  File "cffi/verifier.py", line 69, in load_library
  File "cffi/verifier.py", line 154, in _load_library
  File "cffi/vengine_cpy.py", line 124, in load_library
VerificationError: importing '/root/pylinux/__pycache__/_cffi__xa0c4f46bx1d95b4de.so': No module named _cffi__xa0c4f46bx1d95b4de

Dropbox is the easiest way to share and store your files online. Want to learn more? Head to [http://www.dropbox.com/](http://www.dropbox.com/)

Downloading Dropbox... 100%
Unpacking Dropbox... 100%
Traceback (most recent call last):
  File "dropbox/client/main.py", line 13, in <module>
  File "autogen_explicit_imports.py", line 13, in <module>
  File "ui/common/selective_sync.py", line 6, in <module>
  File "arch/__init__.py", line 28, in <module>
  File "arch/linux/tracing.py", line 8, in <module>
  File "hard_trace.py", line 6, in <module>
  File "client_api/connection_hub.py", line 21, in <module>
  File "client_api/kv_connection.py", line 23, in <module>
  File "pylinux/__init__.py", line 71, in <module>
  File "cffi/api.py", line 311, in verify
  File "dropbox/overrides.py", line 398, in load_library
  File "cffi/verifier.py", line 69, in load_library
  File "cffi/verifier.py", line 154, in _load_library
  File "cffi/vengine_cpy.py", line 124, in load_library
VerificationError: importing '/root/pylinux/__pycache__/_cffi__xa0c4f46bx1d95b4de.so': No module named _cffi__xa0c4f46bx1d95b4de
Done!

dropbox start -i

It then tries again to download Dropbox, as before.

So I am out of luck. Help, please.

---

### Post by kjaspan on 2014-02-06
The various suggestion solutions did not work for me - not even the command:

dropbox start -i

which results in the same errors quoted before.

I finally solved the problem by following the install procedure here:

[https://www.dropbox.com/install](https://www.dropbox.com/install)


Specifically, for my installation:
64-bit:

cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -

Then, I ran the Dropbox daemon from the newly created .dropbox-dist folder.

~/.dropbox-dist/dropboxd

---

