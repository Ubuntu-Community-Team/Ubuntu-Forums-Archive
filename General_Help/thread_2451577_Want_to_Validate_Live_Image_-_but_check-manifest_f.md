---
title: "Want to Validate Live Image - but check-manifest fails."
date: 2020-10-07
forum: General Help
---

### Post by ngj9 on 2020-10-07
Hello, 

I have downloaded [groovy-desktop-amd64.iso]("http://cdimage.ubuntu.com/daily-live/current/groovy-desktop-amd64.iso") and dd'd to usb drive, composing this message in Firefox on the live install. 

I wanted to validate this against [groovy-desktop-amd64.manifest]("http://cdimage.ubuntu.com/daily-live/current/groovy-desktop-amd64.manifest")

I downloaded check-manifest with apt

```
[COLOR=#26A269]**ubuntu@ubuntu**[/COLOR]:[COLOR=#12488B]**~/Desktop**[/COLOR]$ sudo apt install check-manifest
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  python3-toml
The following NEW packages will be installed:
  check-manifest python3-toml
0 upgraded, 2 newly installed, 0 to remove and 111 not upgraded.
Need to get 38.0 kB of archives.
After this operation, 165 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu groovy/universe amd64 python3-toml all 0.10.1-1 [16.0 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu groovy/universe amd64 check-manifest all 0.40-1 [22.1 kB]
Fetched 38.0 kB in 1s (65.2 kB/s)
Selecting previously unselected package python3-toml.
(Reading database ... 193759 files and directories currently installed.)
Preparing to unpack .../python3-toml_0.10.1-1_all.deb ...
Unpacking python3-toml (0.10.1-1) ...
Selecting previously unselected package check-manifest.
Preparing to unpack .../check-manifest_0.40-1_all.deb ...
Unpacking check-manifest (0.40-1) ...
Setting up python3-toml (0.10.1-1) ...
Setting up check-manifest (0.40-1) ...
Processing triggers for man-db (2.9.3-2) ...
[COLOR=#26A269]**ubuntu@ubuntu**[/COLOR]:[COLOR=#12488B]**~/Desktop**[/COLOR]$ check-m
[COLOR=#26A269]**ubuntu@ubuntu**[/COLOR]:[COLOR=#12488B]**~/Desktop**[/COLOR]$ check-m
check-manifest          check-missing-firmware  
[COLOR=#26A269]**ubuntu@ubuntu**[/COLOR]:[COLOR=#12488B]**~/Desktop**[/COLOR]$ check-manifest 
Traceback (most recent call last):
  File "/usr/bin/check-manifest", line 11, in <module>
    load_entry_point('check-manifest==0.40', 'console_scripts', 'check-manifest')()
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 488, in load_entry_point
    return get_distribution(dist).load_entry_point(group, name)
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 2861, in load_entry_point
    return ep.load()
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 2461, in load
    return self.resolve()
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 2467, in resolve
    module = __import__(self.module_name, fromlist=['__name__'], level=0)
  File "/usr/lib/python3/dist-packages/check_manifest.py", line 33, in <module>
    from distutils.filelist import glob_to_re
ModuleNotFoundError: No module named 'distutils.filelist'
[COLOR=#26A269]**ubuntu@ubuntu**[/COLOR]:[COLOR=#12488B]**~/Desktop**[/COLOR]$ sudo check-manifest 
Traceback (most recent call last):
  File "/usr/bin/check-manifest", line 11, in <module>
    load_entry_point('check-manifest==0.40', 'console_scripts', 'check-manifest')()
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 488, in load_entry_point
    return get_distribution(dist).load_entry_point(group, name)
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 2861, in load_entry_point
    return ep.load()
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 2461, in load
    return self.resolve()
  File "/usr/lib/python3/dist-packages/pkg_resources/__init__.py", line 2467, in resolve
    module = __import__(self.module_name, fromlist=['__name__'], level=0)
  File "/usr/lib/python3/dist-packages/check_manifest.py", line 33, in <module>
    from distutils.filelist import glob_to_re
ModuleNotFoundError: No module named 'distutils.filelist'

```

Here's crash reports from /var/crash

[https://pastebin.com/NzZHJYyp](https://pastebin.com/NzZHJYyp)

[https://pastebin.com/pD1eYVvC](https://pastebin.com/pD1eYVvC)

---

### Post by deadflowr on 2020-10-07
check-manifest is irrelevant to what you want to do.
That checks manifest for Python projects.
For image validity check the hashsum.
For hashsum verification check the gpg.

See:
[https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview]("https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview")

When you boot the image it'll run a validity check to make sure the integrity is uncorrupted.

---

