---
title: "VMWare Workstation, Ubuntu and Powerpoint"
date: 2007-06-12
forum: General Help
---

### Post by Strider42 on 2007-06-12
Hi,

Having had no luck with a response from the VMWare forums I'll try here.

I'm running VMWare Workstation 6 on a Ubuntu 7.04 box with Win XP Pro as the guest op system. VM build is 6.0.0-build-45731 and XP is full patched as is Ubuntu.

When I open a chart in PowerPoint in the guest XP VM that has been created by a co-worker on a straight Win XP machine and then close it, even without actually making changes, the fonts become very ragged at the edges, and thus rendered useless. This only happens when editing charts. Text boxes, headers and footers etc. render OK.

Has anyone had this problem and found a workaround, or have any ideas what might be causing the problem?

Many thanks in advance.

---

### Post by hikaricore on 2007-06-12
Just a thought.  Have you properly installed the VMWare Tools on your guest OS?

Other than that I'm not sure, perhaps video performance issues are causing this.

---

### Post by Strider42 on 2007-06-12
Hi hikaricore

Yes, VMWare Tools installed and updated to latest.  It's really odd.  I'm seeing it on 3 machines now too, all with different hardware configs.

---

### Post by hikaricore on 2007-06-12
It could be a bug with VMware.

Have you tried any other VM software?

[VirtualBox]("http://www.virtualbox.org/wiki/Downloads") now supports (if I'm not mistake) VMware virtual machines and has Ubuntu Feisty packages up for download.  ^_^

Might be worth lookin into.

---

