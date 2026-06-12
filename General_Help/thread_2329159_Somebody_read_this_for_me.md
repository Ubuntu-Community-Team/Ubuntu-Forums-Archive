---
title: "Somebody read this for me"
date: 2016-06-28
forum: General Help
---

### Post by maria17 on 2016-06-28
I try opening ubuntu softwate via terminal but only this code comes out. Wait, how do I post here the image?

---

### Post by howefield on 2016-06-28
Don't post the image, copy/pasting the terminal input and output is usually a better option.

To post an image you would use the paperclip icon available in the advanced editor, not the quick reply option, to attach the file to your post.

---

### Post by QDR06VV9 on 2016-06-28
You can also copy the text from the terminal by highlighting the text you want to show..then right click with mouse And choose copy then paste back here the errors.
But try and use Code tags for the output...See my Sig for code tags,
Regards

---

### Post by maria17 on 2016-06-28
I tried to open ubuntu software in my desktop and via terminal. But it only says these:

---

### Post by howefield on 2016-06-28
And threads merged.

---

### Post by maria17 on 2016-06-28
When I open software center via terminal, this comes out:

```
SystemError: E:Could not open file /var/lib/dpkg/status - open (2: No such file or directory), E:The package lists or status file could not be parsed or opened.
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/rnr.py", line 183, in _on_review_stats_data
    self.save_review_stats_cache_file()
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 315, in save_review_stats_cache_file
    t.run()
  File "/usr/lib/python2.7/threading.py", line 504, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 326, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 357, in _dump_bsddbm_for_unity
    flags=bdb.DB_CREATE)
MemoryError: (12, 'Cannot allocate memory -- Lock table is out of available locker entries')
2016-06-29 01:48:46,297 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1422, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1352, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 154, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 171, in init_view
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 238, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 511, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 271, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 450, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 439, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 124, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 317, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 212, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
```

---

### Post by howefield on 2016-06-28
Try the following commands...

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bak
```
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```
```
sudo apt-get update
```

---

### Post by spjackson on 2016-06-28
> **maria17 said:**
> When I open software center via terminal, this comes out:

```
SystemError: E:Could not open file /var/lib/dpkg/status - open (2: No such file or directory),
```

Something bad has happened to get in this state. Do you know what you might have done? Does the folder exist and if so what is in it?
```

ls -l /var/lib/dpkg

```

---

### Post by maria17 on 2016-06-29
When I tried the first code this comes out

```
:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bak
: 
mv: cannot stat `/var/lib/dpkg/status': No such file or directory
:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bak
mv: cannot stat `/var/lib/dpkg/status': No such file or directory
```

---

### Post by howefield on 2016-06-29
> **maria17 said:**
> When I tried the first code this comes out.....

And the second command produced what ?

---

### Post by maria17 on 2016-06-29
Hi! Ever since I purchased my dell laptop last April 2014, ubuntu software, does not connect. What folder are you referring to? I am really new in this. And even when typing in the terminal, I am not sure if I would type continuously the code or to enter when instructed in the forum.

will I type these code separately or shall I type each and then just enter?

When I tried the second code. This comes out

```
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [140 kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [3,340 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [208 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [199 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [202 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [205 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [257 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en [1,698 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en [2,976 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [84.6 kB]
Fetched 2,197 kB in 1min 37s (22.5 kB/s)                                       
Reading package lists... Done
W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease](http://ph.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease)  

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://ph.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://ph.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://ph.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch [http://dell.archive.canonical.com/updates/dists/precise-dell/Release.gpg](http://dell.archive.canonical.com/updates/dists/precise-dell/Release.gpg)  Unable to connect to dell.archive.canonical.com:http:

W: Failed to fetch [http://dell.archive.canonical.com/updates/dists/precise-dell/public/source/Sources](http://dell.archive.canonical.com/updates/dists/precise-dell/public/source/Sources)  Unable to connect to dell.archive.canonical.com:http:

W: Failed to fetch [http://dell.archive.canonical.com/updates/dists/precise-dell/public/binary-amd64/Packages](http://dell.archive.canonical.com/updates/dists/precise-dell/public/binary-amd64/Packages)  Unable to connect to dell.archive.canonical.com:http:

W: Failed to fetch [http://dell.archive.canonical.com/updates/dists/precise-dell/public/binary-i386/Packages](http://dell.archive.canonical.com/updates/dists/precise-dell/public/binary-i386/Packages)  Unable to connect to dell.archive.canonical.com:http:

W: Failed to fetch [http://dell.archive.canonical.com/updates/dists/precise-dell/public/i18n/Translation-en_US](http://dell.archive.canonical.com/updates/dists/precise-dell/public/i18n/Translation-en_US)  Unable to connect to dell.archive.canonical.com:http:

W: Failed to fetch [http://dell.archive.canonical.com/updates/dists/precise-dell/public/i18n/Translation-en](http://dell.archive.canonical.com/updates/dists/precise-dell/public/i18n/Translation-en)  Unable to connect to dell.archive.canonical.com:http:

W: Failed to fetch [http://oem.archive.canonical.com/updates/dists/precise-oem-sp1/Release.gpg](http://oem.archive.canonical.com/updates/dists/precise-oem-sp1/Release.gpg)  Unable to connect to oem.archive.canonical.com:http:

W: Failed to fetch [http://oem.archive.canonical.com/updates/dists/precise-oem-sp1/public/source/Sources](http://oem.archive.canonical.com/updates/dists/precise-oem-sp1/public/source/Sources)  Unable to connect to oem.archive.canonical.com:http:

W: Failed to fetch [http://oem.archive.canonical.com/updates/dists/precise-oem-sp1/public/binary-amd64/Packages](http://oem.archive.canonical.com/updates/dists/precise-oem-sp1/public/binary-amd64/Packages)  Unable to connect to oem.archive.canonical.com:http:

W: Failed to fetch [http://oem.archive.canonical.com/updates/dists/precise-oem-sp1/public/binary-i386/Packages](http://oem.archive.canonical.com/updates/dists/precise-oem-sp1/public/binary-i386/Packages)  Unable to connect to oem.archive.canonical.com:http:

W: Failed to fetch [http://oem.archive.canonical.com/updates/dists/precise-oem-sp1/public/i18n/Translation-en_US](http://oem.archive.canonical.com/updates/dists/precise-oem-sp1/public/i18n/Translation-en_US)  Unable to connect to oem.archive.canonical.com:http:

W: Failed to fetch [http://oem.archive.canonical.com/updates/dists/precise-oem-sp1/public/i18n/Translation-en](http://oem.archive.canonical.com/updates/dists/precise-oem-sp1/public/i18n/Translation-en)  Unable to connect to oem.archive.canonical.com:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.
:~$ sudo mv/var/lib/dpkg/status/var/lib/dpkg/status.bad
```

