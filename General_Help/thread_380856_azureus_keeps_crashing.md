---
title: "azureus keeps crashing"
date: 2007-03-10
forum: General Help
---

### Post by didijeeeke on 2007-03-10
Hi

I have installed azureus with synaptic.
It did work for like one hour but now each time i start azureus it runs 1 second and then it crashes.

I started azureus in console to get the debug output.

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb0432d02, pid=6748, tid=3085080240
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]
#
# An error report file with more information is saved as hs_err_pid6748.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)


I hope you guys can help me.

---

### Post by Famicommie on 2007-03-10
I had all kinds of problems with Azureus when I installed it via Synaptic. Try installing it through Automatix instead. It'll work (almost) like a charm.

The (almost) is because it will not be able to automatically install azureus updates. In order to get the autoupdate feature to work, open up a terminal and type

```
sudo chmod -R 777 /opt/azureus
```
to make everything work perfectly

---

### Post by didijeeeke on 2007-03-10
thanks but it did not work o and azureus was located in /usr/share/azureus/

---

