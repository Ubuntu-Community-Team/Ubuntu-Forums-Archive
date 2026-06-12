---
title: "How to install the GTK version of PCmanFM after doing a minimal install"
date: 2017-08-13
forum: General Help
---

### Post by automate-stuff on 2017-08-13
So I am doing a minimal installation of Ubuntu...I have installed my desktop environment ... now I am about to install the file manager ...Now there are two types of PCManFM (GTK and QT) , I want to install the GTK version....How do I do that ?

---

### Post by vocx on 2017-08-13
> **automate-stuff said:**
> So I am doing a minimal installation of Ubuntu...I have installed my desktop environment ... now I am about to install the file manager ...Now there are two types of PCManFM (GTK and QT) , I want to install the GTK version....How do I do that ?

I ran
```

user@user-laptop:~$ aptitude search pcman
p   pcmanfm                                            - extremely fast and lightweight file manager                  
p   pcmanfm:i386                                       - extremely fast and lightweight file manager                  
p   pcmanfm-dbg                                        - extremely fast and lightweight file manager (debug)          
p   pcmanfm-dbg:i386                                   - extremely fast and lightweight file manager (debug)          
p   pcmanfm-qt                                         - extremely fast and lightweight file and desktop icon manager 
p   pcmanfm-qt:i386                                    - extremely fast and lightweight file and desktop icon manager 
p   pcmanx-gtk2                                        - user-friendly telnet client mainly targets BBS users         
p   pcmanx-gtk2:i386                                   - user-friendly telnet client mainly targets BBS users  

```

So, I guess you need to run
```

sudo apt install pcmanfm

```

The description says it is the GTK+2 version.

---

