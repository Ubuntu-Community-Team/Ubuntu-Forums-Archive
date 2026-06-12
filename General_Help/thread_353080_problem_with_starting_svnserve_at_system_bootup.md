---
title: "problem with starting svnserve at system bootup"
date: 2007-02-04
forum: General Help
---

### Post by mmistroni on 2007-02-04
hi all,
  i have just installed svn for my ubuntu  6.06
i'd like to start it automatically, so by following some posts on the net i found a suggestion to write a script in the /etc/init.d  directory called local with the following content

echo Starting subversion....
svnserve -d -r /home/marco/svn

but when system starts up i think this script is not getting invoked, as if i try to launch the command svn list svn://localhost  it says 'connection refused'

i tried too to use xinet.d, using following script named svnserve

service svnserve
{

port=3690
socket_type=stream
protocol=tcp
wait=no
user=marco
server=/usr/bin/svnserve
server_args= -i -r /home/marco/svn
}

but still the same happen when i try to launch the command svn list svn://localhost

and if i try to launch the command 
sudp ps auxx |fgrep svnserve  

no processes are shown


can anyone help me out?

thanks in advance and regards
 marco

---

### Post by mmistroni on 2007-02-04
ok i have sorted it out

i forgot to add my svnserve to system bootup with this command

 sudo update-rc.d svnserve defaults


regards
 marco

---

### Post by Sondar on 2008-02-27
Hi,

I just thought I'd follow up this thread, for the benefit of those who would like to start [FONT="Courier New"]svnserve[/FONT] via xinetd.

I, too, created the svnserve listed above (with paths, user, group, etc changed to suit my configuration) in the directory[FONT="Courier New"]/etc/xinetd.d[/FONT]. I then restarted xinet with the command

[FONT="Courier New"]sudo /etc/init.d/xinetd restart[/FONT]

and tried to connect to my repositories. Looking in the system log ([FONT="Courier New"]cat /var/log/syslog[/FONT]) gave me a clue as to the problem - I found a line similar to the following:

[FONT="Courier New"]xinetd[6889]: service/protocol combination not in /etc/services: svnserve/tcp[/FONT]

Checking the services with the command [FONT="Courier New"]cat /etc/services | grep 'svn'[/FONT] showed the following two lines:

[FONT="Courier New"]svn             3690/tcp        subversion      # Subversion protocol
svn             3690/udp        subversion[/FONT]

As hinted, the name of the xinetd config block has to match the name of a service in [FONT="Courier New"]/etc/services[/FONT], unless you use the declaration [FONT="Courier New"]type = UNLISTED[/FONT] in the config file. So as to match the service, but still mark this service as belonging to the server deamon, I changed my config file as follows:

```
service svn
{
    id          = svnserve
    *[ ... rest of original config file ... ]*
}

```

A quick restart of xinetd, and I was able to connect to the server without any problems.

---

