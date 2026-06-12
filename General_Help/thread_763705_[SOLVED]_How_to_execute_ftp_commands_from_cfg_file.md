---
title: "[SOLVED] How to execute ftp commands from cfg file?"
date: 2008-04-23
forum: General Help
---

### Post by abcuser on 2008-04-23
Hi,
I would like to execute ftp commands from script file, so I could put this script in crontab. My FTP commands are in script_file.cfg.

On Windows Server I do the following:
```

#command from scheduler:
ftp -i -n -s:script_file.cfg

# commands in script_file.cfg
open 192.168.100.100
user root root_pass
bin
cd /path/
lcd /path/
get file_i_would_like_go_get.txt
bye

```

What is the same procedure on Ubuntu?
Thanks,
Abcuser

---

### Post by abcuser on 2008-04-25
Hi,
I have solved the problem. Solution is at the bottom of web page:
[http://aruljohn.com/info/filetransfer/](http://aruljohn.com/info/filetransfer/)
Thanks,
Abcuser

---

