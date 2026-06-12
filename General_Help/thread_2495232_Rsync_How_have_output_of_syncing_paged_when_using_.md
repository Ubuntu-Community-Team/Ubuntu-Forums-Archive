---
title: "Rsync: How have output of syncing paged when using --dry-run"
date: 2024-02-12
forum: General Help
---

### Post by makem2 on 2024-02-12
I am using the following command:

sudo /usr/bin/rsync --dry-run -avx --delete --append-verify /media/makem/Windows/ pi@192.168.1.222:/media/pi/HDD1/shares/newPCwindows/

It completes without errors but I want to check the output page by page. Where in that command would I add '[COLOR=#0C0D0E][FONT=ui-monospace]ls | less' to give me a paged output?[/FONT][/COLOR]

---

### Post by SeijiSensei on 2024-02-12
I'd send it all to a file with "> some_file_name" at the end of the command and browse the result afterward.

---

### Post by makem2 on 2024-02-12
Thank you

---

### Post by TheFu on 2024-02-12
Redirecting stdout is easy.  Sometimes programs throw their output to stderr instead, so you would want to redirect both stdout AND stderr to the file.  [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) is a README full of information for handling different things in a shell.  I re-read it every year, since I'm not ready to learn some things.  There's always something that I missed that was there in prior years, but I wasn't ready to use it.

---

