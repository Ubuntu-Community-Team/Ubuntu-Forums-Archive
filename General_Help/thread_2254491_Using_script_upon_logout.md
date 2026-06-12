---
title: "Using script upon logout"
date: 2014-11-27
forum: General Help
---

### Post by dpedesigns on 2014-11-27
I created a script who was supposed to run when logging out from Ubuntu 14.04.

I created file ~/.config/upstart/desktopClose.conf

```
    description "Desktop Close Task"
    start on session-end
    task
    script
      firefox 'http://google.com'
    end script
```

This script does what it is intended to do. **However, my problem is that it's not available on guest session.**
[B]
To do list,[/B]

 
[LIST]
[*]- Make the script available to Guest Session. 
[/LIST]
 
I would love if somebody could help me make it available on guest session. Thanks in advance.

---

### Post by bashiergui on 2014-11-30
You choose "logout" and then the script launches firefox and goes to Google's page while or after you're logged out?

Nothing about a guest session is persistent. Guest user names are randomly generated for each session (guest-hndi28b) and then obliterated upon logout. So if the script is running in the context of the guest user it will fail because the guest user won't exist when it's calling the script. I don't really get what the script accomplishes except show in internet history that google was the last page visited. There won't be any internet history for the guest because it will cease existing upon logout.

---

