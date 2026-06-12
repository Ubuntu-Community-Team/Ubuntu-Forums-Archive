---
title: "Ubuntu software updater (and others) keep crashing"
date: 2012-11-09
forum: General Help
---

### Post by aliasforme on 2012-11-09
Hey guys;

I've had a few programs crash on me (firefox, chromium, few others under wine) unexpectedly. Ubuntu also often pops up with windows that ask me to report an error (and then tells me it can't do that because of an invalid package or something:confused:) I'm starting to get worried now that the update manager won't open either. I've attached a screenshot of the error message of software manager so if anyone could provide assistance that would be much appreciated

Thanks

---

### Post by TriumphGuru on 2012-11-09
Hi,

Sorry, I don't have an answer, but I do have almost the same problem.  I don't have apps crashing, but Software Updater doesn't work.  Error Message is:
[COLOR=DarkRed]Reading package lists... Error!
W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.[/COLOR]

Been like this for a month now, I've tried most things to get around it but no success.  I don't want to do a whole clean install if I can avoid it.

I'm running Ubuntu 12.04LTS since it came out.

Thanks in advance for suggestions, advice.

---

### Post by ibjsb4 on 2012-11-09
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter (one line at a time):

sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

That should fix things  :)

And just for your info:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Old_Grey_Wolf on 2012-11-09
> **TriumphGuru said:**
> ...
W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>...

Enter this command to get the key ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
```
Then try updating again.

---

### Post by ibjsb4 on 2012-11-09
Didn't even see that  :(

---

### Post by Old_Grey_Wolf on 2012-11-09
> **ibjsb4 said:**
> Didn't even see that  :(

That is why we recommend people start their own thread rather than post their problem in someone else's thread. :)

---

### Post by aliasforme on 2012-11-09
problem still not fixed:( Same error message keeps popping up each time I try to update

---

### Post by ibjsb4 on 2012-11-09
@aliasforme

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update

And please post any errors

---

### Post by aliasforme on 2012-11-09
When I type that into the terminal some things seem to be updating, while others display 404 not found here are some that have failed:

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ibjsb4 on 2012-11-09
These three ULR's are no longer active and can be removed or just unchecked in software sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

After you have done that, run the update command to see if all errors are cleared.

---

### Post by aliasforme on 2012-11-09
Using the CLI is a bit confusing, so I tried to do this via the software centre, it appears that I can't open the software centre either. It keeps crashing on me every time I open it, without giving me an error message. Also, I still can't open the update manager without the error message. Would these two be linked?

---

### Post by ibjsb4 on 2012-11-10
The software center and update manager do go hand in hand and is a separate problem.  Lets try to get you into the software center since your more comfortable with it.  So one more time in terminal:

gksudo software-center

If that gets you in you should be able to remove sevenmachines/flash from there.  If that does not work it will be necessary to trouble shoot the software center, but one problem at a time.  Lets remove those three ULR's first.  So again in terminal:

cat -n /etc/apt/sources.list

And please post.

---

### Post by aliasforme on 2012-11-10
I tried both commands in the terminal, firstly the sources.list:

```
 1	# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/
     2	
     3	# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
     4	# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted
     5	
     6	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     7	# newer versions of the distribution.
     8	deb http://au.archive.ubuntu.com/ubuntu/ precise main restricted
     9	deb-src http://au.archive.ubuntu.com/ubuntu/ precise main restricted
    10	
    11	## Major bug fix updates produced after the final release of the
    12	## distribution.
    13	deb http://au.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    14	deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    15	
    16	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17	## team. Also, please note that software in universe WILL NOT receive any
    18	## review or updates from the Ubuntu security team.
    19	deb http://au.archive.ubuntu.com/ubuntu/ precise universe
    20	deb-src http://au.archive.ubuntu.com/ubuntu/ precise universe
    21	deb http://au.archive.ubuntu.com/ubuntu/ precise-updates universe
    22	deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates universe
    23	
    24	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25	## team, and may not be under a free licence. Please satisfy yourself as to 
    26	## your rights to use the software. Also, please note that software in 
    27	## multiverse WILL NOT receive any review or updates from the Ubuntu
    28	## security team.
    29	deb http://au.archive.ubuntu.com/ubuntu/ precise multiverse
    30	deb-src http://au.archive.ubuntu.com/ubuntu/ precise multiverse
    31	deb http://au.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    32	deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    33	
    34	## N.B. software from this repository may not have been tested as
    35	## extensively as that contained in the main release, although it includes
    36	## newer versions of some applications which may provide useful features.
    37	## Also, please note that software in backports WILL NOT receive any review
    38	## or updates from the Ubuntu security team.
    39	
    40	deb http://security.ubuntu.com/ubuntu precise-security main restricted
    41	deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    42	deb http://security.ubuntu.com/ubuntu precise-security universe
    43	deb-src http://security.ubuntu.com/ubuntu precise-security universe
    44	deb http://security.ubuntu.com/ubuntu precise-security multiverse
    45	deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    46	
    47	## Uncomment the following two lines to add software from Canonical's
    48	## 'partner' repository.
    49	## This software is not part of Ubuntu, but is offered by Canonical and the
    50	## respective vendors as a service to Ubuntu users.
    51	# deb http://archive.canonical.com/ubuntu precise partner
    52	# deb-src http://archive.canonical.com/ubuntu precise partner
    53	
    54	## This software is not part of Ubuntu, but is offered by third-party
    55	## developers who want to ship their latest software.
    56	deb http://extras.ubuntu.com/ubuntu precise main
    57	deb-src http://extras.ubuntu.com/ubuntu precise main
```

That command did not get me into the software center, here is what the terminal spat out:

```
2012-11-11 09:42:25,394 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-11-11 09:42:26,105 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-11-11 09:42:26,215 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-11-11 09:42:26,220 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 145, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_sevenmachines_flash_ubuntu_dists_precise_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.
2012-11-11 09:42:28,817 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
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
Sorry for the long post, but I really have no idea what's relevent and what's not

---

### Post by ibjsb4 on 2012-11-10
Your sources.list is fine, so the problem is in sources.list.d.  In terminal:

cat -n /etc/apt/sources.list.d

And once again please post.

And we will get to the software center next.

---

### Post by aliasforme on 2012-11-10
here is what the terminal spat out:


```
cat: /etc/apt/sources.list.d: Is a directory
```

---

### Post by ibjsb4 on 2012-11-10
My mistake, that will not work.  Try this in terminal:

gksudo software-properties-gtk

---

### Post by aliasforme on 2012-11-10
that gave me a small window, see attachment. In the "other sources" tab I unchecked the boxes that corresponded with the 404 not found items (the 2 at the bottom, didn't touch anything else), see my other attachment. I then ran the get update command and I am now able to run the update manager, the software center also seems to run fine now:guitar:. Thanks for your help ibjsb4 :KS

---

### Post by ibjsb4 on 2012-11-10
Thats wild  :))

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

