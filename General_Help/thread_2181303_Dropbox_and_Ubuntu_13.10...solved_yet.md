---
title: "Dropbox and Ubuntu 13.10...solved yet?"
date: 2013-10-17
forum: General Help
---

### Post by liquidcross on 2013-10-17
I've heard all over the web that Dropbox no longer works properly in 13.10. Has this been resolved yet? I've love to upgrade, but I use Dropbox all the time for personal and business use.

---

### Post by vasa1 on 2013-10-17
*I've heard all over the web that Dropbox no longer works properly in 13.10. *

Source please. At least one credible one.

---

### Post by liquidcross on 2013-10-17
Oops. Sorry. Here's where I saw it first.

[http://news.softpedia.com/news/Dropbox-Is-Now-Useless-on-Ubuntu-13-10-Nautilus-Crashing-Constantly-384114.shtml](http://news.softpedia.com/news/Dropbox-Is-Now-Useless-on-Ubuntu-13-10-Nautilus-Crashing-Constantly-384114.shtml)

Commenters are saying it may have been fixed in beta, but I still want to be sure before upgrading to the final version.

---

### Post by erasmusp on 2013-10-17
I see one of the user comments at the bottom of this article:

"Comment #2.1 by: annonymous on 28 Sep 2013, 22:10 GMT

Yes, this issue has been fixed after installing the latest updates in 13.10 beta. So happy. "

---

### Post by azurehi on 2013-10-17
In ubuntu 13.10 Final, I am unable to get dropbox to work.  I have gone to xubuntu 13.10 and dropbox works well.

---

### Post by baggins on 2013-10-17
Seems to work fine on my newly updated system.
Is a standard vanilla ubuntu 13.10 system upgraded from a 13.04 (that was a fresh install)
 
There isn't an official dropbox repository for saucy yet. But using the raring repo seems to work fine for now. 
Just remember to change it in a few days (or weeks :) ) when the nice people at dropbox get around to making the new repo.

-- Jon

---

### Post by drs305 on 2013-10-17
I did an upgrade from Raring rather than a clean install and Dropbox continues to work normally for me.

---

### Post by hashimoto on 2013-10-19
Made a clean install but maintained my /home. Dropbox doesn't work...

---

### Post by mJayk on 2013-10-19
Clean install did not work for me 

Apt get update


Started working

---

### Post by ncs_one on 2013-12-05
I downloaded the .deb from the dropbox website (since I can't install  from the software center due to "Unmet dependencies"). To see the  dropbox icon I followed this advice:
```
sudo apt-get install libappindicator1
```

Now the problem is that I can't login to my account and start syncing. I open the "Preferences", under account it says that this computer is not linked to an account, but I can't find a way to add my account...

Any ideas?

Ubuntu Saucy, 32bit version

---

### Post by bapoumba on 2013-12-15
> **ncs_one said:**
> I downloaded the .deb from the dropbox website (since I can't install  from the software center due to "Unmet dependencies"). To see the  dropbox icon I followed this advice:
```
sudo apt-get install libappindicator1
```

Now the problem is that I can't login to my account and start syncing. I open the "Preferences", under account it says that this computer is not linked to an account, but I can't find a way to add my account...

Any ideas?

Ubuntu Saucy, 32bit version

Just had this issue, but my computer was already linked. Please enter **dropbox start** in a terminal, it will give you a link to authorize the computer on the Dropbox site. You can also directly visit the site and auth the computer you are on : [https://www.dropbox.com/account#security](https://www.dropbox.com/account#security)

---

### Post by marpinheiro on 2014-01-28
Hi..

I solved problem in my Ubuntu 13.10 server running:

apt-get install nautilus

I think any bug with Nautilus in ubuntu server edition

Running fine for me.

Att.
Marcio Pinheiro

---

### Post by Revtmyers on 2014-02-07
I have not been able to use DropBox either on one of my systems. Haven't figured out why but every since the issue occured I get an error message that requires me to authenticate super user privledges for it run. Though when I do still nothing happens. With that being said i am only having issues on my laptop which is an AMD setup. I also have a tower which is an Intel setup in which DropBox is running fine on. Both are running Ubuntu 13.10 and I have noticed in general that there are more issues the AMD laptop has in which the Intel tower does not. Some things are common such as Flash issues but the Intel configuration seems to have a smaller amount of issues which are cause both to lock up to the point I have to unplug to power off the units.

---

### Post by Grippon on 2014-02-12
> **hashimoto said:**
> Made a clean install but maintained my /home. Dropbox doesn't work...


I know this is kind of old but, if you get the following at a command prompt:

```
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
VerificationError: importing '/home/f282c439/pylinux/__pycache__/_cffi__xa0c4f46bx1d95b4de.so': No module named _cffi__xa0c4f46bx1d95b4de
^CTraceback (most recent call last):
  File "/usr/bin/dropbox", line 1404, in <module>
    ret = main(sys.argv)
  File "/usr/bin/dropbox", line 1393, in main
    result = commands[argv[i]](argv[i+1:])
  File "/usr/bin/dropbox", line 1241, in start
    if not start_dropbox():
  File "/usr/bin/dropbox", line 728, in start_dropbox
    time.sleep(interval)

```
Then run this
```
sudo rm -rf /var/lib/dropbox/.dropbox-dist
dropbox start -i


```

---

### Post by vladimirtsoi on 2014-06-30
in lubuntu 14.04 dropbox dowmload its deamon and ends its process

---

