---
title: "XSANE problem with authentication"
date: 2005-10-05
forum: General Help
---

### Post by zalun on 2005-10-05
I installed scanner 
It works ok if I use scanimage program through the net with a user and pass (as it should be).
I wrote a ~/.sane/pass correctly and it works without asking for a password.
I use a command: 
```
SANE_DEFAULT_DEVICE='net:192.168.1.134:mustek_pp' scanimage --resolution 150dpi --format tiff -v --mode gray 
```

If I use xsane it of course doesn't ask for a password.
I choose Acquire Preview.
It acquires and displays acquired image.
After that it asks for another password ...
Two wrong entries and it destroys itself.


[edit]
After a while I found that xsane scans the whole image but only into gimp - run from commandline it just hangs up.
[/edit]

verbose info:
```

[sanei_debug] Setting debug level of net to 255.
[net] sane_init: authorize = 0x805414c, version_code = 0xbfffe46c
[net] sane_init: SANE net backend version 1.0.13 (AF-indep+IPv6) from sane-backends 1.0.15
[net] sane_init: Client has little endian byte order
[net] sane_init: searching for config file
[net] sane_init: trying to add localhost
STANDARD NET AUTHORIZATION
[net] add_device: adding backend localhost
[net] add_device: backend localhost added
[net] sane_init: done reading config
[net] sane_init: evaluating environment variable SANE_NET_HOSTS
[net] sane_init: done
[net] sane_get_devices: local_only = 0
[net] connect_dev: trying to connect to localhost
[net] connect_dev: [0] connection succeeded (IPv4)
[net] connect_dev: sanei_w_init
[net] connect_dev: net_init (user=zalun, local version=1.0.3)
[net] connect_dev: freeing init reply (status=Success, remote version=1.0.3)
[net] connect_dev: done
[net] sane_get_devices: got localhost:mustek_pp:mustek-cis600
[net] sane_get_devices: finished (1 devices)
[net] sane_open("localhost:mustek_pp:mustek-cis600")
[net] sane_open: host = localhost, device = mustek_pp:mustek-cis600
[net] sane_open: device found in list
[net] sane_open: net_open
[net] sane_open: authorization required
[net] do_authorization: dev=0x81a90d0 resource=mustek_pp$MD5$1d7b4343642e76612f30
[net] do_authorization: invoking auth_callback, resource = net:localhost:mustek_pp$MD5$1d7b4343642e76612f30
[net] do_authorization: relaying authentication data
[net] sane_open: success
[...]

AFTER THAT I CLICK ON AQUIRE PREVIEW
AFTER SCANNING (it displays in window) XSANE ASKS FOR A PASSWORD TWO TIMES

[...]
[net] sane_control_option: option 4, action 1
[net] sane_control_option: remote control option
[net] sane_control_option: auth required
[net] do_authorization: dev=0x81a6fa8 resource=
[net] do_authorization: invoking auth_callback, resource = net:localhost:
[net] do_authorization: relaying authentication data
[net] sane_control_option: auth required
[net] do_authorization: dev=0x81a6fa8 resource\uffff$
[net] do_authorization: invoking auth_callback, resource = net:localhost\uffff$

(xsane:7470): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()
[net] do_authorization: relaying authentication data
[net] sane_control_option: auth required
[net] do_authorization: dev=0x81a6fa8 resource=\uffff\uffff*
[net] do_authorization: invoking auth_callback, resource = net:localhost:\uffff\uffff*
Naruszenie ochrony pamieci (segfault)

AND SEGMENTATION FAULT

```

---

