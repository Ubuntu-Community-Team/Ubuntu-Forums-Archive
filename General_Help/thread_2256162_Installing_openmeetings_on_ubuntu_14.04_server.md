---
title: "Installing openmeetings on ubuntu 14.04 server"
date: 2014-12-10
forum: General Help
---

### Post by tadewosa on 2014-12-10
Is there anyone who is successful in installing openmeetings on Ubuntu 14.04 server? I’m struggling for more than a month in trying to install it. But with no avail. 
I would be very thankful if I get a step by step instruction.

Thank you in advance

---

### Post by TheFu on 2014-12-10
I haven't tried, but we did find a pre-built virtual machine image with everything already setup. That might be easier.

---

### Post by tadewosa on 2014-12-10
How can I get the "pre-built virtual machine image"?

---

### Post by TheFu on 2014-12-10
> **tadewosa said:**
> How can I get the "pre-built virtual machine image"?

Use internet search to find it based on the hypervisor you will use.  Or just look for "openmeetings appliance" - that is probably best.

This technique also decouples the OS version required for the application from the version you have installed currently. Virtualization is amazing for that.

OTOH, if you absolutely must use 14.04, then this probably doesn't help, at least just yet.  Enterprise software normally takes about a year to become supported post-release. At least that has been my experience - still waiting for 14.04 support for a number of enterprise tools we use here.

---

### Post by tadewosa on 2014-12-10
> **TheFu said:**
> Use internet search to find it based on the hypervisor you will use.  Or just look for "openmeetings appliance" - that is probably best.

This technique also decouples the OS version required for the application from the version you have installed currently. Virtualization is amazing for that.

OTOH, if you absolutely must use 14.04, then this probably doesn't help, at least just yet.  Enterprise software normally takes about a year to become supported post-release. At least that has been my experience - still waiting for 14.04 support for a number of enterprise tools we use here.

Thank you. I really want to use openmeetings for a community based online interactive tutoring for school children. The venture is to run online classes using openmeetings (as an open source) on Ubuntu server. If there are other options I am ready to consider.

---

### Post by TheFu on 2014-12-10
So I've been searching for the appliance you need and haven't found any!  Is Big Blue Button an option? [https://code.google.com/p/bigbluebutton/wiki/BigBlueButtonVM](https://code.google.com/p/bigbluebutton/wiki/BigBlueButtonVM)   VMDK files can be used by other hypervisors, FYI.

For other virtual appliances - [http://www.turnkeylinux.org/](http://www.turnkeylinux.org/)

---

### Post by tadewosa on 2014-12-10
> **TheFu said:**
> So I've been searching for the appliance you need and haven't found any!  Is Big Blue Button an option? [https://code.google.com/p/bigbluebutton/wiki/BigBlueButtonVM](https://code.google.com/p/bigbluebutton/wiki/BigBlueButtonVM)   VMDK files can be used by other hypervisors, FYI.

For other virtual appliances - [http://www.turnkeylinux.org/](http://www.turnkeylinux.org/)

Thank you very much indeed

---