This comes out when I copy that code:
```
:~$ ls -l /var/lib/dpkg
total 8172
drwxr-xr-x 2 root root    4096 Jan 28  2014 alternatives
-rw-r--r-- 1 root root 1562206 Apr 20  2014 available
-rw-r--r-- 1 root root 1543395 Apr 20  2014 available-old
-rw-r--r-- 1 root root       8 Feb  3  2013 cmethopt
-rw-r--r-- 1 root root    1539 Apr 20  2014 diversions
-rw-r--r-- 1 root root    1653 Apr 20  2014 diversions-old
drwxr-xr-x 2 root root  307200 Apr 20  2014 info
-rw-r----- 1 root root       0 Apr 20  2014 lock
drwxr-xr-x 2 root root    4096 Apr 13  2012 parts
-rw-r--r-- 1 root root     135 Feb  3  2013 statoverride
-rw-r--r-- 1 root root 1635286 Jun 29 14:52 status
-rw-r--r-- 1 root root 1635293 Apr 20  2014 status.bad
-rw-r--r-- 1 root root 1635286 Apr 20  2014 status-old
drwxr-xr-x 2 root root    4096 Apr 20  2014 triggers
drwxr-xr-x 2 root root    4096 Apr 20  2014 updates
```

---

### Post by spjackson on 2016-06-29
The error which I quoted above "SystemError: E:Could not open file /var/lib/dpkg/status - open (2: No such file or directory)" indicates that there is no file called 'status' in the folder '/var/lib/dpkg', or perhaps that this folder does not exist. The error you got from
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bak

```
indicates precisely the same thing. However, the output from
```

ls -l /var/lib/dpkg

```
shows that the file named 'status' does exist. The problem you originally reported was because this file did not exist at the time, though we do not know what removed it. As a result of 
```

sudo apt-get update

```
The 'status' file has been recreated. Is your original problem now solved, i.e. can you "open software center via terminal"?

---

### Post by maria17 on 2016-06-29
When I run the update... and somr errors came up...my computer hanged a long time and so i had no choice but to shutdown... when i logged in everyhing was black. Nothing can be found.. except for ubuntu desktop tab. What should i do. I can still open guest account.

I tried to shut it down again and restart. Now it is working. But i cannot connect to internet. Networking is enabled but it should automatically connect.

---

### Post by howefield on 2016-06-29
Quite difficult to follow what you are doing here, just to take a step back for a moment... your original post complained of Software Centre not opening, is this still the case or does it still not open ?

---

### Post by maria17 on 2016-06-29
I am sorry for confusing you. I was in such a haste pace. Anyway here is what happened:

After i followed typing the code suggested to me, my computer updated ubuntu. After sometime of applying changes, my laptop hanged. Update manager was not yet finished. And there were some errors coming up. Since it took so long, I shutdown my computer. When I opened it, it was all black and only the desktop tab appeared. And so I waited a couple of minutes before I restart. Once I restarted again, I noticed I can open ubuntu software.It also seemed my ubuntu was updated to a better version. The only problem now is I could not connect my wireless internet. My cellphone can connect to wireless but my laptop cant. I tried connecting via tether, but to no avail. 

I cannot use wired connection as of the moment. The problem now is I totally cannot connect to wireless internet even if networking is enabled.

---

### Post by howefield on 2016-06-29
Please don't be sorry, it seems that your /var/lib/dpkg/status file had become corrupted or broken in some way and using the status-old file has got you back in business. So, good news.

If you are now on to a separate problem, such as not connecting to the internet I'd suggest opening another thread in the "*[Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336")*" forum. Read this [sticky thread]("http://ubuntuforums.org/showthread.php?t=370108") in that forum and post the information produced by the wireless info script as described.

Not sure what you mean by a "better version" - you were on Precise so still should have 12.04, only updated :)

Just for info, can you post the output of ...

```
cat /etc/lsb-release
```

---

### Post by maria17 on 2016-06-30
Thank you for your continuous support. I have opened a new thread.


This comes out when I type that code.
   cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
dianne@dianne-Inspiron-3437:~$ 
dianne@dianne-Inspiron-3437:~$     Quick reply to this message Quick Reply   Advanced reply Adv Reply   Reply With Quote Reply With Quote   Multi-Quote This Message      
Quick: command not found

---

