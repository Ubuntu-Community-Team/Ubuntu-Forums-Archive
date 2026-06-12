---
title: "SQLDeveloper Crashing"
date: 2008-04-10
forum: General Help
---

### Post by cnolan011 on 2008-04-10
I have SQLDeveloper installed and when I actually connect a database SQLDeveloper crashes and the following appears:


#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xac8801be, pid=29156, tid=2888121232
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_15-b04 mixed mode, sharing)
# Problematic frame:
# C  [libclntsh.so.10.1+0x3491be]
#
# An error report file with more information is saved as hs_err_pid29156.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/home/cnolan/sqldeveloper/sqldeveloper/bin/../../ide/bin/launcher.sh: line 478: 29156 Aborted                 (core dumped) ${JAVA} ${APP_VM_OPTS} ${APP_SCRIPT_USER_HOME} ${APP_ENV_VARS} -classpath ${APP_CLASSPATH} ${APP_MAIN_CLASS} ${APP_APP_OPTS}

---

### Post by cnolan011 on 2008-04-11
FIXED
link below gives solution

[http://forums.oracle.com/forums/thread.jspa?messageID=2458362&#2458362](http://forums.oracle.com/forums/thread.jspa?messageID=2458362&#2458362)

---

