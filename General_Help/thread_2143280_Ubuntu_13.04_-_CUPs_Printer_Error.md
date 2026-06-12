---
title: "Ubuntu 13.04 - CUPs Printer Error"
date: 2013-05-08
forum: General Help
---

### Post by siabost on 2013-05-08
Hi,

On a fresh install of Ubuntu 13.04, Unity I managed to connect to my network Epson Printer and print just fine.
Since then something has gone wrong and when I try to install my network (print-server) printer I get the following error: "There was an error during the CUPS operation: 'server-error-internal-error'."

Using the Printer Config Utility's Trouble Shooter I get this: "Page 1 (Scheduler not running?):
> {'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dests_available': [], 'cups_queue_listed': False}
Page 3 (Local or remote?):
{'printer_is_remote': True}
Page 4 (Remote address):
{'remote_server_ip_address': '192.168.1.150', 'remote_server_name': ''}
Page 5 (Check network server sanity):
{'remote_server_connect_ipp': True,
 'remote_server_cups': False,
 'remote_server_name_resolves': ['192.168.1.150',
                                 '192.168.1.150',
                                 '192.168.1.150'],
 'remote_server_try_connect': '192.168.1.150'}
Page 6 (Locale issues):
{'printer_page_size': None,
 'system_locale_lang': None,
 'user_locale_ctype': 'en_GB',
 'user_locale_messages': 'en_GB'}

Running from Terminal (system-config-printer), I get this:
> :~$ system-config-printer
Caught non-fatal exception.  Traceback:
File "/usr/share/system-config-printer/probe_printer.py", line 253, in _do_find
    fn ()
File "/usr/share/system-config-printer/probe_printer.py", line 281, in _probe_snmp
    stderr=null)
File "/usr/lib/python2.7/subprocess.py", line 711, in __init__
    errread, errwrite)
File "/usr/lib/python2.7/subprocess.py", line 1308, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
Continuing anyway..
Caught non-fatal exception.  Traceback:
File "/usr/share/system-config-printer/probe_printer.py", line 253, in _do_find
    fn ()
File "/usr/share/system-config-printer/probe_printer.py", line 365, in _probe_hplip
    stderr=null)
File "/usr/lib/python2.7/subprocess.py", line 711, in __init__
    errread, errwrite)
File "/usr/lib/python2.7/subprocess.py", line 1308, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
Continuing anyway..
Caught non-fatal exception.  Traceback:
File "/usr/share/system-config-printer/probe_printer.py", line 410, in _probe_smb
    smbc_auth.failed (e)
File "/usr/share/system-config-printer/pysmb.py", line 182, in failed
    raise exc
NoEntryError: (2, 'No such file or directory')
Continuing anyway..

I must have changed something somewhere.
Can anyone help?

Many thanks.

---

### Post by ShermW0829 on 2013-05-09
The same thing just happened here. 

Sherman

---

### Post by tgalati4 on 2013-05-09
Did you perform any updates in the past few days?  Many times, updates will break CUPS out of the blue.

---

### Post by ShermW0829 on 2013-05-10
I can perform %sudo cupsd -l and that works but I assume the life is only for the time the terminal is active.

Sherman

---

### Post by tgalati4 on 2013-05-11
Check to see if you have *avahi-daemon* installed.  A recent update to cups which adds avahi-daemon should fix cups from not starting.

---

### Post by ShermW0829 on 2013-05-11
The avahi-daemon seemed to fix this for me. I rebooted and cupsd -F started automatically.

Thank you;

Sherman

---

