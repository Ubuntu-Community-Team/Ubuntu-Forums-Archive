---
title: "VMware 4.5.2 and clock skew on FreeBSD guest OS"
date: 2005-06-10
forum: General Help
---

### Post by jnichols959 on 2005-06-10
I'm running VMware Workstation 4.5.2 on kubuntu 5.0.4.  I need to run FreeBSD in a vm.  It runs fine except for the fact that the FreeBSD system clock is running over twice as fast as it should.  FreeBSD syncs via ntp when it boots then it proceeds to get ahead of the real time very quickly (about 2 seconds in guest time for evey second of host time).

I'm running a modified version of FreeBSD 4.9 that we're using internally to run a network device.  There's no room on it to install the vmware tools if that would help the situation.  This problem doesn't exist when I'm running the same VMware/FreeBSD stuff on Fedora Core 3.

Any thoughts?

---

### Post by jnichols959 on 2005-06-13
seeing how this was my work machine and i've seen no responses, i'm just going to stay on fedora core.  it's a bit of a disappointment cause i love apt and there seems to be a little more polish to some aspects of ubuntu.

cheers

---

### Post by Wombley on 2005-06-21
[QUOTE=jnichols959]seeing how this was my work machine and i've seen no responses, i'm just going to stay on fedora core.  it's a bit of a disappointment cause i love apt and there seems to be a little more polish to some aspects of ubuntu.

cheers[/QUOTE]

Possibly because this seems to be more of a VMware problem. You may like to try these links (found while looking for solution to another problem):

[http://lists.freebsd.org/pipermail/freebsd-questions/2005-May/086168.html](http://lists.freebsd.org/pipermail/freebsd-questions/2005-May/086168.html)
[http://www.vmware.com/support/kb/enduser/std_adp.php?p_sid=BxhaUjGh&p_lva=1692&p_faqid=1420&p_created=1093994398&p_sp=cF9zcmNoPTEmcF9ncmlkc29ydD0mcF9yb3dfY250PTQmcF9zZWFyY2hfdGV4dD1jbG9jayBydW5uaW5nIGZhc3QmcF9zZWFyY2hfdHlwZT03JnBfcHJvZF9sdmwxPTM3JnBfcHJvZF9sdmwyPTQwJnBfc29ydF9ieT1kZmx0JnBfcGFnZT0x&p_li=](http://www.vmware.com/support/kb/enduser/std_adp.php?p_sid=BxhaUjGh&p_lva=1692&p_faqid=1420&p_created=1093994398&p_sp=cF9zcmNoPTEmcF9ncmlkc29ydD0mcF9yb3dfY250PTQmcF9zZWFyY2hfdGV4dD1jbG9jayBydW5uaW5nIGZhc3QmcF9zZWFyY2hfdHlwZT03JnBfcHJvZF9sdmwxPTM3JnBfcHJvZF9sdmwyPTQwJnBfc29ydF9ieT1kZmx0JnBfcGFnZT0x&p_li=)

---

