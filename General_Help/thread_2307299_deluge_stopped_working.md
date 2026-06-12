---
title: "deluge stopped working"
date: 2015-12-23
forum: General Help
---

### Post by sag3 on 2015-12-23
my deluge bit torrent client stopped working after direct power loss. due to that problem i had to fsck my drive manually after successfully booting up everything is working fine but except deluge.
i tried to run it from terminal and got this error 
```
Traceback (most recent call last):
  File "/usr/bin/deluge", line 9, in <module>
    load_entry_point('deluge==1.3.12', 'gui_scripts', 'deluge')()
  File "/usr/lib/python2.7/dist-packages/pkg_resources/__init__.py", line 558, in load_entry_point
    return get_distribution(dist).load_entry_point(group, name)
  File "/usr/lib/python2.7/dist-packages/pkg_resources/__init__.py", line 2682, in load_entry_point
    return ep.load()
  File "/usr/lib/python2.7/dist-packages/pkg_resources/__init__.py", line 2355, in load
    return self.resolve()
  File "/usr/lib/python2.7/dist-packages/pkg_resources/__init__.py", line 2361, in resolve
    module = __import__(self.module_name, fromlist=['__name__'], level=0)
ImportError: No module named deluge.main
```
please help me.

i tried removing and installing it again 
sudo apt-get remove deluge-torrent
sudo apt-get install deluge-torrent
but it did not worked for me.

then tried removing 
~/.config/deluge/torrentview.state
but still getting same error please help me to solve this.

---

