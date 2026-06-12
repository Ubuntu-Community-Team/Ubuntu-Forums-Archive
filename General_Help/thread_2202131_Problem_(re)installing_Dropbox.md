---
title: "Problem (re)installing Dropbox"
date: 2014-01-27
forum: General Help
---

### Post by DavidS on 2014-01-27
I am running Ubuntu 12.04 on an Asus Netbook and a Desktop computer.  Both were running Dropbox OK until a few days ago.  Now, for some reason, Dropbox won't seem to work on the netbook.

Most of the files still seem to be there, but uninstalling from Ubuntu Software Centre doesn't seem to achieve anything, and trying to re-install produces an error.

So I tried the command line, after looking at threads on these forums, with this result:

```
[FONT=courier new]david@Ubuntu64:~$ sudo apt-get install nautilus-dropbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 nautilus-dropbox : Depends: dropbox but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
david@Ubuntu64:~$
[/FONT]
```
It's possible that at some point I may have installed the version from the Dropbox website - I can't actually remember.

I have run 'dpkg --audit', 'apt-get check' and 'apt-get -f install' all to no avail and without any interesting output.

What do I*need to do to clean things up and get Dropbox working again?

Thanks in advance for any useful advice!

---

### Post by DavidS on 2014-01-29
Further details: when I try to start Dropbox, I repeatedly get a popup dialogue window with the title "Dropbox Installation".  It says:
"In order to use Dropbox, you must download the proprietary daemon."  If I click "Cancel", nothing happens: the dialogue remains on the screen.  If I click "OK", Dropbox is apparently downloaded, but then, when I click the next dialogue to "Start Dropbox", I get the download dialogue again.  This happens even if I have clicked "Don't show this again" in the first window.

Because of these problems, I decided to try starting Dropbox from the command line.  This was the output:

```
david@Ubuntu64:~$ dropbox start -i
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
VerificationError: importing '/home/david/pylinux/__pycache__/_cffi__xa0c4f46bx1d95b4de.so': No module named _cffi__xa0c4f46bx1d95b4de
```

After a pause, the popup window described above appears.  If I click "Cancel", as before the dialogue remains on the screen, but I get the following output;

```
Traceback (most recent call last):
  File "/usr/bin/dropbox", line 346, in handle_cancel
    if self.task:
AttributeError: 'DownloadDialog' object has no attribute 'task'
```

What do I need to do to get rid of these errors and get Dropbox running again?

---

### Post by DavidS on 2014-01-29
The thread  at [http://ubuntuforums.org/showthread.php?t=2179282](http://ubuntuforums.org/showthread.php?t=2179282) led me to [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=734628](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=734628)

By following the suggestions there, I got Dropbox reinstalled and working.

David

---

