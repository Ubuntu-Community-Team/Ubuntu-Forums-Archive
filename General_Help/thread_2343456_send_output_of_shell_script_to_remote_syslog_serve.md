---
title: "send output of shell script to remote syslog server"
date: 2016-11-16
forum: General Help
---

### Post by pratap-txt on 2016-11-16
Hi All,
      I have to send the output of a shell script to a remote syslog server.
      
      I am able to send the entire log coming in my local syslog to remote syslog server including the result of the script.

      But I am trying to find a way so that i can send only the result of my script to remote syslog server.

      My configuration in local machine /etc/rsyslog.d/50-default.conf:
       *.* @remote_syslog_server:514.

     Request you all to provide your suggestion on changing the configuration.

    Thanks
     Pratap

---

### Post by pratap-txt on 2016-11-16
sorry for bothering you all.. I got it, used a facility provided by logger in script file and its working now.Thanks!!!

---

### Post by ajgreeny on 2016-11-16
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

