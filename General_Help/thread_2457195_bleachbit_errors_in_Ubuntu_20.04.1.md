---
title: "bleachbit errors in Ubuntu 20.04.1"
date: 2021-01-27
forum: General Help
---

### Post by jay-eich on 2021-01-27
Greetings!

I have been using bleachbit for many years without a problem. I am careful with the options..
Today, I saw some error messages, when I wes exploring 'dignostics' under the settings tab.

The errors showed up in the terminal window where I did a 'sudo bleachbit.'

```
Automatically preserving language en.
Traceback (most recent call last):
  File "/usr/share/bleachbit/bleachbit/GUI.py", line 334, in diagnostic_dialog
    dialog = self.get_diagnostics_dialog()
  File "/usr/share/bleachbit/bleachbit/GUI.py", line 321, in get_diagnostics_dialog
    txt = Diagnostic.diagnostic_info()
  File "/usr/share/bleachbit/bleachbit/Diagnostic.py", line 89, in diagnostic_info
    s += "\nplatform.dist() = %s" % str(platform.dist())
AttributeError: module 'platform' has no attribute 'dist'

```

Just to check, I ran bleachbit without sudo; selected diagnostics, and the same errors occurred.

 it looks like the --sysinfo option uses the same code...
It gets these errors:
```
bleachbit  --sysinfo
Automatically preserving language en.
Traceback (most recent call last):
  File "/usr/bin/bleachbit", line 48, in <module>
    bleachbit.CLI.process_cmd_line()
  File "/usr/share/bleachbit/bleachbit/CLI.py", line 250, in process_cmd_line
    print(Diagnostic.diagnostic_info())
  File "/usr/share/bleachbit/bleachbit/Diagnostic.py", line 89, in diagnostic_info
    s += "\nplatform.dist() = %s" % str(platform.dist())
AttributeError: module 'platform' has no attribute 'dist'
```


Other:
MATE 1.24.0
Kernel Linux 5.4.0-65-generic x86_64

without those options, bleachbit runs great.

Question:
Should I use launchpad and report a bug?

Thanks in advance,
Jay
;)

---

