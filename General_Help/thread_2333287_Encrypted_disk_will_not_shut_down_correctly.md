---
title: "Encrypted disk will not shut down correctly"
date: 2016-08-08
forum: General Help
---

### Post by JayBurrill on 2016-08-08
Recently, when I attempt to shut down my Dell Latitude E6530 with 16.04 encrypted on a 256GB SSD, the system will not shut down when requested.  Rather the following occurrs:
[LIST=1]
[*]Shutdown is requested
[*]As the system shutdown proceeds with the screen black, error messages are flashed
[*]POST begins
[*]GRUB launches
[*]When Ubuntu is selected from GRUB, sda5_crypt is challenged
[*]The 16.04 Login is raised
[*]The system halts with the user loigged in
[/LIST]

That might be OK.  But when the system is restarted, the system does not POST into GRUB.  Rather, it POSTS directly into the 16.04 Unity GUI as the logged in user!

This is all making me very uneasy.  First, I encrypted the disk for a reason - to protect data.  Although the restart does still ask for sda5_crypt credentials, the GUI login is bypassed, so security is really compromised.


/Jay

---

### Post by wildmanne39 on 2016-08-09
*Thread moved to **General Help**.*

---

### Post by JayBurrill on 2016-09-07
And as this persists, the Restart will actually seem to Hibernate.  The Sytem begins to restart, first GRUB, then Disk Decrypt, then Login.  But instead of finishing with the GUI displayed, the system shut down.  I suspect that it is Hibernating, as when I restart, the system loads directly to the OS.  Sort of like passing Go without collecting $200.

---

### Post by JayBurrill on 2016-09-14
And as this continues, even more odd behaviors arise.  Now, quite frequently, when my system powers off the display, and is supposed to present the login screen when it awakes, it does not.  Instead, the monitors light up right where the left off, and only after 5-10 seconds is the login screen raised.  Seriously?

---

### Post by JayBurrill on 2016-09-14
I do not know if, in fact, these issues are due to the disk encryption.  Or, if it is related to using a docking station.  But since it can take 5-10 minutes to finally get the machine to shut down cleanly, I thought it worth raising the discussion.  And messages displayed during the process did note disk or I/O issues, so I suspected it was something to do with the SSD, perhaps encryption.

I guess I need to learn how to entitle to bring awareness to my issue(s).

---

### Post by JayBurrill on 2016-09-14
And did I mention Hibernate or Suspend was equally impacted?  Either of these commands can put you into a cycle where, rather than suspending in one or the other fashion, the system reboots to a login.  Usually after a login it will suspend or hibernate.  But occasionally the POST/login routine repeats until the dust finally settles and it decides it can indeed suspend or hibernate.

---

### Post by JayBurrill on 2016-09-16
My speculation here, since there is no other input, is that this is not disk related.  I returned to my office after a long absence, and my system started and shut down normally.  I use a similar setup in both places, a dock attached to two external monitors.  However, at home I share those monitors (and keyboard) with my home PC.  So I use an old Belkin KVM for that purpose.  I will mark this ars resolved (or canceled if you allow) since I think that trhe issue is not specific to Ubuntu, necessarily.  Thanks for all of the help.

---

