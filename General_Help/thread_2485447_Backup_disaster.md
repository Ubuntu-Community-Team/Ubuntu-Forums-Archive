---
title: "Backup disaster"
date: 2023-03-29
forum: General Help
---

### Post by jgw on 2023-03-29
I just spent two whole days backing up stuff.  It was a little bit more than 2tb long.  After the backup the program deleted every file that was backed up.  It get better!

I then tried to restore.  There is about 22218 files in one of the folders backed up.  Apparently there are over 800 videos that backup doesn't have the authority to restore.  There were only two folders backed up.  One is missing the ability to restore because it doesn't have permission the other one  Had an unknown air and couldn't restore.  

I also suspect I am going to need to know how to open the backups so I can open them and reconstitute.

Here is why the second folder can't be restored because of an unknown reason (displayed below):

```
Traceback (innermost last):
  File "/usr/bin/duplicity", line 92, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 75, in with_tempdir
    fn()
  File "/usr/lib/python3/dist-packages/duplicity/dup_main.py", line 1555, in main
    action = commandline.ProcessCommandLine(sys.argv[1:])
  File "/usr/lib/python3/dist-packages/duplicity/commandline.py", line 1248, in ProcessCommandLine
    process_local_dir(action, local_pathname)
  File "/usr/lib/python3/dist-packages/duplicity/commandline.py", line 1117, in process_local_dir
    local_path = path.Path(path.Path(local_pathname).get_canonical())
  File "/usr/lib/python3/dist-packages/duplicity/path.py", line 541, in __init__
    self.setdata()
  File "/usr/lib/python3/dist-packages/duplicity/path.py", line 551, in setdata
    self.stat = os.lstat(self.name)
 OSError: [Errno 5] Input/output error: b'/mnt/3tb/Movies'
```

I would appreciate any thoughts anybody has on this one.

---

### Post by jgw on 2023-04-02
I guess there is nothing more to say.  For some reason gparted recognized the file and I got it fixed.

Beware the backup program that comes with ubuntu......................

---

### Post by HermanAB on 2023-04-02
Yup, I learned many moons ago to make my own backup script using rsync, so that the backup is a simple bunch of files that can be restored without requiring special tools.

---

