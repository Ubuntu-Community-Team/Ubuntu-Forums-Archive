---
title: "HowTo: Edit Kmenu Actions (remove/show run, logout, lock, switch user, etc..)"
date: 2008-06-16
forum: General Help
---

### Post by nowshining on 2008-06-16
(used kde 3.5.9)

HowTo: Edit Kmenu Actions (remove/show run, logout, lock, switch user, etc..)

edit (then logout & back in for it to take effect): (with your editor of choice): /home/USERNAME/.kde/share/config/kickerrc

& add anywhere (saving and closing the above file will make kde auto arrange it into its' right place & it puts the KDE actions in alphabitical order so don't get paranoid if the below moved to another place in the kickerrc file)

[KDE Action Restrictions]
lock_session=true #---> add/removes lock session button (true=show false=hide)
logout_session=true #--->add/removes the logout button (true=show false=hide)
run_command=false #--->removes the run command - remove to re-show the run command box as just setting false to true won't work.
start_new_session=false #--> disable start_new_session button (true=enables the ability to start a new session false=disables this ability and only shows the current session)
switch_user=false #---> removes the start new session button (true=show false=hide)

---

