---
title: "lightdm spinning up a user login"
date: 2019-11-30
forum: General Help
---

### Post by Skaperen on 2019-11-30
when a user that is _not yet logged in_ is first spun up by lightdm, is there a "_first script_" it calls, outside of _lightdm stuff_?  what i would like to do is shift the user to a _linux container_.  i think Xorg itself might need to stay running in the host (meaning, i need to extend the socket to reach X across the container boundary) but, i really am aiming to isolate the user in the container (for most users, but not for [COLOR=#800080]**[FONT=courier new]admin[/FONT]**[/COLOR]).

---

### Post by gnusci on 2019-12-01
Did you try reinstalling lightdm?

$ sudo apt-get install --reinstall lightdm ubuntu-desktop

---

### Post by Skaperen on 2019-12-02
no.  how will that help it login a user in a container?

---

### Post by #&amp;thj^% on 2019-12-02
Are you using Docker? How are you trying to use a container?

---

### Post by deadflowr on 2019-12-02
You could probably look back at how they did it for unity8
See the ppa for that here: [https://launchpad.net/~unity8-desktop-session-team/+archive/ubuntu/unity8-preview-lxc]("https://launchpad.net/~unity8-desktop-session-team/+archive/ubuntu/unity8-preview-lxc")
And here's a reference link to show it did add an entry to lightdm login:
[https://www.unixmen.com/install-unity-8-desktop-preview-with-mir-display-server-in-ubuntu/]("https://www.unixmen.com/install-unity-8-desktop-preview-with-mir-display-server-in-ubuntu/")

---

### Post by Skaperen on 2019-12-02
> **1fallen said:**
> Are you using Docker?

no, because Docker containers do not support direct management by scripts in the master host.

> **1fallen said:**
> How are you trying to use a container?

namespaces, cgroups, unshare.

---

### Post by #&amp;thj^% on 2019-12-02
> **Skaperen said:**
> no, because Docker containers do not support direct management by scripts in the master host.



namespaces, cgroups, unshare.

Understood.;) I think deadflowr's advice would be something to research.
Example:
```
lxc-start -n me
lxc-start: me: tools/lxc_start.c: main: 213 You lack access to /home/me/.local/share/lxc

```
also more information and usage: [https://linuxcontainers.org/lxc/manpages/man1/lxc-unshare.1.html](https://linuxcontainers.org/lxc/manpages/man1/lxc-unshare.1.html)
Found one more: [https://ericchiang.github.io/post/containers-from-scratch/](https://ericchiang.github.io/post/containers-from-scratch/)

---

### Post by Skaperen on 2019-12-02
> **deadflowr said:**
> You could probably look back at how they did it for unity8
See the ppa for that here: [https://launchpad.net/~unity8-desktop-session-team/+archive/ubuntu/unity8-preview-lxc](https://launchpad.net/~unity8-desktop-session-team/+archive/ubuntu/unity8-preview-lxc)
And here's a reference link to show it did add an entry to lightdm login:
[https://www.unixmen.com/install-unity-8-desktop-preview-with-mir-display-server-in-ubuntu/](https://www.unixmen.com/install-unity-8-desktop-preview-with-mir-display-server-in-ubuntu/)

unity8 compartmentalizes users into containers?

---

### Post by Skaperen on 2019-12-02
i just read that.  it looks like they are using containers to make a place to install unity, not compartmentalize users.  and i want to stick with Xorg for now.  i don't want to get into moving Xfre to Mir or whatever.

i think all i need is to know how lightdm starts up Xorg.  i guess i'll just have to wedge the Xorg executable and dump the process back trace and see what all is running.  that, or strace lightdm from the text console.

Xorg probably can't run in a container, anyway, due to lack of real console access.  so all i need to do is give the processes in the container the perception that Xorg is there.  but that only needs to communicate with X.

---

### Post by #&amp;thj^% on 2019-12-02
> **Skaperen said:**
> i just read that.  it looks like they are using containers to make a place to install unity, not compartmentalize users.  and i want to stick with Xorg for now.  i don't want to get into moving Xfre to Mir or whatever.

i think all i need is to know how lightdm starts up Xorg.  i guess i'll just have to wedge the Xorg executable and dump the process back trace and see what all is running.  that, or strace lightdm from the text console.

Xorg probably can't run in a container, anyway, due to lack of real console access.  so all i need to do is give the processes in the container the perception that Xorg is there.  but that only needs to communicate with X.
Just needs LXC installed, you don't have to do all that stuff.
The code I just showed you was on Arch with Mate DE.
Looks like a person could get very creative with LXC.
```
lxc(7)                                                                  lxc(7)

NAME
       lxc - linux containers

OVERVIEW
       The  container  technology is actively being pushed into the mainstream
       Linux kernel. It provides resource management  through  control  groups
       and resource isolation via namespaces.

       lxc,  aims to use these new functionalities to provide a userspace con&#8208;
       tainer object which provides full resource isolation and resource  con&#8208;
       trol for an applications or a full system.

       lxc  is  small  enough to easily manage a container with simple command
       lines and complete enough to be used for other purposes.

REQUIREMENTS
       The kernel version >= 3.10 shipped with the  distros,  will  work  with
       lxc, this one will have less functionalities but enough to be interest&#8208;
       ing.

       lxc relies on a set of functionalities  provided  by  the  kernel.  The
       helper script lxc-checkconfig will give you information about your ker&#8208;
       nel configuration, required, and missing features.

FUNCTIONAL SPECIFICATION
       A container is an object isolating some resources of the host, for  the
       application or system running in it.

       The  application / system will be launched inside a container specified
       by a configuration that is either initially created or passed as a  pa&#8208;
       rameter of the commands.

       How to run an application in a container

       Before  running  an application, you should know what are the resources
       you want to isolate. The default configuration is to isolate PIDs,  the
       sysv  IPC  and mount points. If you want to run a simple shell inside a
       container, a basic configuration is needed, especially if you  want  to
       share  the  rootfs.  If  you  want to run an application like sshd, you
       should provide a new network stack and a new hostname. If you  want  to
       avoid conflicts with some files eg.  /var/run/httpd.pid, you should re&#8208;
       mount /var/run with an empty directory. If you want to avoid  the  con&#8208;
       flicts  in  all  the cases, you can specify a rootfs for the container.
       The rootfs can be a directory tree, previously bind  mounted  with  the
       initial rootfs, so you can still use your distro but with your own /etc
       and /home

       Here is an example of directory tree for sshd:

       [root@lxc sshd]$ tree -d rootfs

       rootfs
       |-- bin
       |-- dev
       |   |-- pts
       |   `-- shm
       |       `-- network
       |-- etc
       |   `-- ssh
       |-- lib
       |-- proc
       |-- root
       |-- sbin
       |-- sys
       |-- usr
       `-- var
           |-- empty
           |   `-- sshd
           |-- lib
           |   `-- empty
           |       `-- sshd
           `-- run
               `-- sshd

       and the mount points file associated with it:

            [root@lxc sshd]$ cat fstab

            /lib /home/root/sshd/rootfs/lib none ro,bind 0 0
            /bin /home/root/sshd/rootfs/bin none ro,bind 0 0
            /usr /home/root/sshd/rootfs/usr none ro,bind 0 0
            /sbin /home/root/sshd/rootfs/sbin none ro,bind 0 0

       How to run a system in a container

       Running a system inside a container is paradoxically easier  than  run&#8208;
       ning  an application. Why? Because you don't have to care about the re&#8208;
       sources to be isolated, everything needs to be isolated, the other  re&#8208;
       sources  are  specified as being isolated but without configuration be&#8208;
       cause the container will set them up. eg.  the  ipv4  address  will  be
       setup  by  the system container init scripts. Here is an example of the
       mount points file:

            [root@lxc debian]$ cat fstab

            /dev /home/root/debian/rootfs/dev none bind 0 0
            /dev/pts /home/root/debian/rootfs/dev/pts  none bind 0 0

   CONTAINER LIFE CYCLE
       When the container is created, it contains the  configuration  informa&#8208;
       tion.  When  a  process is launched, the container will be starting and
       running. When the last process running inside the container exits,  the
       container is stopped.

       In  case  of  failure  when  the container is initialized, it will pass
       through the aborting state.

          ---------
         | STOPPED |<---------------
          ---------                 |
              |                     |
            start                   |
              |                     |
              V                     |
          ----------                |
         | STARTING |--error-       |
          ----------         |      |
              |              |      |
              V              V      |
          ---------    ----------   |
         | RUNNING |  | ABORTING |  |
          ---------    ----------   |
              |              |      |
         no process          |      |
              |              |      |
              V              |      |
          ----------         |      |
         | STOPPING |<-------       |
          ----------                |
              |                     |
               ---------------------

   CONFIGURATION
       The container is configured through a configuration file, the format of
       the configuration file is described in lxc.conf(5)

   CREATING / DESTROYING CONTAINERS
       A  persistent  container  object can be created via the lxc-create com&#8208;
       mand. It takes a container name as parameter and optional configuration
       file  and template. The name is used by the different commands to refer
       to this container. The lxc-destroy command will destroy  the  container
       object.

              lxc-create -n foo
              lxc-destroy -n foo

   VOLATILE CONTAINER
       It  is  not  mandatory to create a container object before starting it.
       The container can be directly started with a configuration file as  pa&#8208;
       rameter.

   STARTING / STOPPING CONTAINER
       When  the container has been created, it is ready to run an application
       / system. This is the purpose of the  lxc-execute  and  lxc-start  com&#8208;
       mands.  If  the  container was not created before starting the applica&#8208;
       tion, the container will use the configuration file passed as parameter
       to  the command, and if there is no such parameter either, then it will
       use a default isolation. If the application ended, the  container  will
       be  stopped, but if needed the lxc-stop command can be used to stop the
       container.

       Running an application inside a container is not exactly the same thing
       as  running a system. For this reason, there are two different commands
       to run an application into a container:

              lxc-execute -n foo [-f config] /bin/bash
              lxc-start -n foo [-f config] [/bin/bash]

       The lxc-execute command will run the specified command into a container
       via  an  intermediate process, lxc-init.  This lxc-init after launching
       the specified command, will wait for its end and all  other  reparented
       processes.  (to  support  daemons in the container). In other words, in
       the container, lxc-init has PID 1 and the first process of the applica&#8208;
       tion has PID 2.

       The  lxc-start  command  will directly run the specified command in the
       container. The PID of the first process is 1. If no command  is  speci&#8208;
       fied  lxc-start  will run the command defined in lxc.init.cmd or if not
       set, /sbin/init .

       To summarize, lxc-execute is for running an application  and  lxc-start
       is better suited for running a system.

       If  the  application is no longer responding, is inaccessible or is not
       able to finish by itself, a wild lxc-stop command  will  kill  all  the
       processes in the container without pity.

              lxc-stop -n foo -k

   CONNECT TO AN AVAILABLE TTY
       If  the  container is configured with ttys, it is possible to access it
       through them. It is up to the container to provide a set  of  available
       ttys  to  be used by the following command. When the tty is lost, it is
       possible to reconnect to it without login again.

              lxc-console -n foo -t 3

   FREEZE / UNFREEZE CONTAINER
       Sometime, it is useful to stop all the processes belonging  to  a  con&#8208;
       tainer, eg. for job scheduling. The commands:

              lxc-freeze -n foo

       will put all the processes in an uninteruptible state and

              lxc-unfreeze -n foo

       will resume them.

       This  feature is enabled if the freezer cgroup v1 controller is enabled
       in the kernel.

   GETTING INFORMATION ABOUT CONTAINER
       When there are a lot of containers, it is hard to follow what has  been
       created or destroyed, what is running or what are the PIDs running in a
       specific container. For this reason, the following commands may be use&#8208;
       ful:

              lxc-ls -f
              lxc-info -n foo

       lxc-ls lists containers.

       lxc-info gives information for a specific container.

       Here  is an example on how the combination of these commands allows one
       to list all the containers and retrieve their state.

              for i in $(lxc-ls -1); do
                lxc-info -n $i
              done

   MONITORING CONTAINER
       It is sometime useful to track the states of a container,  for  example
       to monitor it or just to wait for a specific state in a script.

       lxc-monitor command will monitor one or several containers. The parame&#8208;
       ter of this command accepts a regular expression for example:

              lxc-monitor -n "foo|bar"

       will monitor the states of containers named 'foo' and 'bar', and:

              lxc-monitor -n ".*"

       will monitor all the containers.

       For a container 'foo' starting, doing some work and exiting, the output
       will be in the form:

              'foo' changed state to [STARTING]
              'foo' changed state to [RUNNING]
              'foo' changed state to [STOPPING]
              'foo' changed state to [STOPPED]

       lxc-wait  command  will wait for a specific state change and exit. This
       is useful for scripting to synchronize the launch of a container or the
       end. The parameter is an ORed combination of different states. The fol&#8208;
       lowing example shows how to wait for a  container  if  it  successfully
       started as a daemon.

              # launch lxc-wait in background
              lxc-wait -n foo -s STOPPED &
              LXC_WAIT_PID=$!

              # this command goes in background
              lxc-execute -n foo mydaemon &

              # block until the lxc-wait exits
              # and lxc-wait exits when the container
              # is STOPPED
              wait $LXC_WAIT_PID
              echo "'foo' is finished"

   CGROUP SETTINGS FOR CONTAINERS
       The  container  is  tied  with  the control groups, when a container is
       started a control group is created and associated with it. The  control
       group properties can be read and modified when the container is running
       by using the lxc-cgroup command.

       lxc-cgroup command is used to set or  get  a  control  group  subsystem
       which  is associated with a container. The subsystem name is handled by
       the user, the command won't do any syntax  checking  on  the  subsystem
       name, if the subsystem name does not exists, the command will fail.

              lxc-cgroup -n foo cpuset.cpus

       will display the content of this subsystem.

              lxc-cgroup -n foo cpu.shares 512

       will set the subsystem to the specified value.

SEE ALSO
       lxc(7),  lxc-create(1), lxc-copy(1), lxc-destroy(1), lxc-start(1), lxc-
       stop(1), lxc-execute(1), lxc-console(1),  lxc-monitor(1),  lxc-wait(1),
       lxc-cgroup(1),  lxc-ls(1), lxc-info(1), lxc-freeze(1), lxc-unfreeze(1),
       lxc-attach(1), lxc.conf(5)

AUTHOR
       Daniel Lezcano <daniel.lezcano@free.fr>

       Christian Brauner <christian.brauner@ubuntu.com>

       Serge Hallyn <serge@hallyn.com>

       Stéphane Graber <stgraber@ubuntu.com>

Version 3.2.1                     2019-10-09                            lxc(7)
```

---

### Post by Skaperen on 2019-12-02
**lxc** cannot move an existing process to a container.  only that process can move itself (with the appropriate syscalls).  **lxc** can launch new processes (and do usual things like _setuid()_) there, from a process that created the container or moved into it.  but that's not my plan.

i don't have any use for **lxc** even though it may actually be able to accomplish the task.  i already do containers without it.  using some other software, just because it exists and is widely used, to do what i already do for myself, means i add new dependencies for maintenance.  OTOH, if someone has completed exactly the same thing, as i am planning to do, with **lxc** or **docker**, then that would be very interesting and could save me a lot of time.  but digging into a project that achieves a completely different goal would cost me a lot of time.

i should not have mentioned _containers_ as it has distracted from my original question which remains unanswered.  please, let's get off talking about _containers_.

---

### Post by #&amp;thj^% on 2019-12-03
> **Skaperen said:**
> 
i should not have mentioned _containers_ as it has distracted from my original question which remains unanswered.  please, let's get off talking about _containers_.

No more talk of containers then.:p
Good Luck though.

---

### Post by deadflowr on 2019-12-03
Which part do you want to know more about what's going on,
before the login screen or after the login-screen?

---

### Post by Skaperen on 2019-12-03
it would have to be after the login screen because it has to be after the user is identified and authenticated (when appropriate).  it might need to be before Xorg is started because i might need to reconfigure it to use real network connectivity, but at least before the user's DE gets started  since that will need to be started in the per-user cont----r specially configured with some form (maybe overlay) of duplication mount(s).  this can potentially let me put specific users in specific versions of ubuntu or their DE.

---

