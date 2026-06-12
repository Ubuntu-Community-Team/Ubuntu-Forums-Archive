---
title: "Ubuntu 18.04 Screen goes black and then resumes"
date: 2020-07-11
forum: General Help
---

### Post by Robbyx on 2020-07-11
The screen goes black only for about 5 secs. It happens randomly during normal use not at startup.  Mostly it is when running streaming video, but also other times. 

The video comes from the AMD asrock fm2Abbx extreme6+ motherboard. Ram is 15gb

Looking in the syslog for errors shows a batch of these type errors:

```
Failed to enumerate children of /var/tmp/systemd-private-560533a150b34256b7fcb6305eb60ed5-fwupd.service-xi5u78: Error opening directory '/var/tmp/systemd-private-560533a150b34256b7fcb6305eb60ed5-fwupd.service-xi5u78': Permission denied

```
/var/tmp/systemd-private-... directories are owned by root, with only owner having right to access. 

Other errors were:

```
Jul 11 08:19:39 rob-desktop kernel: [    8.314326] ACPI Error: Aborting method \_SB.PCI0.VGA.ATC0 due to previous error (AE_NOT_FOUND) (20200326/psparse-529)
Jul 11 08:19:39 robins-desktop kernel: [    8.314374] ACPI Error: Aborting method \_SB.PCI0.VGA.ATCS due to previous error (AE_NOT_FOUND) (20200326/psparse-529)

```
There were more errors but they did not look associated with video/ screen failure. 


Searching for CRITICAL I found repeats of the following:

gnome-session[2093]: gnome-session-binary[2093]: WARNING: Lost name on bus: org.gnome.SessionManager
Jul 11 02:02:14 rob-desktop gnome-session[2093]: gnome-session-binary[2093]: CRITICAL: We failed, but the fail whale is dead. Sorry....

How do I correct  the cause of the black screen?

---

### Post by Robbyx on 2020-08-01
Does any one have a solution to this random black screen?

---

### Post by gdesilva on 2020-08-02
Hi, I did encounter a similar problem but in my case I am using a dual monitor set up - one monitor on the HDMI port and the other on the DVI port and the issue turned out to be due to a loose connection on the DVI port. Once I plugged the cables securely the problem went away. Worth checking your physical connections just to make sure it is all securely plugged in. Just an idea.

---

### Post by riccardosl45 on 2020-08-29
Same issue here, still not able to fix:
HW: HP 840 G1
  SW: Ubuntu 18.04 LTS

---

