---
title: "rdiff-backup  File &amp;amp;amp;amp;quot;/usr/bin/rdiff-backup&amp;amp;amp;amp;quot;, line 23, in &amp;amp;am"
date: 2007-10-21
forum: General Help
---

### Post by be4truth on 2007-10-21
Hi Everybody,

I am running Gutsy 64bit. I get this error running rdiff-backup:

Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 23, in <module>
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
AttributeError: 'module' object has no attribute 'error_check_Main'

History:
I had some machines with older OS on the network. All the network was on rdiff-backup 1.0.4 or 1.0.5
Since there wasn't a version available for Ubuntu (this is the stable version) I installed rdiff-backup as tar.gz, extracted it in /opt and this was running fine. Now all the old rediff-machines are replaced by ubuntu mainly and i want to shift rdiff-backup here on my machine as well. I removed /usr/bin/rdiff-backup and  /usr/bin/rdiff-backup-statistics . Then I installed rdiff-backup 1.1.14-1 but get the above error.
Any idea what that is. Thx in advance for every help.

---

### Post by be4truth on 2007-10-22
I install version 1.1.14 as tar.gz . Running it shows this error:

Unable to import module xattr.
Extended attributes not supported on filesystem at /home
Unable to import module posix1e from pylibacl package.
ACLs not supported on filesystem at /home
Exception 'need more than 3 values to unpack' raised of class '<type 'exceptions.ValueError'>':
  File "/usr/lib/python2.5/site-packages/rdiff_backup/Main.py", line 302, in error_check_Main
    try: Main(arglist)
  File "/usr/lib/python2.5/site-packages/rdiff_backup/Main.py", line 322, in Main
    take_action(rps)
  File "/usr/lib/python2.5/site-packages/rdiff_backup/Main.py", line 278, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/usr/lib/python2.5/site-packages/rdiff_backup/Main.py", line 332, in Backup
    rpout.conn.fs_abilities.backup_set_globals(rpin)
  File "/usr/lib/python2.5/site-packages/rdiff_backup/fs_abilities.py", line 697, in backup_set_globals
    src_fsa = rpin.conn.fs_abilities.get_readonly_fsa('source', rpin)
  File "/usr/lib/python2.5/site-packages/rdiff_backup/connection.py", line 447, in __call__
    return apply(self.connection.reval, (self.name,) + args)
  File "/usr/lib/python2.5/site-packages/rdiff_backup/connection.py", line 367, in reval
    result = self.get_response(req_num)
  File "/usr/lib/python2.5/site-packages/rdiff_backup/connection.py", line 314, in get_response
    try: req_num, object = self._get()
  File "/usr/lib/python2.5/site-packages/rdiff_backup/connection.py", line 240, in _get
    if format_string == "o": result = cPickle.loads(data)
  File "/usr/lib/python2.5/site-packages/rdiff_backup/rpath.py", line 765, in __setstate__
    conn_number, self.base, self.index, self.data = rpath_state

After trying around a bit - no solutions. I am back to the 1.0.5 version which works without problems.

---

