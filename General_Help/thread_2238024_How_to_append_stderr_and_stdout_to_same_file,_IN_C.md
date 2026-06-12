---
title: "How to append stderr and stdout to same file, IN CORRECT ORDER"
date: 2014-08-05
forum: General Help
---

### Post by bulrush2 on 2014-08-05
I want to append text to a file so it looks exactly as the output to the screen, for bug reporting purposes. The file should look like this: 

```
Samba version 4.1.6-Ubuntu
PID     Username      Group         Machine                        
-------------------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED

Service      pid     machine       Connected at
-------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED
Failed to traverse sessions: NT_STATUS_ACCESS_DENIED

No locked files

```

When I do this: smbstatus >> $outfile 2>&1

the errors and stdout are separated. 

```
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED
Failed to traverse sessions: NT_STATUS_ACCESS_DENIED

Samba version 4.1.6-Ubuntu
PID     Username      Group         Machine                        
-------------------------------------------------------------------

Service      pid     machine       Connected at
-------------------------------------------------------

No locked files

```

How do I append the text to a file so it looks exactly like the screen output? 

I've already looked at several web pages, all of which change the order of stderr. 

Thanks.

---

### Post by steeldriver on 2014-08-05
It's probably a matter of the different stream buffering defaults for terminal versus file output - I can't test your exact scenario, but try something like

```

**stdbuf -oL** smbstatus >> "$outfile" 2>&1

```

---

### Post by bulrush2 on 2014-08-05
Yep, that worked! Thanks.

---

