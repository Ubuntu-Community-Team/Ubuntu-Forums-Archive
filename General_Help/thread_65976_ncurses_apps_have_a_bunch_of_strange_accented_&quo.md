---
title: "ncurses apps have a bunch of strange accented &quot;a&quot; characters"
date: 2005-09-15
forum: General Help
---

### Post by dunja on 2005-09-15
any idea why ncurses apps display like this?
```
                                                                                
                                                                                
     â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”¤ rcconf - Debian Runlevel Configuration toolâ”‚                                                                    â”‚ 
     â”‚    [*] acpi-support                                            #   â”‚ 
     â”‚    [*] acpid                                                   â–’   â”‚    â”‚    [*] alsa                                                    â–’   â”‚    â”‚    [*] apmd                                                    â–’   â”‚    â”‚    [*] atd                                                     â–’   â”‚    â”‚    [*] cron                                                    â–’   â”‚    â”‚    [*] dbus-1                                                  â–’   â”‚    â”‚    [*] gdm                                                     â–’   â”‚    â”‚    [*] gpm                                                     â–’   â”‚    â”‚    [*] inetd                                                   â–’   â”‚    â”‚                                                                    â”‚ 
     â”‚                                                                    â”‚ 
     â”‚                                                                    â”‚ 
     â”‚                                                                    â”‚ 
     â”‚                                                                    â”‚ 
     â”‚                 <Ok>                     <Cancel>                  â”‚ 
     â”‚                                                                    â”‚ 
     â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€                                                                      ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜                         
```
it happens with aterm (my terminal of preference), but not gnome-terminal.

---

### Post by dunja on 2005-09-17
i found the problem.  the virtual terminals i was using (aterm, rxvt) didn't support unicode.  i'm using rxvt-unicode now.

---

