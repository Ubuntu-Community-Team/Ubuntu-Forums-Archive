---
title: "Wanting to run a command on Boot (post network) and another on shutdown"
date: 2017-01-13
forum: General Help
---

### Post by Neill_R on 2017-01-13
Wanting to run a command on Boot (post network) and another on shutdown

hello

Ubuntu 16.04.1 server. During the boot process I want a command to run once the networking is up. The user neill is the account of the ubuntu installer.

please clarify is systemd or upstart the way to do it?

boot 
```


[SIZE=1] /usr/lib/virtualbox/VBoxManage startvm /home/neill/VirtualBox\ VMs/Domain_Controller/Domain_Controller.vbox --type headless[/SIZE]


```

and on shut down

```


[SIZE=1]/usr/lib/virtualbox/VBoxManage controlvm /home/neill/VirtualBox\ VMs/Domain_Controller/Domain_Controller.vbox savestate[/SIZE]


```

---

### Post by SeijiSensei on 2017-01-13
For startup, the easiest solution is to put the command in the file /etc/rc.local, which is run with root privileges at the end of the boot sequence.

I've not run a custom command at shutdown, but you might able to add it to /etc/init.d/vboxautostart-service.  I'd put it after the "start-stop-daemon" command in this stanza:
```

if [ "$system" = "debian" ]; then
    start_daemon() {
        usr="$1"
        shift
        bin="$1"
        shift
        start-stop-daemon --background --chuid $usr --start --exec $bin -- $@
    }
    killproc() {
        start-stop-daemon --stop --exec $@
        **/usr/lib/virtualbox/VBoxManage controlvm /home/neill/VirtualBox\ VMs/Domain_Controller/Domain_Controller.vbox savestate**
    }
    if [ -n "$NOLSB" ]; then
        fail_msg() {
            echo " ...fail!"
        }
        succ_msg() {
            echo " ...done."
        }
        begin_msg() {
            echo -n "$1"
       }
    fi

fi

```

Let us know if that works.

---

