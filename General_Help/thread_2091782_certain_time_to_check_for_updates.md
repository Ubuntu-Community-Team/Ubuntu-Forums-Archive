---
title: "certain time to check for updates?"
date: 2012-12-06
forum: General Help
---

### Post by badman35 on 2012-12-06
I would very much like to setup a time to check for updates on all four of my ubuntu systems is their a way to do that? oh they all are 12.04.1

---

### Post by MoebusNet on 2012-12-07
I am not aware of any way to do that with the GUI for Update Manager (renamed to Software Updater for 12.11).

However if you really need that functionality, have a look at:

[https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo](https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo)

Perhaps cron-apt and/or anacron would fill the bill for you. Read, research and back-up as always.

---

### Post by Kirk Schnable on 2012-12-07
> **MoebusNet said:**
> I am not aware of any way to do that with the GUI for Update Manager (renamed to Software Updater for 12.11).

However if you really need that functionality, have a look at:

[https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo](https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo)

Perhaps cron-apt and/or anacron would fill the bill for you. Read, research and back-up as always.

I'll second this. We are thinking about using cron-apt in the next Linux image we deploy at work.

---

### Post by dcstar on 2012-12-08
> **badman35 said:**
> I would very much like to setup a time to check for updates on all four of my ubuntu systems is their a way to do that? oh they all are 12.04.1

**/etc/cron.daily/apt** is run at a random time during the day or straight after restart by anacron.

Move this script out of this folder and run it specifically at a certain time using a cron job.

---

### Post by badman35 on 2013-06-07
I still need help with this reason being is I have EXEDE satelite internet and I get free unmetered download time from midnite to five am and I want ubuntu to download its updates in that time frame and not when ever it wants to.

---

