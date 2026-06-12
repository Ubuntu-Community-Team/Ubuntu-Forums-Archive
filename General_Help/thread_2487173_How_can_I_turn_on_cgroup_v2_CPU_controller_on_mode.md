---
title: "How can I turn on cgroup v2 CPU controller on modern Ubuntu?"
date: 2023-05-26
forum: General Help
---

### Post by jenyakh on 2023-05-26
[SIZE=4][COLOR=#232629][FONT=-apple-system]On Ubuntu 22.04, I get:
[/FONT][/COLOR][/SIZE]
```

[SIZE=3]# cat /sys/fs/cgroup/cgroup.controllers

cpuset memory hugetlb pids rdma misc[/SIZE]

```

[SIZE=4][COLOR=#232629][FONT=-apple-system]I really need **cpu** contoller. Could you, please, help on how to enable it?[/FONT][/COLOR][/SIZE]

---

### Post by jenyakh on 2023-05-26
[COLOR=#232629][FONT=-apple-system]As explained here [/FONT][/COLOR][https://serverfault.com/a/931180/518713](https://serverfault.com/a/931180/518713)[COLOR=#232629][FONT=-apple-system] an [/FONT][/COLOR][https://unix.stackexchange.com/a/635645/346609](https://unix.stackexchange.com/a/635645/346609)[COLOR=#232629][FONT=-apple-system] I needed just to add [/FONT][/COLOR]cgroup_no_v1=all[COLOR=#232629][FONT=-apple-system] as a kernel boot option in my grub config and update grub, and reboot. And here it is. None legacy [/FONT][/COLOR]cpu[COLOR=#232629][FONT=-apple-system] is mounted as cgroup v1. So it becomes available for cgroup v2.[/FONT][/COLOR]

---

