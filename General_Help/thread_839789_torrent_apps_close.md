---
title: "torrent apps close"
date: 2008-06-24
forum: General Help
---

### Post by mutation on 2008-06-24
i have tried ktorrent, deluge and azureus and all three torrent apps randomly quit, no errors, not message in any logs i could find, i have searched the forums and tried every fix I could find with no solution. and one have any ideas where i should start? :confused:

---

### Post by graabein on 2008-07-02
I started Deluge today and got this error dump:

```
Traceback (most recent call last):
  File "/usr/bin/deluge", line 133, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 117, in start_deluge
    interface.start(get_cmd_line_torrents())
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1029, in start
    self.update()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1208, in update
    self.update_torrent_info_widget()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1282, in update_torrent_info_widget
    self.tab_details.update(unique_id)
  File "/var/lib/python-support/python2.5/deluge/tab_details.py", line 173, in update
    self.paint_customprogress()
  File "/var/lib/python-support/python2.5/deluge/tab_details.py", line 82, in paint_customprogress
    gc = progress_window.new_gc()
AttributeError: 'NoneType' object has no attribute 'new_gc'

```

---

