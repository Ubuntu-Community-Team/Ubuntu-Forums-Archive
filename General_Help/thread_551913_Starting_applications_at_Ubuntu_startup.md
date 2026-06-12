---
title: "Starting applications at Ubuntu startup"
date: 2007-09-15
forum: General Help
---

### Post by mmistroni on 2007-09-15
hello all,

i am trying to use a continuous integration server named Continuum (Apache Continuum), and i
want to start it automatically when Ubuntu loads up
I am using Dapper Drake.
my continuum is installed in  /opt/continuum-1.0.3.
to start it up, there's a script in /opt/continuum-1.0.3/bin/linux/run.sh by passing the argument console
so i have created a continuum script in my etc/xinet.d directory with following content

service continuum
{

port=3691
socket_type=stream
protocol=tcp
wait=no
user=marco
server=/opt/continuum-1.0.3/bin/linux/run.sh
server_args= console
}

but when i restart Ubuntu, it looks like this script is not being invoked, as the application is not started up automatically....

could anyone help me out?

thanks in advance and regards
  marco

---

### Post by HermanAB on 2007-09-15
Xinetd is a super daemon that starts other daemons upon request. In other words, someone has to try to connect to the port of that application, to cause xinetd to start it.

You may want to launch your server using the init system, the inittab system or rc.local instead.

'Hope that helps!

H.

---

