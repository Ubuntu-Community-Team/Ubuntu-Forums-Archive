---
title: "crontab on ubuntu core"
date: 2019-07-16
forum: General Help
---

### Post by matteoraggi on 2019-07-16
on raspbian I was using cronjob, but on ubuntu core we have timer, are there soem snaps or easy documentations about it?

---

### Post by #&amp;thj^% on 2019-07-16
Kind of vague in dscription, but:
```
CRONTAB(1)                       User Commands                      CRONTAB(1)

NAME
       crontab - maintains crontab files for individual users

SYNOPSIS
       crontab [-u user] <file | ->
       crontab [-u user] <-l | -r | -e> [-i] [-s]
       crontab -n [ hostname ]
       crontab -c
       crontab -V

DESCRIPTION
       Crontab  is the program used to install a crontab table file, remove or
       list the existing tables used to serve the cron(8) daemon.   Each  user
       can  have their own crontab, and though these are files in /var/spool/,
       they are not intended to be edited directly.  For SELinux in MLS  mode,
       you can define more crontabs for each range.  For more information, see
       selinux(8).

       In this version of Cron it is possible to use a network-mounted  shared
       /var/spool/cron  across a cluster of hosts and specify that only one of
       the hosts should run the crontab jobs in the  particular  directory  at
       any  one  time.  You may also use crontab(1) from any of these hosts to
       edit the same shared set of crontab files, and to set and  query  which
       host should run the crontab jobs.

       Running  cron  jobs  can  be allowed or disallowed for different users.
       For this purpose, use the  cron.allow  and  cron.deny  files.   If  the
       cron.allow  file  exists,  a user must be listed in it to be allowed to
       use cron If the cron.allow file does not exist but the  cron.deny  file
       does exist, then a user must not be listed in the cron.deny file in or&#8208;
       der to use cron.  If neither of these files exists, only the super user
       is  allowed  to use cron.  Another way to restrict access to cron is to
       use PAM authentication in /etc/security/access.conf to  set  up  users,
       which  are  allowed  or disallowed to use crontab or modify system cron
       jobs in the /etc/cron.d/ directory.

       The temporary directory can be set in an environment variable.   If  it
       is not set by the user, the /tmp directory is used.

OPTIONS
       -u     Specifies  the name of the user whose crontab is to be modified.
              If this option is not used,  crontab  examines  "your"  crontab,
              i.e.,  the  crontab  of  the person executing the command. If no
              crontab exists for a particular user, it is created for him  the
              first time the crontab -u command is used under his username.

       -l     Displays the current crontab on standard output.

       -r     Removes the current crontab.

       -e     Edits the current crontab using the editor specified by the VIS&#8208;
              UAL or EDITOR environment variables.  After you  exit  from  the
              editor, the modified crontab will be installed automatically.

       -i     This  option  modifies  the  -r  option to prompt the user for a
              'y/Y' response before actually removing the crontab.

       -s     Appends the  current  SELinux  security  context  string  as  an
              MLS_LEVEL  setting to the crontab file before editing / replace&#8208;
              ment occurs - see the documentation of MLS_LEVEL in crontab(5).

       -n     This option is relevant only if cron(8) was started with the  -c
              option,  to  enable  clustering  support.  It is used to set the
              host in the cluster which should run the jobs specified  in  the
              crontab  files  in the /var/spool/cron directory.  If a hostname
              is supplied, the host whose hostname returned by  gethostname(2)
              matches  the  supplied hostname, will be selected to run the se&#8208;
              lected cron jobs subsequently.  If there is no host in the clus&#8208;
              ter matching the supplied hostname, or you explicitly specify an
              empty hostname, then the selected jobs will not be run  at  all.
              If  the hostname is omitted, the name of the local host returned
              by gethostname(2) is used.  Using this option has no  effect  on
              the  /etc/crontab  file  and the files in the /etc/cron.d direc&#8208;
              tory, which are always run, and considered  host-specific.   For
              more information on clustering support, see cron(8).

       -c     This  option is only relevant if cron(8) was started with the -c
              option, to enable clustering support.  It is used to query which
              host  in  the cluster is currently set to run the jobs specified
              in the crontab files in the directory /var/spool/cron ,  as  set
              using the -n option.

       -V     Print version and exit.

SEE ALSO
       crontab(5), cron(8)

FILES
       /etc/cron.allow
       /etc/cron.deny

STANDARDS
       The  crontab  command  conforms to IEEE Std1003.2-1992 (``POSIX'') with
       one exception: For replacing the current crontab with data  from  stan&#8208;
       dard  input  the  -  has to be specified on the command line.  This new
       command syntax differs from previous versions of Vixie Cron, as well as
       from the classic SVR3 syntax.

DIAGNOSTICS
       An informative usage message appears if you run a crontab with a faulty
       command defined in it.

AUTHOR
       Paul Vixie &#10216;vixie@isc.org&#10217;
       Colin Dean &#10216;colin@colin-dean.org&#10217;

cronie                            2012-11-22                        CRONTAB(1)
```
Man pages are very useful: [https://manpages.ubuntu.com/](https://manpages.ubuntu.com/)
Also: [https://help.ubuntu.com/community/man](https://help.ubuntu.com/community/man)

---

### Post by matteoraggi on 2019-07-17
No, crontab is read only on ubuntu core, here the solution, thanks: [https://forum.snapcraft.io/t/how-to-manage-timers-cronjob-on-ubuntu-core/12323](https://forum.snapcraft.io/t/how-to-manage-timers-cronjob-on-ubuntu-core/12323)

---

### Post by #&amp;thj^% on 2019-07-17
If this is Solved, would you mark as [Solved]

---

### Post by matteoraggi on 2019-07-17
I need time to check the solution, also days or weeks. then I will be happy to write resolved, thanks.

---

