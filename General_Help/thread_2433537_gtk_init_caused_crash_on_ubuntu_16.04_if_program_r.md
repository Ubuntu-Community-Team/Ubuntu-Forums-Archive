---
title: "gtk_init caused crash on ubuntu 16.04 if program run without sudo"
date: 2019-12-20
forum: General Help
---

### Post by andrey-kurulev on 2019-12-20
[COLOR=#242729][FONT=Arial]gtk_init caused crash on ubuntu 16.04 if run program without sudo. If run with sudo, then have not problem. On other ubuntu versions also have not problem with and without sudo.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Minimally reproducible example:
[/FONT][/COLOR]
```

[FONT=courier new]#include<gtk/gtk.h>

int main(int argc,char* argv[])
{
    gtk_init (&argc,&argv);

    for(int i =0; i <10;++i)
[/FONT][FONT=courier new]    {
[/FONT][FONT=courier new]        printf("%d\n", i);
[/FONT][FONT=courier new]        usleep(1000*1000);
[/FONT][FONT=courier new]    }

[/FONT][FONT=courier new]    return 0;
}
[/FONT]
```

[COLOR=#242729][FONT=Arial]Stacktrace:
[/FONT][/COLOR]
```

[FONT=courier new]Thread2"dconf worker" received signal SIGSEGV,Segmentation fault.
[Switching to Thread0xb6567b40(LWP 6735)]
0xb71bbfd0 in g_source_set_ready_time () from /lib/i386-linux-gnu/libglib-2.0.so.0
(gdb) bt
#0  0xb71bbfd0 in g_source_set_ready_time () from /lib/i386-linux-gnu/libglib-2.0.so.0
#1  0xb73e8bf4 in g_task_get_type () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#2  0xb744b6a0 in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#3  0xb743eb00 in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#4  0xb73bd0e9 in g_initable_init () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#5  0xb743f230 in g_bus_get_sync () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#6  0xb668c314 in ?? () from /usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so
#7  0xb668c423 in ?? () from /usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so
#8  0x0807e22a in g_main_context_dispatch ()
#9  0x0807e638 in g_main_context_iterate.isra ()
#10 0x0807e700 in g_main_context_iteration ()
#11 0xb668c58b in ?? () from /usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so
#12 0x0809eabd in g_thread_proxy ()
#13 0xb7aaf295 in start_thread (arg=0xb6567b40) at pthread_create.c:333
#14 0xb79d10ae in clone () at ../sysdeps/unix/sysv/linux/i386/clone.S:114
[/FONT]
```

[COLOR=#242729][FONT=Arial]I tried to compare strace output with sudo and without - without sudo is being created problem thread dconf worker, but if run with sudo it thread is not being created and programm work correctly[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What can be done to fix this problem?[/FONT][/COLOR]

---

