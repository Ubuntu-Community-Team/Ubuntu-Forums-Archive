---
title: "Anyone using Mullvad on 17.04"
date: 2017-04-13
forum: General Help
---

### Post by saiyon on 2017-04-13
On a clean install of Ubuntu or Ubuntu-Gnome I install gdebi and then Mullvad (download deb from their website).

When I fire up Mullvad it does not run / ask me for my customer number. The process stays alive though and has to be manually killed.

It works fine in Xubuntu 17.04.

I have emailed them a support ticket and if I get a fix will post here but thought I would reach out to the community as well.

Cheers

Saiyon

---

### Post by howefield on 2017-04-14
Can't give you a solution except for to confirm the issue.

Did you start from the terminal, might be worth including the output in your support ticket ?

```
mullvad 
Using GTK2
changing directory to /usr/lib/python2.7/dist-packages/mullvad
Setting logging directory to /home/hugh/.cache/mullvad/log

(mullvad:10715): Gtk-WARNING **: gtk_disable_setlocale() must be called before gtk_init()
Setting logging directory to /home/hugh/.cache/mullvad/log
CRITICAL: An uncaught exception occured: Traceback (most recent call last):
  File "/usr/bin/mtunnel", line 9, in <module>
    load_entry_point('mullvad==62', 'console_scripts', 'mtunnel')()
  File "/usr/lib/python2.7/dist-packages/mullvad/tunnelprocess.py", line 126, in main
    main_args(args)
  File "/usr/lib/python2.7/dist-packages/mullvad/tunnelprocess.py", line 116, in main_args
    tp = TunnelProcess(pipe_dir, settings, args.confdir)
  File "/usr/lib/python2.7/dist-packages/mullvad/tunnelprocess.py", line 41, in __init__
    self.tunnel = mtunnel.Tunnel(settings, conf_dir)
  File "/usr/lib/python2.7/dist-packages/mullvad/mtunnel.py", line 142, in __init__
    self.route_manager = route.get_route_manager()
  File "/usr/lib/python2.7/dist-packages/mullvad/route.py", line 33, in get_route_manager
    return RouteManager()
  File "/usr/lib/python2.7/dist-packages/mullvad/route.py", line 256, in __init__
    self.gw = _find_default_gateway()
  File "/usr/lib/python2.7/dist-packages/mullvad/route.py", line 401, in _find_default_gateway
    routing_table = proc.run_assert_ok(['netstat', '-r', '-n'])
  File "/usr/lib/python2.7/dist-packages/mullvad/proc.py", line 49, in run_assert_ok
    return _get_proc().run_assert_ok(args, stdin)
  File "/usr/lib/python2.7/dist-packages/mullvad/proc.py", line 194, in run_assert_ok
    (code, stdout, stderr) = self.run(args, stdin)
  File "/usr/lib/python2.7/dist-packages/mullvad/proc.py", line 173, in run
    proc = self.open(args)
  File "/usr/lib/python2.7/dist-packages/mullvad/proc.py", line 148, in open
    **hide_window)
  File "/usr/lib/python2.7/subprocess.py", line 390, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1024, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
```

---

### Post by saiyon on 2017-04-14
Confirmed exactly the same problem. I re-installed ubuntu-gnome 16.04 and all works again.

Have a feeling mullvad will only support the LTS version. They haven't got back to me yet.

---

### Post by saiyon on 2017-04-19
Update:

Seems that Ubuntu 17.04 does not install netstat.

Therefore run:

sudo apt-get install net-tools

This should work.

---

### Post by saiyon on 2017-04-19
Sorry forgot to add that Mullvad support have been responsive and helpful!

---

