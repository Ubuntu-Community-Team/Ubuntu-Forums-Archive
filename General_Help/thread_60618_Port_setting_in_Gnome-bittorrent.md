---
title: "Port setting in Gnome-bittorrent"
date: 2005-08-28
forum: General Help
---

### Post by Trojan1313 on 2005-08-28
I know I can use gnome-btdownload some-option to set the port range, but how do I set a default port-range for gnome-bittorrent?

---

### Post by nevienc on 2005-09-12
[QUOTE=Trojan1313]I know I can use gnome-btdownload some-option to set the port range, but how do I set a default port-range for gnome-bittorrent?[/QUOTE]
 I used 
```
gnome-btdownload --minport 1234 --maxport 1234
```

but I get:
```
Traceback (most recent call last):
  File "/usr/bin/gnome-btdownload", line 979, in ?
    run(sys.argv[1:])
  File "/usr/bin/gnome-btdownload", line 974, in run
    client = GtkClient(args)
  File "/usr/bin/gnome-btdownload", line 667, in __init__
    previous_save_location = check_for_previous_save_location(bt_state_args)
  File "/usr/bin/gnome-btdownload", line 615, in check_for_previous_save_location
    digest     = sha.new(get_url(bt_state_args.path_origin, max_torrent_size)).hexdigest()
  File "/usr/bin/gnome-btdownload", line 103, in get_url
    handle = gnomevfs.open(uri, gnomevfs.OPEN_READ)
gnomevfs.InvalidURIError: Invalid URI
``` ](*,)

---

### Post by virka on 2005-10-16
I am having the same problem.

Can anyone provide some help please?

martin@ubuntu:~$ gnome-btdownload --minport 6001 --maxport 6100
Traceback (most recent call last):
  File "/usr/bin/gnome-btdownload", line 981, in ?
    run(sys.argv[1:])
  File "/usr/bin/gnome-btdownload", line 976, in run
    client = GtkClient(args)
  File "/usr/bin/gnome-btdownload", line 667, in __init__
    previous_save_location = check_for_previous_save_location(bt_state_args)
  File "/usr/bin/gnome-btdownload", line 615, in check_for_previous_save_location
    digest     = sha.new(get_url(bt_state_args.path_origin, max_torrent_size)).hexdigest()
  File "/usr/bin/gnome-btdownload", line 103, in get_url
    handle = gnomevfs.open(uri, gnomevfs.OPEN_READ)
gnomevfs.InvalidURIError: Invalid URI

---

### Post by yanokwa on 2007-05-27
try min_port and max_port

---

