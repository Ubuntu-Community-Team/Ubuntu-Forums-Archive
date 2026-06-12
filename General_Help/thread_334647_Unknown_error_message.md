---
title: "Unknown error message"
date: 2007-01-09
forum: General Help
---

### Post by paulyche on 2007-01-09
I keep getting strange (kernel?) error messages outputting to the terminal when I have a terminal open. There doesn't seem to be any other effect...

Any ideas?

```

Message from syslogd@paul-desktop at Tue Jan  9 13:17:25 2007 ...
paul-desktop kernel: [17184258.636000] Bad page state in process 'Xorg'

Message from syslogd@paul-desktop at Tue Jan  9 13:17:25 2007 ...
paul-desktop kernel: [17184258.636000] page:c18d8a00 flags:0xc0000000 mapping:00000000 mapcount:-32 count:0

Message from syslogd@paul-desktop at Tue Jan  9 13:17:25 2007 ...
paul-desktop kernel: [17184258.636000] Trying to fix it up, but a reboot is needed

Message from syslogd@paul-desktop at Tue Jan  9 13:17:25 2007 ...
paul-desktop kernel: [17184258.636000] Backtrace:

```

---

### Post by paulyche on 2007-01-10
bump

---

### Post by paulyche on 2007-01-11
I think I've solved the problem. Seems to be a faulty RAM chip.

---

