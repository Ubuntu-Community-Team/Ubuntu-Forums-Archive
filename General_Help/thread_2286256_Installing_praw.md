---
title: "Installing praw"
date: 2015-07-11
forum: General Help
---

### Post by huff2 on 2015-07-11
Hi all,
I recently installe pip and am now trying  to install praw. I'm using pip install praw but I'm getting this error:         [FONT=monospace][COLOR=#b21818]Exception:[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#b21818]Traceback (most recent call last):                      [/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#b21818]  File "/usr/local/lib/python2.7/dist-packages/pip/basec[/COLOR]
ommand.py", line 223, in main                           [COLOR=#000000] [/COLOR]
[COLOR=#b21818]    status = self.run(options, args)                    [/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#b21818]  File "/usr/local/lib/python2.7/dist-packages/pip/comma[/COLOR]
nds/install.py", line 299, in run                       [COLOR=#000000] [/COLOR]
[COLOR=#b21818]    root=options.root_path,                             [/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#b21818]  File "/usr/local/lib/python2.7/dist-packages/pip/req/r[/COLOR]
eq_set.py", line 646, in install                        [COLOR=#000000] [/COLOR]
[COLOR=#b21818]    **kwargs                                            [/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#b21818]  File "/usr/local/lib/python2.7/dist-packages/pip/req/r[/COLOR]
eq_install.py", line 813, in install                    [COLOR=#000000] [/COLOR]
[COLOR=#b21818]    self.move_wheel_files(self.source_dir, root=root)   [/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#b21818]  File "/usr/local/lib/python2.7/dist-packages/pip/req/r[/COLOR]
eq_install.py", line 1008, in move_wheel_files          [COLOR=#000000] [/COLOR]
[COLOR=#b21818]    isolated=self.isolated,                             [/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#b21818]  File "/usr/local/lib/python2.7/dist-packages/pip/wheel[/COLOR]
.py", line 339, in move_wheel_files                     [COLOR=#000000] [/COLOR]
[COLOR=#b21818]    clobber(source, lib_dir, True)                      [/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#b21818]  File "/usr/local/lib/python2.7/dist-packages/pip/wheel[/COLOR]
.py", line 317, in clobber                              [COLOR=#000000] [/COLOR]
[COLOR=#b21818]    shutil.copyfile(srcfile, destfile)                  [/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#b21818]  File "/usr/lib/python2.7/shutil.py", line 83, in copyf[/COLOR]
ile                                                     [COLOR=#000000] [/COLOR]
[COLOR=#b21818]    with open(dst, 'wb') as fdst:                       [/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#b21818]IOError: [Errno 13] Permission denied: '/usr/local/lib/p[/COLOR]
ython2.7/dist-packages/update_checker_test.pyc'  
[/FONT]

---

### Post by huff2 on 2015-07-11
I fixed it. I used sudo pip install praw instead.

---

